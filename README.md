# sisr-nextcloud

## WSL UBUNTU 20.04 - WINDOWS 10

j'ai décidé d'utiliser wsl sous windows car il est plus rapide à configurer et à installer.

L'image dessous montre ubuntu 22.04 mais j'ai changé a ubuntu 20.04
![image](https://github.com/Pyncro/sisr-nextcloud/blob/main/img/wsl.PNG)


### Prérequis
![image](https://github.com/Pyncro/sisr-nextcloud/blob/main/img/apt%20upgrade.PNG)

```sudo apt-get update && upgrade```

```sudo apt dist-upgrade```


### Install Apache2

``
sudo apt install apache2 mariadb-server libapache2-mod-php php-gd php-mysql 
php-curl php-mbstring php-intl php-gmp php-bcmath php-xml php-imagick php-zip
```

### Download nextcloud

!image](https://github.com/Pyncro/sisr-nextcloud/blob/main/img/wget%20nextcloud.PNG)

```wget https://download.nextcloud.com/server/releases/nextcloud-18.0.0.zip```

unzip le fichier dans /home

![image](https://github.com/Pyncro/sisr-nextcloud/blob/main/img/file%20installed.PNG)
```
sudo apt install unzip

ls

unzip nextcloud-18.0.0.zip
```
