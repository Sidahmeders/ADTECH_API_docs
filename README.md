# A-Dentech Endpoints


## **SignIn/Get a Single User**
```
GET https://adentech/users/login
```

`Request Parameters`
```    
(
    email: "string" <required>,
    password: "string" <required>
)
```

> Response Object
```
{
    token: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c",
    data: {
        user: {
            _id: "string",
            patients_id: "arrayList",
            first_name: "string", 
            last_name: "string", 
            birth_date: "date",
            email: "string", 
            profile_image: "buffer",
            identity_card: "buffer",
            year_of_study: "integer",
            phone_number: "integer"
            gender: "string",
            faculty: "string",
            country: "string",
            year_of_study: "integer",
            grade: "string",
            specialty: "string",
            role: "string"
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
    first_name: "string" <required>,
    last_name: "string" <required>,
    birth_date: "date" <required>,
    email: "string" <required>,
    password: "string" <required>,
    password2: "string" <required>,
    profile_image: "buffer",
    identity_card: "buffer" <required>,
    phone_number: "integer",
    gender: "string" <required>,
    faculty: "string",
    country: "string",
    year_of_study: "integer",
    grade: "string",
    specialty: "string"
)
```

> Response Object
```
{
    token: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c",
    data: {
        user: {
            _id: "string",
            patients_id: "arrayList",
            role: "string"
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

Headers: {
    auth-token: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c" <required>
}
```

> Response Object
```
{
    data: {
        patients: [
            {
                _id: "string",
                user_id: "string", 
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
                apointment: "date"
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

## Add apointment to an existing patient OR create a new patient with apointment
```
POST https://adentech/users/patients/apointments
```

`Request Parameters`
```
(
    user_id: "string" <required >(if dentist/user exist),
    apointment: "date" <required>
)

Headers: {
    auth-token: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c" <required>
}
```

> Response Object
```
{
    data: {
        patient: {
            _id: "string",
            full_name: "string",
            apointment: "date",
            phone_number: "integer"
        }
    }
}
```

## Return/Get all the apointments a user have
```
GET https://adentech/users/patients/apointments
```

`Request Parameters`
```
(
    user_id: "string" <required>
)

Headers: {
    auth-token: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c" <required>
}
```

> Response Object
```
{
    data: {
        patient: {
            _id: "string",
            apointment: "date",
            full_name: "string",
            phone_number: "integer"
        }
    }
}
```

## Add/Post a new Patient
```
POST https://adentech/patients
```

`Request Parameters`
```
(
    user_id: "string" <required>,
    first_name: "string" <required>,
    last_name: "string" <required>,
    gender: "string" <required>,
    age: "integer" <required>,
    address: "string",
    phone_number: "integer",
    email: "string",
    marital_status: "string",
    job: "string,
    faculty_access: "arrayList",
    apointment: "date"
)

Headers: {
    auth-token: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c" <required>
}
```

> Response Object
```
{
    data: {
        patient: {
            _id: "string",
            user_id: "string" <required>,
            first_name: "string" <required>,
            last_name: "string" <required>,
            gender: "string" <required>,
            age: "integer" <required>,
            address: "string",
            phone_number: "integer",
            email: "string",
            marital_status: "string",
            job: "string",
            faculty_access: "arrayList",
            apointment: "date",
            date_of_modification: "date",
            date_of_creation: "date",
            __v: "integer"
        }
    }
}
```

## Add/Post Patient Records

### add generalExamination collections

#### examenEndobuccal collection

```
POST https://adentech/generalExamination/examenEndobuccal
```

`Request Parameters`
```
(
    user_id: "string" <required>,
    patient_id: "string" <required>,
    overture_buccal: "string",
    hygiene_buccaux_dentaires: "string",
    etat_muqueuses_levre_sup: "string",
    etat_muqueuses_levre_inf: "string",
    etat_muqueuses_jugale: "string",
    etat_muqueuses_palatin: "string",
    etat_muqueuses_planche: "string",
    etat_muqueuses_langual: "string",
    etat_muqueuses_gengival: "string",
    etat_muqueuses_autres_lesion: "string",
)

Headers: {
    auth-token: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c" <required>
}
```

> Response Object
```
{}
```

#### examenExobuccal collection

```
POST https://adentech/generalExamination/examenExobuccal
```

`Request Parameters`
```
(
    user_id: "string" <required>,
    patient_id: "string" <required>,
    inspection_symetrie_faciale: "string",
    inspection_coloration_teguments: "string",
    inspection_autres: "string",
    palpation_atm_douleur: "string",
    palpation_atm_bruite_articulaire: "string",
    palpation_atm_jeu_condyliene: "string",
    palpation_atm_autres: "string",
    palpation_chaine_ganglionaire_localisation: "string",
    palpation_chaine_ganglionaire_nombre: "string",
    palpation_chaine_ganglionaire_taille: "string",
    palpation_chaine_ganglionaire_tempirature: "string",
    palpation_muscles_masseter: "string",
    palpation_muscles_temporal: "string",
    palpation_muscles_pterygoidien_interne: "string",
    palpation_muscles_pterygoidien_externe "string",
)

Headers: {
    auth-token: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c" <required>
}
```

> Response Object
```
{}
```

#### medicalAnamnese collection

```
POST https://adentech/generalExamination/medicalAnamnese
```

`Request Parameters`
```
(
    user_id: "string" <required>,
    patient_id: "string" <required>,
    motif_consultation: "string",
    mauvaise_habitude: "string",
    AG_personnel_maladie: "string",
    AG_personnel_traitement: "string",
    AG_mere_maladie: "string",
    AG_pere_traitement: "string",
    AG_mere_traitement: "string",
    AG_pere_maladie: "string",
    AS_personnel_odf: "string",
    AS_personnel_oce: "string",
    AS_personnel_pcb: "string",
    AS_personnel_proth: "string",
    AS_personnel_paro: "string",
    AS_mere_odf: "string",
    AS_mere_oce: "string",
    AS_mere_pcb: "string",
    AS_mere_paro: "string",
    AS_mere_proth: "string",
    AS_pere_odf: "string",
    AS_pere_oce: "string",
    AS_pere_pcb: "string",
    AS_pere_proth: "string",
    AS_pere_paro: "string",
    AS_autres: "string"
)

Headers: {
    auth-token: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c" <required>
}
```

> Response Object
```
{}
```

#### ----- collection

```
GET https://adentech/-----/-----
```

`Request Parameters`
```
(
    user_id: "string" <required>,
    patient_id: "string" <required>,
)
```

> Response Object
```
{}
```


