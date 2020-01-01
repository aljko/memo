# Commande Docker
## Chercher/manipuler une image sur le hub
```shell
docker search <nom de l'image>
```
Téléchargement d'une image
```shell
docker pull <nom de l'image>
```
Liste des images téléchargées
```shell
docker images
```
Suppression de conteneur
```shell
docker rm <ID du conteneur>
```
Forcer la suppresion d'un conteneur
```shell
docker rm -f <ID du conteneur>
```
Suppression d'image
```shell
docker rmi <ID de l'image>
```
Afficher tous les conteneurs
```shell
docker ps -a
```
Afficher les conteneurs executés
```shell
docker ps
```
## Lancement d'une image
```shell
docker run -ti <ID de l'image>
```
Arreter un conteneur
```shell
docker stop <ID du conteneur>
```
Afficher les differences entre le conteneur active et l'image
```shell
docker diff <ID du conteneur>
```
## Création d'image
Créer un fichier nommé Dockerfile
```
FROM ubuntu:18.04
MAINTAINER Medved

RUN apt-get update && \
    apt-get install -y apache2
```
Création de l'image
```shell
docker build .
```
Création et nommage de l'image
```shell
docker build -t nomDeMonImage .
```

docker commit <3 Premieres caractère de ID> <nom nouvelle image>

docker save <nom de l'image> > </emplacement>

docker run -p <port exterieur:port interieur> <nom de l'image>


docker run -d --name some-ghost -p 3001:2368 -v /path/to/ghost/blog:/var/lib/ghost/content ghost:1-alpine
