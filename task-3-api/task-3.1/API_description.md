# Регистрация API

## HTTP метод + URL
POST /api/users/register

## Описание
Метод предназначем для регистрации нового пользователя в системе

## Входные данные
### Request body

firstName
  - Type: string
  - Required: yes
  - Restrictions: maximum length 50 characters
  - Description: имя пользователя

lastName
  - Type: string
  - Required: yes
  - Restrictions: maximum length 50 characters
  - Description: фамилия пользователя

Email
  - Type: string
  - Required: yes
  - Restrictions:
      valid email format
      unique value
  - Description: email пользователя

Password:
  - Type: string
  - Required: yes
  - Restrictions:
  - minimum length 8 characters
  - Description: пароль пользователя

confirmPassword:
  - Type: string
  - Required: yes
  - Restrictions:
  - must match password
  - Description: подтверждение пароля
## Выходные параметры при успешном ответе
### 201 Сreated
### Response Body
userId
  - Type: integer
  - Required: yes
  - Description: уникальный идентификатор пользователя

message
  - Type: string
  - Required: yes
  - Description: сообщение о результате операции
## Выходные параметры при ответе с ошибкой
errorCode
  - Type: string
  - Required: yes
  - Restrictions:
      - uppercase format
      - snake_case
  - Description: код ошибки

message
  - Type: string
  - Required: yes
  - Restrictions:
    - maximum length 255 characters
  - Description: описание ошибки

details
  - Type: array of strings
  - Required: no
  - Restrictions:
      - may contain multiple validation errors
  - Description: дополнительная информация об ошибках валидации
## Описание ошибок - коды ответов
### 400 Bad request
Некорректные входные данные
Возможные причины:
  - обязательные поля не заполнены
  - неверный email
  - пароль слишком короткий
  - Password и cofirmPassword не совпадают
### 409 Conflict
Пользователь с таким Email уже существует
### 500 Internal Server Error
Внутрення ошибка сервера

## Пример запроса
```JSON
{
  "firstName": "Ivan",
  "lastName": "Petrov",
  "email": "ivan.petrov@example.com",
  "password": "StrongPass123",
  "confirmPassword": "StrongPass123"
}
```

## Пример ответа
```JSON
{ 
  "userId": 101, 
  "message": "User successfully registered" 
}
```
 
