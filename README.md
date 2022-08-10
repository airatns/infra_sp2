# Infra_SP2

В данном проекте реализовал задачу по сборке и запуску **YaMDb** в контейнерах **Docker**. Создан дамп базы.

YaMDb - это проект, который собирает отзывы пользователей на произведения.

Бэкенд для проекта YaMDb реализован по ссылке:

>*https://github.com/airatns/api_yamdb*

## **Регистрация нового пользователя**
Для регистрации сделайте POST-запрос с данными **email** и **username** на адрес:

>*http://127.0.0.1:8000/api/v1/auth/signup/*

Затем на ваш электронный почтовый ящик придёт **confirmation_code**.

## **Получение JWT-токена**
Для аутентификации сделайте POST-запрос с данными **username** и **confirmation_code** на адрес:

>*http://127.0.0.1:8000/api/v1/auth/token/*

Вам будет выдан **token** для запросов к API.

Срок действия токена **14 дней**.

### **Пример использования JWT-токена**

>*Bearer ey8Df...*

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

Создать суперпользователя:

>*docker-compose exec web python manage.py createsuperuser*

Наполнение базы тестовыми данными:

>*docker-compose exec web python manage.py loaddata fixtures.json*

## **Проверить, что приложение успешно разворачивается:**

>*http://localhost/admin/*
