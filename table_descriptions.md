# Table Descriptions & Queries

## patient_data
- **Description**: All patient data
- **Number of Records**: 4624058
**Query to create table**:
```sql
SELECT *
FROM AAOCHIN2023.S391.OBSERVATION_FACT
```

## ckd_observations
- **Description**: Patient visit data that relates to chronic kidney disease
- **Number of Records**: 693490
- **Number of Unique Patients**: 118974 
**Query to create table**:
```sql
SELECT *
FROM AAOCHIN2023.S391.OBSERVATION_FACT
WHERE CONCEPT_CD IN (SELECT CONCEPT_CD
  FROM AAOCHIN2023.common.CONCEPT_DIMENSION
  WHERE NAME_CHAR like '%chronic kidney disease%')
```
