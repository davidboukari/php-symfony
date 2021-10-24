# php-symfony

![image](https://user-images.githubusercontent.com/32338685/138593403-e1dae628-cb78-4c02-b678-6149edef48c9.png)


* https://symfony.com/
* https://getcomposer.org/

## Installation Centos 8
https://www.cloudbooklet.com/how-to-install-lamp-stack-apache-mysql-mariadb-php-on-centos-8/

* Apache
```
sudo yum install httpd
sudo systemctl enable httpd --now
```

* mysql
```
sudo yum install mariadb-server mariadb -y
sudo systemctl enable mariadb --now
mysql_secure_installation
```

* php
```
sudo yum install -y php php-mysqlnd php-json

php --ini
Configuration File (php.ini) Path: /etc
Loaded Configuration File:         /etc/php.ini
Scan for additional .ini files in: /etc/php.d
Additional .ini files parsed:      /etc/php.d/20-bz2.ini,
/etc/php.d/20-calendar.ini,
/etc/php.d/20-ctype.ini,
/etc/php.d/20-curl.ini,
...
```

* Open firewall
```
sudo firewall-cmd --permanent --zone=public --add-service=http
sudo firewall-cmd --permanent --zone=public --add-service=https
sudo firewall-cmd --reload 
```

## Composer
* https://getcomposer.org/download/

## symfony
```
wget https://get.symfony.com/cli/installer -O - | bash
```
