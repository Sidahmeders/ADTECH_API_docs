
# A-Dentech Endpoints


## **Get All Users**
```
GET /https://adentech/users
```

 `Request Parameters`
```
(
    email: "string",
    is_admin: boolean,
)

Headers: {
    "token": "<required>"
}
```

> `Response Objects`
```
[
    {"dentist_id": 1, "first_name": "John", ...},
    {"dentist_id": 2, "first_name": "Sara", ...},
    {"dentist_id": 3, "first_name": "Karl", ...},
    ...
]
```

## **Get a Single User**
```
GET /https://adentech/users/login
```

`Request Parameters`
```    
(
    email: "string",
    password: "string"
)
```

> Response Object
```
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
    "user": {
        "dentist_id": 99,
        "first_name": "John", 
        "last_name": "Markus", 
        "email": "example@gmail.com", 
        "birth_date": "1995-05-23",
        "year_of_study": 2,
        "phone_number": "0555403010"
    }
}
```

## **Create/Post New User**
```
POST /https://adentech/users/register
```

`Request Parameters`
```    
(
    f_name: "string",
    l_name: "string",
    birth_date: "year-month-day",
    email: "string",
    password: "string",
    ...
    ...
)
```

> Response Object
```
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c"
    "user": {
        "dentist_id": 99,
        "first_name": "John", 
        "last_name": "Markus", 
        "email": "example@gmail.com", 
        "birth_date": "1995-05-23",
        "year_of_study": 2,
        "phone_number": "0555403010"
    }
}
```

## Parameters Data Type, Preference & Format

|             |dentist_id |birth_date  |first_name|last_name|phone_number  |
|-------------|-----------|------------|----------|---------|--------------|
|**data_type**|Integer    |Date        |String    |String   |String        |
|**prefernce**|required   |required    |required  |required |optional      |
|**format**   |999        |"1999-06-25"|"John"    |"Doe"    |"05-55-44...."|