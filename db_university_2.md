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

```
```

### Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

```
```

### Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

```
```

### Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

```
```

### Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

```
```

### BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.

```
```