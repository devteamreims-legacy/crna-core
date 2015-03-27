# README
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
