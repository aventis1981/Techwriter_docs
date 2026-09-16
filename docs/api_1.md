#### Service title: 
GET/users

#### Goal:
This API returns the whole list of users in system.

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



