#### Service title: 
GET/users

#### Goal:
This API returns the whole list of users in system.

> **Important:** API does not support the filtration by fields (name, email, address ect). To get a user send `GET /users/{id}`.


#### Request parameters:

<table>
  <!-- Шапка таблицы: названия колонок -->
  <thead>
    <tr>
      <th>Parameter</th>                 <!-- Колонка 1: название режима -->
      <th>Type</th>     <!-- Колонка 2: подробности -->
	  <th>Obligatory</th>     
	  <th>Description</th>     
    </tr>
  </thead>
  <!-- Тело таблицы: строки с данными -->
  <tbody>
    <!-- Строка 1 -->
    <tr>
      <td><strong>-<strong></td>      
      <td><strong>-<strong></td>
	  <td><strong>-<strong></td>
	  <td>Endpoint does nor accept any parameters for filtration.</td>
    </tr>
  </tbody>
</table>


#### Request headers 

| Header | Value | Obligatory | Comment |
|-----------|----------|--------------|------------|
| `Accept` | `application/json` | no | It is recommended to indecate explicitly. Server returns JSON in case of `Accept: */*`. |
| `Authorization` | — | no | - |

#### Supported Formats

!!! warning "API limitation"
    API does not support content negotiation. All `Accept` values return 
     JSON with code `200`. This is a deviation from HTTP standard.

API works **with JSON only**. The header `Accept` is ignored: server returns always 
`Content-Type: application/json` regerdless the client's request. 

| Request header | Expected behaviour | Actual behaviour |
|---|---|---|
| `Accept: application/json` | `200 OK`, JSON | ✅ `200 OK`, JSON |
| `Accept: application/xml` | `406 Not Acceptable` | ❌ `200 OK`, JSON (standard deviation) |
| `Accept: */*` | `200 OK`, дефолтный формат | ✅ `200 OK`, JSON |

#### Request example (Postman / cURL)

##### Postman

```http
GET https://jsonplaceholder.typicode.com/users
Accept: application/json

##### cURL 
curl -X GET \
  https://jsonplaceholder.typicode.com/users \
  -H "Accept: application/json"
  
  
##### Successful response 
 - Status: 200 OK

- Content type: application/json; charset=utf-8

- Respponse body: array of objects -  users (10 records).

- Example of short response:
[
  {
    "id": 1,
    "name": "Leanne Graham",
    "username": "Bret",
    "email": "Sincere@april.biz",
    "address": {
      "street": "Kulas Light",
      "suite": "Apt. 556",
      "city": "Gwenborough",
      "zipcode": "92998-3874",
      "geo": {
        "lat": "-37.3159",
        "lng": "81.1496"
      }
    },
    "phone": "1-770-736-8031 x56442",
    "website": "hildegard.org",
    "company": {
      "name": "Romaguera-Crona",
      "catchPhrase": "Multi-layered client-server neural-net",
      "bs": "harness real-time e-markets"
    }
  }
]



