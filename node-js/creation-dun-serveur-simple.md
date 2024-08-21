# Création d'un serveur simple

## Utilisation du module `http` pour créer un serveur basique

### **Présentation du module `http`**

Le module `http` est un module intégré dans Node.js qui permet de créer un serveur web. Il offre une API pour gérer les requêtes HTTP entrantes et envoyer des réponses.

### **Création d'un serveur**

*   Créez un fichier `server.js` et ajoutez le code suivant :

    ```javascript
    const http = require('http');

    const serveur = http.createServer((req, res) => {
        // Réponse HTTP
        res.statusCode = 200; // Statut OK
        res.setHeader('Content-Type', 'text/plain');
        res.end('Bonjour, monde !\n');
    });

    const port = 3000;
    serveur.listen(port, () => {
        console.log(`Le serveur tourne sur http://localhost:${port}/`);
    });
    ```

### **Explication du code**&#x20;

* `http.createServer()` : Crée un serveur HTTP qui réagit aux requêtes entrantes.
* `req` : Objet représentant la requête HTTP entrante.
* `res` : Objet représentant la réponse HTTP sortante.
* `res.statusCode` : Définit le code de statut HTTP à 200 (OK).
* `res.setHeader('Content-Type', 'text/plain')` : Définit l'en-tête HTTP Content-Type à `text/plain` pour indiquer que la réponse est du texte brut.
* `res.end('Bonjour, monde !\n')` : Envoie la réponse "Bonjour, monde !" au client et termine la connexion.
* `serveur.listen(port, callback)` : Démarre le serveur sur le port spécifié et exécute le callback une fois que le serveur est prêt.

### **Exécution du serveur**

*   Dans le terminal, exécutez le fichier `server.js` :

    ```bash
    node server.js
    ```
*   Vous devriez voir un message confirmant que le serveur tourne :

    ```
    Le serveur tourne sur http://localhost:3000/
    ```
* Ouvrez un navigateur web et accédez à `http://localhost:3000/`. Vous devriez voir affiché "Bonjour, monde !".

## Gestion des requêtes et des réponses

### **Détection du chemin de la requête**

* Vous pouvez personnaliser la réponse en fonction de l'URL demandée par le client.
*   Par exemple, modifiez votre fichier `server.js` pour répondre différemment selon l'URL :

    ```javascript
    const http = require('http');

    const serveur = http.createServer((req, res) => {
        const url = req.url;
        res.statusCode = 200;
        res.setHeader('Content-Type', 'text/plain');

        if (url === '/') {
            res.end('Bienvenue à la page d\'accueil !\n');
        } else if (url === '/about') {
            res.end('À propos de nous\n');
        } else {
            res.statusCode = 404;
            res.end('Page non trouvée\n');
        }
    });

    const port = 3000;
    serveur.listen(port, () => {
        console.log(`Le serveur tourne sur http://localhost:${port}/`);
    });
    ```

#### **Exécution**

* Relancez le serveur et visitez `http://localhost:3000/`, `http://localhost:3000/about`, et une URL inexistante comme `http://localhost:3000/unknown`.
* Notez les différentes réponses en fonction du chemin de l'URL.
