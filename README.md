# php-symfony

![image](https://user-images.githubusercontent.com/32338685/138593403-e1dae628-cb78-4c02-b678-6149edef48c9.png)

![image](https://user-images.githubusercontent.com/32338685/138609040-63e04df3-e474-47e8-b696-a4d875b6c04e.png)



* https://symfony.com/
* https://getcomposer.org/
* https://twig.symfony.com/  (template)  
 
## Links
* lorem ipsum text: https://www.faux-texte.com/lorem-ipsum-1.htm
* stripe (paiment): https://stripe.com/docs/testing
* stripe tests cards: https://stripe.com/docs/testing
* mailjet: https://app.mailjet.com/account/sender 
* mailjet: https://github.com/mailjet/mailjet-apiv3-php
* 
### icons: 
* https://www.iconfinder.com/search?q=minus
* https://www.flaticon.com/search?word=trash
* https://fontawesome.com/v5.15/icons?d=gallery&p=2&q=trash

### Images
* https://www.pexels.com/fr-fr/

### color panel
* https://flatuicolors.com/

```
# EasyAdmin: To search icon go to fontawesome: https://fontawesome.com/v5.15/icons?d=gallery&p=2&q=tag
        yield MenuItem::linktoDashboard('Dashboard', 'fa fa-home');
        yield MenuItem::linkToCrud('Utilisateurs', 'fas fa-user', User::class);
        yield MenuItem::linkToCrud('Commandes', 'fas fa-shopping-cart', Order::class);
        yield MenuItem::linkToCrud('Categories', 'fas fa-list', Category::class);
        yield MenuItem::linkToCrud('Produits', 'fas fa-tag', Product::class);
        yield MenuItem::linkToCrud('Carrier', 'fas fa-truck', Carrier::class);
```

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
To connect to the DB
```
mysql -u root -p -h 127.0.0.1
show databases
    -> ;
+---------------------+
| Database            |
+---------------------+
| information_schema  |
| laboutiquefrancaise |
| mysql               |
| performance_schema  |


MariaDB [laboutiquefrancaise]> show tables;
+-------------------------------+
| Tables_in_laboutiquefrancaise |
+-------------------------------+
| address                       |
| carrier                       |
| category                      |
| doctrine_migration_versions   |
| header                        |
| order                         |
| order_details                 |
| product                       |
| user                          |
+-------------------------------+
9 rows in set (0.001 sec)

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

## Install extension
sudo yum install -y php php-mysqlnd php-json 
sudo yum install -y zip unzip php-zip
### Datetime
sudo yum install php-intl

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

## twig
* debug
```
{{ dump(carrier) }}
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

* Rollback doctrine migration
```
 symfony console doctrine:migrations:migrate prev
 


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

```
symfony console debug:router --show-controllers
 -------------------------- -------- -------- ------ ------------------------------------- --------------------------------------------------------- 
  Name                       Method   Scheme   Host   Path                                  Controller                                               
 -------------------------- -------- -------- ------ ------------------------------------- --------------------------------------------------------- 
  _wdt                       ANY      ANY      ANY    /_wdt/{token}                         web_profiler.controller.profiler::toolbarAction()        
  _profiler_home             ANY      ANY      ANY    /_profiler/                           web_profiler.controller.profiler::homeAction()           
  ... 
  products                   ANY      ANY      ANY    /nos-produits                         App\Controller\ProductController::index()                
  product                    ANY      ANY      ANY    /produit/{slug}                       App\Controller\ProductController::show()                 
  register                   ANY      ANY      ANY    /inscription                          App\Controller\RegisterController::index()               
 ...
  _preview_error             ANY      ANY      ANY    /_error/{code}.{_format}              error_controller::preview() 
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


* Upgrade easy admin
```
[dboukari@localhost laboutiquefrancaise]$ composer update easycorp/easyadmin-bundle
Loading composer repositories with package information
Updating dependencies
Lock file operations: 0 installs, 1 update, 0 removals
  - Upgrading easycorp/easyadmin-bundle (v3.5.14 => v3.5.17)
Writing lock file
Installing dependencies from lock file (including require-dev)
Package operations: 0 installs, 1 update, 0 removals
  - Downloading easycorp/easyadmin-bundle (v3.5.17)
  - Upgrading easycorp/easyadmin-bundle (v3.5.14 => v3.5.17): Extracting archive
Generating optimized autoload files
composer/package-versions-deprecated: Generating version class...
composer/package-versions-deprecated: ...done generating version class
116 packages you are using are looking for funding.
Use the `composer fund` command to find out more!

What about running composer global require symfony/thanks && composer thanks now?
This will spread some ??  by sending a ??  to the GitHub repositories of your fellow package maintainers.

Run composer recipes at any time to see the status of your Symfony recipes.

Executing script cache:clear [OK]
Executing script assets:install public [OK]
```


### Doctrine remove a field
* Remove the field declaration in the entity and it getter and setter
* symfony console doctrine:migrations:list
* symfony console doctrine:migrations:diff
* symfony console doctrine:migrations:migrate


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
* Carrier (Transporteur)
```
# entity carrer
Symfony console make:entity
Carrier
name string 255 notnull
description text notnull
price float notnull
: 
symfony console migration:migrate

symfony console doctrine:migrations:migrate

# easyadmin Carrier
$ symfony console make:admin:crud
1 
```
* Order
```
$ symfony console make:entity
Order
user: relation User manytoOne nodotsuppressorphan
createAt: datetime
carrierName: string
carrierPrice: float
delivery: string 
```

* OrderDetails
```
$ symfony console make:entity
OrderDetails
myOrder: relation Order manyToOne noorphan
product: string 255
quantity: interger
price: float
total: float

$ symfony console make:migration
$ symfony console doctrine:migration:migrate
```
* The form Order is not linked to an Entity juste press ENTER
```
symfony console make:form
Order: The form Order is not linked to an Entity juste press ENTER
```
* Order isPaid
```
$ symfony console make:entity
Order
isPaid: Boolean notnull

$ symfony console make:migration
$ symfony console doctrine:migration:migrate
```

## Mapping Order OrderDetails
```
symfony console make:admin:crud
3(Order)
```


## Paiment
* https://stripe.com/fr/payments
* Test cards numbers: https://stripe.com/docs/testing

* Update order by using reference
```
symfony console make:entity
reference string 255 not null

symfony console make:migration
symfony console doctrine:migration:migrate

symfony console make:entity
Order
stripeSessionId string 255 nullable
symfony console make:migration
symfony console doctrine:migration:migrate


$ symfony console make:Controller
OrderSuccessController

$ symfony console make:Controller
OrderCancelController

```

## Sort in OrderRepository
```
   /*
     * findSuccessOrders()
     * Permet d'afficher les commandes dans l'espace membre
     */
    public function findSuccessOrders(){
        // o is alias of order
        return $this->createQueryBuilder('o')
            ->andWhere('o.isPaid = 1')
            ->orderBy('o.id', 'DESC')
            ->getQuery()
            ->getResult();
    }
```


## Mailjet
* https://app.mailjet.com
* developer page: https://app.mailjet.com/auth/get_started/developer
* https://dev.mailjet.com/email/guides/?_ga=2.251615686.1578905070.1639659281-457607442.1639659281#getting-started
* https://github.com/mailjet/mailjet-apiv3-php

```
composer require mailjet/mailjet-apiv3-php

```

## Easyadmin
* Actions: https://symfony.com/bundles/EasyAdminBundle/3.x/actions.html


## Cookie consent
* https://github.com/ConnectHolland/cookie-consent-bundle

## Password reset
* https://symfony.com/doc/4.4/security/reset_password.html
```
composer require symfonycasts/reset-password-bundle
    .....

symfony bin/console make:reset-password
```



## Env variables
```
symfony console debug:container --env-vars

symfony console about

# Ex: update .env and print $_
print_r($_SERVER)
```

## Manage Errors pages
```
composer require symfony/twig-pack
mkdir -p templates/bundles/TwigBundle/Exception
touch templates/bundles/TwigBundle/Exception/error.html.twig

symfony console cache:clear
```


## Contact page
```
$ symfony console make:Controller
Contact

$ symfony console make:form
Contact
(empty to no link it to an entity)

```


### Deployment
<img width="1551" alt="image" src="https://user-images.githubusercontent.com/32338685/148135287-f3b5a507-0df7-4df6-a4fe-03026dda491f.png">


https://symfony.com/doc/current/deployment.html

```
1/ .env   
set env=prod
set DATABASE_URL
2/ after each update: symfony console cache:clear


```
