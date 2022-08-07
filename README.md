## **Что за проекту**
Yamdb - это проект, который собирает отзывы пользователей на произведения.

## **Шаблон наполнения env-файла**
* DB_ENGINE
* DB_NAME
* POSTGRES_USERя
* P0OSTGRES_PASSWORD
* DB_HOST
* DB_PORT

## **Описание команд для запуска приложения в контейнерах**
1. Загрузить Docker-образ
>docker pull airatns/yamdb:v1

2. Запустить контейнер
sudo docker run -d -p 8080:80 airatns/yamdb:v1

>docker run --name <имя контейнера> -it -p 8000:8000 yamdb

3. Проверить работу проекта
>http://localhost/

## **Описание команд для заполнения базы данными**
1. Зайти в консоль сервиса web в папку с manage.py

2. Залить данные из файла с дампом
>docker-compose exec web python manage.py loaddata fixtures.json
