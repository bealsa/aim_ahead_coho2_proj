# Table Descriptions & Queries

## ckd_observations
- **Description**: Patient visit data that relates to chronic kidney disease (CKD-related Diagnosis)
- **Number of Records**: 693490
- **Number of Unique Patients**: 118974 
- **Query to create table**:
```sql
SELECT *
FROM AAOCHIN2023.S391.OBSERVATION_FACT
WHERE CONCEPT_CD IN (SELECT CONCEPT_CD
  FROM AAOCHIN2023.common.CONCEPT_DIMENSION
  WHERE NAME_CHAR like '%chronic kidney disease%')
```

## ckd_patient_labs
- **Description**: All labs results from ckd patients (identified from `ckd_observations` table)
- **Number of Records**: 
- **Number of Unique Patients**:  
- **Query to create table**:
```sql
SELECT O.*
FROM AAOCHIN2023.S391.OBSERVATION_FACT AS O
INNER JOIN AAOCHIN2023.common.CONCEPT_DIMENSION AS C ON C.CONCEPT_CD = O.CONCEPT_CD
INNER JOIN S391.dbo.patient_data AS P on P.PATIENT_NUM = O.PATIENT_NUM
WHERE C.CONCEPT_PATH LIKE '\i2b2\LabLOINC%'
```

## patient_data
- **Description**: All patient data
- **Number of Records**: 4624058
- **Query to create table**:
```sql
SELECT *
FROM AAOCHIN2023.S391.PATIENT_DIMENSION
```

## provider data
- **Description**: All provider data
- **Number of Records**: 23840
- **Query to create table**:
```sql
SELECT *
FROM AAOCHIN2023.S391.PROVIDER_DIMENSION
```



