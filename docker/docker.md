### Commande Docker ?local.dev
## lancement conteneur
```shell
docker run -ti <nom de l'image>
```
## Voir les conteneurs executés
```shell
docker ps
```
## Voir les differences entre le conteneur active 
```shell
docker diff <3 Premieres caractère de ID>

docker images

docker commit <3 Premieres caractère de ID> <nom nouvelle image>

docker save <nom de l'image> > </emplacement>

docker run -p <port exterieur:port interieur> <nom de l'image>

docker rm -f <nom de l'image>

docker run -d --name some-ghost -p 3001:2368 -v /path/to/ghost/blog:/var/lib/ghost/content ghost:1-alpine

docker stop <3 Premieres caractère de ID> 
```
