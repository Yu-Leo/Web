# Разработка Интернет Приложений (РИП) 2023

Отчеты по лабораторным работам и ДЗ отправлять на почту `aikanev@bmstu.ru`

## [Видеозаписи лекций в youtube](https://youtube.com/playlist?list=PLLELLTvDgUQ9cpB1XzSuZ0mNSBkbjVNJ_)
#### Образ виртуальной машины Linux [Ubuntu 22.04](https://github.com/iu5git/Standards/blob/main/Linux/Linux.md) для выполнения заданий курса 

## Лекции
### Бекенд
* [Лекция 1. История Web, MVC, Django](lectures/Lecture_1_Web.pdf) 

* [Лекция 2. Базы данных, ER, миграции, ORM](lectures/Lecture_2_Databases_ORM.pdf) 

* [Лекция 3. Методология Agile, состав команды. Диаграммы UML. Работа в git](lectures/Lecture_3_Agile_UML_Git.pdf)

* [Лекция 4. OSI, HTTP. Стандарты интернета](lectures/Lecture_4_HTTP.pdf)

* [Лекция 5. Веб-сервис. REST. Swagger. Микросервисы](lectures/Lecture_5_Web_Service.pdf)

* Лекция 8. Авторизация, куки, сессии, Permissions.

* Лекция 9. Redis. JWT. SSO

* Лекция 14. WebSocket, grpc. S3, очереди

### Фронтенд
* Лекция 6. Введение в React, жизненный цикл компонентов, CORS

* Лекция 7. React Hooks

* Лекция 10. Redux

* Лекция 11. POST Ajax, Axios

* Лекция 12. Адаптивная верстка. PWA

* Лекция 13. Нативные приложения. React Native, Tauri

* Лекция 15. Резерв

## Лабораторные работы
В рамках практических работ по курсу необходимо каждому разработать заявочную систему на услуги по своей предметной области. Система состоит из веб-сервиса, фронтенд приложения, нативного приложения и второго асинхронного сервиса.

У каждого своя предметная область на весь курс: бронирование отелей, билетов в театр/кинотеатр, онлайн-магазин по вариантам, тему выбирать из списка ниже. По каждой теме есть ключевой процесс, в котором `пользователь` оформляет `заявки`, в которой может быть несколько `услуг`. Также есть `модератор`, который может редактировать список `услуг` и одобрять `заявки`. От предметной области зависят: названия ролей пользователей, названия сущностей `услуг` и `заявок`, список полей для них, возможные статусы и изменяемые в них поля. В `нативном приложении` нужно реализовать интерфейс `гостя` - только просмотр `услуг`.

Основной вариант лабораторных по бэкенду - это Django и `Go`. Но можно выполнять также на `Java`, `C#` и `Node.js`, при выполнении условия лабораторных работ. Для фронтенда только `React`+`Redux`+`axios`+`React-Bootstrap`

Каждая лабораторная - это `sprint`, этап разработки по `agile`, под каждую отдельная именованная по теме ветка в `git`. Всего 4 репозитория: под каждый бекенд, фронтенд и нативное приложение. Каждая работа демонстрируется и защищается отдельно. При защите необходимо продемонстрировать работу приложения по своей теме, UML диаграмму из `StarUML`, репозиторий github с кодом и ответить на вопросы. По первому модулю необходимо также сделать ТЗ, а по второму отчет по курсу - РПЗ.

* [Примеры UML и ER диаграмм](/tutorials/homework)

## Лабораторные 2023

#### Лабораторная 1 

- **Цель работы**: выбор варианта-темы на весь курс, знакомство с разработкой бэкенда и разработка дизайна для 2 страниц
- **Порядок показа**: показать две страницы приложения, объяснить заголовки во вкладке `Network`, объяснить шаблоны, контроллеры этих страниц и коллекцию данных
- **Контрольные вопросы**: MVC, Django/Go, шаблонизация, HTTP, Web, HTML
- **Задание**: Базовая шаблонизация в Django (для Go просто HTML) для `услуг`, создание дизайна приложения

Создание базового интерфейса, состоящего из двух страниц. Первая для просмотра списка `услуг` (отели, товары, рейсы и тд) в виде карточек с наименованием, ценой и картинкой. При клике по карточке происходит переход на вторую страницу с подробной информацией об `услуге` (даты, описание и тд) 

В приложении должны быть использованы стили, для каждого элемента списка подгружается свое изображение. Разработать стиль приложения, который будет применяться далее в последующих лабораторных по фронтенду. `CSS` вынести в отдельный файл. Все данные для обеих страниц нужно брать прямо из коллекции, без использования БД.

Добавить поле input для фильтрации на сервере списка `услуг` по одному из полей (наименование, цена), отображаемых на странице (по умолчанию отображать все). Поле поиска должно сохраняться после запроса. Всего в приложении должно быть 2 GET запроса и одна модель-коллекция. Без `JavaScript`

* [Инструкция по работе c Python](/tutorials/python/python.md)
* [Методические указания Django](/tutorials/lab1-py/lab1_tutorial.md)
* [Методические указания Golang](/tutorials/lab1-go/README.md)

#### Лабораторная 2

