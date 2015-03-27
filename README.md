# README
## Prérequis installés :
* Git
* node.js
* Compass
```
$ gem update --system && gem install compass
```
* grunt-cli
```
$ npm install -g grunt-cli
```
* nodemon
```
npm install -g nodemon
```
## Git & sources
Puller le dépot "core"
```
$ git clone https://github.com/devteamreims/crna-core
$ cd crna-core
```
Initialiser les sous modules
```
$ git submodule update --init crna-server
$ git submodule update --init crna-client
```
Se placer sur la branche master et puller les sous modules
```
$ cd crna-client
$ git checkout master
$ git pull

$ cd ../crna-server
$ git checkout master
$ git pull
```

## Installation des modules node & bower
Dans le répertoire crna-client :
```
$ cd crna-client
$ npm install
$ bower install
```
Idem dans le répertoire server (sauf bower) :
```
$ cd crna-server
$ npm install
```

## Lancer l'application (en production)
En mode production, il faut tout d'abord générer la partie front-end.
```
$ cd crna-client
$ grunt build --force
```
Ici, grunt (un équivalent de make en C), va "compiler" la partie client, et la placer dans le répertoire du serveur. Les fichiers SASS vont être transformés en .CSS, le javascript va être "minifié". Bref, tout ça est visible dans le fichier Gruntfile.js.

Une fois le frontend généré, il suffit de lancer le backend :
```
$ cd crna-server
$ npm start
```

## Lancer l'application (développement)
On commence par le frontend. Au lieu de tout compiler et copier dans la partie backend, on lance :
```
$ cd crna-client
$ grunt serve
```
Grunt compile le client, "watche" les répertoires pour le recompiler à la volée, et vous le propose sur localhost:9000

On lance ensuite le backend :
```
$ cd crna-server
$ npm test
```
Et on se connecte sur http://localhost:3000/.
Le répertoire "crna-server/dist" est bypassé, le backend vous sert le frontend directement à partir de ce que Grunt compile à la volée dans "crna-client/.tmp"

Voilà ! Pfiouf !

## Plus d'informations
L'architecture est décrite ici : http://start.jcolemorrison.com/building-an-angular-and-express-app-part-1/ avec les explications de "pourquoi c'est si compliqué".

Au final, on a 2 dépots, un qui contient le code du frontend, un autre qui contient le code du backend. Les deux sont liés par le dépot "core". Le frontend est généré puis servi au navigateur via le backend.
