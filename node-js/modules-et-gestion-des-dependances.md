# Modules et gestion des dépendances

## Création et utilisation de modules personnalisés

### **Qu'est-ce qu'un module personnalisé ?**

* Un module personnalisé est simplement un fichier JavaScript que vous créez pour encapsuler certaines fonctionnalités que vous souhaitez réutiliser dans votre application.
* Cela permet de structurer votre code en petits blocs réutilisables, facilitant ainsi la maintenance et l'évolution du projet.

### **Création d'un module simple**

*   Créez un nouveau fichier `math.js` dans votre projet avec le contenu suivant :

    ```javascript
    // math.js

    function addition(a, b) {
        return a + b;
    }

    function soustraction(a, b) {
        return a - b;
    }

    module.exports = {
        addition,
        soustraction
    };
    ```
* Ici, vous définissez deux fonctions (`addition` et `soustraction`) et les exportez à l'aide de `module.exports`, ce qui permet à ces fonctions d'être utilisées dans d'autres fichiers.

### **Utilisation du module dans un autre fichier**

*   Créez un fichier `app.js` dans le même dossier et ajoutez le code suivant :

    ```javascript
    const math = require('./math');

    const x = 10;
    const y = 5;

    console.log(`L'addition de ${x} et ${y} est : ${math.addition(x, y)}`);
    console.log(`La soustraction de ${x} et ${y} est : ${math.soustraction(x, y)}`);
    ```
* Ici, vous importez votre module `math` en utilisant `require('./math')` (le chemin relatif vers votre fichier `math.js`) et utilisez les fonctions exportées pour effectuer des opérations.

#### **Exécution :**

*   Dans le terminal, exécutez le fichier `app.js` :

    ```bash
    node app.js
    ```
* Vous devriez voir le résultat des opérations mathématiques dans la console.

## Gestion des dépendances avec npm

### **Installation de packages npm**&#x20;

* npm permet d'installer et de gérer des bibliothèques tierces dans votre projet. Ces bibliothèques sont appelées **dépendances**.
*   Par exemple, pour installer la bibliothèque `lodash` (un ensemble d'outils utilitaires pour JavaScript), exécutez la commande suivante :

    ```bash
    npm install lodash
    ```
* `lodash` sera ajouté au dossier `node_modules`, et une entrée sera ajoutée dans le fichier `package.json` sous `dependencies`.

### **Utilisation d'un package npm**&#x20;

*   Ajoutez `lodash` à votre projet en l'utilisant dans votre fichier `app.js` :

    ```javascript
    const _ = require('lodash');

    const tableau = [1, 2, 3, 4, 5];
    const inversé = _.reverse([...tableau]);

    console.log('Tableau inversé :', inversé);
    console.log('Tableau original :', tableau); // Notez que le tableau original est modifié
    ```
* Ici, `lodash` est utilisé pour inverser les éléments d'un tableau.

### **Désinstallation de packages npm**&#x20;

*   Pour désinstaller un package que vous n'utilisez plus, vous pouvez exécuter :

    ```bash
    npm uninstall lodash
    ```
* Cela supprimera le package de votre dossier `node_modules` et de `package.json`.

### **Installation de dépendances globales**&#x20;

*   Certaines dépendances peuvent être installées globalement pour être utilisées dans tous vos projets Node.js. Par exemple, pour installer `nodemon` (un outil qui redémarre automatiquement votre serveur à chaque modification de fichier), exécutez :

    ```bash
    npm install -g nodemon
    ```
* Vous pouvez ensuite lancer vos scripts avec `nodemon` au lieu de `node` pour une meilleure expérience de développement.
