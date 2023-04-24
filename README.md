# API for Yatube

[![Python](https://img.shields.io/badge/-Python-464641?style=flat-square&logo=Python)](https://www.python.org/)
[![Django](https://img.shields.io/badge/Django-464646?style=flat-square&logo=django)](https://www.djangoproject.com/)
[![Pytest](https://img.shields.io/badge/Pytest-464646?style=flat-square&logo=pytest)](https://docs.pytest.org/en/6.2.x/)
[![Postman](https://img.shields.io/badge/Postman-464646?style=flat-square&logo=postman)](https://www.postman.com/)

### Description

Social network for publishing personal records.
REST API implementation for the Yatube project.

### Functional

- Subscribing and unsubscribing from an authorized user;
- An authorized user views posts, creates new ones,
  removes and modifies them;
- View communities;
- Commenting, viewing, deleting and updating comments;
- Filtering by fields;

### How to start a project:

Clone the repository and change into it on the command line:

```
git clone https://github.com/Vladislav-Rybachuk/api_final_yatube.git
```

```
cd api_final_yatube
```
Create and activate virtual environment:

```
python3 -m venv env
```

* If you have MacOS/Linux

    ```
    source env/bin/activate
    ```

* If you have windows

    ```
    source env/scripts/activate
    ```

Install dependencies:

   ```
   python3 -m pip install --upgrade pip
   pip install -r requirements.txt
   ```

Install dependencies:

```
python3 manage.py migrate
```

Run project:

```
python3 manage.py runserver
```
### Request examples

Getting a token

Send a POST request to `api/v1/jwt/create/` and send 2 fields to `data`:

1. `username` 
2. `password` 

Create a post

Send a POST request to `api/v1/posts/` and pass the required  `text` field, specify `Authorization`:`Bearer <token>` in the header.

1. Request example:

   ```json
   {
     "text": "My first post."
   }
   ```
2. Answer example:

   ```json
   {
     "id": 2,
     "author": "Dmitrii",
     "text": "My first post.",
     "pub_date": "2023-01-22T12:00:22.021094Z",
     "image": null,
     "group": null
   }
   ```

Commenting on a user post

Send a POST request to `api/v1/posts/{post_id}/comments/` and pass the required fields `post` and `text`, specify `Authorization`:`Bearer <token>` in the header.

1. Request example:

   ```json
   {
     "post": 1,
     "text": "Text"
   }
   ```  

2. Answer example:

   ```json
   {
     "id": 1,
     "author": "Dmitrii",
     "text": "Теxt",
     "created": "2022-04-22T12:06:13.146875Z",
     "post": 1
   }
   ```

## Resource

```python
# Project documentation
http://127.0.0.1:8000/redoc/
```

```python
# API testing software, Postman
https://www.postman.com/
```
