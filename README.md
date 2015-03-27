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
$ npm install grunt-cli
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
