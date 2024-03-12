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

```sql
SELECT *
FROM `students`
WHERE TIMESTAMPDIFF(YEAR, `date_of_birth`, CURDATE()) > 30;

```

## Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea

```sql
SELECT * FROM `courses`
WHERE `period` =  'I semestre'
AND `year` = 1;
```

## Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020

```sql
SELECT * FROM `exams`
WHERE `date` = '2020-06-20'
AND `hour` > '14:00:00';
```

```sql
SELECT *
FROM `exams`
WHERE `date` = '2020-06-20'
AND HOUR(`hour`) >= 14;
```

## Selezionare tutti i corsi di laurea magistrale

```sql
SELECT *
FROM `degrees`
WHERE `level` = 'magistrale';
```

## Da quanti dipartimenti è composta l'università?

```sql
SELECT COUNT(id)
FROM `departments`;
```

## Quanti sono gli insegnanti che non hanno un numero di telefono?

```sql
SELECT COUNT(phone)
FROM `teachers`
WHERE `phone` IS NOT NULL;
```

```sql
SELECT COUNT(`phone`) AS `numero insegnanti`
FROM `teachers`;
```

```sql
SELECT `cfu`, COUNT(*) AS `numero_corsi`
FROM `courses`
GROUP BY `cfu`;
```

## contare gli studenti raggruppati per anno di nascita

```sql
SELECT YEAR(`date_of_birth`) AS `year_of_birth`,
COUNT(*) AS `studenti_nati`
FROM `students`
GROUP BY YEAR(`date_of_birth`);
```

## selezionare il voto più basso per ogni appello di esame

```sql
SELECT MIN(`vote`) AS `worst_vote`,
 `exam_id`
FROM `exam_student` GROUP BY `exam_id`;
```

# selezionare tutti i corsi di laurea informatica

```sql
SELECT
	`degrees`.`id` AS `degrees_id`,
    `degrees`.`name` AS `degrees_name`,
    `degrees`.`level` AS `degrees_level`,

	`courses`.`id` as `course_id`,
    `courses`.`name` as `course_name`,
    `courses`.`period` as `course_period`,
    `courses`.`year` as `course_year`,
    `courses`.`cfu` as `course_cfu`

FROM `degrees`

INNER JOIN `courses`
ON `degrees`.`id` =  `courses`.`degree_id`;

```

# seleziona le informazioni sul corso con id = 144, con tutti gli appelli d'esame

```sql
SELECT
	`exams`.*,
    `courses`.*

FROM `courses`

INNER JOIN `exams`
ON `courses`.`id` = `exams`.`course_id`

WHERE `courses`.`id` = 144;

```

# selezionare quale dipartimento appartine il corso di laurea in diritto dell'economia,

```sql
SELECT
`departments`.`name`

FROM `departments`

INNER JOIN `degrees`
ON `departments`.`id` = `degrees`.`department_id`

WHERE `degrees`.`name` = "Corso di Laurea in Diritto dell'Economia";
```

# selezionare tutti gli appelli del Corso Magistrale in Fisica del primo anno,

```sql
SELECT `exams`*

FROM `exams`

INNER JOIN `courses`
ON `exams`.`course_id`

INNER JOIN `degrees`
ON `courses`.`degree_id`

# TODO: AGGIUNGI FROM AND JOIN

WHERE `degrees`.`name` = "Corso di laurea Magistrale in fisica"
AND `courses`.`year` = 1
```

# Selezionare tutti i docenti che insegnano nel Corso di Laurea in lettere

```sql
SELECT DISTINCT `teachers`.*

FROM `teachers`

INNER JOIN `course_teacher`
ON `teachers`.`id` = `course_teacher`.`teacher_id`

INNER JOIN `courses`
ON `courses`.`id` = `course_teacher`.`course_id`

INNER JOIN `degrees`
ON `courses`.`degree_id` = `degrees`.`id`

WHERE `degrees`.`name` = 'Corso di Laurea in lettere'
ORDER BY `teachers`.`surname` ASC;
```
