# DESCRIPTION GENERALE DU PROJET

Le projet bpmine consiste à interagir avec le monde réel à partir de minetest. 

A partir de ses actions dans le jeu, le joueur déclenche des commandes vers les différents équipements de notre maison.

## Qu'est ce que minetest ?

Si vous ne connaissez pas minecraft, c'est un célèbre jeu où l'on casse et l'on empile des blocks pour façonner son propre monde. On évolue à plusieurs dans cet environnement, et s'il n'y a pas de but réèl, l'intérêt du jeu réside dans la collaboration entre les joueurs. Ces derniers doivent s'entraîder et exploiter les ressources trouvées pour progresser ensemble et construire leur monde.

Minecraft est un jeu payant appartenant aujourd'hui à Microsoft.

Minetest est un jeu similaire mais gratuit et open source. C'est donc tout naturellement que nous avons choisit de jouer avec celui-ci. 

Voir https://www.minetest.net/ pour plus détails.

Le logiciel est écrit principaalement en C++ pour les plateformes Windows, Linux et Android.  

Le code de la boucle de jeu et les interractions entre les joueurs et le monde sont écrites en Lua. Cela permet d'étendre les fonctionnalités du jeu à l'aide de MODs que l'on peut ajouter facilement.

## Quels sont les équipements de la maison que l'on commande ?

Nous commandons les lampes Hue (Philips) que nous avons installées dans notre maison depuis plusieurs années. Voir https://www.philips-hue.com/fr-fr.

Nous commandons aussi des bandeaux de LEDs que nous avons installés dans la cabane de notre chat.

Voir le projet https://github.com/bpmine/minou_uino pour en savoir plus.

La liste n'est pas exhaustive et de nombreux équipements pourrons rejoindre la liste.

## Comment ça marche ?

### Vue globale de l'ensemble

![GitHub Logo](/images/architecture.png)

Le serveur minetest et la passerelle de domotique communiquent à l'aide d'un broker de messages Rabbitmq. Par ce biais, ils s'échangent des messages.

La passerelle de domotique pilote les équipements de la maison.

### La partie Rabbitmq - Le broker de messages

Rabbitmq est un serveur permettant l'échange de messages asynchrones entre plusieurs applications. Ici, il permet les échanges entre la passerelle de domotique et le serveur minetest.

Voir: https://www.rabbitmq.com/

### La partie minetest et ses mods

Deux mods et un serveur d'interface doivent être ajoutés au serveur minetest de base.

#### Serveur d'interface minetest/rabbitmq

Sur le serveur minetest, il faut installer un serveur d'interface entre les MODs du jeu écrits en Lua et le rabbitmq.

C'est le logiciel https://github.com/bpmine/wsrabbit qui gère cette interface.

Il répond à des requêtes de webservice de la part du serveur minetest et relaye les messages de et vers le rabbitmq.

#### MOD msg_bridge

Ce MOD Lua permet à tout autre MOD de minetest:
- de poster des messages vers rabbitmq;
- de s'abonner aux messages entrants.

Voir: https://github.com/bpmine/mods/tree/master/msg_bridge

#### MOD domotic

Ce MOD Lua permet à tout autre MOD de minetest de commander les équipements de domotique.
Il utilise le MOD msg_bridge pour poster les messages de commande pour la passerelle de domotique.

Voir: https://github.com/bpmine/mods/tree/master/domotic

### La partie passerelle de domotique

La passerelle de domotique est un serveur du réseau local de notre maison. Ce programme communique avec rabbitmq et relaye les commandes vers les équipements.

Voir: https://github.com/bpmine/domgw

### Les équipements faits-maison

Ces équipements sont basés sur des cartes arduino (https://www.arduino.cc/). Ils sont commandable par webservice sur le réseau local de la maison.

Voir: https://github.com/bpmine/minou_uino
