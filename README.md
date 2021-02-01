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

### La partie Rabbitmq - Le broker de messages

### La partie minetest et ses mods

### La partie passerelle de domotique

### Les équipements faits-maison
