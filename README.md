# A-Dentech mobile-app Endpoints

## **SignIn/get a Single User**
```
POST https://adentech/users/login
```

`Request Body Parameters`
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
            phone_number: "integer",
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

`Request Body Parameters`
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
    faculty: "string" <required>,
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
            first_name: "string",
            last_name: "string", 
            birth_date: "date",
            email: "string",
            profile_image: "buffer",
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

## **Return/Get all the patients a user have**
```
GET https://adentech/users/patients?user_id
```

`Request Query Parameters`
```
(
    user_id: "string" <required>
)

Headers: { auth-token } <required>
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
                appointment: "date"
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

## Add/Update appointment to an existing patient OR create a new patient with appointment
```
POST https://adentech/users/patients/appointments
```

`Request Body Parameters`
```
(
    patient_id: "string" <required> (if patient exist),
    user_id: "string" <required> (if patient_does not exist),
    appointment: "date" <required>
)

Headers: { auth-token } <required>
```

> Response Object
```
{
    data: {
        patient: {
            _id: "string",
            full_name: "string",
            appointment: "date",
            phone_number: "integer"
        }
    }
}
```

## Return/Get all the appointments a user have
```
GET https://adentech/users/patients/appointments?user_id
```

`Request Query Parameters`
```
(
    user_id: "string" <required>
)

Headers: { auth-token } <required>
```

> Response Object
```
{
    data: {
        patients: [
            {
                _id: "string",
                appointment: "date",
                full_name: "string",
                phone_number: "integer"
            },
            { ... }
        ]
    }
}
```

## Add/Post a new Patient
```
POST https://adentech/patients
```

`Request Body Parameters`
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
    appointment: "date"
)

Headers: { auth-token } <required>
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
            appointment: "date",
            date_of_modification: "date",
            date_of_creation: "date",
            __v: "integer"
        }
    }
}
```

## Add/Post Patients Record

### *** add generalExamination collections ***

#### examenEndobuccal collection

```
POST https://adentech/generalExamination/examenEndobuccal
```

`Request Body Parameters`
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

Headers: { auth-token } <required>
```

> Response Object
```
{}
```

#### examenExobuccal collection

```
POST https://adentech/generalExamination/examenExobuccal
```

`Request Body Parameters`
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

Headers: { auth-token } <required>
```

> Response Object
```
{}
```

#### medicalAnamnese collection

```
POST https://adentech/generalExamination/medicalAnamnese
```

`Request Body Parameters`
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

Headers: { auth-token } <required>
```

> Response Object
```
{}
```

### *** add OCE collections ***

#### carieDentaire collection

```
POST https://adentech/oce/carieDentaire
```

`Request Body Parameters`
```
(
    user_id: "string" <required>,
    patient_id: "string" <required>,
    tooth_number: "integer",
    motif_consultation: "string",
    histoire_maladie: "string",
    class_black: "integer",
    class_sit_sta: "string",
    diagnostic_positive: "string",
    diagnostic_etiologique: "string",
    diagnostic_différentiel: "string",
    decision_therapeutique: "string"
)

Headers: { auth-token } <required>
```

> Response Object
```
{}
```

#### signsEtRadio collection

```
POST https://adentech/oce/signsEtRadio
```

`Request Body Parameters`
```
(
    user_id: "string" <required>,
    patient_id: "string" <required>,
    tooth_number: "integer",
    sign_subjective_provoque: "string",
    sign_subjective_spontanne: "string",
    sign_subjective_autres: "string",
    sign_objective_vitalite: "string",
    sign_objective_percussion_axial: "string",
    sign_objective_percussion_lateral: "string",
    sign_objective_palpation_fond_vestibule: "string",
    sign_objective_mobilite: "string",
    radio_panoramique: "string",
    radio_retroslviolsire_couronne: "string",
    radio_retroslviolsire_racine: "string"
)

