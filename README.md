# A-Dentech Endpoints


## **SignIn/Get a Single User**
```
GET /https://adentech/users/login
```

`Request Parameters`
```    
(
    "email": "string" <required>,
    "password": "string" <required>
)
```

> Response Object
```
{    
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c",
    "data":{
        "user": {
            "_id": 99,
            "first_name": "John", 
            "last_name": "Markus", 
            "email": "example@gmail.com", 
            "birth_date": "1995-05-23",
            "year_of_study": 2,
            "phone_number": "0555403010"
        }
    }
}
```

## **SignUp/Post a New User**
```
POST /https://adentech/users/register
```

`Request Parameters`
```    
(
    "first_name": "string" <required>,
    "last_name": "string" <required>,
    "birth_date": "date" <required>,
    "email": "string" <required>,
    "password": "string" <required>,
    "password2": "string" <required>,
    "profile_image": "buffer",
    "identity_card": "buffer",
    "phone_number": "number",
    "gender": "string" <required>,
    "faculty": "string",
    "country": "string",
    "year_of_study": "date",
    "grade": "string",
    "specialty": "string"
)
```

> Response Object
```
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c",
    data: {
        user: {
            "dentist_id": 99,
            "role": "basic"
        }
    }
}
```

## Parameters Data Type, Preference & Format

|             |dentist_id |birth_date  |first_name|last_name|phone_number  |
|-------------|-----------|------------|----------|---------|--------------|
|**data_type**|Integer    |Date        |String    |String   |String        |
|**prefernce**|required   |required    |required  |required |optional      |
|**format**   |999        |"1999-06-25"|"John"    |"Doe"    |"05-55-44...."|