- **Цель работы**: разработка структуры базы данных и ее подключение к бэкенду 
- **Порядок показа**: показать панель администратора/adminer, добавить запись, посмотреть данные через select в БД, показать шаблоны страниц. Объяснить модели, контроллеры для созданных таблиц
- **Контрольные вопросы**: ORM, SQL, модель и миграции
- **ER диаграмма**: таблицы, связи, столбцы, типы столбцов и их длина, первичные, внешние ключи
- **Задание**: Создание базы данных `PostgreSQL` по теме работы, подключение к созданному шаблонизатору

Необходимо разработать структуру БД по выбранной теме и ее реализовать с учетом требований ниже. Использовать таблицу `услуг` в страницах разработанного приложения. Наполнить таблицы БД данными через `админку Django` или `Adminer`. Получение `услуг`, поиск и фильтрацию удаленных записей сделать через `ORM`.

Для карточек таблицы `услуг` добавить кнопку логического удаления услуги (через статус) с помощью выполнения SQL запроса без ORM.

**Требования к БД**: 

Обязательно наличие 4 таблицы: `услуг` (статус удален/действует), `заявок` (статус, дата создания, дата формирования, дата завершения, `создатель` и `модератор`), `м-м заявки-услуги`, `пользователей`

Обязательно наличие 5 или более статусов `заявок`: черновик, в работе, завершён, отклонён, удалён. Названия таблиц и их полей должны соответствовать предметной области.

