# Проект «API для Yatube»

### Краткое описание проекта
Учебный проект API для социальной сети. Пользователи могут публиковать посты, просматривать чужие посты, подписываться на авторов и комментировать их записи. 
Для аутентификации используются JWT-токены. Аутентифицированным пользователям разрешено изменение и удаление своего контента; в остальных случаях доступ предоставляется только для чтения.


### **Стек**
![python version](https://img.shields.io/badge/Python-3.7-green)
![django version](https://img.shields.io/badge/Django-2.2-green)
![djangorestframework version](https://img.shields.io/badge/DRF-3.12-green)
![djoser version](https://img.shields.io/badge/djoser-2.1-green)
![simplejwt version](https://img.shields.io/badge/DRFsimplejwt-4.7-green)

### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/Antonros/api_final_yatube.git
```
```
cd api_final_yatube
```
Cоздать и активировать виртуальное окружение:
```
python -m venv venv
```
```
source venv/Scripts/activate
```
```
python -m pip install --upgrade pip
```    

Установить зависимости из файла requirements.txt:
``` 
pip install -r requirements.txt
```   

Выполнить миграции:
```
python manage.py migrate
```       
    
Запустить проект:
```
python manage.py runserver
```

### Примеры использования

Придумайте новую пару «логин-пароль» и отправьте POST-запрос на http://127.0.0.1:8000/api/v1/users/, передав их в полях username и password.

Теперь можно получить токен: отправьте POST-запрос на эндпоинт .../api/v1/jwt/create/, передав действующий логин и пароль в полях username и password. 

API вернёт JWT-токен:

```
{
    "refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoicmVmcmVzaCIsImV4cCI6MTYyMDk0MTQ3NywianRpIjoiODUzYzE5MTg5NzMwNDQwNTk1ZjI3ZTBmOTAzZDcxZDEiLCJ1c2VyX2lkIjoxfQ.0vJBPIUZG4MjeU_Q-mhr5Gqjx7sFlO6AShlfeINK8nA",
    "access": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ0b2tlbl90eXBlIjoiYWNjZXNzIiwiZXhwIjoxNjIwODU1Mzc3LCJqdGkiOiJkY2EwNmRiYTEzNWQ0ZjNiODdiZmQ3YzU2Y2ZjNGE0YiIsInVzZXJfaWQiOjF9.eZfkpeNVfKLzBY7U0h5gMdTwUnGP3LjRn5g8EIvWlVg"
} 
```
Токен вернётся в поле access, а данные из поля refresh пригодятся для обновления токена. Этот токен также надо будет передавать в заголовке каждого запроса, в поле Authorization. Перед самим токеном должно стоять ключевое слово Bearer и пробел.

Пример POST-запроса. Добавление нового поста. Анонимные запросы запрещены.

```
POST /api/v1/posts/

Request samples

{
    "text": "Вечером собрались в редакции «Русской мысли», чтобы поговорить о народном театре. Проект Шехтеля всем нравится.",
    "group": 1
} 
```

Пример GET-запроса. Получить список всех публикаций. При указании параметров limit и offset выдача должна работать с пагинацией.
```
GET /api/v1/posts/
GET /api/v1/posts/?limit=2&offset=1
```

Пример POST-запроса. Добавление нового комментария к публикации. Анонимные запросы запрещены. Где post_id - номер поста.

```
POST /api/v1/posts/{post_id}/comments/

Request samples

{
    "text": "Новый комментарий к посту"
} 
```

Пример GET-запроса. Получение всех комментариев к публикации. Где post_id - номер поста.
```
GET /api/v1/posts/{post_id}/comments/
```




### Документация к API проекта Yatube доступна по адресу
```
http://127.0.0.1:8000/redoc/
```

### **Автор**
[Росляков Антон](https://github.com/Antonros/)
