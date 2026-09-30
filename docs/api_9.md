# API: Удаление объекта  (`DELETE /objects/{id}`)

Ресурс для удаления объекта.
---

> **Важно:** Базовый URL вынесен в Postman-Environment как переменная `{{base_url}}`.  
> Пример значения: `https://api.restful-api.dev`.


## Описание запроса

| Параметр | Значение |
| --- | --- |
| **Метод** | `DELETE` |
| **URL** | `{{base_url}}/objects/{id}`|
| **Аутентификация** | Не требуется |
| **Accept** | `application/json` |

>Accept указывает ожидаемый формат ответа. Content-Type не передается - DELETE не имеет  тела запроса.

---

### Примеры запросов

Для конкретного объекта (например, id=1)
```bash
curl -X DELETE "https://api.restful-api.dev/objects/1"
```

В Postman использовать: {{base_url}}/objects/{id}
где {id} — уникальный идентификатор объекта, существующего в системе.

## Коды ответов и поведение
|Код	|Статус	|Поведение API	|Что документировать для разработчика|
| --- | --- | --- | --- |
|200 |OK	|Успех	|Возвращает JSON с сообщением "message": "Object with id = {id} has been deleted." |	
|404 |Not Found |Объект не найден |Возвращает  "error": "The Object with id = {id} doesn't exist. " |


## Пример успешного ответа (200 OK)
Пример ответа для объекта с id=1:
```json
{
    "message": "Object with id = 1 has been deleted."
}
```
## Пример ответа при ошибке 404 (Not Found)
```json
{
    "error": "Object with id = 2 doesn't exist."
}
```

## Связанные эндпоинты

- `GET /objects` — получить список объектов.
- `GET /objects/{id}` — получить один объект по id.
- `GET /objects?id=...` — получить объекты по заданным параметрам.
- `POST /objects` — создать объект.
- `PUT /objects/{id}` — обновить объект полностью.
- `PATCH /objects/{id}` — частично обновить объект.
