# API для проекта YamDB

![yamdb workflow](https://github.com/1karp/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

## Описание проекта

Реализация API для проекта YamDB.
Документация лежит по адресу http://localhost/redoc/


### Список некоторых используемых технологий/пакетов:

* Django==2.2.16
* django-filter==21.1
* djangorestframework==3.12.4
* djangorestframework-simplejwt
* requests
* PyJWT
* Docker
* Nginx
* Gunicorn


### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone git@github.com:1karp/infra_sp2.git
cd infra_sp2/infra
```

Затем нужно создать файл .env с переменными окружения, необходимыми для работы приложения, данные для примера можно посмотреть в файле .env.example:

```
nano .env
```



Запустить Docker-compose

```
docker-compose up -d
```
Будут созданы и запущены в фоновом режиме необходимые для работы приложения контейнеры (db, web, nginx).


Затем нужно внутри контейнера web выполнить миграции, создать суперпользователя и собрать статику:

```
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py createsuperuser
docker-compose exec web python manage.py collectstatic --no-input 
```




## Примеры запросов

```
Категории: GET /api/v1/categories/
Жанры: GET /api/v1/genres/
Произведения:GET  /api/v1/titles/
Отзывы: GET /api/v1/titles/{title_id}/reviews/
Комментарии: GET /api/v1/titles/{title_id}/reviews/{review_id}/comments/
```
