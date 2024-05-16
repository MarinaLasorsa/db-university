## JOIN

1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT `students`.*, `degrees`.`name` AS 'degree_name' 
FROM `students` 
INNER JOIN `degrees` 
ON `degrees`.`id` = `students`.`degree_id` 
WHERE `degrees`.`name` = 'Corso di Laurea in Economia'; 


2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
Neuroscienze

SELECT `degrees`.*, `departments`.`name` AS 'department_name' 
FROM `degrees` 
INNER JOIN `departments` 
ON `departments`.`id` = `degrees`.`department_id` 
WHERE `departments`.`name` = 'Dipartimento di Neuroscienze' AND `degrees`.`level` = 'magistrale'; 


3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT `courses`.*, `teachers`.`name` AS 'teacher_name', `teachers`.`surname` AS 'teacher_surname' 
FROM `courses` 
INNER JOIN `course_teacher` 
ON `courses`.`id` = `course_teacher`.`course_id` 
INNER JOIN `teachers` 
ON `teachers`.`id` = `course_teacher`.`teacher_id` 
WHERE `teachers`.`id` = 44; 

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
nome

SELECT `students`.`name` AS 'student_name', `students`.`surname` AS 'student_surname', `degrees`.*, `departments`.`name` as 'department_name' 
FROM `students` 
INNER JOIN `degrees` 
ON `degrees`.`id` = `students`.`degree_id` 
INNER JOIN `departments` 
ON `departments`.`id` = `degrees`.`department_id` 
ORDER BY `students`.`name` ASC, `students`.`surname` ASC; 


5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT `degrees`.*, `courses`.`name` as 'course_name', `teachers`.`name` AS 'teacher_name', `teachers`.`surname` AS 'teacher_surname' 
FROM `degrees` 
INNER JOIN `courses` 
ON `degrees`.`id` = `courses`.`degree_id` 
INNER JOIN `course_teacher` 
ON `courses`.`id` = `course_teacher`.`course_id` 
INNER JOIN `teachers` 
ON `teachers`.`id` = `course_teacher`.`teacher_id` 
GROUP BY `degrees`.`name`


6. Selezionare tutti i docenti che insegnano nel Dipartimento di
Matematica (54)
7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
per ogni esame, stampando anche il voto massimo. Successivamente,
filtrare i tentativi con voto minimo 18.