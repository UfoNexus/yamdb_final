![example event parameter](https://github.com/UfoNexus/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg?event=push)

# Проект «api_yamdb»
Ссыла на развернутый проект - http://158.160.1.8/

## 1 Описание

Проект предназначен для создания API для приложеия YaMDb.
YaMDb собирает отзывы (Review) пользователей на произведения (Titles).
Произведения делятся на категории: «Книги», «Фильмы», «Музыка».

API предоставляет возможность взаимодействовать с социальной сетью по следующим направлениям:

  - авторизовываться
  - создавать свои отзывы и управлять ими (изменять/удалять)
  - комментировать отзывы других пользователей
  - просматривать комментарии к своему и другим отзывам
  - просматривать произведения и жанры произведений

## 2 Наполнение виртуального окружения переменными

В корне проекта создать файл .env\
Структура файла:
- DJANGO_SECRET_KEY=<добавляем секретный ключ, который генерирует Django>
- DB_ENGINE=<указываем бэкэнд базы, например django.db.backends.postgresql>
- DB_NAME=<имя базы данных>
- POSTGRES_USER=<имя пользователя БД>
- POSTGRES_PASSWORD=<пароль БД>
- DB_HOST=<название сервиса (контейнера docker)>
- DB_PORT=<порт для подключения к БД>

## 3 Алгоритм запуска проекта локально

Перейти в директорию /infra/. Выполнить команду:
```
docker compose up -d --build
```

Перейти в директорию /api_yamdb/. Выполнить следующие команды:
```
docker compose exec web python manage.py migrate
docker compose exec web python manage.py collectstatic
```
Создание нового суперпользователя:
```
docker compose exec web python manage.py createsuperuser
```

## 4 Заполнение БД данными из файла JSON
```
docker compose exec web python manage.py loaddata fixtures.json 
```

### Автор проекта
https://github.com/UfoNexus
