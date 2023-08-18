# Разработка Интернет Приложений (РИП) 2023

Отчеты по лабораторным работам и ДЗ отправлять на почту `aikanev@bmstu.ru`

## [Видеозаписи лекций в youtube](https://youtube.com/playlist?list=PLLELLTvDgUQ9cpB1XzSuZ0mNSBkbjVNJ_)
#### Образ виртуальной машины Linux [Ubuntu 20.04](https://github.com/iu5git/Standards/blob/main/Linux/Linux.md) для выполнения заданий курса 

## Лекции
### Бекенд
[Лекция 1. История Web, трехуровневая модель приложений, MVC](https://github.com/iu5git/web-2022/blob/main/lectures/web_intro.pdf) 

[Лекция 2. Методология Agile, состав команды. Диаграммы UML](https://github.com/iu5git/web-2022/blob/main/lectures/Lecture_2_Agile_UML.pdf)

[Лекция 3. Основы Web, шаблонизация, Django](https://github.com/iu5git/web-2022/blob/main/lectures/Lecture_3_Web_Django.pdf)

[Лекция 4. Базы данных, ER, PostgreSQL. ORM. Админка Django. Курсоры](https://github.com/iu5git/web-2022/blob/main/lectures/Lecture_4_Databases_Django_ORM.pdf)

[Лекция 5. Веб-сервис. Swagger. Микросервисы](https://github.com/iu5git/web-2022/blob/main/lectures/Lecture_5_Web_Service.pdf)

[Лекция 6. Работа в git. Примеры специализированных сервисов - S3, уведомления, очереди](https://github.com/iu5git/web-2022/blob/main/lectures/Lecture_6_Special_Services.pdf)

### Фронтенд
[Лекция 7. Введение в фронтенд и React](https://github.com/iu5git/web-2022/blob/main/lectures/Lecture_7_React_Introduction.pdf)

[Лекция 8. React, сборка, компоненты](/lectures/Lecture_8_React.pdf)

[Лекция 9. Redux, hooks](/lectures/Lecture_9_Redux.pdf)

[Лекция 10. Ajax, запросы на React. WebSocket](/lectures/Lecture_10_Ajax.pdf)

[Лекция 11. Авторизация, куки, хранилище сессий](/lectures/Lecture_11_Authorization.pdf) 

[Лекция 12. JWT. SSO](/lectures/Lecture_12_jwt.pdf) 

### Мобильные приложения

[Лекция 13. Общая лекция про мобильные приложения. PWA](/lectures/Lecture_13_PWA.pdf) 

[Лекция 14. Плюсы и минусы React Native. Сетевое взаимодействие на Swift](/lectures/Lecture_14_Swift.pdf) 

### Инфраструктура

[Лекция 15. Резюме, Tauri, Agile, DevOps](/lectures/Lecture_15_Deploy.pdf)

## Лабораторные работы
В рамках практических работ по курсу необходимо каждому разработать заявочную систему на услуги по своей предметной области. Система состоит из веб-сервиса, фронтенд приложения, нативного приложения и второго асинхронного сервиса.

У каждого своя предметная область на весь курс: бронирование отелей, билетов в театр/кинотеатр, онлайн-магазин по вариантам, тему выбирать из списка ниже. По каждой теме есть ключевой процесс, в котором `пользователь` оформляет `заявки`, в которой может быть несколько `услуг`. Также есть `модератор`, который может редактировать список `услуг` и одобрять `заявки`. От предметной области зависят: названия ролей пользователей, названия сущностей `услуг` и `заявок`, список полей для них, возможные статусы и изменяемые в них поля. В `нативном приложении` нужно реализовать интерфейс `гостя` - только просмотр `услуг`.

Основной вариант лабораторных по бэкенду - это Django и `Go`. Но можно выполнять также на `Java`, `C#` и `Node.js`, при выполнении условия лабораторных работ. Для фронтенда только `React`+`Redux`+`axios`+`React-Bootstrap`

Каждая лабораторная - это `sprint`, этап разработки по `agile`, под каждую отдельная ветка в `git`. Каждая работа демонстрируется и защищается отдельно. При защите необходимо продемонстрировать работу приложения по своей теме, UML диаграмму из `StarUML`, репозиторий github с кодом и ответить на вопросы. По первому модулю необходимо также сделать ТЗ, а по второму отчет по курсу - РПЗ.

* [Примеры UML и ER диаграмм](/tutorials/homework)

## Лабораторные 2023

#### Лабораторная 1 

- **Цель работы**: выбор варианта-темы на весь курс, знакомство с разработкой бэкенда и разработка базового дизайна 
- **Порядок показа**: показать две страницы приложения, объяснить шаблоны, контроллеры этих страниц и коллекцию данных
- **Контрольные вопросы**: MVC, Django/Go, шаблонизация, HTTP, Web, HTML
- **Задание**: Базовая шаблонизация в Django (для Go просто HTML) для `услуг`

Создание базового интерфейса, состоящего из двух страниц. Первая для просмотра списка `услуг` (отели, товары, рейсы и тд) в виде карточек с наименованием, ценой и картинкой. При клике по карточке происходит переход на вторую страницу с подробной информацией об `услуге` (даты, описание и тд) 

В приложении должны быть использованы стили, для каждого элемента списка подгружается свое изображение. Все данные для обеих страниц нужно брать прямо из коллекции, без использования БД.

Добавить поле input для фильтрации списка `услуг` по выбранному полю (наименование, цена), отображаемых на странице (по умолчанию отображать все).

* [Инструкция по работе c Python](/tutorials/python/python.md)
* [Методические указания Django](/tutorials/lab1-py/lab1_tutorial.md)
* [Методические указания Golang](/tutorials/lab1-go/README.md)

#### Лабораторная 2

- **Цель работы**: разработка структуры базы данных и ее подключение к бэкенду 
- **Порядок показа**: показать панель администратора/adminer, добавить запись, посмотреть данные через select в БД, показать шаблоны страниц. Объяснить модели, контроллеры для созданных таблиц
- **Контрольные вопросы**: ORM, SQL, модель и миграции
- **ER диаграмма**: таблицы, связи, столбцы, типы столбцов и их длина, первичные, внешние ключи
- **Задание**: Создание базы данных `PostgreSQL` по теме работы, подключение к созданному шаблонизатору

Необходимо разработать структуру БД по выбранной теме и ее реализовать с учетом требований ниже. Использовать таблицу `услуг` в страницах разработанного приложения. Наполнить таблицы БД данными через `админку Django` или `Adminer`.

Для карточек таблицы `услуг` добавить кнопку логического удаления услуги (через статус) с помощью выполнения SQL запроса без ORM.

**Требования к БД**: 

Обязательно наличие 4 таблицы: `услуг` (статус удален/действует), `заявок` (статус, дата создания, дата формирования, дата завершения и `модератор`), `м-м заявки-услуги`, `пользователей`

Обязательно наличие 5 или более статусов `заявок`: введён, в работе, завершён, отменён, удалён. Названия таблиц и их полей должны соответствовать предметной области.

* [Методические указания Django](/tutorials/lab2-py/lab2_tutorial.md)
* [Методические указания Golang](/tutorials/lab2-go/README.md)
* [Курс по основам БД](https://aiintro.docs.iu5edu.ru/docs/db/)

#### Лабораторная 3

- **Цель работы**: создание веб-сервиса в бэкенде для использования его в `SPA`
- **Порядок показа**: выполнить GET списка, сделать POST новой записи, показать новые данные через select. Объяснить модели, сериализаторы, контроллеры, роутеры для методов веб-сервиса
- **Контрольные вопросы**: веб-сервис, REST, RPC, HTTP, OSI ISO
- **Диаграмма классов** с детализацией бэкенда (домены методов по `url` с интерфейсами, модели, таблицы БД) + insomnia/postman
- **Задание**: Создание веб-сервиса со всей итоговой бизнес логикой, но без авторизации, подключение его к БД и тестирование в `insomnia`/`swagger`/`postman`

Создание **веб-сервиса** для получения/редактирования данных из вашей БД. Для изображений `услуг` использовать `Minio` или хранение файлов картинок в бинарном виде в БД.

Требуется разработать все методы для реализации итоговой бизнес логики вашего приложения. Методы и `url` в `API` должны соответствовать `REST`. Для списка `услуг` и `заявок` нужно предусмотреть фильтрацию на бэкенде. Для логических действий в приложении (оплата, подтверждение, завершение) предусмотреть отдельные методы для обновления конкретных полей (статусы нельзя менять с любого на любой). 

* [Методические указания DRF](/tutorials/lab3-py/lab3_tutorial.md). Переделать на `API view`
* [Методические указания Golang](/tutorials/lab3-go/README.md)

#### Лабораторная 4

- **Цель работы**: Разработка базового SPA на React
- **Порядок показа**: показать две страницы фронтенда в браузере из `localhost` и в `GitHub Pages`, фильтрация заявок. Внести изменения в БД, показать их во фронтенде. Объяснить код компонентов, передаваемые props, вызовы fetch.
- **Контрольные вопросы**: react, props, компонент, элемент, состояние, хуки, жизненный цикл компонента
- **Deployment диаграмма** узлы: фронтенда, веб-сервиса, базы данных, web-сервера со статикой. Узлы соединить протоколами, компоненты фронтенда и бэкенда поместить в узлах, указать API между ними.
- **Задание**: Разработать две страницы фронтенд приложения на `React`, `TS` и подключить его к веб-сервису. Подготовить ТЗ на итоговую систему. 

Разработать базовый интерфейс приложения на `React` для `гостя`, аналогичный двум страницам из лабораторной работы №1 для просмотра `услуг`. При этом на странице списка `услуг` должны быть все обходимые фильтры (по диапазону дат, названию, цене) с фильтрацией на бэкенде. Использовать компоненты `React-Bootstrap`. Необходимо развернуть фронтенд на `GitHub Pages`.

В приложении должна быть навигационная панель `navbar` для списка базовых страниц, а также навигационной цепочки `breadcrumbs`, где отображается путь от базовой страницы к текущей. 

Содержимое карточек получать из веб-сервиса лабораторной №3. Ajax-запросы написать самостоятельно через `fetch`. Ограничение с `CORS` решить через проксирование `React`. В методах `fetch` предусмотреть получение данных из коллекции с `mock`-объектами при отсутствии доступа к вашему бэкенду (если он не поддерживает `HTTPS`).

* [Методические указания](/tutorials/lab4/lab4_tutorial.md). Переделать на TS
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

Добавление на странице услуг кнопки `Добавить` для внесения данной услуги в новую заявку. Добавление страницы `конструктора` заявки, где можно удалить уже добавленные в заявку услуги, поменять их количество или `подтвердить` заявку. После кнопки `подтвердить` новая заявка создается в БД, а до этого хранится в `Redux Toolkit`

* [Методические указания Redux](/tutorials/lab5/lab5_tutorial.md)
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
- **Диаграммы**: диаграмма состояний для статусов `заявок` и диаграмма прецедентов. Актуализировать все диаграммы из лабораторных, все диаграммы должны соответствовать реализованной вами системе
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
6. **Заключение**
7. **Список использованных источников**  
8. **Приложение. Техническое задание**

#### Дополнительные задания
1. Индексы в БД, большое количество `услуг` (> 100000) и пагинация (+4 балла)
2. Адаптивность дизайна (+2 балла)
3. Кодогенерация из swagger (+2 балла)

### Темы 2023:

#### Удаленные вычисления
1. Система заявок на вычисления: факториал, НОД и тд. `Услуги` - виды вычислений, `заявки` - запрос с входными данными и результатами.
2. Аналитическое моделирование потоков в метро `Услуги` - виды моделирования, `заявки` - запрос с входными данными и результатами.
3. Аналитическое моделирование загруженности сетевого оборудования `Услуги` - виды моделирования по оборудованию, `заявки` - запрос с входными данными и результатами.
4. Статистические расчеты. `Услуги` - статистические величины (мат ожидание, дисперсия и тд), `заявки` - данные для расчетов с результатом

#### Малый бизнес
1. Система заявок для поваров в быстром питании на приготовление. `Услуги` - виды блюд с указанием поваров, `заявки` - заказ на приготовление блюд.
2. Рецепты автоматического приготовления пищи. `Услуги` - продукты, `заявки` - рецепты 
3. Заявки от коллцентра мелкого бизнеса: менеджер-создатель заявки, исполнитель+курьер. `Услуги` - услуги данного бизнеса, `заявки` - заявки от клиентов на услуги.
4. Продажа очков. `Услуги` - свойства линз, `заявки` - заказы от покупателей на линзы
5. Книжное издательство. `Услуги` - работы издательства (печать, брошюрование и тд), `заявки` - заказы на издание книги

#### Компьютерные игры
1. Карточная игра Эволюция. `Услуги` - карты Эволюции, `заявки` - карточные ходы соперников в игре
2. Автоматический подбор игроков для игры. `Услуги` - карты, игровые локации, `заявки` - игры, список участников автоматически собирается из поданных ими запросов

#### Химическое производство
1. Оборудование для химических лабораторий. `Услуги` - лабораторное оборудование, `заявки` - заявки на приобретение
2. One-pot синтезы. `Услуги` - исходные вещества, `заявки` - проведение синтеза при заданных условиях
3. Производство косметики. `Услуги` - вещества для производства, `заявки` - виды косметики с указанием состава
4. Производство лекарств из готовых веществ. `Услуги` - действующие и др вещества, `заявки` - составляющие лекарств
5. Производство красок из красителей. `Услуги` - готовые красители и др вещества, `заявки` - виды красок (батик, гуаш) по цветам

#### Производство
1. Система заявок на производстве
2. Продажа авиазапчастей для бизнес-джетов. `Услуги` - авиазапчасти, `заявки` - заявки на приобретение комплектующих. Связаться с Антоновым А.И.
3. Поставки комплектующий для производства электроавтомобилей. `Услуги` - комплектующие, `заявки` - заявки от завода по сборке к заводам комплектующих
4. Поставки деталей для сборки CubeSat. `Услуги` - детали для CubeSat, `заявки` - заявки на сборку CubeSat
5. Склад комплектующих. `Услуги` - список комлектующих для хранения с размером для места, `заявки` - заявки на доставку и отгрузку комплектующих 
6. Кораблестроительная программа. `Услуги` - классы кораблей, `заявки` - заказ кораблей от государства 

#### Электронные услуги
1. Визовый центр РФ - заявки на визы. `Услуги` - виды виз, `заявки` - заявки на получение нужной визы.
2. Автоматический контроль паспортов на границе. `Услуги` - паспорта, которые заведены в системе, `заявки` - факты пересечения границы по паспорту
3. Банковские счета. `Услуги` - банковские договоры, `заявки` - открытие новых счетов в рамках банковского договора

#### ИТ услуги
1. Консалтинг по ИТ безопасности. `Услуги` - виды консалтинга, `заявки` - заявки на проведение консалтинга
2. Обслуживание ИТ инфраструктуры. `Услуги` - виды проводимых работ, `заявки` - заявки по настройке сетевого оборудованию, виртуалки и тд
3. Мониторинг ИТ угроз. `Услуги` - виды угроз, `заявки` - факты возникновения угроз в подразделении компании
4. Сайт КТС. `Услуги` - виды разработки, `заявки` - заявки от заказчиков
5. Аренда виртуальных машин. `Услуги` - тарифы на аренду, `заявки` - заявки на аренду кластера машин

#### Транспорт
1. Заявки контроля маршрута беспилотных летательных аппаратов. `Услуги` - районы города, `заявки` - заявки на пролет объекта в данной районе в определенное время.
2. Контроль нарушений ПДД самокатами и др средств индивидуальной мобильности с двигателем. `Услуги` - виды нарушений и штрафы для них, `заявки` - факты нарушения из средств фиксации
3. Приобретение абонементов на общественный транспорт. `Услуги` - виды абонементов на различный транспорт, `заявки` - приобретение абонементов на карту
4. Проезд по транспортной карте 90 минут. `Услуги` - маршруты транспорта, `заявки` - проезд по транспортной карте в 90 минут с указанием маршрута транспорта

#### Космос
1. Заявки на доставку грузов на Марс на Starship. `Услуги` - товары, доставляемы на Марс на Starship, `заявки` - заявки на конкретный объем товаров
2. Учет перелетов Starship между земными космодромами. `Услуги` - конкретные космические корабли, `заявки` - заявки на перелет кораблей между площадками
3. Отчеты по добыче ресурсов (вода, углекислый газ, гелий и тд) на Луне. `Услуги` - добываемые ресурсы, `заявки` - месячные отчеты об объеме добычи в конкретном месте Луны
4. Заявки на переходы космических аппаратов на различные орбиты. `Услуги` - доступные орбиты, `заявки` - заявки на переход спутников на орбиту.
5. Автоматические межпланетные станции (АМС). `Услуги` - космические объекты, `заявки` - космические полеты АМС к этим объектам.
6. Станции на поверхности Марса. `Услуги` - географические объекты на поверхности Марса, `заявки` - автоматические марсианские станции, успех/потеря/работает
7. Эволюция ближайших к Солнцу звезд. `Услуги` - ближайшие звезды, `заявки` - события в эволюции этих звезд, при завершении `заявки` меняется таблица `услуг`.
8. Запуск спутников с космодрома Восточный. `Услуги` - имеющиеся заявки на доставку КА на орбиту, `заявки` - полет ракеты-носителя с указанной полезной нагрузкой
9. Астрономия для астрологов. `Услуги` - планеты, `заявки` - присутствие в созвездии указанных планет в данное время
10. Анализ реликтового излучения. `Услуги` - анализируемые спектры, `заявки` - космические аппараты для анализа реликтового излучения

#### МГТУ
1. Технадзор строительных объектов МГТУ. `Услуги` - строящиеся здания в кампусе МГТУ, `заявки` - проверки технадзора данных строек
2. Мероприятия музея МГТУ. `Услуги` - виды проводимых в музее мероприятий, `заявки` - заявки для групп на данные мероприятия
3. Бронирование аудиторий МГТУ. `Услуги` - аудитории МГТУ, `заявки` - заявки на бронирование аудиторий под проводимое мероприятие
4. Парковка МГТУ. `Услуги` - парковки МГТУ, `заявки` - заявки на пропуск/абонементы автомобилей на парковки
5. Запись на спортивные курсы МГТУ. `Услуги` - еженедельные группы по курсам, `заявки` - запись на группы
6. Сайт конференции. `Услуги` - авторы статей, `заявки` - заявка на публикацию статьи
7. Проведение митапов по ИИ. `Услуги` - спикеры, `заявки` - митапы 

#### Социальные услуги
1. Трудоустройство женщин в отпуске по уходу за ребенком. `Услуги` - вакансии для женщин с детьми, `заявки` - подача заявок на вакансии от женщин
2. Система трудоустройства для инвалидов. `Услуги` - вакансии для инвалидов, `заявки` - подача заявок на вакансию от инвалидов
3. Система социальной помощи инвалидам - доставка еды, сопровождение на мероприятие и тд. `Услуги` - оказываемые услуги, `заявки` - заявки на них от инвалидов
4. Заказы на молочную кухню (для детей). `Услуги` - виды продуктов, `заявки` - заявки от родителей 
5. Справочник по медицине катастроф и первой помощи. `Услуги` - виды первой помощи, `заявки` - виды поражений при чрезвычайных ситуациях

#### История
1. История ВОВ - участники ВОВ и их привязка к архивным документам (личные карточки, наградные, ЖБД итд). `Услуги` - архивные документы, `заявки` - привязка участника с наградой/событием к документу
2. Высочайшие вершины Земли и их покорители. `Услуги` - знаменитые покорители, `заявки` - экспедиции по покорению вершин. 
3. Система археологов - находки и их привязка к раскопкам. `Услуги` - места археологических раскопок, `заявки` - факты находок предметов с группировкой по экспедиции
4. Эпоха географических открытий. `Услуги` - первооткрыватели, `заявки` - их открытия
5. Животные рекордсмены. `Услуги` - виды рекордов (самые большие, самые быстрые и тд), `заявки` - жившие виды животных 
6. Морские битвы на Тихом океане. `Услуги` - конкретные корабли, `заявки` - составы соединений с адмиралом и указанием победа/поражение
7. Походы викингов. `Услуги` - города, `заявки` - походы викингов
8. Древнерусские княжества. `Услуги` - княжества, `заявки` - правители княжеств по периодам
9. Освоение Дальнего Востока и Сибири. `Услуги` - населенные пункты и географические объекты, `заявки` - экспедиции и походы в XVI-XVIII веках
10. Палеонтология. `Услуги` - геологические периоды, `заявки` - ископаемые животные (отряды-рода)

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
