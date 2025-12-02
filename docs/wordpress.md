# Wordpress

On utilise une machine de base de donnée et une autre pour le wordpress

## Installation de mariaDB

Installation du paquet de mariadb 
```
Sudo apt-get install mariadb-server
```

la commande mysql qui me permet de me connecter à la l'interface de mysql
```
sudo mysql –u root –p
```

ensuite il faut créé la base de donnée 
VILEGES;
```
## Installation du WordPress

Il nous faut apache pour installer le workpress
```
```
CREATE DATABASE wp_tours_sportludique;
```

ensuite je vérifie que la base de donnée a été créer 
```
SHOW DATABASES;
```

autorisé la connection à la base de donnée avec le wordpress
```
GRANT ALL PRIVILEGES ON *.* TO 'nom d'utilisateur'@'ip-serv-wordpress' IDENTIFIED BY 'ton_mot_de_passe' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```
## Installation du WordPress

Il nous faut apache pour installer le workpress
```
sudo apt install apache2
```

Ensuite j'ajoute les modules php que j'ai besoin 

```
sudo apt install php php-mysql php-xml php-mbstring php-curl php-zip php-gd php-intl -y
```
on install et decompresse le le dossier wordpress
```
wget https://wordpress.org/latest.tar.gz
tar -xvf latest.tar.gz
```
on déplace tout les dossiers wordpress dans le dossier /var/www/html/
```
sudo mv wordpress/* /var/www/wordpress/
```
on donne les droits apache 
```
sudo chown -R www-data:www-data /var/www/wordpress/
sudo chmod -R 755 /var/www/wordpress/
```
on créait le virtalhost
```
sudo nano /etc/apache2/sites-available/wp.tours.sportludique.fr.conf
```
```
/** The name of the database for WordPress */
define( 'DB_NAME', 'nom de la base de donnée' );

/** Database username */
define( 'DB_USER', 'nom d'utilisateur' );

/** Database password */
define( 'DB_PASSWORD', 'mot de passe' );

/** Database hostname */
define( 'DB_HOST', 'ip de la base de donnée' );
```
la conf dans le fichier 
```
<VirtualHost *:80>
    ServerName wp.tours.sportludique.fr
    DocumentRoot /var/www/wordpress
    ServerAdmin webmaster@localhost

    <Directory /var/www/wordpress>
        AllowOverride All
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/wp_error.log
    CustomLog ${APACHE_LOG_DIR}/wp_access.log combined
</VirtualHost>
```

ensuite on active le site et on desactive le site d'apache
```
sudo a2site wp.tours.sportludique.fr.conf
sudo a2dessite 000-default.conf
```

ensuite j'ai ajouté sur les paramétres de connection pour la base de donnée 

```
sudo cp wp-config-sample.php wp-config.php

sudo nano /var/www/wordpress/wp-config.php
```

```
/** The name of the database for WordPress */
define( 'DB_NAME', 'nom de la base de donnée' );

/** Database username */
define( 'DB_USER', 'nom d'utilisateur' );

/** Database password */
define( 'DB_PASSWORD', 'mot de passe' );

/** Database hostname */
define( 'DB_HOST', 'ip de la base de donnée' );
```VILEGES;
```

## interface web
sur l'interface web 

dans les paramètres de la page de l'administration j'ai mit le nom domaine du site.


## Sécurisation SSL 

