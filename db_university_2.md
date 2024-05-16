# DB University: Group By & Join


## - Group By

### Contare quanti iscritti ci sono stati ogni anno

```sql
SELECT YEAR(`enrolment_date`) AS `anno_iscrizione`, 
COUNT(*) AS `iscrizione_numero`
FROM `students`
GROUP BY YEAR(`enrolment_date`);
```

### Contare gli insegnanti che hanno l'ufficio nello stesso edificio

```sql
SELECT `office_address` AS `edificio`,
COUNT(*) AS `numero_insegnanti`
FROM `teachers`
GROUP BY `office_address`;
```

### Calcolare la media dei voti di ogni appello d'esame

```sql
SELECT AVG(vote) as `media_voto`, `exam_id` as `esame_id`
FROM `exam_student`
GROUP BY `exam_id`;
```

### Contare quanti corsi di laurea ci sono per ogni dipartimento
```sql
SELECT `department_id` AS `numero_dipartimento`,
COUNT(*) AS `numero_corsi`
FROM `degrees`
GROUP BY `department_id`;
```


## - Join

### Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

```sql
SELECT s.name, s.surname
FROM students s
JOIN degrees d
	ON s.degree_id = d.id
WHERE
	d.name = 'Corso di Laurea in Biologia';
```

### Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

```sql
SELECT d.name AS `laurea_magistrale`, dp.name AS `nome_dipartimento`
FROM degrees d
JOIN departments dp
    ON d.department_id = dp.id
WHERE d.level = 'magistrale'
AND dp.name = 'Neuroscienze';
```

### Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

```sql
SELECT c.name AS `nome_corso`
FROM teachers t
JOIN course_teacher ct
    ON t.id = ct.teacher_id
JOIN courses c
    ON ct.course_id = c.id
WHERE t.id = 44;
```

### Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

```sql
SELECT s.surname AS cognome, s.name AS nome, dp.name AS nome_dipartimento, d.website AS sito_internet
FROM students s
JOIN degrees d
    ON s.degree_id = d.id
JOIN departments dp
    ON dp.id = d.department_id
ORDER BY s.surname, s.name;
```

### Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

```
```

### Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

```sql
SELECT t.surname AS cognome_docente, t.name AS nome_docente
FROM departments dp
JOIN teachers t
    ON dp.id = t.id
WHERE dp.id = 5;
```

### BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.

```
```