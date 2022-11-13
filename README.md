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


```sudo nano  /etc/apache2//sites-available/nextcloud.conf```
Entre ces informations
![image](https://github.com/Pyncro/sisr-nextcloud/blob/main/img/nano%20conf%20file.PNG)


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
