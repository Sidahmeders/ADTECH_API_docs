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
            "patients_id": "arrayList",
            "_id": "string",
            "first_name": "string", 
            "last_name": "string", 
            "email": "string", 
            "birth_date": "string",
            "year_of_study": "integer",
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
    "identity_card": "buffer" <required>,
    "phone_number": "integer",
    "gender": "string" <required>,
    "faculty": "string",
    "country": "string",
    "year_of_study": "integer",
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
            "patients_id": "arrayList,
            "dentist_id": "string",
            "role": "string"
        }
    }
}
```
