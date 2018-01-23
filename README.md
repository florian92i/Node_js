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

*******

> err: les erreurs

> req: la requête du visiteur

> res: la réponse à renvoyer (la page HTML et les informations d'en-tête)

> next: un callback vers la prochaine fonction à appeler

### Les bases d'EJS (front)

*******

``npm install ejs``

     app.get('/etage/:etagenum/chambre', function(req, res) {
         res.render('chambre.ejs', {etage: req.params.etagenum});
      });

> Ce code fait appel à un fichier chambre.ejs qui doit se trouver dans un sous-dossier appelé "views". Créez donc un ``fichier/views/``

> Exemple de code html

    <h1>Vous êtes dans la chambre</h1>

    <p>Vous êtes à l'étage n°<%= etage %></p>
    
    
## Plusieurs paramètres et des boucles

    app.get('/compter/:nombre', function(req, res) {
    var noms = ['Robert', 'Jacques', 'David'];
    res.render('page.ejs', {compteur: req.params.nombre, noms: noms});
    });
    
> On transmet le nombre envoyé en paramètre et une liste de noms sous forme de tableau. Ensuite, dans le template EJS :

    <h1>Je vais compter jusqu'à <%= compteur %></h1>

    <p><%
       for(var i = 1 ; i <= compteur ; i++) {
         %>

    <%= i %>... 

    <% } %></p>

    <p>Tant que j'y suis, je prends un nom au hasard qu'on m'a envoyé :
    <%= noms[Math.round(Math.random() * (noms.length - 1))] %>
    </p>
