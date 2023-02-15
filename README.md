# API для Yatube

[![Python](https://img.shields.io/badge/-Python-464641?style=flat-square&logo=Python)](https://www.python.org/)
[![Django](https://img.shields.io/badge/Django-464646?style=flat-square&logo=django)](https://www.djangoproject.com/)
[![Pytest](https://img.shields.io/badge/Pytest-464646?style=flat-square&logo=pytest)](https://docs.pytest.org/en/6.2.x/)
[![Postman](https://img.shields.io/badge/Postman-464646?style=flat-square&logo=postman)](https://www.postman.com/)

### Oписание

Социальная сеть для публикации личных записей. 
Реализация REST API для проекта Yatube.

### Функционал

- Подписка и отписка от авторизованного пользователя;
- Авторизованный пользователь просматривает посты, создавёт новые,
 удаляет и изменяет их;
- Просмотр сообществ;
- Комментирование, просмотр, удаление и обновление комментариев;
- Фильтрация по полям.

### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/Vladislav-Rybachuk/api_final_yatube.git
```

```
cd api_final_yatube
```
Cоздать и активировать виртуальное окружение:

```
python3 -m venv env
```

* Если у вас Linux/macOS

    ```
    source env/bin/activate
    ```

* Если у вас windows

    ```
    source env/scripts/activate
    ```

```
python3 -m pip install --upgrade pip
```

Установить зависимости:

   ```
   python3 -m pip install --upgrade pip
   pip install -r requirements.txt
   ```

Выполнить миграции:

```
python3 manage.py migrate
```

Запустить проект:

```
python3 manage.py runserver
```
### Примеры запросов

Получение токена

Отправить POST-запрос на адрес `api/v1/jwt/create/` и передать 2 поля в `data`:

1. `username` - имя пользователя.
2. `password` - пароль пользователя.

Создание поста

Отправить POST-запрос на адрес `api/v1/posts/` и передать обязательное поле `text`, в заголовке указать `Authorization`:`Bearer <токен>`.

1. Пример запроса:

   ```json
   {
     "text": "Мой первый пост."
   }
   ```
2. Пример ответа:

   ```json
   {
     "id": 2,
     "author": "Dmitrii",
     "text": "Мой первый пост.",
     "pub_date": "2023-01-22T12:00:22.021094Z",
     "image": null,
     "group": null
   }
   ```

Комментирование поста пользователя

Отправить POST-запрос на адрес `api/v1/posts/{post_id}/comments/` и передать обязательные поля `post` и `text`, в заголовке указать `Authorization`:`Bearer <токен>`.

1. Пример запроса:

   ```json
   {
     "post": 1,
     "text": "Тест"
   }
   ```  

2. Пример ответа:

   ```json
   {
     "id": 1,
     "author": "Dmitrii",
     "text": "Тест",
     "created": "2022-04-22T12:06:13.146875Z",
     "post": 1
   }
   ```

## Ресурсы

```python
# Документаия проекта
http://127.0.0.1:8000/redoc/
```

```python
# ПО для тестирования API, Postman
https://www.postman.com/
```