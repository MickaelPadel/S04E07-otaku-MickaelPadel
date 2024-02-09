
# O'taku

``` sql

-- connection a la base de donner  
sudo -i -u postgres psql;

-- Creer un utilisateur 
CREATE USER jeanjean WITH PASSWORD 'jeanjean';

-- Creer la bases de données. 
CREATE DATABASE otaku OWNER jeanjean;

-- test de la connexion a la  base de données. 
psql -U jeanjean -d otaku

-- Excuéter un script de base de données . 
psql -U jeanjean -d otaku -f data.sql

-- requête pour récupérer les données 15 premieres lignes. 
 SELECT * FROM viewing LIMIT 15;

 --requête pour sélectionner toutes les données, rangées dans un ordre aléatoire 
  SELECT * FROM viewing ORDER BY random();

 --Écrire une requête pour récupérer 15 lignes de manière aléatoire
 SELECT * FROM viewing ORDER BY random() LIMIT 15;

 -- la moyenne d'âge des téléspectateurs, classée par pays et par odre alphabetiques. round() pour mettre les chiffres rond. 
 SELECT viewer_country,
 ROUND(AVG(viewer_age_group ))
 FROM viewing
 GROUP BY viewer_country
 ORDER BY viewer_country ASC;

-- le nombre d'épisodes regardés, classés par tranche d'âge, et rangé par tranche d'âge décroissant. 
SELECT  viewer_age_group, count(episode) AS nb_visionnage
FROM viewing
GROUP BY viewer_age_group
ORDER BY viewer_age_group DESC;

-- BONUS CACTUS (attention, ça parait simple mais ça pique !) : le nombre de visionnage par an. 
SELECT EXTRACT(YEAR FROM viewing_date) AS year ,
COUNT(*) As nb_view,
viewer_country AS country
FROM viewing
GROUP BY year,country
ORDER BY year, country ASC;

-- le nombre de visionnage par an autre versions.
SELECT EXTRACT(YEAR FROM viewing_date) AS year ,
COUNT(*) As nb_view
FROM viewing
GROUP BY year;

-- # Effacer la valeur contenue dans la colonne binge_session pour les enrengistrement ayant un id compris entre 500 et 600.
UPDATE viewing SET binge_session = NULL where id BETWEEN 500 AND 600;
