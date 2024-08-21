# Gestion des modèles et des vues avec  EJS

## **Qu'est-ce qu'EJS ?**

**EJS (Embedded JavaScript)** est un moteur de templates qui permet d'intégrer du code JavaScript dans des fichiers HTML.&#x20;

Il est simple à utiliser pour rendre des vues dynamiques avec Express.js.

## **Installation et configuration de EJS**

*   Installez EJS via npm :

    ```bash
    npm install ejs
    ```
*   Configurez Express pour utiliser EJS comme moteur de templates dans votre `app.js` :

    ```javascript
    const express = require('express');
    const app = express();
    const path = require('path');

    // Configuration du moteur de templates
    app.set('view engine', 'ejs');
    app.set('views', path.join(__dirname, 'views'));

    // Route pour la page d'accueil
    app.get('/', (req, res) => {
        res.render('index', { title: 'Page d\'accueil', message: 'Bienvenue sur la page d\'accueil !' });
    });

    const port = 3000;
    app.listen(port, () => {
        console.log(`Le serveur Express est en cours d'exécution sur http://localhost:${port}/`);
    });
    ```
* **Explication :**
  * `app.set('view engine', 'ejs')` : Définit EJS comme moteur de templates.
  * `app.set('views', path.join(__dirname, 'views'))` : Définit le répertoire où Express cherchera les fichiers de template EJS.

## **Création d'un fichier de template avec EJS**

*   Créez un répertoire `views` à la racine de votre projet et ajoutez un fichier `index.ejs` dans ce répertoire avec le contenu suivant :

    ```html
    <!DOCTYPE html>
    <html>
      <head>
        <title><%= title %></title>
      </head>
      <body>
        <h1><%= message %></h1>
        <p>Bienvenue sur notre site web.</p>
      </body>
    </html>
    ```
* **Explication :**
  * `<%= title %>` et `<%= message %>` : Les variables passées depuis le routeur sont intégrées dans le template.

**Exécution :**

* Exécutez votre application et accédez à `http://localhost:3000/`. Vous devriez voir la page HTML rendue avec le titre et le message dynamiques.

## Rendu de vues dynamiques avec Express.js et EJS

### **Passage de données aux templates**

* Vous pouvez passer des données dynamiques aux templates en les incluant dans l'appel à `res.render()`.
*   Par exemple, modifiez votre route pour passer plus de données :

    ```javascript
    app.get('/profile/:username', (req, res) => {
        const username = req.params.username;
        res.render('profile', { title: 'Profil de l\'utilisateur', username: username });
    });
    ```
*   Créez un fichier `profile.ejs` dans le répertoire `views` avec le contenu suivant :

    ```html
    <!DOCTYPE html>
    <html>
      <head>
        <title><%= title %></title>
      </head>
      <body>
        <h1>Profil de l'utilisateur</h1>
        <p>Nom d'utilisateur: <%= username %></p>
      </body>
    </html>
    ```

**Exécution :**

* Accédez à une URL comme `http://localhost:3000/profile/JohnDoe`. Vous devriez voir une page HTML avec le nom d'utilisateur affiché dynamiquement.
