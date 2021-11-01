# php-symfony

![image](https://user-images.githubusercontent.com/32338685/138593403-e1dae628-cb78-4c02-b678-6149edef48c9.png)

![image](https://user-images.githubusercontent.com/32338685/138609040-63e04df3-e474-47e8-b696-a4d875b6c04e.png)



* https://symfony.com/
* https://getcomposer.org/
* https://twig.symfony.com/  (template)

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
sudo yum install epel-release

$ sudo dnf module list php
Dernière vérification de l’expiration des métadonnées effectuée il y a 0:05:57 le lun. 25 oct. 2021 20:56:29 CEST.
CentOS Linux 8 - AppStream
Name                                             Stream                                              Profiles                                                               Summary
php                                              7.2 [d]                                             common [d], devel, minimal                                             PHP scripting language
php                                              7.3                                                 common [d], devel, minimal                                             PHP scripting language
php                                              7.4 [e]                                             common [d], devel, minimal                                             PHP scripting language


sudo yum install -y php php-mysqlnd php-json 
sudo yum install -y zip unzip php-zip

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

## start project
```
symfony new --version=3.4 my_project_name_3.4 --full

symfony new  my_project_name --full
```

* start symfony
``` 
symfony serve
symfony serve --port=8000
```


## User
```
symfony console make:user

=> Security  : Update
=> src\Repository : Get, Search (quering)
=> src\Entity: Mapping BDD User 


```

* Create DB
```
symfony  console doctrine:database:create
Created database `laboutiquefrancaise` for connection named default

```

* Create migration files
```
symfony console make:migratio       
  Success! 
 Next: Review the new migration "migrations/Version20211030095706.php"
 Then: Run the migration with php bin/console doctrine:migrations:migrate
 See https://symfony.com/doc/current/bundles/DoctrineMigrationsBundle/index.html

```


* Migrate to DB
```
symfony console doctrine:migration:migrate

 WARNING! You are about to execute a migration in database "laboutiquefrancaise" that could result in schema changes and data loss. Are you sure you wish to continue? (yes/no) [yes]:
 >    

[notice] Migrating up to DoctrineMigrations\Version20211030095706
[notice] finished in 99ms, used 10M memory, 1 migrations executed, 1 sql queries

```

## Set up DB connexion
```
.env
```

## Entity & Migration
```
# Create Entity object for the BDD
symfony console make:entity

# Create migration files
symfony console make:migration

# Do the migration with the DB
symfony console doctrine:migration:migrate
```

## Easyadmin

```
# Map an Entity to Easyadmin
symfony console make:admin:crud
```

## Debug router
```
 symfony console debug:router
 -------------------------- -------- -------- ------ ----------------------------------- 
  Name                       Method   Scheme   Host   Path                               
 -------------------------- -------- -------- ------ ----------------------------------- 
  _wdt                       ANY      ANY      ANY    /_wdt/{token}                      
  _profiler_home             ANY      ANY      ANY    /_profiler/                        
  _profiler_search           ANY      ANY      ANY    /_profiler/search                  
  _profiler_search_bar       ANY      ANY      ANY    /_profiler/search_bar              
  _profiler_phpinfo          ANY      ANY      ANY    /_profiler/phpinfo                 
  _profiler_search_results   ANY      ANY      ANY    /_profiler/{token}/search/results  
  _profiler_open_file        ANY      ANY      ANY    /_profiler/open                    
  _profiler                  ANY      ANY      ANY    /_profiler/{token}                 
  _profiler_router           ANY      ANY      ANY    /_profiler/{token}/router          
  _profiler_exception        ANY      ANY      ANY    /_profiler/{token}/exception       
  _profiler_exception_css    ANY      ANY      ANY    /_profiler/{token}/exception.css   
  home                       ANY      ANY      ANY    /                                  
  register                   ANY      ANY      ANY    /inscription                       
  _preview_error             ANY      ANY      ANY    /_error/{code}.{_format}           
 -------------------------- -------- -------- ------ ----------------------------------- 
```
