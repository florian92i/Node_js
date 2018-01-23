# Node_js
Contient des infos sur node_js
## Req et Res

>La fonction de callback est donc appelée à chaque fois qu'un visiteur se connecte à notre site. Elle prend 2 paramètres :

>La requête du visiteur : cet objet contient toutes les informations sur ce que le visiteur a demandé. On y trouve le nom de la page 
>appelée, les paramètres, les éventuels champs de formulaires remplis...


>La réponse que vous devez renvoyer : c'est cet objet qu'il faut remplir pour donner un retour au visiteur. Au final, res contiendra en >général le code HTML de la page à renvoyer au visiteur.


## NPM

### Installer un module

*******

``npm install nomdumodule``

### Update d'un module

`` npm update``

> NPM va chercher sur les serveurs s'il y a de nouvelles versions des modules, puis mettre à jour les modules installés sur votre machine 

*******

### Les diffents statu

> err: les erreurs

> req: la requête du visiteur

> res: la réponse à renvoyer (la page HTML et les informations d'en-tête)

> next: un callback vers la prochaine fonction à appeler
