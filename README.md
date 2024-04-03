# Prüfungsvorbereitung: MariaDB, phpmyadmin und Wordpress

blog-network erstellen:\
$ docker network create blog-network

MariaDB-Contaiber erstellen:\
$ docker run -d --name=mariadb --network blog-network -e MARIADB_ROOT_PASSWORD=sml12345 mariadb

phpmyadmin-Container erstellen:\
$ docker run --name phpmyadmin --network blog-network -d -e PMA_HOST=mariadb -p 8080:80 phpmyadmin

Unter phpmyadmin "Benutzerkonten" ("User accounts") ein Benutzerkonto hinzufügen. (Add user account)
1) Benutzername: blog\
2) Passwort generieren: Generieren klicken\
3) Passwort notieren! z.B. in Notepad++\
4) Erstelle eine Datenbank mit gleichem Namen und gewähre alle Rechte. --> anhaken\
5) OK klicken (unten)

Wordpress-Container erstellen:\
$ docker container run -d --network blog-network -e WORDPRESS_DB_HOST=mariadb -e WORDPRESS_DB_USER=blog -e WORDPRESS_DB_PASSWORD="Password" -e WORDPRESS_DB_NAME=blog -p 8081:80 wordpress




