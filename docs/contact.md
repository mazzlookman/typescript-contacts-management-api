# Contact API Spec

## Create Contact

Endpoint: POST /api/contacts

Request Header:
- X-API-TOKEN: token

Request Body:
```json
{
  "first_name": "Bella Rizky",
  "last_name": "Kharisma",
  "email": "bella@test.com",
  "phone": "088212348765"
}
```

Response Body: <br>
`Success`:
```json
{
  "code": 201,
  "status": "Created",
  "data": {
    "id": 1,
    "first_name": "Bella Rizky",
    "last_name": "Kharisma",
    "email": "bella@test.com",
    "phone": "088212348765"
  }
}
```

`Failed`:
```json
{
  "code": 422,
  "status": "Unprocessable Entity",
  "errors": [
    {
      "first_name": "First name must not blank"
    },
    {
      "phone": "Phone must not blank"
    }
  ]
}
```

## Get Contact

Endpoint: GET /api/contacts/:id

Request Header:
- X-API-TOKEN: token

Response Body: <br>
`Success`:
```json
{
  "code": "200",
  "status": "OK",
  "data": {
    "first_name": "Bella Rizky",
    "last_name": "Kharisma",
    "email": "bella@test.com",
    "phone": "088212348765"
  }
}
```

`Failed`:
```json
{
  "code": 404,
  "status": "Not Found",
  "errors": "No contact found"
}
```

## Update Contact

Endpoint: PUT /api/contacts/:id

Request Header:
- X-API-TOKEN: token

Request Body:
```json
{
  "first_name": "Bella Rizky",
  "last_name": "Kharisma",
  "email": "bella@test.com",
  "phone": "088212348765"
}
```

Response Body: <br>
`Success`:
```json
{
  "code": "200",
  "status": "OK",
  "data": {
    "first_name": "Bella Rizky",
    "last_name": "Kharisma",
    "email": "bella@test.com",
    "phone": "088212348765"
  }
}
```

`Failed`:
```json
{
  "code": 422,
  "status": "Unprocessable Entity",
  "errors": [
    {
      "first_name": "First name must not blank"
    },
    {
      "phone": "Phone must not blank"
    }
  ]
}
```

## Remove Contact

Endpoint: DELETE /api/contacts/:id

Request Header:
- X-API-TOKEN: token

Response Body: <br>
`Success`:
```json
{
  "code": "200",
  "status": "OK",
  "data": {
    "is_deleted": true
  }
}
```

`Failed`:
```json
{
  "code": 404,
  "status": "Not Found",
  "errors": "No contact found"
}
```

## Search Contact

Endpoint : GET /api/contacts

Query Parameter :
- name : string, contact first name or contact last name, optional
- phone : string, contact phone, optional
- email : string, contact email, optional
- page : number, default 1
- size : number, default 10

Request Header :
- X-API-TOKEN : token

Response Body: <br>
`Success`:

```json
{
  "code": "200",
  "status": "OK",
  "data": {
    "contacts": [
      {
        "id": 1,
        "first_name": "Bella Rizky",
        "last_name": "Kharisma",
        "email": "bella@test.com",
        "phone": "088212348765"
      },
      {
        "id": 2,
        "first_name": "Bella Rizky",
        "last_name": "Kharisma",
        "email": "bella@test.com",
        "phone": "088212348765"
      }
    ],
    "paging": {
      "current_page" : 1,
      "total_page" : 10,
      "size" : 10
    }
  }
}
```

`Failed`:
```json
{
  "code": 401,
  "status": "Unauthorized",
  "errors": "You must login first!"
}
```