# Методические указания по выполнению лабораторной работы №2

## Работа с PostgreSQL

Процесс запуска и настройки PostgreSQL в Docker-контейнере при помощи docker-compose подробно описан в [соответствующих методических указаниях](../lab2-db/README.md).

При объяснении интеграции Python и Django с PostgreSQL я буду исходить из того, что сам PostgreSQL у вас уже поднят и доступен для подключения.

## Работа с PostgreSQL из Python

Для начала разберём пример работы с PostgreSQL из Python **без Django ORM**.

Установим при помощи пакетного менеджера `pip` пакет `psycopg2-binary`, который содержит классы и функции для взаимодействия с PostgreSQL:

```shell
pip install psycopg2-binary
```

Создадим в нашей БД таблицу `books`:

```sql
CREATE TABLE books (
    id SERIAL PRIMARY KEY,
    name VARCHAR(30) NOT NULL,
    description VARCHAR(255) NOT NULL
);
```

Напишем небольшой скрипт, который:
1. Подключается к БД
2. Добавляет новую запись в таблицу в таблицу `books`

```python
import psycopg2


conn = psycopg2.connect(
            host="localhost",
            port="5432",
            user="postgres",
            password="postgres",
            dbname="postgres")

cursor = conn.cursor()

query = "INSERT INTO books (id, name, description) VALUES(1, 'Мастер и Маргарита', 'Крутая книга')"

cursor.execute(query)

conn.commit()

cursor.close()
conn.close()
```

## Работа с Django ORM

Django ORM позволяет работать с БД как с Python-объектами, что облегчает и ускоряет разработку. Однако стоит помнить, что в некоторых случаях сложные SQL-запросы, составленные при помощи ORM, могут быть менее оптимальны, чем составленные разработчиком вручную.

