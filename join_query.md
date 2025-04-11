1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT students.*
FROM students
JOIN degrees ON students.degree_id = degrees.id
WHERE degrees.name = "Corso di Laurea in Economia";



2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

SELECT degrees.*
FROM degrees
JOIN departments ON degrees.department_id = departments.id
WHERE degrees.level = "magistrale" 
AND departments.name = "Dipartimento di Neuroscienze";



3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT courses.*, teachers.name AS teacher_name, teachers.surname AS teacher_surname
FROM courses
JOIN course_teacher ON courses.id = course_teacher.course_id
JOIN teachers ON teachers.id = course_teacher.teacher_id
WHERE teachers.id = 44;



4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti
	e il relativo dipartimento, in ordine alfabetico per cognome e nome
    
SELECT students.*, degrees.*
FROM students
JOIN degrees ON students.degree_id = degrees.id
JOIN departments ON degrees.department_id = departments.id
ORDER BY students.surname, students.name ASC;



5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti (1317)

SELECT degrees.name AS degree_name, courses.name AS course_name, teachers.name AS teacher_name, teachers.surname AS teacher_surname
FROM degrees
JOIN courses ON courses.degree_id = degrees.id
JOIN course_teacher ON course_teacher.course_id = courses.id
JOIN teachers ON teachers.id = course_teacher.teacher_id



6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

SELECT DISTINCT teachers.name, teachers.surname
FROM course_teacher
JOIN courses ON courses.id = course_teacher.course_id
JOIN teachers ON teachers.id = course_teacher.teacher_id
JOIN degrees ON degrees.id = courses.degree_id
JOIN departments ON departments.id = degrees.department_id
WHERE departments.name = "Dipartimento di Matematica";



7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. 
  Successivamente, filtrare i tentativi con voto minimo 18. (21880)
    
SELECT students.id, students.name, students.surname, courses.name AS course_name, COUNT(courses.name) AS attempts, MAX(exam_student.vote)
FROM students
JOIN exam_student ON students.id = exam_student.student_id
JOIN exams ON exams.id = exam_student.exam_id
JOIN courses ON exams.course_id = courses.id
WHERE exam_student.vote >= 18
GROUP BY students.id, courses.name