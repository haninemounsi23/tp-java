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
