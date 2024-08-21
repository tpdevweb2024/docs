# Routage avec Express JS

## Création de routes basiques

### **Qu'est-ce qu'une route ?**

* Une **route** dans Express.js est une combinaison d'une méthode HTTP (GET, POST, etc.) et d'un chemin d'URL spécifique. Elle détermine comment l'application répond à une requête client à une URL spécifique.
* Par exemple, une route peut être définie pour répondre aux requêtes GET sur `/about` avec une page "À propos".

### **Définir des routes avec Express**&#x20;

*   Reprenons l'exemple précédent avec le fichier `app.js`. Ajoutez plusieurs routes pour différents chemins :

    ```javascript
    const express = require('express');
    const app = express();

    // Route pour la page d'accueil
    app.get('/', (req, res) => {
        res.send('Bienvenue sur la page d\'accueil !');
    });

    // Route pour la page "À propos"
    app.get('/about', (req, res) => {
        res.send('À propos de nous');
    });

    // Route pour la page "Contact"
    app.get('/contact', (req, res) => {
        res.send('Contactez-nous à contact@example.com');
    });

    const port = 3000;
    app.listen(port, () => {
        console.log(`Le serveur Express est en cours d'exécution sur http://localhost:${port}/`);
    });
    ```
* **Explication :**
  * `app.get('/about', callback)` : Définit une route qui répond aux requêtes GET sur `/about`.
  * Les autres routes fonctionnent de manière similaire pour leurs chemins respectifs (`/contact`, etc.).

#### **Exécution :**

* Exécutez votre application et testez les routes dans le navigateur en accédant à `http://localhost:3000/`, `http://localhost:3000/about`, et `http://localhost:3000/contact`.

## Gestion des paramètres de route et des requêtes

### **Paramètres de route**

* Les **paramètres de route** permettent de capturer des valeurs dynamiques dans les segments d'URL.
* Par exemple, vous pouvez capturer un `id` d'utilisateur dans une URL comme `/users/:id`.
*   Modifiez votre `app.js` pour inclure une route avec un paramètre de route :

    ```javascript
    app.get('/users/:id', (req, res) => {
        const userId = req.params.id;
        res.send(`Utilisateur demandé avec ID : ${userId}`);
    });
    ```
* **Explication :**
  * `req.params.id` : Capture la valeur dynamique `id` de l'URL et l'utilise dans la réponse.

### **Gestion des requêtes GET avec query string**

* Une **query string** est une partie de l'URL qui contient des paramètres sous forme de paires clé-valeur après le symbole `?`.
* Par exemple, une URL comme `/search?q=express` peut être utilisée pour une recherche.
*   Ajoutez une route qui gère les requêtes avec une query string :

    ```javascript
    app.get('/search', (req, res) => {
        const query = req.query.q;
        res.send(`Vous avez recherché : ${query}`);
    });
    ```
* **Explication :**
  * `req.query.q` : Accède à la valeur du paramètre `q` dans la query string.

**Exécution :**

* Exécutez l'application et testez les paramètres de route en accédant à `http://localhost:3000/users/123` (où `123` est l'ID de l'utilisateur).
* Testez également la route avec query string en accédant à `http://localhost:3000/search?q=express`.
