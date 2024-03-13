## Selezionare tutti gli studenti nati nel 1990 (160)

    SELECT * FROM `students` 
    WHERE YEAR(`date_of_birth`) = 1990;  || 
    WHERE `date_of_birth` BETWEEN '1990-01-01' AND '1990-12-31';

## Selezionare tutti i corsi che valgono più di 10 crediti (479)

    SELECT * FROM `courses` 
    WHERE `cfu` > 10;

## Selezionare tutti gli studenti che hanno più di 30 anni
    SELECT * FROM `students`
    WHERE YEAR(CURDATE()) - YEAR(`date_of_birth`) > 30;

## Selezionare tutti corsi del primo semestre del primo anno di un qualsiasi corsodilaurea (286)
    SELECT * FROM `courses`  
    WHERE `year` = 1 AND `period` = 'I semestre';

## Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)

    SELECT * FROM `exams` 
    WHERE `date` = '2020-06-20' AND hour(`hour`) > 13;

## Selezionare tutti i corsi di laurea magistrale (38)

    SELECT * FROM `degrees`
    WHERE `level` = 'magistrale';


## Da quanti dipartimenti è composta l'università? (12)

    SELECT COUNT(*) 
    FROM `departments`;

## Quanti sono gli insegnanti che non hanno un numero di telefono? (50)
    SELECT COUNT(`phone`) 
    FROM `teachers`;


# EX-Query GROUP BY 

## Contare quanti iscritti ci sono stati ogni anno 

    SELECT
	COUNT(*) AS `students`,
	YEAR(`enrolment_date`) AS `enrolment_year`
    FROM `students`
    GROUP BY YEAR(`enrolment_date`);

## contare gli insegnanti che hanno l'uffivio nello stesso edifficio

    SELECT
	COUNT(*) AS `teachers`,
    `office_address`
    FROM `teachers`
    GROUP BY `office_address`;

## clacolare la media dei voti di ogni  appello

    SELECT
    `exam_id`,
    AVG(vote) AS `vote_avarage`
    FROM `exam_student`
    GROUP BY `exam_id`;

## contre quanti corsi di laurea ci sono in ogni departimento
    
    SELECT
	`department_id`,
    COUNT(*) AS `degrees`
    FROM `degrees`
    GROUP BY `department_id`;