* [Методические указания PostgreSQL](/tutorials/lab2-db/README.md)
* [Методические указания Django](/tutorials/lab2-py/lab2_tutorial.md)
* [Методические указания Golang](/tutorials/lab2-go/README.md)
* [Курс по основам БД](https://aiintro.docs.iu5edu.ru/docs/db/)

#### Лабораторная 3

- **Цель работы**: создание веб-сервиса в бэкенде для использования его в `SPA`
- **Порядок показа**: Через `insomnia`/`postman` выполнить GET списка `услуг`, добавить `услугу` в `заявку`, изменить и сформировать `заявку`, ошибка при изменении статуса. Показать измененные данные через select. Объяснить модели, сериализаторы, контроллеры, роутеры для методов веб-сервиса
- **Контрольные вопросы**: веб-сервис, REST, RPC, HTTP, OSI ISO
- **Диаграмма классов** с детализацией бэкенда (домены методов по `url` с интерфейсами, перечислить все методы, модели, таблицы БД) + insomnia/postman
- **Задание**: Создание веб-сервиса со всей итоговой бизнес логикой, но без авторизации, подключение его к БД и тестирование в `insomnia`/`postman`

Создание **веб-сервиса** для получения/редактирования данных из вашей БД. Требуется разработать все методы для реализации итоговой бизнес логики вашего приложения. Для изображений `услуг` использовать `Minio` или хранение файлов картинок в бинарном виде в БД.

**Требования к веб-сервису**

Методы и `url` в `API` должны соответствовать `REST`. Для списка `услуг` и `заявок` нужно предусмотреть фильтрацию на бэкенде. Взаимодействие с БД через `ORM`. Не делать `POST` `заявки`. Для логических действий в приложении (оплата, подтверждение, завершение) предусмотреть отдельные методы для обновления конкретных полей (статусы нельзя менять с любого на любой):
- Услуги - список, одна запись, добавление, изменение, удаление, добавление в заявку
- Заявки - список, одна запись, изменение, статусы создателя, статусы модератора, удаление
- м-м - удаление из заявки, изменение количества/значения в м-м 

* [Методические указания DRF](/tutorials/lab3-py/lab3_tutorial.md). Только через `API view`
* [Методические указания Golang](/tutorials/lab3-go/README.md)
* [Пример подключения S3-хранилища](https://github.com/iu5git/Networking/tree/main/S3)
* [Пример использования Minio в Python](https://github.com/iu5git/Networking/tree/main/Minio_Python)

#### Лабораторная 4

- **Цель работы**: Разработка базового SPA на React
- **Порядок показа**: показать две страницы фронтенда в браузере из `localhost` и в `GitHub Pages`, фильтрация заявок. Внести изменения в БД, показать их во фронтенде. Объяснить код компонентов, передаваемые props, вызовы fetch.
- **Контрольные вопросы**: react, props, компонент, элемент, состояние, хуки, жизненный цикл компонента
- **Deployment диаграмма** узлы: фронтенда, веб-сервиса, базы данных, web-сервера со статикой. Узлы соединить протоколами, компоненты фронтенда и бэкенда поместить в узлах, указать API между ними.
- **Задание**: Разработать две страницы фронтенд приложения на `React`, `TS` и подключить его к веб-сервису. Подготовить ТЗ на итоговую систему. 

Разработать базовый интерфейс приложения на `React` для `гостя`, аналогичный двум страницам из лабораторной работы №1 для просмотра `услуг`. При этом на странице списка `услуг` должны быть все обходимые фильтры (по диапазону дат, названию, цене) с фильтрацией на бэкенде. Использовать компоненты `React-Bootstrap`. Необходимо развернуть фронтенд на `GitHub Pages`.

В приложении должна быть навигационная панель `navbar` для списка базовых страниц, а также навигационной цепочки `breadcrumbs`, где отображается путь от базовой страницы к текущей. В этой лабораторной никакого `Redux`, а `Context` вообще в курсе использовать нельзя.

Содержимое карточек получать из веб-сервиса лабораторной №3. Ajax-запросы написать самостоятельно через `fetch`. Ограничение с `CORS` решить через проксирование `React`. В методах `fetch` предусмотреть получение данных из коллекции с `mock`-объектами при отсутствии доступа к вашему бэкенду (если он не поддерживает `HTTPS`).

* [Методические указания](/tutorials/lab4/lab4_tutorial.md). Только на TS
* [Progressive Web App и адаптивный дизайн](/tutorials/pwa/PWA.md)

**ТЗ** на итоговую систему:
- цель
- назначение - краткое описание для чего, кто работает в системе
- задачи
- методы веб-сервиса таблицей с группировкой по доменам: метод, url, описание, входные, выходные данные
- Описание UI - список окон и какие действия для каких групп пользователей доступны. Указать, какие методы бэкенда при этом вызываются.
- требования к аппаратному обеспечению для сервера и клиента
- требования к программному обеспечению с версиями для серверных компонентов и для клиента

#### Лабораторная 5

- **Цель работы**: Завершение бэкенда для `SPA`
- **Порядок показа**: выполнить авторизацию через `swagger`, использовать содержимое куки для остальных запросов через `swagger`. Показать, что при отсутствии прав возникает ошибка.
- **Контрольные вопросы**: куки, сессия, redis, jwt, авторизация, аутентификация
- **Sequence диаграмма**: весь набор `HTTP` запросов по бизнес-процессу
- **Задание**: Добавление авторизации и `swagger` в веб-сервис

Реализовать методы бэкенда для `аутентификации` и `регистрации`. Авторизация через хранение сессий и куки. Автозаполнение пользователя в таблице `заявок` при создании новой. Добавить описание методов для `swagger`.

Добавить проверку `Permissions` для методов `модератора`. Без авторизации в `Swagger` должно быть доступно только чтение-получение данных через API, с авторизацией - методы `пользователя`, а для `модератора` доступны все методы.

* [Настройка через WSL](https://github.com/iu5git/Networking/tree/main/kafka_wsl)
* [Методические указания DRF Redis](https://github.com/iu5git/web-2022/blob/main/tutorials/lab7-py/lab7_tutorial.md)
* [Методические указания Golang JWT](https://github.com/iu5git/web-2022/tree/main/tutorials/lab7-go/README.md)

#### Лабораторная 6

- **Цель работы**: Завершение интерфейса `пользователя` в `React`
- **Порядок показа**: показать добавление `заявки`. Пояснить в коде использование `redux` и `axios`. Показать авторизацию в браузере и содержимое localStorage/cookie.
- **Контрольные вопросы**: схема redux, reducer, store, контекст, axios
- **Диаграмма классов** с детализацией бэкенда и фронтенда: добавить методы авторизации, фронтенд разделить на страницы, добавить у страниц зависимость от API.
- **Activity диаграмма/BPMN** для итогового бизнес-процесса для ДЗ: описание бизнес-процесса, разделение на дорожки по ролям пользователей, действия соответствуют операциям пользователей в вашей системе.
- **Задание**: Добавить авторизацию и возможность оформления `заявок` во фронтенд через `Redux Toolkit`

Добавить страницы для регистрации и авторизации. Добавить окно для просмотра списка `заявок` пользователя в виде таблицы. Добавить в меню пункты для новых страниц. Для обращений к методам веб-сервиса использовать `axios`.

Добавление менеджера состояний `Redux Toolkit` для хранения создаваемой заявки и состояния интерфейса после авторизации. В приложении должно быть реализовано переключение между интерфейсом гостя и интерфейсом пользователя по кнопке `Вход`/`Выход`. При выходе должно сбрасываться содержимое конструктора новой заявки.

Добавление на странице услуг кнопки `Добавить` для внесения данной услуги в новую заявку. Добавление страницы `конструктора` заявки, где можно удалить уже добавленные в заявку услуги, поменять их количество или `подтвердить` заявку. Эта же страница также используется для просмотра старых заявок из списка. После кнопки `подтвердить` новая заявка создается в БД, а до этого хранится в `Redux Toolkit`

* [Методические указания Redux](/tutorials/redux/redux_toolkit.md)
* [Методические указания Axios](/tutorials/lab6/lab6_tutorial.md)

#### Лабораторная 7

- **Цель работы**: Создание нативного приложения
- **Порядок показа**: Отредактировать услуги в БД, продемонстрировать изменение в нативном приложении  
- **Контрольные вопросы**: виды нативных приложений и отличие от web-приложений, react-native, pwa, tauri
- **Задание**: Создание приложения для `гостя` на iOS/Android/Tauri/Qt/React-native и подключением к веб-сервису

Создание простого нативного приложения для интерфейса гостя (без авторизации и редактирования), состоящий из 2 страниц. Подключить приложение к разработанному API.

* [Методические указания iOS (Swift)](https://github.com/iu5git/web-2022/blob/main/tutorials/ios_tutorial/ios_tutorial.md)
* [Методические указания Android (Java)](https://github.com/iu5git/web-2022/blob/main/tutorials/android_tutorial/android_tutorial.md)
* [Методические указания React Native + Redux Toolkit](/tutorials/react-native/react_native.md)
* [Методические указания Tauri](/tutorials/tauri/)
* Qt

#### Лабораторная 8

- **Цель работы**: Знакомство с межсервисным взаимодействием и асинхронностью
- **Порядок показа**: вызвать через `insomnia` grpc-метод асинхронного сервиса, показать что в основном приложении появился результат
- **Контрольные вопросы**: grpc, асинхронность, веб-сервис
- **Задание**: Создание асинхронного сервиса для отложенного действия (вычисление, моделирование, оплата и тд)

Требуется разработать второй простой асинхронный сервис на другом языке (кто делал на Django - Go и наоборот) с одним grpc-методом для выполнения отложенного действия в вашей системе (вычисление, моделирование, оплата и тд). 

В исходном веб-сервисе также необходимо добавить grpc-метод для внесения результатов.

#### Домашнее Задание

- **Цель работы**: Закрепление полученный знаний
- **Порядок показа**: создать заявку в интерфейсе `пользователя`. Авторизоваться под `модератором`, одобрить `заявку` и отредактировать список `услуг`.
- **Отчет**: отчет необходимо отправить на почту [aikanev@bmstu.ru](). Оценивается раскрытие предметной области в описании и приложении, корректность оформления отчета.
- **Контрольные вопросы**: любые вопросы по реализации интерфейса `модератора`
- **Диаграммы**: диаграмма состояний для статусов `заявок` и диаграмма прецедентов. Актуализировать все диаграммы из лабораторных, все диаграммы должны соответствовать реализованной вами системе. Все диаграммы должны быть читаемые, шрифт на них должен не отличаться по размеру от шрифта текста отчета.
- **Задание**: Реализовать интерфейс `модератора` и подготовить итоговый отчет

Необходимо добавить в приложение React интерфейс `модератора`, доступный после его авторизации и имеющий следующие отличия:
- Новое окно редактирования `услуг`, список услуг отображается таблицей. Доступно добавление новых услуг (обязательные и необязательные поля), редактирование, удаление.
- В окне списка `заявок` доступны кнопки для смены статуса заявок. Также есть поля фильтрации по диапазону `дат формирования`, пользователю и статусу заявок.

**Отчет-РПЗ** по всем лабораторным и ДЗ:
1. **Введение** (актуальность, цель, назначение, требования, задачи)
2. **Бизнес-процесс**. Описание предметной области. Диаграмма прецедентов, диаграмма состояний и деятельности/BPMN
3. **Архитектура**. Диаграммы развертывания, ER с назначением таблиц и диаграмма классов с детализацией бэкенда и фронтенда
4. **Алгоритмы**. Диаграмма последовательности HTTP запросов
5. **Описание интерфейса**. Перечень окон, их назначение и выполняемые пользователями действия
6. **Заключение**. Перечень выполненных задач и достигнутые результаты. Ссылка на GitHub
7. **Список использованных источников**  
8. **Приложение. Техническое задание**

#### Дополнительные задания
1. Индексы в БД, большое количество `услуг` (> 100000) и пагинация (+4 балла). Порядок показа: показать пагинацию с фильтрацией по индексу в React-приложении. Включить и отключить индекс - показать отличие во времени запроса.
2. Адаптивность дизайна (+2 балла). Перейти в адаптивный режим браузера, поменять ширину. Объяснить настройки для размера карточек, количества колонок и тд.
3. Кодогенерация из `swagger` (+2 балла). Показать применение сгенерированного кода фронтенда из `swagger`.

### Темы 2023:

#### Удаленные вычисления
1. ~~Система заявок на вычисления: факториал, НОД и тд. `Услуги` - виды вычислений, `заявки` - запрос с входными данными и результатами.~~
2. ~~Аналитическое моделирование потоков в метро `Услуги` - виды моделирования, `заявки` - запрос с входными данными и результатами.~~
3. ~~Аналитическое моделирование загруженности сетевого оборудования `Услуги` - виды моделирования по оборудованию, `заявки` - запрос с входными данными и результатами.~~
4. ~~Статистические расчеты. `Услуги` - статистические величины (мат ожидание, дисперсия и тд), `заявки` - данные для расчетов с результатом~~
5. ~~Шифрование кодом с обнаружением ошибок. `Услуги` - данные, `заявки` - запросы на шифрование/расшифровку с результатом обнаружения ошибки~~
6. ~~Шифрование кодом для коррекции ошибок. `Услуги` - данные, `заявки` - запросы на шифрование/расшифровку с результатом коррекции ошибки~~
7. ~~Прогноз погоды. `Услуги` - виды данных (температура, давление, влажность), `заявки` - запросы на предсказание погоды через авторегрессию~~
8. ~~Бинарные операции. `Услуги` - бинарные операции, `заявки` - заявки на вычисления~~
9. ~~Применение фильтров к изображению. `Услуги` - типы опрераций (изменение яркости, контраста и тд), `заявки` - заявки для применение преобразований к изображению.~~
10. Расчет платежа по ипотеке. `Услуги` - виды расчета (страховка, ежемесячные платежи, аннуитет или равными долями), `заявки` - заявки на расчет
11. ~~Расчет квартплаты. `Услуги` - набор показателей, `заявки` - расчет по каждой квартире~~

#### Малый бизнес
1. ~~Система заявок для поваров в быстром питании на приготовление. `Услуги` - виды блюд с указанием поваров, `заявки` - заказ на приготовление блюд.~~
2. ~~Рецепты автоматического приготовления пищи. `Услуги` - продукты, `заявки` - рецепты~~ 
3. ~~Заявки от коллцентра мелкого бизнеса: менеджер-создатель заявки, исполнитель+курьер. `Услуги` - услуги данного бизнеса, `заявки` - заявки от клиентов на услуги.~~
4. ~~Продажа очков. `Услуги` - свойства линз, `заявки` - заказы от покупателей на линзы~~
5. ~~Книжное издательство. `Услуги` - работы издательства (печать, брошюрование и тд), `заявки` - заказы на издание книги~~
6. ~~Размещение товаров на маркетплейсе. `Услуги` - категории товаров, `заявки` - заявки от продавцов на размещение товара~~
7. 2НДФЛ. `Услуги` - набор кодов для отчислений, `заявки` - справки 2 НДФЛ за месяц
8. Бухгалтерский баланс компании. `Услуги` - добавочный капитал, заемные средства и тд, `заявки` - отчетность компании по показателям

#### Компьютерные игры
1. ~~Карточная игра Эволюция. `Услуги` - карты Эволюции, `заявки` - карточные ходы соперников в игре~~
2. ~~Автоматический подбор игроков для игры. `Услуги` - карты, игровые локации, `заявки` - игры, список участников автоматически собирается из поданных ими запросов~~

#### Химическое производство
1. ~~Оборудование для химических лабораторий. `Услуги` - лабораторное оборудование, `заявки` - заявки на приобретение~~
2. ~~One-pot синтезы. `Услуги` - исходные вещества, `заявки` - проведение синтеза при заданных условиях~~
3. ~~Производство косметики. `Услуги` - вещества для производства, `заявки` - виды косметики с указанием состава~~
4. ~~Производство лекарств из готовых веществ. `Услуги` - действующие и др вещества, `заявки` - составляющие лекарств~~
5. ~~Производство красок из красителей. `Услуги` - готовые красители и др вещества, `заявки` - виды красок (батик, гуаш) по цветам~~

#### Производство
1. ~~Система заявок на производстве. `Услуги` - используемые программы станков с ЧПУ, `заявки` - заказ на изготовление детали~~
2. ~~Продажа авиазапчастей для бизнес-джетов. `Услуги` - авиазапчасти, `заявки` - заявки на приобретение комплектующих. Связаться с Антоновым А.И.~~
3. ~~Поставки комплектующий для производства электроавтомобилей. `Услуги` - комплектующие, `заявки` - заявки от завода по сборке к заводам комплектующих~~
4. ~~Поставки деталей для сборки CubeSat. `Услуги` - детали для CubeSat, `заявки` - заявки на сборку CubeSat~~
5. ~~Склад комплектующих. `Услуги` - список комлектующих для хранения с размером для места, `заявки` - заявки на доставку и отгрузку комплектующих~~
6. ~~Кораблестроительная программа. `Услуги` - классы кораблей, `заявки` - заказ кораблей от государства~~
7. ~~Фаблаб. `Услуги` - виды проводимых работ на фаблабе, `заявки` - заказы на печать микроэлектроники~~
8. ~~Разработка месторождений. `Услуги` - виды работ по разработке (бурение, геологоразведка), `заявки` - этапы освоения месторождений~~
9. ~~Заказ на постройку самолета.  `Услуги` - комплектация самолета, `заявки` - производство пассажирского самолета~~
10. ~~Техприемка авиадвигателей. `Услуги` - состав партии двигателей, `заявки` - этапы приемки~~
11. ~~Сборка ракетоносителей Ангара разных типов.  `Услуги` - комплектующие, блоки, двигатели для разных типов ракет Ангара. `заявки` - заявка на производство ракетоносителя~~


#### Электронные услуги
1. ~~Визовый центр РФ - заявки на визы. `Услуги` - виды виз, `заявки` - заявки на получение нужной визы.~~
2. ~~Автоматический контроль паспортов на границе. `Услуги` - паспорта, которые заведены в системе, `заявки` - факты пересечения границы по паспорту~~
3. ~~Банковские счета. `Услуги` - банковские договоры, `заявки` - открытие новых счетов в рамках банковского договора~~
4. ~~Заявки на изготовление документов при смене фамилии. `Услуги` - виды документов для замены, `заявки` - заявка на замену с указанием новой фамилии и причины~~
5. ~~Электронная таможня. `Услуги` - виды товаров, ценностей, валют для провоза, `заявки` - заявки для декларирование провозимых товаров.~~
6. ~~Регистрация новых препаратов. `Услуги` - список болезней для лечений препаратом, `заявки` - заявки на регистрацию нового препарата~~
7. ~~Регистрация новых видов животных. `Услуги` - места обитания животных, `заявки` - заявки на открытие нового вида с указанием рода~~
8. ~~Уведомления электронных услуг. `Услуги` - получатели уведомления, `заявки` - отправка уведомления~~
9. ~~Сервис для самозанятых. `Услуги` - виды предоставляемых услуг `заявки` - заявка на регистрацию замозанятого с указанием ФИО, деятельности и др данных~~
10. ~~Сбор средств на реконструкцию исторических зданий. `Услуги` - виды работ по реконструкции `заявки` - заявки на реконструкцию и сбор средств~~
11. ~~Электронное голосование. `Услуги` - варианты названий для объектов города, `заявки` - результаты голосования~~
12. ~~Заявка на проведение тендера. `Услуги` - участники тендера, `заявки` - статусы тендера~~
13. ~~Договоры банка. `Услуги` - набор услуг банка, `заявки` - заявка на подключение к обслуживанию~~
14. ~~Чаты. `Услуги` - чаты, `заявки` - отправка сообщений (м-м сообщений-`заявок` для ответов вместо м-м к `услугам`)~~
15. ~~Групповая отправка файла в мессенджере. `Услуги` - получатели, `заявки` - процесс отправки файла~~
16. ~~Регистрация участников на спортивное соревнование. `Услуги` - участники, `заявки` - заявка для команды на участие~~
17. ~~Банкомат. `Услуги` - различные виды купюр, `заявки` - операции внесения/снятия наличных~~
18. ~~Удаленная поддержка. `Услуги` - виды происшествий, `заявки` - обращения от пользователей~~
19. ~~Счетчики воды. `Услуги` - разные адреса, `заявки` - фиксация показаний от счетчиков~~


#### ИТ услуги
1. ~~Консалтинг по ИТ безопасности. `Услуги` - виды консалтинга, `заявки` - заявки на проведение консалтинга~~
2. ~~Обслуживание ИТ инфраструктуры. `Услуги` - виды проводимых работ, `заявки` - заявки по настройке сетевого оборудованию, виртуалки и тд~~
3. ~~Мониторинг ИТ угроз. `Услуги` - виды угроз, `заявки` - факты возникновения угроз в подразделении компании~~
4. ~~Сайт КТС. `Услуги` - виды разработки, `заявки` - заявки от заказчиков~~
5. ~~Аренда виртуальных машин. `Услуги` - тарифы на аренду, `заявки` - заявки на аренду кластера машин~~
6. ~~Заявки на подключение провайдера. `Услуги` - виды работ по подключению, `заявки` - заявка от клиента на подключение~~
7. ~~Заявки на установку серверного ПО. `Услуги` - программное обеспечение, `заявки` - заявки от сотрудников~~
8. ~~Создание датацентра. `Услуги` - комплектующие, аппаратное обеспечение, `заявки` - процесс создания датацентра~~
9. ~~Голосовой помощник. `Услуги` - доступные действия помощника, `заявки` - интенты пользователя~~

#### Транспорт
1. ~~Заявки контроля маршрута беспилотных летательных аппаратов. `Услуги` - районы города, `заявки` - заявки на пролет объекта в данной районе в определенное время.~~
2. ~~Контроль нарушений ПДД самокатами и др средств индивидуальной мобильности с двигателем. `Услуги` - виды нарушений и штрафы для них, `заявки` - факты нарушения из средств фиксации~~
3. ~~Приобретение абонементов на общественный транспорт. `Услуги` - виды абонементов на различный транспорт, `заявки` - приобретение абонементов на карту~~
4. ~~Проезд по транспортной карте 90 минут. `Услуги` - маршруты транспорта, `заявки` - проезд по транспортной карте в 90 минут с указанием маршрута транспорта~~
5. ~~Заявки на стоянку судна в порту. `Услуги` - конкретные корабли, `заявки` - заявки на нахождение корабля в данному порту.~~
6. ~~Севморпуть, заявки на проводку ледоколами. `Услуги` - транспортные корабли ледового класса, `заявки` - заявки на проводку кораблей ледоколом с указанием начальной и конечной точки проводки.~~
7. ~~Логистика контейнеров. `Услуги` - список контейнеров с указанием груза, `заявки` - заявка на перевозку со списком контейнеров и транспортным средством~~
8. ~~Платная дорога. `Услуги` - участки платной дороги, `заявки` - оплата и проезд~~
9. ~~Авиарейсы. `Услуги` - авиакомпании, `заявки` - авиарейсы с указанием отправки, назначения~~
10. ~~Страховка на автотранспорт. `Услуги` - водители в страховке, `заявки` - заявка на оформление страховки~~
11. ~~Регистрация авиабагажа. `Услуги` - единицы багажа с кодами, `заявки` - доставка багажа с делением по рейсам~~

#### Космос
1. ~~Заявки на доставку грузов на Марс на Starship. `Услуги` - товары, доставляемы на Марс на Starship, `заявки` - заявки на конкретный объем товаров~~
2. ~~Учет перелетов Starship между земными космодромами. `Услуги` - конкретные космические корабли, `заявки` - заявки на перелет кораблей между площадками~~
3. ~~Отчеты по добыче ресурсов (вода, углекислый газ, гелий и тд) на Луне. `Услуги` - добываемые ресурсы, `заявки` - месячные отчеты об объеме добычи в конкретном месте Луны~~
4. ~~Заявки на переходы космических аппаратов на различные орбиты. `Услуги` - доступные орбиты, `заявки` - заявки на переход спутников на орбиту.~~
5. ~~Автоматические межпланетные станции (АМС). `Услуги` - космические объекты, `заявки` - космические полеты АМС к этим объектам.~~
6. ~~Станции на поверхности Марса. `Услуги` - географические объекты на поверхности Марса, `заявки` - автоматические марсианские станции, успех/потеря/работает~~
7. ~~Эволюция ближайших к Солнцу звезд. `Услуги` - ближайшие звезды, `заявки` - события в эволюции этих звезд, при завершении `заявки` меняется таблица `услуг`.~~
8. ~~Запуск спутников с космодрома Восточный. `Услуги` - имеющиеся заявки на доставку КА на орбиту, `заявки` - полет ракеты-носителя с указанной полезной нагрузкой~~
9. ~~Астрономия для астрологов. `Услуги` - планеты, `заявки` - присутствие в созвездии указанных планет в данное время~~
10. ~~Анализ реликтового излучения. `Услуги` - анализируемые спектры, `заявки` - космические аппараты для анализа реликтового излучения~~
11. ~~Полеты к Gateaway. `Услуги` - модули станции Gateaway и космические корабли, `заявки` - миссии с указанием состава и цели~~
12. ~~Полеты Orion. `Услуги` - астронавты, `заявки` - полет с указанием назначения и команды~~
13. ~~Mars Sample Return Mission. `Услуги` - гильзы-пробирки с грунтом от Perseverance, `заявки` - миссии Mars Sample Return Mission с указанием гильз~~
14. ~~Грузовые корабли к МКС. `Услуги` - грузы для доставки на МКС, `заявки` - полеты грузовых кораблей к МКС~~


#### МГТУ
1. ~~Технадзор строительных объектов МГТУ. `Услуги` - строящиеся здания в кампусе МГТУ, `заявки` - проверки технадзора данных строек~~
2. ~~Мероприятия музея МГТУ. `Услуги` - виды проводимых в музее мероприятий, `заявки` - заявки для групп на данные мероприятия~~
3. ~~Бронирование аудиторий МГТУ. `Услуги` - аудитории МГТУ, `заявки` - заявки на бронирование аудиторий под проводимое мероприятие~~
4. ~~Парковка МГТУ. `Услуги` - парковки МГТУ, `заявки` - заявки на пропуск/абонементы автомобилей на парковки~~
5. ~~Запись на спортивные курсы МГТУ. `Услуги` - еженедельные группы по курсам, `заявки` - запись на группы~~
6. ~~Сайт конференции. `Услуги` - авторы статей, `заявки` - заявка на публикацию статьи~~
7. ~~Проведение митапов по ИИ. `Услуги` - спикеры, `заявки` - митапы~~С 
8. ~~Составление расписания преподавателей. `Услуги` - преподаватели, `заявки` - занятия (день недели+время+ауд). Не должно быть двух занятий в одно время у преподавателя~~
9. ~~Составление расписания групп. `Услуги` - учебные группы, `заявки` - занятия (день недели+время+ауд). Не должно быть двух занятий в одно время у группы~~
10. ~~Заявки на специалистов ГУИМЦ (сурдопереводчиков, сурдоакустики и тд). `Услуги` - специалисты центра ГУИМЦ, `заявки` - заявка на специалистов на конкретное время и место.~~
11. ~~Заявки на техническое оборудование (проекторы, экраны и тд). `Услуги` - виды оборудования, `заявки` - заявка на предоставление оборудования в аудиторию на время.~~
12. ~~Заявки на пропуски для посетителей. `Услуги` - корпусы МГТУ, `заявки` - заявка со списком посетителей, временем посещения~~
13. ~~Пропуски на выходные и праздничные дни. `Услуги` - список сотрудников, `заявки` - заявка на работу в выходной, праздничный или ночью с указанием причины.~~
14. ~~Составление занятий. `Услуги` - задания для выполнения, `заявки` - занятия со списком для выполнения студентами~~
15. ~~Заявки на совместный доступ к документы. `Услуги` - документы, `заявки` - заявки на предоставление доступа на редактирование к документам.~~
16. ~~Приказы ректора. `Услуги` - подразделения МГТУ для ознакомления с приказом, `заявки` - приказы ректора~~
17. ~~Проверка кода студентов. `Услуги` - языки программирования, `заявки` - заявка от студента на проверку кода преподавателем~~
18. ~~Формирование групп на прохождение медосмотра. `Услуги` - доступное время для записи на медосмотр, `заявки` - заявки от студентов для включения в группу на медосмотр~~
19. ~~Мероприятия профкома МГТУ. `Услуги` - билеты в музеи, театры, конкурсы и тд, `заявки` - подача заявок на бесплатное распределение билетов~~
20. ~~Заявки на повышение квалификации. `Услуги` - курсы, `заявки` - прохождения курса/программы дисциплин~~
21. ~~Выставки МГТУ. `Услуги` - направления/тематика выставки, `заявки` - выставка с указанием даты, времени и помещения~~
22. ~~Обратная связь по курсу. `Услуги` - группы студентов, `заявки` - запрос от преподавателя на проведение опроса по выборанным группам~~
23. ~~Приказы об отчислении. `Услуги` - студенты, `заявки` - приказы на отчисление студентов~~
24. ~~Приемная комиссия. `Услуги` - специальности для поступления, `заявки` - продача документов для поступления~~
25. ~~Составление маршрута. `Услуги` - доступные переходы между корпусами в капмусе, `заявки` - заявка на объединение участков в единый маршрут - или ошибка~~


#### Социальные услуги
1. ~~Трудоустройство женщин в отпуске по уходу за ребенком. `Услуги` - вакансии для женщин с детьми, `заявки` - подача заявок на вакансии от женщин~~
2. ~~Система трудоустройства для инвалидов. `Услуги` - вакансии для инвалидов, `заявки` - подача заявок на вакансию от инвалидов~~
3. ~~Система социальной помощи инвалидам - доставка еды, сопровождение на мероприятие и тд. `Услуги` - оказываемые услуги, `заявки` - заявки на них от инвалидов~~
4. ~~Заказы на молочную кухню (для детей). `Услуги` - виды продуктов, `заявки` - заявки от родителей~~
5. ~~Справочник по медицине катастроф и первой помощи. `Услуги` - виды первой помощи, `заявки` - виды поражений при чрезвычайных ситуациях~~
6. ~~Сервис для работодателей. `Услуги` - города, в которых будет открыта вакансия, `заявки` - заявки на создание вакансий~~

#### История
1. ~~История ВОВ - участники ВОВ и их привязка к архивным документам (личные карточки, наградные, ЖБД итд). `Услуги` - архивные документы, `заявки` - привязка участника с наградой/событием к документу~~
2. ~~Высочайшие вершины Земли и их покорители. `Услуги` - знаменитые покорители, `заявки` - экспедиции по покорению вершин.~~
3. ~~Система археологов - находки и их привязка к раскопкам. `Услуги` - места археологических раскопок, `заявки` - факты находок предметов с группировкой по экспедиции~~
4. ~~Эпоха географических открытий. `Услуги` - первооткрыватели, `заявки` - их открытия~~
5. ~~Животные рекордсмены. `Услуги` - виды рекордов (самые большие, самые быстрые и тд), `заявки` - жившие виды животных~~
6. ~~Морские битвы на Тихом океане. `Услуги` - конкретные корабли, `заявки` - составы соединений с адмиралом и указанием победа/поражение~~
7. ~~Походы викингов. `Услуги` - города, `заявки` - походы викингов~~
8. ~~Древнерусские княжества. `Услуги` - княжества, `заявки` - правители княжеств по периодам~~
9. ~~Освоение Дальнего Востока и Сибири. `Услуги` - населенные пункты и географические объекты, `заявки` - экспедиции и походы в XVI-XVIII веках~~
10. ~~Палеонтология. `Услуги` - геологические периоды, `заявки` - ископаемые животные (отряды-рода)~~
11. ~~История живописи. `Услуги` - картины художников, `заявки` - заявки на экспертизу для отнесение данных картин какому-то художнику~~
12. ~~Атомные электростанции СССР и СНГ. `Услуги` - реакторы для энергоблоков, `заявки` - история электростанций~~
13. Регистрация погодных явлений на метеостанции. `Услуги` - погодное явление, `заявки` - значения показателей - запись за день
14. Регистрация температуры на метеостанциях Москвы. `Услуги` - метеостанции Москвы, `заявки` - регистрация за день

## Лабораторные 2022

* [Задания 2022 года](2022.md)

## Вопросы к экзамену и РК (примерные)
1. Опишите шаблон MVC, структуру и назначение компонентов.
2. Опишите схему, как реализован шаблон MVC в фреймворке Django.
3. Что такое Django? Его назначение и возможности.
4. Что такое шаблонизация Django? Приведите примеры.
5. Опишите протокол HTTP. Схему работы и основные понятия.
6. Опишите стек протоколов интернета TCP/IP.
7. Перечислите основные составляющие web и опишите их.
8. Что такое HTML, CSS? Приведите примеры.
9. Что такое URI? Опишите элементы URI для HTTP.
10. Виды баз данных. Приведите примеры и отличия.
11. Объясните назначение ORM, ее составляющие. Укажите преимущества и недостатки ORM.
12. Что такое модель и миграция?
13. Укажите группы SQL запросов, их примеры и назначение.
14. Что такое веб-сервис? Отличие от веб-сервера.
15. Что такое Web API? Назначение и применение.
16. Микросервисная архитектура. Отличия от монолитной архитектуры.
17. Перечислите требования REST, опишите их.
18. Что такое RPC? Варианты RPC и их отличия.
19. Что такое Swagger? Назначение и использование.
20. Что такое AJAX? Схема работы и назначение.
21. Назначение JSON и XML. Примеры и отличия.
22. Что такое git? Опишите схему работы с ветками GitHub.
1. Методология разработки Agile. Состав IT команды.
2. Перечислите основные диаграммы UML и их назначение.
3. Что такое Web реального времени? Что такое WebSocket?
4. Укажите отличия XmlHttpRequest и fetch. Приведите примеры.
5. Перечислите отличия Axios от fetch. Приведите примеры.
6. Что такое React? Что такое компонент, его состояния и свойства.
7. Структура React проекта. Назначение Babel и WebPack.
8. Жизненный цикл React компонента.
9. Назначение хуков useState и useEffect.
10. Назначение хуков useContext и useReducer.
11. Опишите схему работы менеджера состояний Redux.
12. Опишите работу Redux на диаграмме последовательности.
13. Какие параметры передаются при создании Store? Их назначение.
14. Что такое Cors? Укажите варианты решения.
15. Что такое Redis? Его назначение и варианты применения.
16. Опишите схему авторизации с помощью JWT.
17. Опишите схему авторизации с помощью сессий.
18. Что такое авторизация и аутентификация? Укажите варианты авторизации и их отличия.
19. Что такое SSO? Схема работы.
20. Протокол OAuth. Схема работы.
21. Отличия мобильных и веб-приложения. Языки и технологии для разработки мобильных приложений.
22. Что такое pwa? Отличия от других вариантов приложений.
23. Плюсы и минусы разработки на React Native.
24. Назначение фреймворков Electron и Tauri. Их отличия.
25. Опишите этапы подхода DevOps. Назначение GitHub Pages.

#### Команда курса выражает благодарность за помощь в подготовке материалов для данного курса