С полными возможностями Django ORM можно ознакомиться в [официальной документации](https://docs.djangoproject.com/en/5.1/topics/db/).

Перейдем к рассмотрению возможностей Django ORM для решения задач лабораторной работы. Возьмём за основу проект, созданный в рамках [предыдущей лабораторной работы](../lab1-py/lab1_tutorial.md) и добавим в него интеграцию с PostgreSQL.

Разобьём всю работу на 5 этапов:

1. Реализация без Django ORM
2. Настройка подключения к БД и создание модели услуг
3. Создание моделей заявок и модели для связи many-to-many (услуги в заявке)
4. Получение данных об услуге при помощи курсора
5. Удаление и фильтрация услуг

Для простоты объяснения выберем предметную область "Интернет-магазин". Услуги - товары, заявки - заказы, который собирает и оформляет покупатель.

### Реализация без Django ORM

#### База

**Структура проекта**

```
.
├── bmstu
│   ├── asgi.py
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── bmstu_lab
│   ├── admin.py
│   ├── apps.py
│   ├── __init__.py
│   ├── migrations
│   │   ├── __init__.py
│   ├── models.py
│   ├── templates
│   │   ├── base.html
│   │   ├── product.html
│   │   └── products_list.html
│   ├── tests.py
│   └── views.py
├── db.sqlite3
└── manage.py
```

**urls.py**

```python
from django.contrib import admin
from django.urls import path

from bmstu_lab import views


urlpatterns = [
    path('admin/', admin.site.urls),
    path('products/', views.get_products_list_page, name='products_list'),
    path('products/<int:id>/', views.get_product_page, name='product'),
]
```

**base.html**
```html
<!doctype html>
<html lang="en" class="h-100">
<head>
    <meta charset="utf-8">
    <title>{% block title %}{% endblock %}</title>
</head>
<body>
<div class="container">
    {% block content %}{% endblock %}
</div>
</body>
</html>
```

**views.py**

```python
PRODUCTS_LIST = [
    {
        "id": 1,
        "title": "Хлеб",
        "price": 35,
    },
    {
        "id": 2,
        "title": "Молоко",
        "price": 80,
    },
    {
        "id": 3,
        "title": "Сыр",
        "price": 300,
    },
    {
        "id": 4,
        "title": "Колбаса",
        "price": 500,
    }
]

ITEMS_IN_CART = 2
```

#### Список услуг

**views.py**
```python
def get_products_list_page(request):
    """
    Получение страницы списка товаров
    """

    return render(request,
                  'products_list.html',
                  {
                      "data": {
                          "products": PRODUCTS_LIST,
                          "items_in_cart": ITEMS_IN_CART,
                      }
                  })
```

**products_list.html**
```html
{% extends 'base.html' %}

{% block title %}Товары{% endblock %}

{% block content %}
    Корзина [{{ data.items_in_cart }}]
    <h1>Список товаров</h1>
    <ul>
    {% for product in data.products %}
            <li><a href="{% url 'product' product.id %}">{{ product.title }}</a> - {{ product.price }} руб.</li>
        {% empty %}
            Товаров нет
        {% endfor %}
    </ul>
{% endblock %}
```
#### Страница услуги

**views.py**
```python
def get_product_page(request, id):
    """
    Получение страницы товара
    """

    for product in PRODUCTS_LIST:
        if product["id"] == id:
            return render(request,
                          "product.html",
                          {
                              "data": product
                          })
    return render(request, "product.html")
```

**product.html**
```html
{% extends 'base.html' %}

{% block title %}Товар{% endblock %}

{% block content %}
    <h1>Информация о товаре "{{ data.title }}"</h1>
    <li>Название: <strong>{{ data.title }}</strong></li>
    <li>Цена: <strong>{{ data.price }} руб.</strong></li>
{% endblock %}
```


### Настройка подключения к БД и создание модели услуг

Добавим подключение к PostgreSQL.

Для этого в **settings.py** необходимо указать:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'postgres',
        'USER': 'postgres',
        'PASSWORD': 'postgres',
        'HOST': 'localhost',
        'PORT': 5432,
    }
}
```

После чего применим автоматически созданные миграции Django:

```shell
python3 manage.py migrate
```

Добавим модель товара (услуги) в **models.py**:

```python
from django.db import models

class Product(models.Model):
    title = models.CharField(max_length=255)
    price = models.DecimalField(max_digits=10, decimal_places=2)
    is_active = models.BooleanField(default=True)

    def __str__(self):
        return self.title
```

Создадим миграцию:

```shell
python3 manage.py makemigrations
```

И применим её:

```shell
python3 manage.py migrate
```

Добавим товары в таблицу SQL-запросом:

```sql
INSERT INTO public.bmstu_lab_product (id, title, price, is_active) VALUES
(1, 'Хлеб', 35, True),
(2, 'Молоко', 80, True),
(3, 'Сыр', 300, True),
(4, 'Колбаса', 500, True);
```

И перепишем метод получения страницы списка товаров при помощи Django ORM в **views.py**:

```python
def get_products_list_page(request):
    """
    Получение страницы списка товаров
    """

    return render(request,
                  'products_list.html',
                  {
                      "data": {
                          "products": Product.objects.all(),
                          "items_in_cart": ITEMS_IN_CART,
                      }
                  })
```

### Создание моделей заявок и связи связи услуги-заявки

Добавим 2 оставшиеся модели (заявок и связи услуги-заявки) в файл **models.py**

```python
from django.contrib.auth.models import User

# ...

class Order(models.Model):
    class RequestStatus(models.TextChoices):
        DRAFT = "DRAFT"
        DELETED = "DELETED"
        FORMED = "FORMED"
        COMPLETED = "COMPLETED"
        REJECTED = "REJECTED"

    status = models.CharField(
        max_length=10,
        choices=RequestStatus.choices,
        default=RequestStatus.DRAFT,
    )

    creation_datetime = models.DateTimeField(auto_now_add=True)
    formation_datetime = models.DateTimeField(blank=True, null=True)
    completion_datetime = models.DateTimeField(blank=True, null=True)
    client = models.ForeignKey(User, on_delete=models.CASCADE, related_name='created_requests')
    manager = models.ForeignKey(User, on_delete=models.CASCADE, related_name='managed_requests', blank=True, null=True)

    def __str__(self):
        return str(self.id)