Headers: { auth-token } <required>
```

> Response Object
```
{}
```

#### traumatismeDentaireDents collection

```
POST https://adentech/oce/traumatismeDentaireDents
```

`Request Body Parameters`
```
(
    user_id: "string" <required>,
    patient_id: "string" <required>,
    tooth_number: "integer",
    description_tiente: "string",
    description_etat_dent: "string",
    description_trait_fracture: "string",
    lesion_associees: "string",
    diagnostic_tissu_dur_pulpe: "string",
    diagnostic_complication_paro: "string",
    diagnostic_pulpaire: "string",
    decision_therapeutique: "string",
    pronostic: "string"
)

Headers: { auth-token } <required>
```

> Response Object
```
{}
```

#### traumatismeDentairePatient collection

```
POST https://adentech/oce/traumatismeDentairePatient
```

`Request Body Parameters`
```
(
    user_id: "string" <required>,
    patient_id: "string" <required>,
    motif_consultation: "string",
    etat_general_actuel: "string",
    date_traumatisme: "date",
    cause_tarumatiame: "string",
    circonstance_traumatisme: "string",
    etat_generale_cephale: "string",
    etat_general_pert_conscience: "string",
    etat_generale_nauses: "string",
    etat_generale_saignement: "string",
    pronostic: "string"
)

Headers: { auth-token } <required>
```

> Response Object
```
{}
```

### *** add ODF collections ***

#### moulage collection

```
POST https://adentech/odf/moulage
```

`Request Body Parameters`
```
(
    user_id: "string" <required>,
    patient_id: "string" <required>,
    maxillaire_forme: "string",
    maxillaire_symetrie: "string",
    maxillaire_profondeur_voute: "string",
    maxillaire_malposition: "string",
    maxillaire_ddm: "string",
    maxillaire_indice_ponte_D4G4: "string",
    maxillaire_indice_ponte_D6G6: "string",
    maxillaire_indice_doumange: "string",
    mandubule_forme: "string",
    mandubule_symetrie: "string",
    mandubule_malposition: "string",
    mandubule_indice_pont_D4G4: "string",
    mandubule_indice_pont_D6G6: "string"
)

Headers: { auth-token } <required>
```

> Response Object
```
{}
```

#### anemnese collection

```
POST https://adentech/odf/anemnese
```

`Request Body Parameters`
```
(
    user_id: "string" <required>,
    patient_id: "string" <required>,
    motif_consultation: "string",
    antecedente_odf_duree: "string",
    antecedente_odf_type: "string",
    tics_habitude: "string"
)

Headers: { auth-token } <required>
```

> Response Object
```
{}
```

#### diagnosticTraitement collection

```
POST https://adentech/odf/diagnosticTraitement
```

`Request Body Parameters`
```
(
    user_id: "string" <required>,
    patient_id: "string" <required>,
    dp_class_squelettique: "string",
    dp_forme_clinique: "string",
    dp_typologie_faciale: "string",
    dp_direction_croissance_faciale: "string",
    dp_direction_croissance_mandibulaire: "string",
    dp_anomalies_associees: "string",
    diagnostic_etiologique: "string",
    diagnostic_differentiel: "string",
    plan_trt_objective_squeletique: "string",
    plan_trt_objective_fonctionnels: "string",
    plan_trt_objective_occlusaux: "string",
    plan_trt_objective_esthetiques: "string",
    plan_trt_principes_moyens: "string",
    plan_trt_contension : "string",
    plan_trt_pronostic: "string"
)

Headers: { auth-token } <required>
```

> Response Object
```
{}
```

#### endobuccal collection

```
POST https://adentech/odf/endobuccal
```

`Request Body Parameters`
```
(
    user_id: "string" <required>,
    patient_id: "string" <required>,
    hygien_bucaux_dentaire: "string",
    probleme_paro: "string",
    langue_volume: "string",
    langue_situation: "string",
    langue_frien_linguale: "string",
    age_dentaire: "integer",
    satde_dentitin: "string",
    chemin_fermeture: "string"
)

Headers: { auth-token } <required>
```

> Response Object
```
{}
```

#### exobuccal collection

```
POST https://adentech/odf/exobuccal
```

`Request Body Parameters`
```
(
    user_id: "string" <required>,
    patient_id: "string" <required>,
    symetrie_faciale: "string",
    parallelisme_trois_ligne: "string",
    typologie_facial: "string",
    profile_izard: "string",
    profile_ricketts: "string",
    muscilature_joues: "string",
    muscilature_levres_repos: "string",
    muscilature_levres_fonction: "string",
    sillons_slm: "string",
    sillons_sng: "string"
)

