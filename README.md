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
* Icons: https://fontawesome.com/
* Ex: https://fontawesome.com/v5.15/icons?d=gallery&p=2&q=list
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

## List service which we can inject dependencies
```
symfony console debug:autowiring

Autowirable Types
=================

 The following classes & interfaces can be used as type-hints when autowiring:
 
 App\Kernel (kernel)
 
 Interface for annotation readers.
 Doctrine\Common\Annotations\Reader (annotations.cached_reader)
 
 Doctrine\Common\Persistence\ManagerRegistry (doctrine)
 
 A database abstraction-level connection that implements features like events, transaction isolation levels, configuration, emulated transaction nesting, lazy connecting and more.
 Doctrine\DBAL\Connection (doctrine.dbal.default_connection)
 Doctrine\DBAL\Connection $defaultConnection (doctrine.dbal.default_connection)
 
 Connection interface. Driver connections must implement this interface.
 Doctrine\DBAL\Driver\Connection (doctrine.dbal.default_co
```

### a specific service type
```
ymfony console debug:autowiring session

Autowirable Types
=================

 The following classes & interfaces can be used as type-hints when autowiring:
 (only showing classes/interfaces matching session)
 
 SessionHandlerInterface (session.handler.native_file)
 
 FlashBagInterface.
 Symfony\Component\HttpFoundation\Session\Flash\FlashBagInterface (session.flash_bag)
 
 Interface for the session.
 Symfony\Component\HttpFoundation\Session\SessionInterface (.session.do-not-use) - deprecated
 
 SessionAuthenticationStrategyInterface.
 Symfony\Component\Security\Http\Session\SessionAuthenticationStrategyInterface (security.authentication.session_strategy)

```

## Easyadmin
* https://symfony.com/bundles/EasyAdminBundle/current/index.html
```
composer require easycorp/easyadmin-bundle

symfony console make:admin:dashboard

symfony console make:admin:crud
```

### Create entity Category
```
#### Create Entity Category
symfony console make:entity
Category

#### Create a migration file
symfony console make:migration           
  Success! 
 Next: Review the new migration "migrations/Version20211203172513.php"
 Then: Run the migration with php bin/console doctrine:migrations:migrate
 See https://symfony.com/doc/current/bundles/DoctrineMigrationsBundle/index.html

#### Use doctrine to migrate to the DB
symfony console doctrine:migration:migrate

 WARNING! You are about to execute a migration in database "laboutiquefrancaise" that could result in schema changes and data loss. Are you sure you wish to continue? (yes/no) [yes]:
 > yes

[notice] Migrating up to DoctrineMigrations\Version20211203172513
[notice] finished in 267.5ms, used 10M memory, 1 migrations executed, 1 sql queries

####  
symfony console make:admin:crud

Search icons:
* https://fontawesome.com/v5.15/icons?d=gallery&p=2&q=list

```

## Product Administration (Easyadmin)
```
# Create Entity Product for the db mapping
$ symfony console make:entity
name, slug, illustration, subtitle (string 255)
description (text)
price (float)
category (relation, Category, ManyToOne )

# Create a migration file (sql file to update the DB)
$ symfony console make:migration

# Migrate (update) the DB
$ symfony console doctrine:migration:migrate

# Create the admin page
$ symfony console make:admin:crud


`#### slug
* A slug: Ex: écharpe rouge française => echarpe-route-francaise


```

## Product (View controller)
```
symfony console make:controller

```


## Cart
```
symfony console make:controller


```
* Table bootstrap: https://getbootstrap.com/docs/5.1/content/tables/


## Address
* Entity
```
symfony console make:entity
Address
* user: Relation ManyToOne `notnull  new field insise User: addresses nosupressorphan
* 

* name string 255 notnull
* firstname string 255 notnull
* lastname string 255 notnull
* company string 255 null
* address string 255 notnull
* postal: string 255 notnull
* city string 255 
* country: string 255
* phone: string 255

symfony console make:migration

symfony console doctrine:migrations:migrate

```
* Code Controller
```
symfony console make:Controller
AccountAddress

symfony console make:form
Address
```
* Bootstrap card for address: https://getbootstrap.com/docs/4.0/components/card/
```
<div class="card" style="width: 18rem;">
  <img class="card-img-top" src="..." alt="Card image cap">
  <div class="card-body">
    <h5 class="card-title">Card title</h5>
    <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
    <a href="#" class="btn btn-primary">Go somewhere</a>
  </div>
</div>
```

## Order
* Carrer
```
# entity carrer
Symfony console make:Controller
Career
name string 255 notnull
description text notnull
price float notnull

symfony console migration:migrate

symfony console doctrine:migrations:migrate

# easyadmin carrer
symfony console make:admin:crud
1 
```
