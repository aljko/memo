# Créer un projet Symfony 4

### Telechargement de l'outil d’installation de Symfony.
```bash    
    wget https://get.symfony.com/cli/installer -O - | bash
```
### Installation globale.
```bash
    sudo mv /home/TonNomUtilisateurLinux/.symfony/bin/symfony /usr/local/bin/symfony
    symfony -v
```
### Verification que la machine a tout pour lancer Symfony correctement.
    symfony check:requirements

### Créer un nouveau projet.
    symfony new --full wild-series --version=lts

### Créer un nouveau projet light.
    symfony new wild-series

### Allumer le serveur web de symfony.
    symfony server:start

### Allumer le serveur web de symfony en tâche de fond.
    symfony server:start -d

### Eteindre le serveur web de symfony en tâche de fond.
    symfony server:stop

### Allumer le serveur web de symfony afin de pouvoir utiliser ton serveur depuis un autre ordinateur ou un portable.
    symfony server:start 192.168.1.20

### Toutes tes options console possibles.
    bin/console list

### Concernant ton environnement de projet.
    bin/console about

### Installation, mise à jour et suppression de dépendance.
    composer require logger
    composer update logger
    composer remove logger
