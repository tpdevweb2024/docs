# Installation d'Express JS

## **Installation d'Express.js via npm**&#x20;

*   Pour installer Express.js dans votre projet, ouvrez votre terminal dans le répertoire de votre projet et exécutez la commande suivante :

    ```bash
    npm install express
    ```
* Cela ajoutera Express.js comme dépendance dans votre projet et l'ajoutera au fichier `package.json`.

## **Création d'une application Express de base**&#x20;

*   Créez un fichier `app.js` et ajoutez le code suivant pour créer une application Express de base :

    ```javascript
    const express = require('express');
    const app = express();

    app.get('/', (req, res) => {
        res.send('Bonjour, monde depuis Express.js !');
    });

    const port = 3000;
    app.listen(port, () => {
        console.log(`Le serveur Express est en cours d'exécution sur http://localhost:${port}/`);
    });
    ```
* **Explication :**
  * `express()` : Crée une nouvelle instance de l'application Express.
  * `app.get('/', callback)` : Définit une route GET pour la racine (`/`) de l'application. Le callback est exécuté lorsque cette route est accédée, et il envoie une réponse "Bonjour, monde depuis Express.js !".
  * `app.listen(port, callback)` : Démarre le serveur sur le port spécifié et exécute le callback une fois que le serveur est prêt.

## **Exécution de l'application**&#x20;

*   Dans le terminal, exécutez le fichier `app.js` :

    ```bash
    node app.js
    ```
* Accédez à `http://localhost:3000/` dans votre navigateur. Vous devriez voir le message "Bonjour, monde depuis Express.js !" affiché sur la page.
