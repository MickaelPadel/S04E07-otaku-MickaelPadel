
# O'taku

<!-- connection a la base de donner  -->
sudo -i -u postgres psql;

<!-- Creer un utilisateur  -->
CREATE USER jeanjean WITH PASSWORD 'jeanjean';

<!-- Creer la bases de données. -->
CREATE DATABASE otaku OWNER jeanjean;

<!-- test de la connexion a la  base de données. -->
psql -U jeanjean -d otaku

<!-- Excuéter un script de base de données . -->
psql -U jeanjean -d otaku -f data.sql

<!-- requête pour récupérer les données 15 premieres lignes. -->
 SELECT * FROM viewing LIMIT 15;

 <!--requête pour sélectionner toutes les données, rangées dans un ordre aléatoire -->
  SELECT * FROM viewing ORDER BY random();
 <!--Écrire une requête pour récupérer 15 lignes de manière aléatoire-->
 SELECT * FROM viewing ORDER BY random();
 <!-- la moyenne d'âge des téléspectateurs, classée par pays. -->
 SELECT viewer_country,
 AVG(viewer_age_group )
 FROM viewing
 GROUP BY vierwer_country ;
<!-- le nombre d'épisodes regardés, classés par tranche d'âge, et rangé par tranche d'âge décroissant. -->
SELECT  viewer_age_group, count(episode) AS nb_episode
FROM viewing
GROUP BY viewer_age_group
ORDER BY viewer_age_group DESC;
<!-- BONUS CACTUS (attention, ça parait simple mais ça pique !) : le nombre de visionnage par an. -->
