# Node_js
Contient des infos sur node_js



## NPM

### Installer un module

*******

``npm install nomdumodule``
*******

### Update d'un module
*******

`` npm update``

> NPM va chercher sur les serveurs s'il y a de nouvelles versions des modules, puis mettre à jour les modules installés sur votre machine 



## Les bases d'EJS (front)

*******

## Installation EJS
``npm install ejs``

     app.get('/etage/:etagenum/chambre', function(req, res) {
         res.render('chambre.ejs', {etage: req.params.etagenum});
      });

> Ce code fait appel à un fichier chambre.ejs qui doit se trouver dans un sous-dossier appelé "views". Créez donc un ``fichier/views/``

> Exemple de code html

    <h1>Vous êtes dans la chambre</h1>

    <p>Vous êtes à l'étage n°<%= etage %></p>
    
    *******

### Plusieurs paramètres et des boucles

*******

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
*******

## Les bases node (back)

*******


### Req et Res

*******

>La fonction de callback est donc appelée à chaque fois qu'un visiteur se connecte à notre site. Elle prend 2 paramètres :

>La requête du visiteur : cet objet contient toutes les informations sur ce que le visiteur a demandé. On y trouve le nom de la page 
>appelée, les paramètres, les éventuels champs de formulaires remplis...


>La réponse que vous devez renvoyer : c'est cet objet qu'il faut remplir pour donner un retour au visiteur. Au final, res contiendra en >général le code HTML de la page à renvoyer au visiteur.
*******

### Les diffents statut

*******

> err: les erreurs

> req: la requête du visiteur

> res: la réponse à renvoyer (la page HTML et les informations d'en-tête)

> next: un callback vers la prochaine fonction à appeler
*******

### Middleware niveau application

> ``app.use`` La fonction est exécutée à chaque fois que l’application reçoit une demande.

> ``app.get``  Illustre une route et sa fonction de gestionnaire (système de middleware). La fonction gère les demandes GET 

> ``app.post``  illustre une route et sa fonction de gestionnaire (système de middleware). La fonction gère les demandes POST
*******

# Socket.io

## Envoi et réception de messages

### Le serveur veut envoyer un message au client

> Serveur

     io.sockets.on('connection', function (socket) {
           socket.emit('message', 'Vous êtes bien connecté !');
     });
     
> Client

     <script>
          var socket = io.connect('http://localhost:8080');
          socket.on('message', function(message) {
               alert('Le serveur a un message pour vous : ' + message);
          })
     </script>
     
*******

### Le client veut envoyer un message au serveur

> Client 

     $('#poke').click(function () {
          socket.emit('message', 'Salut serveur, ça va ?');
     })
> Serveur 

     // Quand le serveur reçoit un signal de type "message" du client    
    socket.on('message', function (message) {
        console.log('Un client me parle ! Il me dit : ' + message);
    });	

> Les deux mots clées : ``emit`` = envoyer et ``on`` = recevoir

*******
