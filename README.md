# API Yatube v1

Первая версия API популярной социальной сети для блогеров **Yatube**. 
Предоставляет доступ к данным моделей Comment, Follow, Group, Post всем 
пользователям на чтение (кроме модели Follow), аутентифицированным по 
JWT-токену пользователям - на запись и изменение только своих данных 
(кроме модели Group)

### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/cnlis/api_final_yatube.git
```

```
cd api_final_yatube
```

Cоздать и активировать виртуальное окружение:

```
python3 -m venv env
```

```
source env/bin/activate
```

Установить зависимости из файла requirements.txt:

```
python3 -m pip install --upgrade pip
```

```
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

### Полная документация к API в формате ReDoc приведена по адресу /redoc/

### Примеры запросов

####GET-запрос на получение списка постов
```url
/api/v1/posts/
```
Параметры:
- limit - Количество публикаций на страницу
- offset - Номер страницы после которой начинать выдачу

Пример результата:
```json
{
    "count": 1,
    "next": null,
    "previous": "http://127.0.0.1:8000/api/v1/posts/?limit=1",
    "results": []
}
```

####POST-запрос на создание публикации
```url
/api/v1/posts/
```
Передаваемые данные:
- text (обязательное)
- image
- group

Пример результата:
```json
{
    "id": 1,
    "author": "kirill",
    "text": "sample post",
    "pub_date": "2022-01-13T13:31:22.380496Z",
    "image": null,
    "group": null
}
```

####GET-запрос на получение поста
```url
/api/v1/posts/{id}/
```

Пример результата:
```json
{
    "id": 1,
    "author": "kirill",
    "text": "sample post",
    "pub_date": "2022-01-13T13:31:22.380496Z",
    "image": null,
    "group": null
}
```

####POST-запрос на создание комментария
```url
/api/v1/posts/{id}/comments/
```

Передаваемые данные:
- text (обязательное)

Пример результата:
```json
{
    "id": 1,
    "author": "kirill",
    "post": 1,
    "text": "sample comment",
    "created": "2022-01-13T13:34:36.059131Z"
}
```

####GET-запрос на получение комментария
```url
/api/v1/posts/{id}/comments/{id}/
```

Пример результата:
```json
{
    "id": 1,
    "author": "kirill",
    "post": 1,
    "text": "sample comment",
    "created": "2022-01-13T13:34:36.059131Z"
}
```
