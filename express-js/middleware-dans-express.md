# Middleware dans Express

## Qu'est-ce qu'un middleware ?

Un **middleware** dans Express.js est une fonction qui a accès à l'objet requête (`req`), à l'objet réponse (`res`), et à la fonction suivante dans le cycle de traitement des requêtes d'une application (`next`).

Les middlewares peuvent effectuer des tâches comme :

* L'exécution de code.
* La modification des objets `req` et `res`.
* La fin du cycle de requête/réponse.
* L'appel de la fonction `next()` pour passer au middleware suivant.

### **Exemple simple de middleware :**

*   Ajoutez un middleware de journalisation (logging) pour chaque requête dans votre application `app.js` :

    ```javascript
    const express = require('express');
    const app = express();

    // Middleware de journalisation
    app.use((req, res, next) => {
        console.log(`${req.method} ${req.url}`);
        next(); // Passe au middleware suivant
    });

    // Route pour la page d'accueil
    app.get('/', (req, res) => {
        res.send('Bienvenue sur la page d\'accueil !');
    });

    const port = 3000;
    app.listen(port, () => {
        console.log(`Le serveur Express est en cours d'exécution sur http://localhost:${port}/`);
    });
    ```
* **Explication :**
  * `app.use(middlewareFunction)` : Utilise un middleware pour toutes les routes.
  * Dans cet exemple, le middleware journalise chaque requête (la méthode HTTP et l'URL) avant de passer au middleware ou à la route suivante grâce à `next()`.
  * Lancez l'application et accédez à plusieurs URL (par exemple, `/`, `/about`). Vous verrez les requêtes journalisées dans la console.

## Utilisation de middlewares intégrés et tiers

### **Middlewares intégrés dans Express**

* Express.js inclut des middlewares prêts à l'emploi pour des tâches courantes, comme servir des fichiers statiques ou analyser le corps des requêtes.
* **Middleware pour servir des fichiers statiques :**
  * Utilisez `express.static` pour servir des fichiers comme des images, des CSS ou des JavaScript depuis un dossier spécifique.
  *   Ajoutez ce middleware dans votre `app.js` :

      ```javascript
      app.use(express.static('public'));
      ```
  * **Explication :** Tous les fichiers dans le dossier `public` seront accessibles directement via l'URL. Par exemple, un fichier `public/logo.png` sera accessible via `http://localhost:3000/logo.png`.
* **Middleware pour parser les corps des requêtes (body-parser) :**
  * Express.js intègre désormais le middleware `express.json()` pour analyser les requêtes au format JSON.
  *   Ajoutez ce middleware pour gérer les requêtes POST avec un corps JSON :

      ```javascript
      app.use(express.json());
      ```

### **Middlewares tiers :**

* Il existe de nombreux middlewares créés par la communauté pour ajouter des fonctionnalités à Express.js.
* **Exemple avec `morgan` (middleware de journalisation avancée) :**
  *   Installez `morgan` via npm :

      ```bash
      npm install morgan
      ```
  *   Ajoutez-le à votre application :

      ```javascript
      const morgan = require('morgan');
      app.use(morgan('dev'));
      ```
  * **Explication :** `morgan('dev')` journalise les requêtes HTTP avec des informations supplémentaires utiles pour le développement.

## Gestion des erreurs avec les middlewares

### **Middleware de gestion des erreurs :**

* Les middlewares de gestion des erreurs sont définis après toutes les routes et autres middlewares.
*   Ajoutez un middleware de gestion des erreurs à la fin de votre `app.js` :

    ```javascript
    app.use((err, req, res, next) => {
        console.error(err.stack);
        res.status(500).send('Quelque chose a mal tourné !');
    });
    ```
* **Explication :**
  * Ce middleware attrape les erreurs passées par `next(err)` et renvoie une réponse générique avec un statut HTTP 500.
