# Домашнее задание к лекции «Docker Compose»

Реализован работа сервера из домашего задания `CRUD: Склады и запасы` с помощь котейниизации с использованием:

* Nginx 
* PostgreSQL запускается до Django.
* Django запускается через Gunicorn

![контейниеры Docker](/img/pic1.png)

* [Docerfile](/stocks_products/Dockerfile) для `django` в директории stocks_products
* [Docerfile](/nginx/Dockerfile) для `nginx` в директории nginx
* [Конфигурация](/nginx/nginx.conf) для `nginx` в директории nginx
* Настройки для базы данных следует указать в файле переменых окружения [.env.db](/.env.db)
* Права доступа для django следует указать в файле переменных окружения [.env.dev](/.env.dev)
* [Docer-compose файл](\docker-compose.yml) в корне проекта


Для проверки работоспособности сревера реализована загрузка вебстраницы с сообщением "Stock logistic!!!"

Для проверки работсопосбности REST API можно использовать команды из [requests-examples.http](stocks_products/requests-examples.http)


## Развёртывание проекта

Для развёртывания могут потребоваться sudo права. Команды следует выполнять в корневом каталоге проекта.


* сборка:

```bash
 docker-compose build
```

* запук:

```bash:
 docker-compose up -d
```

* применение миграций  

```bash:
 docker-compose exec web python manage.py migrate --noinput
```

* остановка сервера и удаление контейнеров:

```bash:
docker-compose down -v
```