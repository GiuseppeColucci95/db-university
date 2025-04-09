## TRACCIA
Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:
-sono presenti diversi **Dipartimenti** (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
-ogni Dipartimento offre più **Corsi di Laurea** (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
-ogni Corso di Laurea prevede diversi **Corsi** (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
-ogni Corso può essere tenuto da diversi **Insegnanti**;
-ogni Corso prevede più **appelli d'Esame**;
-ogni **Studente** è iscritto ad un solo Corso di Laurea;
-ogni Studente può iscriversi a più appelli di Esame;
-per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente. 

Pensiamo a quali entità (tabelle) creare  per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.

## University DB

## Table name: `departments`
**Table columns**
- id: (BIGINT) - primary key - auto increments - NOT NULL
- name: VARCHAR(50) - NOT NULL
- address: VARCHAR(255) - NOT NULL

## Table name: `degree_courses`
**Table columns**
- id: (BIGINT) - primary key - auto increments - NOT NULL
- name: VARCHAR(50) - NOT NULL
- code: VARCHAR(20) - NOT NULL
- years: (TINYINT) - NULL

## Table name: `courses`
**Table columns**
- id: (BIGINT) - primary key - auto increments - NOT NULL
- name: VARCHAR(50) - NOT NULL
- CFU: (TINYINT) - NOT NULL

## Table name: `teachers`
**Table columns**
- id: (BIGINT) - primary key - auto increments - NOT NULL
- name: VARCHAR(50) - NOT NULL
- lastname: VARCHAR(50) - NOT NULL

## Table name: `exams_calls`
**Table columns**
- id: (BIGINT) - primary key - auto increments - NOT NULL
- course_id: (BIGINT) - foreign key - NOT NULL
- date: (DATE) - NOT NULL
- time: (TIME) - NOT NULL

## Table name: `students`
**Table columns**
- id: (BIGINT) - primary key - auto increments - NOT NULL
- name: VARCHAR(50) - NOT NULL
- lastname: VARCHAR(50) - NOT NULL

## Table name: `degree_course_course`
**Table columns**
- id: (BIGINT) - primary key - auto increments - NOT NULL
- degree_course_id: (BIGINT) - foreign key - NOT NULL
- course_id: (BIGINT) - foreign key - NOT NULL

## Table name: `course_teacher`
**Table columns**
- id: (BIGINT) - primary key - auto increments - NOT NULL
- course_id: (BIGINT) - foreign key - NOT NULL
- teacher_id: (BIGINT) - foreign key - NOT NULL

## Table name: `student_call`
**Table columns**
- id: (BIGINT) - primary key - auto increments - NOT NULL
- student_id: (BIGINT) - foreign key - NOT NULL
- exam_call_id: (BIGINT) - foreign key - NOT NULL

