
## Коды ответов и поведение
|Код	|Статус	|Описание |Поведение API| Метод |
| --- | --- | --- | --- | --- |
|**200** |OK	| `GET /objects`| Успех |	Возвращает JSON-массив `objects`|
|<span style="color: #5F9ED1;">***200***</span> |OK	| `POST /objects`|  Объект создан	|Возвращает JSON с данными объекта *(<span style="color: #5F9ED1;">нестандартно, в реальном API должно быть 201)</span>*  |
|**401** |Unauthorized	| `GET /collections` | Невалидный или истёкший JWT (только при ?auth-type=jwt)	|Возвращает "error": "Invalid or expired JWT token." | 
|**403** | Forbidden | `GET /collections` | Доступ запрещен (нет `api_key`) |Возвращает  "error": "API key is missing. To use this API, include your API key in the 'x-api-key' header. If you don’t have one, create an account and get your API key here: https://restful-api.dev/dashboard " | 
|**403** |Forbidden	|`GET /collections` | Доступ запрещен (неверный `api_key`)	|Возвращает "error": "Invalid API key. Please check your API key on the dashboard: https://restful-api.dev/dashboard" |	 
|**405** |Method not allowed|  `POST /collections` | Метод не разрешен (`collection` создается с помощью другого метода: `POST/ collections/{collectionName}/objects`)|Возвращает JSON с данными (timestamp, status, error, path) |
|**409** |Conflict	|  POST /register | Пользователь уже существует|Возвращает "error": "User already exists." |

<button type="button" style="background-color: #4682B4; color: white; border: none; padding: 8px 16px; border-radius: 4px; cursor: pointer;">Посмотреть пример</button>

