# Infra_SP2

В данном проекте реализовал задачу по сборке и запуску **YaMDb** в контейнерах **Docker**. Создан дамп базы.

YaMDb - это проект, который собирает отзывы пользователей на произведения.

Бэкенд для проекта YaMDb реализован по ссылке:

>*https://github.com/airatns/api_yamdb*

## **Стек технологий**

Python, Django, Docker, Gunicorn, Nginx, Ubuntu

## **Подготовка:**

Клонировать репозиторий и перейти в него в командной строке:

>*git clone git@github.com:airatns/infra_sp2.git*

Прописать параметры окружения в файле .env:

* SECRET_KEY=<SECRET_KEY>

* DEBUG=<True | False>

* DB_ENGINE=django.db.backends.postgresql

* DB_NAME=postgres

* POSTGRES_USER=postgres

* POSTGRES_PASSWORD=postgres

* DB_HOST=db

* DB_PORT=5432

## **Сборка и запуск приложения в контейнерах:**

Перейти в папку и запустить утилиту **docker-compose**:

>*cd infra/*

>*docker-compose up -d --build*

По окончании работы **docker-compose** сообщит, что контейнеры собраны и запущены:

>*Creating infra_db_1 ... done*

>*Creating infra_web_1 ... done*

>*Creating infra_nginx_1 ... done*

Выполнить миграции, создать суперпользователя и собрать статику:

>*docker-compose exec web python manage.py migrate*

>*docker-compose exec web python manage.py createsuperuser*

>*docker-compose exec web python manage.py collectstatic --no-input*

## **Наполнение базы тестовыми данными:**

Перейти из текущей папки в папку с **manage.py** и загрузить тестовые данные:

>*cd ..*

>*cd api_yamdb/*

>*docker-compose exec web python manage.py loaddata fixtures.json*

## **Проверить, что приложение успешно разворачивается:**

>*http://localhost/admin/*
