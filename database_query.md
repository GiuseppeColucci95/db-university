SELECT * 
FROM `students`
WHERE `date_of_birth` LIKE '1990%';

SELECT * 
FROM `courses` 
WHERE `cfu` > 10';

SELECT * 
FROM `students`
WHERE TIMESTAMPDIFF(YEAR, `date_of_birth`, CURDATE()) > 30

SELECT *
FROM `courses`
WHERE `year` = 1
AND `period` = 'I semestre';

SELECT * 
FROM `exams`
WHERE `date` = '2020-06-20' 
AND `hour` > '14:00:00';

SELECT * 
FROM `degrees` 
WHERE `level` = 'magistrale';

SELECT COUNT(id) AS `total_departments`
FROM `departments`;

SELECT *
FROM `teachers`
WHERE ISNULL(phone);