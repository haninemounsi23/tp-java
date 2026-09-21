# tp-java

## 2. Communication en mode UDP

### Q2.1 - Que se passe-t-il si le client est lancé sans serveur ?

En UDP, le client peut envoyer un message même si le serveur n'est pas lancé.
Il n'y a pas de connexion préalable entre le client et le serveur.

Si aucun serveur n'écoute sur le port utilisé, le message est simplement perdu.

### Q2.2 - Quel est le numéro de port utilisé ?

Le port utilisé est le port **1234**.

On le retrouve :
- côté serveur avec `new DatagramSocket(1234)`
- côté client dans le `DatagramPacket`

Le port 1234 est adapté pour ce TP car il est supérieur aux ports système 0 à 1023.
Il faut cependant vérifier qu'il n'est pas déjà utilisé par une autre application.

### Q2.3 - Communication dans les deux sens

Le programme est ensuite modifié pour que le serveur renvoie au client la chaîne qu'il a reçue.

Le fonctionnement devient :

Client → Serveur : `Hello World`

Serveur → Client : `Hello World`

Le serveur récupère l'adresse IP et le port du client grâce au paquet reçu, puis utilise ces informations pour lui renvoyer le message.

Le client envoie donc d'abord son message, puis attend la réponse du serveur avant de se fermer.


### Q4.1 – Le fonctionnement est-il correct ?

Oui.
Le client se connecte au serveur sur le port 80.
Il envoie une requête HTTP et affiche la réponse.
La commande > permet d'enregistrer la réponse dans un fichier.

Exemple :

java Clienthttp www.univ-rouen.fr > ur.txt

### Q4.2 – Le contenu du fichier est-il conforme à ce qui est attendu ?

Oui.
La réponse contient une ligne de statut HTTP, des en-têtes, une ligne vide et le contenu de la page.

### Q4.3 – La sortie contient-elle uniquement du HTML ?

Non.
La réponse contient aussi les informations HTTP et les en-têtes.
Le code HTML arrive après les en-têtes.

### Q4.4 – Test avec www.javaworld.com

Le résultat n'est pas le même que dans un navigateur.
Dans notre test, le serveur peut renvoyer une erreur 1003.
Notre client HTTP est très simple et n'envoie pas toutes les informations d'un navigateur.

### Q4.5 – Pourquoi le résultat est-il différent d'un navigateur ?

Un navigateur est plus complet que notre programme.
Il gère les redirections et HTTPS.
Il charge aussi le CSS, les images et le JavaScript.
Notre programme affiche seulement la réponse HTTP reçue.

### Q4.6 – Signification des principaux en-têtes HTTP

Date : date de la réponse.

Server : informations sur le serveur Web.

Content-Type : type du contenu envoyé.

Content-Length : taille du contenu.

Location : adresse utilisée pour une redirection.

Connection : gestion de la connexion TCP.

Il faut garder uniquement les en-têtes réellement présents dans ur.txt.
