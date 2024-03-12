## 1. Contare quanti iscritti ci sono stati ogni anno

```sql

SELECT YEAR(`enrolment_date`) AS `enrolment_date`,
COUNT(*) AS `studneti_inscritti`
FROM `students`
GROUP BY YEAR(`enrolment_date`);
```

## 2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

```sql
SELECT `office_address` AS `indirizzo`,
COUNT(*) AS `professori`
FROM `teachers`
GROUP BY `office_address`;
```

## 3. Calcolare la media dei voti di ogni appello d'esame

```sql
SELECT AVG(`vote`) AS `average_vote`,
	`exam_id`
FROM `exam_student`
GROUP BY `exam_id`;
```

## 4. Contare quanti corsi di laurea ci sono per ogni dipartimento

```sql
SELECT `department_id` AS `department`,
COUNT(*) AS `numero_di_corsi`
FROM `degrees`
GROUP BY `department_id`;
```