Headers: { auth-token } <required>
```

> Response Object
```
{}
```

#### resulteCepholomettrie collection

```
POST https://adentech/odf/exobuccal
```

`Request Body Parameters`
```
(
    user_id: "string" <required>,
    patient_id: "string" <required>,
    rapport_cranio_faciaux_sagittaux_sna: "string",
    rapport_cranio_faciaux_sagittaux_snb: "string",
    rapport_cranio_faciaux_sagittaux_anb: "string",
    rapport_cranio_faciaux_sagittaux_convexite: "string",
    rapport_cranio_faciaux_sagittaux_se: "string",
    rapport_cranio_faciaux_sagittaux_sl: "string",
    rapport_cranio_faciaux_sagittaux_scg: "string",
    rapport_cranio_faciaux_sagittaux_s_fpm: "string",
    mensuration_basales_fpm_ena: "string",
    mensuration_basales_at_chateau: "string",
    mensuration_basales_longeur_mandibule: "string",
    mensuration_basales_xipm: "string",
    direction_croissance_fma_tweed: "string",
    direction_croissance_axe_brodie: "string",
    direction_croissance_axe_facial_Rickeets: "string",
    mensurations_verticales_hes: "string",
    mensurations_verticales_hei: "string",
    mensurations_verticales_hauteur_ramale: "string",
    mensurations_verticales_ena_xipm: "string",
    papport_dento_squellettes_6ptv: "string",
    rapport_dento_squelletique_if: "string",
    rapport_dento_squellettes_im: "string",
    rapport_dento_squellettes_ia_po_angle: "string",
    rapport_dento_squellettes_ia_oo_distance: "string",
    rapport_dento_squellettes_ia_po_angle: "string",
    rapport_dento_squellettes_ia_po_distance: "string",
    rapport_dento_dentaire_ii: "string",
    esthetique_ls_ligne_e: "string",
    esthetique_li_ligne_e: "string",
    esthetique_angle_z: "string"
)

Headers: { auth-token } <required>
```

> Response Object
```
{}
```

### *** add PARO collections ***

#### examenGingival collection

```
POST https://adentech/paro/examenGingival
```

`Request Body Parameters`
```
(
    user_id: "string" <required>,
    patient_id: "string" <required>,
    sector_gingival: "string",
    contour: "string",
    couleur: "string",
    volume: "string",
    aspect: "string",
    consistance: "string",
    hga: "integer",
    pma: "integer",
    pi: "integer",
    gi: "integer",
    sbi: "integer",
    cote_l: "string"
)

Headers: { auth-token } <required>
```

> Response Object
```
{}
```

#### examenSondage collection

```
POST https://adentech/paro/examenSondage
```

`Request Body Parameters`
```
(
    user_id: "string" <required>,
    patient_id: "string" <required>,
    pv1: "string",
    pv2: "string",
    pv3: "string",
    pp1: "string",
    pp2: "string",
    pp3: "string",
    rv: "string",
    rp: "string",
    tooth_number: "string"
)

Headers: { auth-token } <required>
```

> Response Object
```
{}
```

#### indices collection

```
POST https://adentech/paro/indices
```

`Request Body Parameters`
```
(
    user_id: "string" <required>,
    patient_id: "string" <required>,
    insertion_frien_sup: "string",
    insertion_frien_inf: "string",
    insertion_frien_lingual: "string",
    insertion_frien_autres: "string",
    atteints_furcation_1: "string",
    atteints_furcation_2: "string",
    atteints_furcation_3: "string",
    atteints_furcation_4: "string",
    indice_abrasion_1: "string",
    indice_abrasion_2: "string",
    indice_abrasion_3: "string",
    indice_abrasion_4: "string",
    indice_abrasion_5: "string",
    indice_mobilite_1: "string",
    indice_mobilite_2: "string",
    indice_mobilite_3: "string",
    indice_mobilite_4: "string",
    indice_recession_1: "string",
    indice_recession_2: "string",
    indice_recession_3: "string",
    indice_recession_4: "string",
    biotype_parodontal: "string"
)

