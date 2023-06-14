# leyn_store

1) Склонировать репозиторий с гита: git clone ...
2) Создать виртуальное окружение: python -m venv venv
3) Подключить виртуальное окружение в настройках Pycharm
4) Скачать PostgreSQL с оф сайта: https://www.postgresql.org/
5) Скачать PgAdmin с оф сайта: https://www.pgadmin.org/
6) Создать базу данных: 
открыть командную строку от имени администратора
cd C:\Program Files\PostgreSQL\{version}\bin, где PostgreSQL, установлен
ввести psql -U postgres
ввести команды:
CREATE DATABASE store_db;
CREATE ROLE store_username with password 'store_password';
ALTER ROLE "store_username" WITH LOGIN;
GRANT ALL PRIVILEGES ON DATABASE "store_db" to store_username;
ALTER USER store_username CREATEDB;
Открыть pgAdmin4, перейти в store_db/Schemas, открыть свойства public и изменить поле owner на store_username
7)Установить все зависимости: В терминале PyCharm написать команду pip install -r requirements.txt
8)Создать миграции: python manage.py makemigrations
9)Применить миграции: python manage.py migrate
10)Загрузить фикстуры: python manage.py loaddata products/fixtures/goods.json|categories.json
11)Создать суперпользователя: python manage.py createsuperuser
12)Подключить вебхук для платежной системы stripe: 
???скачать stripe-cli: https://github.com/stripe/stripe-cli/releases/tag/v1.14.7
???разархевировать и перенести файл stripe.exe в дерикторию проекта
ввести команду в терминале: stripe login
перейти по ссылке и авторизироваться ???drudakov03@mail.ru diplomleeynn1A???
ввести команду: stripe listen --forward-to 127.0.0.1:8000/webhook/stripe/
13)Запустить сайт: python manage.py runserver
14)Авторезироваться под аккаунтом суперюзера, перейти в панель администратора, открыть вкладку products, пересохранить все товары.
ГОТОВО
