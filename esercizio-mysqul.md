# EX SQL

## Selezionare tutti gli studenti nati nel 1990

```sql
SELECT *
FROM `students`
WHERE YEAR(`date_of_birth`) = 1990;
```

## Selezionare tutti i corsi che valgono più di 10 crediti

```sql
SELECT *
FROM `courses`
WHERE `cfu` > 10;
```

## Selezionare tutti gli studenti che hanno più di 30 anni

```sql
SELECT *
FROM `students`
WHERE YEAR(`date_of_birth`) < 1994;
```

## Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea

```sql
SELECT * FROM `courses`
WHERE `period` =  'I semestre' AND `year` = 1;
```

## Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020
