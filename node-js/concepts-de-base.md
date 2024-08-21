# Concepts de base

## Comprendre le modèle événementiel et non-bloquant de Node.js

### **Modèle événementiel**

* Node.js repose sur un modèle événementiel. Contrairement aux serveurs traditionnels qui bloquent le processus pour attendre une réponse (bloquant), Node.js gère les opérations de manière asynchrone.
* Le **boucle d'événements** (event loop) est au cœur de Node.js. Elle permet à Node.js de gérer les opérations asynchrones (comme les requêtes réseau ou la lecture de fichiers) sans bloquer le reste du code.

### **Exemple simple**&#x20;

*   Voici un exemple pour illustrer ce concept. Créez un fichier `example.js` :

    ```javascript
    console.log('Avant');

    setTimeout(() => {
        console.log('Pendant');
    }, 2000);

    console.log('Après');
    ```
*   Exécutez ce fichier avec la commande :

    ```bash
    node example.js
    ```
* L'ordre d'exécution sera : "Avant", "Après", puis "Pendant". Ce comportement montre que l'exécution de `setTimeout` est asynchrone.

## Introduction aux modules Node.js

### **Les modules dans Node.js**&#x20;

* Un module est un ensemble de fonctions ou d'objets JavaScript que vous pouvez réutiliser dans d'autres parties de votre application.
* Node.js propose plusieurs modules intégrés (built-in), comme `fs` (système de fichiers), `http` (création de serveurs), et `path` (manipulation des chemins de fichiers).

### **Exemple d'utilisation d'un module intégré**&#x20;

*   Créez un fichier `module_example.js` :

    ```javascript
    const fs = require('fs');

    fs.readFile('example.txt', 'utf8', (err, data) => {
        if (err) {
            console.error('Erreur de lecture:', err);
            return;
        }
        console.log('Contenu du fichier:', data);
    });
    ```
* Cet exemple lit le contenu d'un fichier `example.txt` (que vous pouvez créer avec un simple texte) et l'affiche dans la console. Si le fichier n'existe pas, une erreur sera affichée.

## Utilisation du gestionnaire de paquets npm

### **Qu'est-ce que npm ?**

* npm (Node Package Manager) est le gestionnaire de paquets par défaut de Node.js. Il permet d'installer des bibliothèques (packages) JavaScript, de gérer les dépendances, et de partager du code avec la communauté.

### **Initialisation d'un projet Node.js avec npm**&#x20;

*   Ouvrez votre terminal, créez un nouveau dossier pour votre projet et naviguez à l'intérieur :

    ```bash
    mkdir mon-projet
    cd mon-projet
    ```
*   Initialisez un nouveau projet npm avec :

    ```bash
    npm init -y
    ```
* Cela créera un fichier `package.json` qui contiendra des informations sur votre projet et ses dépendances.

### **Installation d'un package avec npm**&#x20;

*   Installez un package populaire, comme `express` (que nous verrons plus tard) :

    ```bash
    npm install express
    ```
* Le package sera ajouté dans un dossier `node_modules` et mentionné dans `package.json` sous les dépendances.
