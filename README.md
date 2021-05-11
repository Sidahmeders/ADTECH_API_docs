# A-Dentech Endpoints


## **SignIn/Get a Single User**
```
GET https://adentech/users/login
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
    "data": {
        "user": {
            "patients_id": "arrayList",
            "_id": "string",
            "first_name": "string", 
            "last_name": "string", 
            "birth_date": "date",
            "email": "string", 
            "profile_image": "buffer",
            "identity_card": "buffer",
            "year_of_study": "integer",
            "phone_number": "integer"
            "gender": "string",
            "faculty": "string",
            "country": "string",
            "year_of_study": "integer",
            "grade": "string",
            "specialty": "string",
            "role": "string"
        }
    }
}
```

## **SignUp/Post a New User**
```
POST https://adentech/users/register
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
            "_id": "string",
            "role": "string"
        }
    }
}
```

## **Return/Get all the patients a user have**
```
GET https://adentech/users/patients
```

`Request Parameters`
```
(
    user_id: "string" <required>
)
```

> Response Object
```
{
    "data": {
        "users": [
            {
                "_id": "string",
                "dentist_id": "string", 
                first_name: "string",
                last_name: "string",
                gender: "string",    
                age: "string",
                address: "string",
                phone_number: "string",
                email: "string",
                marital_status: "string",
                job: "string",
                faculty_access: "string",
                apointment: "string"
            },
            {
                ...
                ...
            },
            ...
        ]
    }
}
```

## **Add apointment to an existing user OR create a new user with apointment**
```
POST https://adentech/users/patients/apointments
```


## ** Return/Get all the apointments a user have**
```
GET https://adentech/users/patients/apointments
```


## **Add/Post a new Patient/ **
```
POST https://adentech/patients
```

