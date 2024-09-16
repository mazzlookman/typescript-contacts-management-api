# Address API Spec

## Create Address

Endpoint : POST /api/contacts/:idContact/addresses

Request Header :
- X-API-TOKEN : token

Request Body :
```json
{
  "street" : "Jalan Apa",
  "city" : "Kota Apa",
  "province" : "Provinsi Apa",
  "country" : "Negara Apa",
  "postal_code" : "23123"
}
```

Response Body: <br>
`Success`:
```json
{
  "code": 201,
  "status": "Created",
  "data" : {
    "id" : 1,
    "street" : "Jalan Apa",
    "city" : "Kota Apa",
    "province" : "Provinsi Apa",
    "country" : "Negara Apa",
    "postal_code" : "23123"
  }
}
```

`Failed`:
```json
{
  "code": 422,
  "status": "Unprocessable Entity",
  "errors" : [
    {
      "postal_code": "postal_code is required"
    }
  ]
}
```

## Get Address

Endpoint : GET /api/contacts/:idContact/addresses/:idAddress

Request Header :
- X-API-TOKEN : token

Response Body: <br>
`Success`:

```json
{
  "code": 200,
  "status": "OK",
  "data" : {
    "id" : 1,
    "street" : "Jalan Apa",
    "city" : "Kota Apa",
    "province" : "Provinsi Apa",
    "country" : "Negara Apa",
    "postal_code" : "23123"
  }
}
```

`Failed`:
```json
{
  "code": 404,
  "status": "Not Found",
  "errors": "No address found"
}
```

## Update Address

Endpoint : PUT /api/contacts/:idContact/addresses/:idAddress

Request Header :
- X-API-TOKEN : token

Request Body :
```json
{
  "street" : "Jalan Apa",
  "city" : "Kota Apa",
  "province" : "Provinsi Apa",
  "country" : "Negara Apa",
  "postal_code" : "23123"
}
```

Response Body: <br>
`Success`:
```json
{
  "code": 200,
  "status": "OK",
  "data" : {
    "id" : 1,
    "street" : "Jalan Apa",
    "city" : "Kota Apa",
    "province" : "Provinsi Apa",
    "country" : "Negara Apa",
    "postal_code" : "23123"
  }
}
```

`Failed`:
```json
{
  "code": 422,
  "status": "Unprocessable Entity",
  "errors" : [
    {
      "postal_code": "postal_code is required"
    }
  ]
}
```

## Remove Address

Endpoint : DELETE /api/contacts/:idContact/addresses/:idAddress

Request Header :
- X-API-TOKEN : token

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
  "errors": "No address found"
}
```

## List Address

Endpoint : GET /api/contacts/:idContact/addresses

Request Header :
- X-API-TOKEN : token

Response Body: <br>
`Success`:
```json
{
  "code": "200",
  "status": "OK",
  "data" : [
    {
      "id" : 1,
      "street" : "Jalan Apa",
      "city" : "Kota Apa",
      "province" : "Provinsi Apa",
      "country" : "Negara Apa",
      "postal_code" : "23123"
    },
    {
      "id" : 2,
      "street" : "Jalan Apa",
      "city" : "Kota Apa",
      "province" : "Provinsi Apa",
      "country" : "Negara Apa",
      "postal_code" : "23123"
    }
  ]
}
```

`Failed`:
```json
{
  "code": 404,
  "status": "Not Found",
  "errors": "No address found"
}
```