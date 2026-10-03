
## Коды ответов и поведение
|Код	|Статус	|Описание |Поведение API| Метод |
| --- | --- | --- | --- | --- |
|200 |OK	|Успех	|Возвращает JSON-массив `objects`| GET /objects|
|200 |OK	|Успех	|Возвращает JSON с данными объекта (нестандартно, в реальном API должно быть 201)  | POST /objects|
|401 |Unauthorized	| Невалидный или истёкший JWT (только при ?auth-type=jwt)	|Возвращает "error": "Invalid or expired JWT token." | |
|403 | Forbidden |Доступ запрещен (нет `api_key`) |Возвращает  "error": "API key is missing. To use this API, include your API key in the 'x-api-key' header. If you don’t have one, create an account and get your API key here: https://restful-api.dev/dashboard " | |
|403 |Forbidden	|Доступ запрещен (неверный `api_key`)	|Возвращает "error": "Invalid API key. Please check your API key on the dashboard: https://restful-api.dev/dashboard" |	 |
|409 |Conflict	| Польхователь уже существует|Возвращает "error": "User already exists." | POST /register |

