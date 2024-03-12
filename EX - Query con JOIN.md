## 1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

```sql
SELECT DISTINCT
	`students`.*


FROM `students`

INNER JOIN `degrees`
ON `students`.`degree_id` = `degrees`.`id`

INNER JOIN `courses`
ON `degrees`.`id` = `courses`.`degree_id`

WHERE `degrees`.`name` = 'Corso di Laurea in Economia'
ORDER BY `students`.`surname` ASC;
```

## 2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

```sql
SELECT `courses`.*

FROM `courses`

INNER JOIN `degrees`
ON `degree_id` = `degrees`.`id`

INNER JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`

WHERE `departments`.`name` = 'Dipartimento di Neuroscienze'
AND `degrees`.`level` = 'magistrale';
```

## 3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
