SELECT * 
FROM `students`
WHERE `date_of_birth` LIKE '1990%';

SELECT * 
FROM `courses` 
WHERE `cfu` > '10';

SELECT * 
FROM `students`
WHERE YEAR(date_of_birth) <= '1994' 
AND MONTH(date_of_birth) <= '04' 
AND DAY(date_of_birth) <= '10';

SELECT *
FROM `courses`
WHERE `year` = '1' 
AND `period` = 'I semestre';

SELECT * 
FROM `exams`
WHERE `date` = '2020-06-20' 
AND `hour` > '14:00:00';

SELECT * 
FROM `degrees` 
WHERE `level` = 'magistrale';

SELECT COUNT(name)
FROM `departments`;

SELECT *
FROM `teachers`
WHERE ISNULL(phone);