Headers: { auth-token } <required>
```

> Response Object
```
{}
```

#### interpretationRadiologic collection

```
POST https://adentech/paro/interpretationRadiologic
```

`Request Body Parameters`
```
(
    user_id: "string" <required>,
    patient_id: "string" <required>,
    desmodente: "string",
    lamina_dura: "string",
    lyse_profondeur_superficielle: "string",
    lyse_profondeur_profonde: "string",
    lyse_profondeur_terminal: "string",
    lyse_forme_horizontal: "string",
    lyse_forme_vertical: "string",
    lyse_forme_vertical: "string",
    rapport_cr_legerement_augmente: "string",
    rapport_cr_augmente: "string",
    rapport_cr_tres_augmente: "string",
    rapport_dentodentaire: "string",
    malposition_dentaire: "string",
    megration_d_premaire: "string",
    megration_d_secondaire: "string",
    trabeculation_osseuses_max: "string",
    trabeculation_osseuses_mand: "string"
)

Headers: { auth-token } <required>
```

> Response Object
```
{}
```

#### diagnosticTraitement collection

```
POST https://adentech/paro/interpretationRadiologic
```

`Request Body Parameters`
```
(
    user_id: "string" <required>,
    patient_id: "string" <required>,
    diagnostic_etiologique: "string",
    diagnostic_positive: "string",
    diagnostic_deffirentiel: "string",
    traitement_urgence: "string",
    traitement_initial: "string",
    revaluation: "string",
    traitement_correctif: "string",
    maintenance: "string",
    pronostic_global: "string",
    pronostic_unitaire: "string"
)

Headers: { auth-token } <required>
```

> Response Object
```
{}
```

### *** add Prothese collections ***

#### edentePartielle collection

```
POST https://adentech/prothese/edentePartielle
```

`Request Body Parameters`
```
(
    user_id: "string" <required>,
    patient_id: "string" <required>,
    motif_consultation: "string",
    kenedy_apelgate_maxillaire: "string",
    kenedy_apelgate_mandibule: "string",
    decision_therapeutique: "string"
)

Headers: { auth-token } <required>
```

> Response Object
```
{}
```

#### edenteTotal collection

```
POST https://adentech/prothese/edenteTotal
```

`Request Body Parameters`
```
(
    user_id: "string" <required>,
    patient_id: "string" <required>,
    motif_consultation: "string"
    linda_maxillaire: "string"
    linda_mandibule: "string"
    decision_therapeutique: "string
)

Headers: { auth-token } <required>
```

> Response Object
```
{}
```

## get Patients Record

### *** get generalExamination collections ***

#### examenEndobuccal collection
```
GET https://adentech/generalExamination/examenEndobuccal?patient_id
```
### examenExobuccal collection
```
GET https://adentech/generalExamination/examenExobuccal?patient_id
```
### medicalAnamnese collection
```
GET https://adentech/generalExamination/medicalAnamnese?patient_id
```

`Request Query Parameters`
```
(
    patient_id: "string" <required>,
)

Headers: { auth-token } <required>
```

> Response Object
```
{
    data: {
        patientRecord: { ... }
    }
}
```


## update Patients Record

### *** update generalExamination collections ***

#### examenEndobuccal collection
```
PUT https://adentech/generalExamination/examenEndobuccal
```
### examenExobuccal collection
```
PUT https://adentech/generalExamination/examenExobuccal
```
### medicalAnamnese collection
```
PUT https://adentech/generalExamination/medicalAnamnese
```

`Request Query Parameters`
```
(
    patient_id: "string" <required>,
    [record_entry1]: ...,
    [record_enrty2]: ...,
    ....
)

Headers: { auth-token } <required>
```

> Response Object
```
{
    data: {
        patientRecord: { ... }
    }
}
```

## error response Object

```
{
    error: {
        type: "error type",
        messgae: "error message"
    }
}
```
