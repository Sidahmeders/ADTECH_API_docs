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
    profile_image: "buffer" <required>,
    identity_card: "buffer" <required>,
    phone_number: "integer",
    gender: "string" <required> [options]< male, female >,
    faculty: "string" <required>,
    country: "string",
    year_of_study: "integer" < 1-st, 2-nd, 3-rd, 4-th, 5-th, 6-th >,
    grade: "string" [options] < student, resident, assistant, master_assistant, professor >,
    specialty: "string" [options]< OCE, ODF, PARO, PROTHESE, PCB >
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
            role: "string" [options]< _unAuthorized, student, professor >
        }
    }
}
```

> ***Users Role***
```
_unAuthorized: can't create/update/delete new patients or patients record
_student: can create/update new patients and patients record
_assistant/_professor: can create/update new patients and patients record, plus some related utilities based on specialty (odf-chart, cephalometric-chart, etc...).
```

## **Return/Get all the patients a user have**
```
GET https://adentech/users/patients?user_id
```

`Request Query Parameters`
```
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
                specialty_access: "arrayList",
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
    first_name: "string" <required>,
    last_name: "string" <required>,
    gender: "string" <required> [options]< male, female >,
    age: "integer" <required>,
    address: "string",
    phone_number: "integer",
    email: "string",
    marital_status: "string" [options]< single, married >,
    job: "string,
    specialty_access: "arrayList" [options]< OCE, ODF, PARO, PROTHESE, PCB >,
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
            specialty_access: "arrayList",
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
    patient_id: "string" <required>,
    overture_buccal: "string" [option]<suffisant, <insuffisant, [number]>>,
    hygiene_buccaux_dentaires: "string" <required> [options]<mauvais, moyenne, bon>,
    etat_muqueuses_levre_sup: "string" [options]<RAS, [anything]>,
    etat_muqueuses_levre_inf: "string" [options]<RAS, [anything]>,
    etat_muqueuses_jugale: "string" [options]<RAS, [anything]>,
    etat_muqueuses_palatin: "string" [options]<RAS, [anything]>,
    etat_muqueuses_planche: "string" [options]<RAS, [anything]>,
    etat_muqueuses_langual: "string" [options]<RAS, [anything]>,
    etat_muqueuses_gengival: "string" [options]<RAS, [anything]>,
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
    patient_id: "string" <required>,
    inspection_symetrie_faciale: "string" [options]<normal, [anything]>,
    inspection_coloration_teguments: "string" [options]<normal, [anything]>,
    inspection_autres: "string",
    palpation_atm_douleur: "string" [options]<oui, no>,
    palpation_atm_bruite_articulaire: "string" [options]<claquement, craquement, crepitation, non>,
    palpation_atm_jeu_condyliene: "string" [options]<ressaut, asymetrique, symetrique, subluxation, [anything]>,
    palpation_atm_autres: "string",
    palpation_chaine_ganglionaire_localisation: "string" [options]<submental, submendibular, sous_angular, [anything]>,
    palpation_chaine_ganglionaire_nombre: "integer",
    palpation_chaine_ganglionaire_taille: "string",
    palpation_chaine_ganglionaire_tempirature: "string" [options]<chaude, froide>,
    palpation_muscles_masseter: "string" [options]<isotonique, hypertrophique, douleure, [anything]>,
    palpation_muscles_temporal: "string" [options]<isotonique, hypertrophique, douleure, [anything]>,
    palpation_muscles_pterygoidien_interne: "string" [options]<isotonique, hypertrophique, douleure, [anything]>,
    palpation_muscles_pterygoidien_externe "string" [options]<isotonique, hypertrophique, douleure, [anything]>,
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
    patient_id: "string" <required>,
    motif_consultation: "string" <required> [options]<fonctionnele, esthetique, douleure, [anything]>,
    mauvaise_habitude: "string",
    AG_personnel_maladie: "string" <required> [options]<non, [anything]>,
    AG_personnel_traitement: "string" <required> [options]<non, [anything]>,
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
    patient_id: "string" <required>,
    tooth_number: "integer" <required>,
    motif_consultation: "string" <required> [options]<fonctionnele, esthetique, douleure, [anything]>,
    histoire_maladie: "string",
    class_black: "integer" [options]<cl1, cl2, cl3, cl4, cl5>,
    class_sit_sta: "string" [options]<sit_sta[1<1, 2, 3, 4>, 2<1, 2, 3, 4>, 3<1, 2, 3, 4>]>,
    diagnostic_positive: "string" <required> [options]<baume1, baume2, baume3, baume4>,
    diagnostic_etiologique: "string" <required> [options]<carie, traumtisme, [anything]>,
    diagnostic_différentiel: "string" [options]<baume1, baume2, baume3, baume4>,
    decision_therapeutique: "string" <required> [options]<dentinogene, cementogene, osteocementogene>
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
    patient_id: "string" <required>,
    tooth_number: "integer" <required>,
    sign_subjective_provoque: "arrayList" [options]<chaude, froide, sucre, [anything]>,
    sign_subjective_spontanne: "string" [options]<ague, spontanne>,
    sign_subjective_autres: "string",
    sign_objective_vitalite: "string" [options]<postive, negtive>,
    sign_objective_percussion_axial: "string" [options]<postive, negtive>,
    sign_objective_percussion_lateral: "string" [options]<postive, negtive>,
    sign_objective_palpation_fond_vestibule: "string" [options]<postive, negtive>,
    sign_objective_mobilite: "string" [options]<postive, negtive>,
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
    patient_id: "string" <required>,
    tooth_number: "integer" <required>,
    description_tiente: "string",
    description_etat_dent: "string",
    description_trait_fracture: "string" [options]<tier_coronaire, tier_radiculare, tier_apical>,
    lesion_associees: "string" <required> [options]<fracture, alviolaire, fracture, basale, fracture, nasale, non>,
    diagnostic_tissu_dur_pulpe: "string" <required>,
    diagnostic_complication_paro: "string" <required>,
    diagnostic_pulpaire: "string" <required>,
    decision_therapeutique: "string" <required>,
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
    patient_id: "string" <required>,
    motif_consultation: "string" <required> [options]<fonctionnele, esthetique, douleure, [anything]>,
    etat_general_actuel: "string" <required>,
    date_traumatisme: "date" <required>,
    cause_tarumatiame: "string" <required>,
    circonstance_traumatisme: "string" <required>,
    etat_generale_cephale: "string" <required> [options]<oui, no>,
    etat_general_pert_conscience: "string" <required> [options]<oui, no>,
    etat_generale_nauses: "string" <required> [options]<oui, no>,
    etat_generale_saignement: "string" <required> [options]<oui, no>,
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
    patient_id: "string" <required>,
    maxillaire_forme: "string",
    maxillaire_symetrie: "string",
    maxillaire_profondeur_voute: "string",
    maxillaire_malposition: "string",
    maxillaire_ddm: "integer",
    maxillaire_indice_ponte_D4G4: "integer",
    maxillaire_indice_ponte_D6G6: "integer",
    maxillaire_indice_doumange: "integer",
    mandubule_forme: "string",
    mandubule_symetrie: "string",
    mandubule_malposition: "string",
    mandubule_indice_pont_D4G4: "integer",
    mandubule_indice_pont_D6G6: "integer"
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
    patient_id: "string" <required>,
    motif_consultation: "string" <required> [options]<fonctionnele, esthetique, douleure, [anything]>,
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
    patient_id: "string" <required>,
    dp_class_squelettique: "string" <required> [options]<cl1, cl2, cl3>,
    dp_forme_clinique: "string" <required>,
    dp_typologie_faciale: "string" <required> [options]<open_bite, normo_bite, deep_bite>,
    dp_direction_croissance_faciale: "string" <required> [options]<anterieur, posterieur, moyenne>,
    dp_direction_croissance_mandibulaire: "string" <required> [options]<anterieur, posterieur, moyenne>,
    dp_anomalies_associees: "string" <required>,
    diagnostic_etiologique: "string" <required>,
    diagnostic_differentiel: "string" <required>,
    plan_trt_objective_squeletique: "string" <required>,
    plan_trt_objective_fonctionnels: "string" <required>,
    plan_trt_objective_occlusaux: "string" <required>,
    plan_trt_objective_esthetiques: "string" <required>,
    plan_trt_principes_moyens: "string" <required>,
    plan_trt_contension : "string" <required>,
    plan_trt_pronostic: "string" <required>
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
    patient_id: "string" <required>,
    hygien_bucaux_dentaire: "string" <required> [options]<mauvais, moyenne, bon>,
    probleme_paro: "string" [options]<oui, no>,
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
POST https://adentech/odf/resulteCepholomettrie
```

`Request Body Parameters`
```
(
    patient_id: "string" <required>,
    rapport_cranio_faciaux_sagittaux_sna: "integer",
    rapport_cranio_faciaux_sagittaux_snb: "integer",
    rapport_cranio_faciaux_sagittaux_anb: "integer",
    rapport_cranio_faciaux_sagittaux_convexite: "integer",
    rapport_cranio_faciaux_sagittaux_se: "integer",
    rapport_cranio_faciaux_sagittaux_sl: "integer",
    rapport_cranio_faciaux_sagittaux_scg: "integer",
    rapport_cranio_faciaux_sagittaux_s_fpm: "integer",
    mensuration_basales_fpm_ena: "integer",
    mensuration_basales_at_chateau: "integer",
    mensuration_basales_longeur_mandibule: "integer",
    mensuration_basales_xipm: "integer",
    direction_croissance_fma_tweed: "integer",
    direction_croissance_axe_brodie: "integer",
    direction_croissance_axe_facial_Rickeets: "integer",
    mensurations_verticales_hes: "integer",
    mensurations_verticales_hei: "integer",
    mensurations_verticales_hauteur_ramale: "integer",
    mensurations_verticales_ena_xipm: "integer",
    papport_dento_squellettes_6ptv: "integer",
    rapport_dento_squelletique_if: "integer",
    rapport_dento_squellettes_im: "integer",
    rapport_dento_squellettes_ia_po_angle: "integer",
    rapport_dento_squellettes_ia_oo_distance: "integer",
    rapport_dento_squellettes_ia_po_angle: "integer",
    rapport_dento_squellettes_ia_po_distance: "integer",
    rapport_dento_dentaire_ii: "integer",
    esthetique_ls_ligne_e: "integer",
    esthetique_li_ligne_e: "integer",
    esthetique_angle_z: "integer"
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
    patient_id: "string" <required>,
    motif_consultation: "string" <required> [options]<fonctionnele, esthetique, douleure, [anything]>,
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
    patient_id: "string" <required>,
    motif_consultation: "string" <required> [options]<fonctionnele, esthetique, douleure, [anything]>,
    linda_maxillaire: "string",
    linda_mandibule: "string",
    decision_therapeutique: "string"
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