class ProductInOrder(models.Model):
    order = models.ForeignKey(Order)
    product = models.ForeignKey(Product)
    quantity = models.CharField(max_length=255)

    def __str__(self):
        return f"{self.request_id}-{self.software_id}"

    class Meta:
        unique_together = ('order', 'product'),
```

Не забываем создать и применить миграции!

Поскольку в одной заявке не может быть 2 одинаковых услуги, зададим это ограничение:

```python
    class Meta:
        unique_together = ('order', 'product'),
```

Перепишем метод получения страницы товаров:

```python
def get_products_list_page(request):
    """
    Получение страницы списка товаро
    """

    USER_ID = 1
    draft_order = Order.objects.filter(client_id=USER_ID,
                                   status=Order.RequestStatus.DRAFT).first()
    return render(request,
                  'products_list.html',
                  {
                      "data": {
                          "products": Product.objects.all(),
                          "items_in_cart": (get_items_in_request(draft_order.id) if draft_order is not None else 0),
                      }
                  })
```

Создадим супер-пользователя командой:

```shell
python3 manage.py createsuperuser
```

При помощи SQL-запросов можно создать черновик заявки для этого пользователя и добавить в него товара.

### Получение данных при помощи курсора

Перепишем метод получения страницы товара в **views.py**. Будем получать данные о товаре при помощи raw SQL запроса

```python
def get_product_page(request, id):
    """
    Получение страницы товара"""

    query = "SELECT title, price FROM bmstu_lab_product WHERE id = %s"

    with connection.cursor() as cursor:
        cursor.execute(query, [id])
        row = cursor.fetchone()

    if not row:
        return render(request, 'product.html')

    return render(request,
                  "product.html",
                  {
                      "data": {
                          "title": row[0],
                          "price": row[1],
                      },
                  })
```

### Удаление и фильтрация услуг

Добавим возможность удалять услуги. Для этого добавим хэндлер в **views.py**

```python
def remove_product(request, id):
    if request.method != "POST":
        return redirect('products_list')
    try:
        product = Product.objects.get(id=id)
        product.is_active = False
        product.save()
        return redirect('products_list')
    except Product.DoesNotExist:
        return redirect('products_list')
```

и строчку в **urls.py**:

```python
urlpatterns = [
    # ...
    path('remove_product/<int:id>/', views.remove_product, name='remove_product'),
]
```

Поскольку теперь часть товаров может быть помечена как удалённые, нам не нужно выводить их в списке товаров, а так же отображать информацию по ним. Отредактируем соответствующие обработчики:

```python

def get_products_list_page(request):
    """
    Получение страницы списка товаров"""

    USER_ID = 1
    draft_order = Order.objects.filter(client_id=USER_ID,
                                       status=Order.RequestStatus.DRAFT).first()
    return render(request,
                  'products_list.html',
                  {
                      "data": {
                          "products": Product.objects.filter(is_active=True),
                          "items_in_cart": (get_items_in_request(draft_order.id) if draft_order is not None else 0),
                      }
                  })

def get_product_page(request, id):
    """
    Получение страницы товарa
    """

    query = "SELECT title, price FROM bmstu_lab_product WHERE id = %s AND is_active = True"

    with connection.cursor() as cursor:
        cursor.execute(query, [id])
        row = cursor.fetchone()

    if not row:
        return render(request, 'product.html')

    return render(request,
                  "product.html",
                  {
                      "data": {
                          "title": row[0],
                          "price": row[1],
                      },
                  })

```
