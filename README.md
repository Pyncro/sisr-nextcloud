# sisr-nextcloud

## WSL UBUNTU 20.04 - WINDOWS 10

j'ai décidé d'utiliser wsl sous windows car il est plus rapide à configurer et à installer.

L'image montre ubuntu 22.04 mais j'ai changé a ubuntu 20.04
![image](https://github.com/Pyncro/sisr-nextcloud/blob/main/img/wsl.PNG)


### Prérequis
![image](https://github.com/Pyncro/sisr-nextcloud/blob/main/img/apt%20upgrade.PNG)

```sudo apt-get update && upgrade```

```sudo apt dist-upgrade```


### Install Apache2

```
sudo apt install apache2 mariadb-server libapache2-mod-php php-gd php-mysql 
php-curl php-mbstring php-intl php-gmp php-bcmath php-xml php-imagick php-zip
```

### Download nextcloud

![image](https://github.com/Pyncro/sisr-nextcloud/blob/main/img/wget%20nextcloud.PNG)

```wget https://download.nextcloud.com/server/releases/nextcloud-18.0.0.zip```

unzip le fichier dans /home

![image](https://github.com/Pyncro/sisr-nextcloud/blob/main/img/file%20installed.PNG)

```
sudo apt install unzip

ls

unzip nextcloud-18.0.0.zip
```

### Permission

![image](https://github.com/Pyncro/sisr-nextcloud/blob/main/img/alt1.PNG)

```
sudo mv nextcloud /var/www/html/nextcloud/

sudo mkdir /var/www/html/nextcloud/data

sudo chown -R www-data:www-data /var/www/html/nextcloud/

sudo chown -R 755 /var/www/html/nextcloud/

```


```sudo nano  /etc/apache2/sites-available/nextcloud.conf```
Entre ces informations

![image](https://github.com/Pyncro/sisr-nextcloud/blob/main/img/nano%20conf%20file.PNG)



</VirtualHost>

```sudo nano /etc/apache2/apache2.conf```
Tape a la fin du fichier

AcceptFilter http none
AcceptFilter https none


### Enable Apache2

service apache2 start

![image](https://github.com/Pyncro/sisr-nextcloud/blob/main/img/APACHE2%20WORKS.PNG)

service apache2 restart

![image](https://github.com/Pyncro/sisr-nextcloud/blob/main/img/apache2%20up%20and%20running.PNG)

!
![image](https://github.com/Pyncro/sisr-nextcloud/blob/main/img/127001.PNG)

#### Mysql

![image](https://github.com/Pyncro/sisr-nextcloud/blob/main/img/mysql%20install.PNG)

![image](https://github.com/Pyncro/sisr-nextcloud/blob/main/img/nextcloud%20privileges.PNG)

### IP configuration
Supprime l'adresse ip par défaut si nécessaire

![image](https://github.com/Pyncro/sisr-nextcloud/blob/main/img/change%20ip%20address.PNG)


Ajouter la nouvelle adresse ip comme autre entrer

![image](https://github.com/Pyncro/sisr-nextcloud/blob/main/img/add%20ip%20to%20access.PNG)


### Nextcloud config

https://127.0.0.1

![image](https://github.com/Pyncro/sisr-nextcloud/blob/main/img/it%20works.PNG)


![image](https://github.com/Pyncro/sisr-nextcloud/blob/main/img/it%20works%20also.PNG)



## UBUNTU 20.04 - VMWARE WORKSTATION
```sudo apt-get update```
```sudo apt-get upgrade```
```sudo apt install apache2 mariadb-server libapache2-mod-php7.4``
``sudo apt install php7.4-gd php7.4-mysql php7.4-curl php7.4-mbstring php7.4-intl```
```sudo apt install php7.4-gmp php7.4-bcmath php-imagick php7.4-xml php7.4-zip```



## Mariadb configuration

```
mariadb>

CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
CREATE DATABASE IF NOT EXISTS nextcloud CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;
GRANT ALL PRIVILEGES ON nextcloud.* TO 'username'@'localhost';
FLUSH PRIVILEGES;
quit;

```

## Nextcloud download & configuration

```wget https://download.nextcloud.com/server/releases/nextcloud-18.0.0.zip```

```
sudo apt install unzip

unzip nextcloud-18.0.0.zip
```

```
sudo mv nextcloud /var/www/html/nextcloud/

sudo mkdir /var/www/html/nextcloud/data

sudo chown -R www-data:www-data /var/www/html/nextcloud/

sudo chown -R 755 /var/www/html/nextcloud/

```

```sudo nano  /etc/apache2/sites-available/nextcloud.conf```

```
<VirtualHost *:80>
  DocumentRoot /var/www/html/nextcloud/
  ServerName  monge.nextcloud.com

  <Directory /var/www/html/nextcloud/>
    Require all granted
    AllowOverride All
    Options FollowSymLinks MultiViews

    <IfModule mod_dav.c>
      Dav off
    </IfModule>
  </Directory>
</VirtualHost>
```


</VirtualHost>

### Enable mods & sites

```a2ensite nextcloud.conf```
``` a2enmod rewrite ```
``` a2enmod headers ```
``` a2enmod env ```
``` a2enmod dir ```
``` a2enmod mime ```

```sudo nano /etc/apache2/apache2.conf```
Tape a la fin du fichier

```AcceptFilter http none```

```AcceptFilter https none```

