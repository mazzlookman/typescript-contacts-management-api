# User API Spec

## Register User

Endpoint: POST /api/users

Request Body:
```json
{
  "email": "bella@test.com",
  "password": "strong",
  "name": "Bella Rizky"
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
    "email": "bella@test.com",
    "name": "Bella Rizky"
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
      "email": "Email must not blank"
    },
    {
      "name": "Name must not blank"
    }
  ]
}
```

## Login User

Endpoint: POST /api/users/login

Request Body:
```json
{
  "email": "bella@test.com",
  "password": "strong"
}
```

Response Body:
`Success`:
```json
{
  "code": 200,
  "status": "OK",
  "data": {
    "email": "bella@test.com",
    "name": "Bella Rizky",
    "token": "uuid"
  }
}
```

`Failed`:
```json
{
  "code": 401,
  "status": "Unauthorized",
  "errors": "Username or password wrong"
}
```

## Get User

Endpoint: GET /api/users/current

Request Header:
- X-API-TOKEN: token

Response Body: <br>
`Success`:
```json
{
  "code": 200,
  "status": "OK",
  "data": {
    "email": "bella@test.com",
    "name": "Bella Rizky"
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

## Update User

Endpoint: PATCH /api/users/current

Request Header:
- X-API-TOKEN: token

Request Body:
```json
{
  "password": "strong", // optional
  "name": "Bella Rizky" // optional
}
```

Response Body: <br>
`Success`:
```json
{
  "code": 200,
  "status": "OK",
  "data": {
    "email": "bella@test.com",
    "name": "Bella Rizky"
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

## Logout User

Endpoint: DELETE /api/users/current

Request Header:
- X-API-TOKEN: token

Response Body: <br>
`Success`:
```json
{
  "code": 200,
  "status": "OK",
  "data": {
    "is_logged_out": true
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