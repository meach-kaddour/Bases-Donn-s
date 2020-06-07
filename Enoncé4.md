
## Énoncé 4 

## 0. Créer la base de `HR` en se base sur le shéma relationnelle illustré sur l'image `HR-DB.jpeg`.

 <!-- ``exemple create

CREATE TABLE employess( 
    employee_id INT PRIMARY KEY NOT NULL, 
    first_name VARCHAR(20), 
    lastt_name VARCHAR(25), 
    email VARCHAR(25), 
    phone_number VARCHAR(20),
    hire_date DATE, job_id VARCHAR(10),
    salary INT, commmisssion_pct INT,
    manager_id INT, department_id INT,
    FOREIGN KEY (job_id) REFERENCES jobs(jobt_id),
    FOREIGN ``KEY (department_id) REFERENCES departments(department_id) 
       ) -->


## 1. Question d'insertion  des donnés  voila un exemple d'un requet d'enregistrement
<!-- &/1/
INSERT into countries (country_id,country_name,region_id)
VALUES
('AR', 'Argentina', '2'),
('AU', 'Australia', '3'),
('BE', 'Belgium', '1'),
('BR', 'Brazil', '2'),
('CA', 'Canada', '2'),
('CH', 'Switzerland', '1'),
('CN', 'China', '3'),
('DE', 'Germany', '1'),
('DK', 'Denmark', '1'),
('EG', 'Egypt', '4'),
('FR', 'France', '1'),
('HK', 'HongKong', '3'),
('IL', 'Israel', '4'),
('IN', 'India', '3'),
('IT', 'Italy', '1'),
('JP', 'Japan', '3'),
('KW', 'Kuwait', '4'),
('MX', 'Mexico', '2'),
('NG', 'Nigeria', '4'),
('NL', 'Netherlands', '1'),
('SG', 'Singapore', '3'),
('UK', 'United Kingdom', '1'),
('US', 'United States of America', '2'),
('ZM', 'Zambia', '4'),
('ZW', 'Zimbabwe', '4') -->


## 8. Écrire une requête pour afficher les noms (prénom, nom) en utilisant les alias `Prénom`, `Nom`.

<!-- SELECT first_name "NOM",lastt_name "Prénom" FROM `employess` ; -->

## 9. Écrire une requête pour obtenir l'ID unique du département à partir de la table des employés.

<!-- SELECT DISTINCT `department_id` FROM `employess` -->

## 10. Écrire une requête pour obtenir tous les détails de l'employé à partir de la table des employés, par ordre de prénom, en ordre décroissant.
 
 <!-- SELECT * FROM `employess` ORDER BY first_name DESC -->

## 11. Écrire une requête pour obtenir les noms (prénom, nom), le salaire, la CP de tous les employés (la CP est calculée à 15 % du salaire).

<!-- SELECT first_name  "Prénom",lastt_name "Nom",salary "Salaire",salary *0.15 "CD" FROM `employess`;  -->

## 12. Écrire une requête pour obtenir l'ID de l'employé, les noms (prénom, nom), le salaire dans l'ordre croissant du salaire.

<!-- SELECT employee_id ,first_name  "Prénom",lastt_name "Nom",salary "Salaire"FROM `employess` ORDER BY salary ASC;  -->

## 13. Effectuez une recherche pour obtenir le total des salaires payables aux salariés.

<!-- SELECT SUM(salary) FROM `employess` -->

## 14. Effectuez une recherche pour obtenir le salaire moyen et le nombre de salariés dans le tableau des salariés.

<!-- SELECT AVG(salary) "moyen du salaire", COUNT(employee_id) "Nombre des employes" FROM `employess`; -->

## 15. Écrire une requête pour obtenir le nombre d'employés travaillant dans l'entreprise.

<!-- SELECT COUNT(employee_id) "Nombre des employes" FROM `employess`; -->

## 16. Écrire une requête pour obtenir le nombre d'emplois disponibles dans le tableau des employés.

<!-- SELECT DISTINCT job_id " le nombre d'emplois disponibles dans le tableau des employés" FROM `employess`; -->

## ## 17. Écrire une requête pour obtenir tous les prénoms du tableau des employés en majuscules.

<!-- SELECT UPPER(first_name) FROM `employess` -->

## 18. Écrire une requête pour obtenir les 3 premiers caractères du prénom dans la table des employés.

<!-- SELECT SUBSTR(first_name,1,3) FROM `employess` -->


## 19. Effectuez une recherche pour obtenir le salaire maximum et minimum du tableau des employés.

<!-- SELECT MAX(salary) "maximum salaire", MIN(salary)  "minmum salire"  FROM `employess`; -->

## 20. Rédigez une requête pour afficher le nom (prénom, nom) et le salaire de tous les employés dont le salaire n'est pas compris entre 10 000 et 15 000 dollars.

<!-- SELECT `first_name`, `lastt_name`, `salary`FROM `employess` WHERE salary >=10000 AND salary<=15000; -->

## 21. Rédigez une requête pour afficher le nom (prénom, nom) et l'ID du département de tous les employés des départements 30 ou 100 par ordre croissant.
 
 <!-- SELECT  `first_name`, `lastt_name`, `department_id` FROM `employess`  WHERE department_id BETWEEN 30 AND 100 ORDER BY (department_id) ASC ; -->

## 22. Rédigez une requête pour afficher le nom (prénom, nom) et le salaire de tous les employés dont le salaire ne se situe pas dans la fourchette de 10 000 à 15 000 dollars et qui se trouvent dans le département 30 ou 100.

<!-- SELECT  `first_name`, `lastt_name`, `department_id` FROM `employess`  WHERE department_id BETWEEN 30 AND 100  AND salary >=10000 AND salary<=15000 ORDER BY (department_id) ASC ; -->

## 23. Rédigez une requête pour afficher le nom (prénom, nom) et la date d'embauche pour tous les employés qui ont été embauchés en 1987.

<!-- select first_name,lastt_name,start_date
 from employess,job_history
 where  start_date ='1987-09-17'
 GROUP BY start_date; -->
 
## 24. Rédigez une requête pour trouver le nom (prénom, nom) de tous les employés qui travaillent dans le département informatique.

<!-- select first_name,lastt_name from employess,departments where department_name='it' -->


## 25. Rédigez une requête pour trouver les adresses (ID_lieu, adresse_rue, ville, état_province, nom_pays) de tous les départements.
- Conseil : utilisez JOINTURE NATURELLE

<!-- SELECT departments.department_name,locations.location_id,locations.street_address,locations.postal_code,locations.city,locations.state_province,countries.country_name
FROM departments
INNER JOIN locations
ON locations.location_id=departments.location_id
INNER JOIN countries
ON locations.country_id=countries.country_id; -->

## 26. Rédigez une requête pour afficher le titre du poste et le salaire moyen des employés. 

<!-- SELECT jobs.job_title, AVG(employess.salary)
FROM (jobs
INNER JOIN employess ON employess.job_id=jobs.jobt_id)
GROUP BY job_title; -->

## 27. Rédigez une requête pour calculer l'âge en année.


<!-- SELECT employee_id, FLOOR(DATEDIFF(CURRENT_TIME(),hire_date)/365) "AGE" FROM `employess` ; -->

## 28. Rédigez une requête pour mettre à jour la partie du numéro de téléphone dans la table des employés. Dans le numéro de téléphone, la sous-chaîne "124" sera remplacée par "999".

<!-- SELECT REPLACE(phone_number,'515','999') FROM `employess` -->
