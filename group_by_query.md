1. Contare quanti iscritti ci sono stati ogni anno

SELECT COUNT(students.name), YEAR(students.enrolment_date)
FROM students
GROUP BY YEAR(students.enrolment_date)



2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

SELECT teachers.office_address, COUNT(teachers.office_address)
FROM teachers
GROUP BY teachers.office_address



3. Calcolare la media dei voti di ogni appello d'esame

SELECT AVG(vote), exam_student.exam_id
FROM exam_student
GROUP BY exam_student.exam_id



4. Contare quanti corsi di laurea ci sono per ogni dipartimento

SELECT COUNT(degrees.name), departments.name
FROM degrees
JOIN departments ON departments.id = degrees.department_id
GROUP BY departments.name