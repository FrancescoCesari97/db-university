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

```sql
SELECT `courses`.*

FROM `courses`

INNER JOIN `course_teacher`
ON `courses`.`id` = `course_teacher`.`course_id`

INNER JOIN `teachers`
ON `course_teacher`.`teacher_id` = `teachers`.`id`

WHERE `teachers`.`name` = 'Fulvio'
AND `teachers`.`surname` = 'Amato'
```

## 4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

```sql
SELECT  `students`.`name`, `students`.`surname`, `degrees`.`name` AS `corso`, `departments`.`name` AS `dipartimento`
FROM `students`

INNER JOIN `degrees`
ON `degrees`.`id` = `students`.`degree_id`

INNER JOIN `departments`
ON `departments`.`id` = `degrees`.`department_id`

ORDER BY `students`.`surname`;
```

## 5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

```sql
SELECT `degrees`.`name`, `courses`.`name`, `teachers`.`name`
FROM `degrees`

INNER JOIN `courses`
ON `courses`.`degree_id` = `degrees`.`id`


INNER JOIN `course_teacher`
ON `courses`.`id` = `course_teacher`.`course_id`

INNER JOIN `teachers`
ON `course_teacher`.`teacher_id` = `teachers`.`id`;
```

## 6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

```sql
SELECT `teachers`.*
FROM `teachers`

INNER JOIN `course_teacher`
ON `teachers`.`id` = `course_teacher`.`teacher_id`

INNER JOIN `courses`
ON `courses`.`id` = `course_teacher`.`course_id`

INNER JOIN `degrees`
ON `degrees`.`id` = `courses`.`degree_id`

INNER JOIN `departments`
ON `departments`.`id` = `degrees`.`department_id`

WHERE `departments`.`name` = 'Dipartimento di matematica';
```
