## Doctrine
# Installation de doctrine sur un projet skeleton
```shell
composer require symfony/orm-pack
```
# Installation des assistances en ligne de commande
```shell
composer require symfony/maker-bundle --dev
```
Fichier de configuration *.env.local*  à la racine de ton projet. A duplique avec le fichier déjà existant *.env* 
```php
# .env.local
DATABASE_URL="mysql://your_username:your_pwd@127.0.0.1:3306/wild-series"
```
..* Type de base de données : mysql
..* Utilisateur : your_username
..* Mot de passe : your_pwd
..* Hôte : 127.0.0.1 (ou localhost)
..* Port : 3306 (port standard de MySql)
..* Base de données : wild-series

## Création du cablage 
```php
php bin/console doctrine:database:create
```
## Création d'une entité
```php
php bin/console make:entity
```
```php
Main types
  * string
  * text
  * boolean
  * integer (or smallint, bigint)
  * float

Relationships / Associations
  * relation (a wizard will help you build the relation)
  * ManyToOne
  * OneToMany
  * ManyToMany
  * OneToOne

Array/Object Types
  * array (or simple_array)
  * json (or json_array)
  * object
  * binary
  * blob

Date/Time Types
  * datetime (or datetime_immutable)
  * datetimetz (or datetimetz_immutable)
  * date (or date_immutable)
  * time (or time_immutable)
  * dateinterval

Other Types
  * decimal
  * guid
```
## Mettre à jour la base de données.
```shell
php bin/console make:migration
```
Pour chaque ordre SQL, Doctrine Migration va générer son ordre SQL inverse.
## Pour exécuter cette migration (et de réellement impacter le schéma de la base de données).
```shell
php bin/console doctrine:migrations:migrate
```
## Liste des outils doctrine.
```shell
php bin/console
```
## Mise à jour d’une entité.
```shell
php bin/console make:entity --regenerate
```
## Détection des entités.
```shell
php bin/console doctrine:mapping:info
```
## Validation des entités.
```shell
php bin/console doctrine:schema:validate
```
## Contrôle des migrations.
```shell
php bin/console doctrine:migrations:status
```
## Exécuter des migrations de manière unitaire.
```shell
php bin/console doctrine:migrations:execute [nom de fichier de ta migration] --down
```
## Exécuter une migration dans le sens inverse.
```shell
php bin/console doctrine:migrations:execute [nom de fichier de ta migration] --up
```







