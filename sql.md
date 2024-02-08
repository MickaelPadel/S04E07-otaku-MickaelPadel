
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
