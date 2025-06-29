## Описание
Яндекс Практикум. Проект. API для Yatube

## Установка

#### 1. Клонирование проекта
```powershell
git clone https://github.com/maksimon17/api_final_yatube.git
```
#### 2. Перейти в папку проекта и создать виртуальное окружение
```powershell
cd ./api_final_yatube/
python -m venv venv
```
#### 3. Активировать виртуальное окружение
```powershell
# для OS Lunix и MacOS
source venv/bin/activate

# для OS Windows
source venv/Scripts/activate
```
#### 4. Установить зависимости
```powershell
python3 -m pip install --upgrade pip
pip install -r requirements.txt
```
#### 5. Выполнить миграции на уровне проекта:
```powershell
cd yatube_api
python3 manage.py makemigrations
python3 manage.py migrate
```
#### 6. Запустить проект:
```powershell
python manage.py runserver
```

## Примеры запросов

Получение токена

Отправить POST-запрос на адрес `api/v1/jwt/create/` и передать 2 поля в `data`:

1. `username` - имя пользователя.
2. `password` - пароль пользователя.

Создание поста

Отправить POST-запрос на адрес `api/v1/posts/` и передать обязательное поле `text`, в заголовке указать `Authorization`:`Bearer <токен>`.

1. Пример запроса:

   ```json
   {
     "text": "Пост о тестировании проекта"
   }
   ```

2. Пример ответа:

   ```json
   {
     "id": 1,
     "author": "maksimon17",
     "text": "Пост о тестировании проекта",
     "pub_date": "2025-05-16T12:00:22.021094Z",
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
     "text": "Тест комментария"
   }
   ```

2. Пример ответа:

   ```json
   {
     "id": 1,
     "author": "maksimon17",
     "text": "Тест комментария",
     "created": "2025-05-16T12:00:22.021094Z",
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