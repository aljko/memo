## Relation "Many-To-One" avec Doctrine.
### Créer la relation dans Symfony.
```shell
~/Wild/Quetes/wild-series/symfony(master ✗) bin/console make:entity

 Class name of the entity to create or update (e.g. GrumpyPizza):
 > Program

 Your entity already exists! So let's add some new fields!

 New property name (press <return> to stop adding fields):
 > category

 Field type (enter ? to see all types) [string]:
 > ManyToOne

 What class should this entity be related to?:
 > Category

 Is the Program.category property allowed to be null (nullable)? (yes/no) [yes]:
 > no

 Do you want to add a new property to Category so that you can access/update Program objects from it - e.g. $category->getPrograms()? (yes/no) [yes]:
 > no

 updated: src/Entity/Program.php

 Add another property? Enter the property name (or press <return> to stop adding fields):
 > 


           
  Success! 
           

 Next: When you're ready, create a migration with make:migration
```
### Modifier la relation dans Symfony.
```shell
~/Wild/Quetes/wild-series/symfony(master ✗) bin/console update:entity
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