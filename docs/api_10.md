# API: Просмотр коллекций  (`GET /collections`)

Ресурс для просмотра коллекций пользователя. Метод требует аутентификации с помощью api_key.

> **Важно:** Базовый URL вынесен в Postman-Environment как переменная `{{base_url}}`.  
> Пример значения: `https://api.restful-api.dev`.

## Описание запроса

| Параметр | Значение |
| --- | --- |
| **Метод** | `GET` |
| **URL** | `{{base_url}}/collections` |
| **Аутентификация** | `api_key` - обязательно.  Bearer JWT - опционально (работает вместе с `api_key`, но не вместо него) |
| **Accept** | `application/json` |
| **Формат ответа** | JSON-массив объектов `collection` |

>Accept указывает ожидаемый формат ответа. Content-Type не передается - GET не имеет  тела запроса.

---

### Запрос cURL

```bash
curl -X GET "https://api.restful-api.dev/collections" \
  -H "x-api-key: {{api_key}}"
```

## Коды ответов и поведение
|Код	|Статус	|Описание |Поведение API|
| --- | --- | --- | --- |
|200 |OK	|Успех	|Возвращает JSON-массив объектов `collection`|	
|403 | Forbidden |Доступ запрещен (нет `api_key`) |Возвращает  "error": "API key is missing. To use this API, include your API key in the 'x-api-key' header. If you don’t have one, create an account and get your API key here: https://restful-api.dev/dashboard " |
|403 |Forbidden	|Доступ запрещен (неверный `api_key`)	|Возвращает "error": "Invalid API key. Please check your API key on the dashboard: https://restful-api.dev/dashboard" |	
|401 |Unauthorized	| Невалидный или истёкший JWT (только при ?auth-type=jwt)	|Возвращает "error": "Invalid or expired JWT token." |

>- Важно: для авторизации необходимо использовать `api_key`. `Api_key` пользователь получает при регистрации на сервисе `https://api.restful-api.dev`. 
>`Api_key` не имеет срока годности и служит средством аутентификации для ряда приватных методов, в том числе:
>     - `GET /collections`
>     - `GET /collections/{collection}/objects`
>- Опционально **вместе** с `api_key` может использоваться также `JWT-token`. `JWT-токен` создается при регистрации пользователя с помощью метода `POST /register` 
>или аутентификации существующего пользователя с помощью метода `POST /login`. `JWT`-токен имеет срок годности, установленный при его запросе.


## Пример успешного ответа (200 OK)
Пример ответа - массив с 2 ресурсами `collection` (каждая коллекция содержит по 2 объекта):
```json
[
    {
        "collectionName": "MyCollection1",
        "objectCount": 2
    },
    {
        "collectionName": "MyCollection2",
        "objectCount": 2
    }
]
```
## Условие для успешного ответа 
Коллекции с объектами будут показаны в том случае, если они были ранее созданы пользователем.
Коллекция создается с помощью метода `POST /collections/{collection}/objects`: 
данный метод создает объект и добавляет его в указанную коллекцию, либо одновременно создает коллекцию, если она еще не существует.
 

## Структура ключевых полей
|Поле	|Тип	|Описание	|
| --- | --- | --- | 
|collectionName|string| Наименование коллекции	|
|objectCount	|number|	Количество объектов в коллекции | 

## Связанные эндпоинты

- `POST /collections/{collection}/objects` — создать объект и коллекцию.
- `GET /collections/{collection}/objects` — получить список объектов в коллекции.

