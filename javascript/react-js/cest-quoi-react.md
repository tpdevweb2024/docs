# C'est quoi React ?

## Introduction à React et à CRA (Create React App)

### Qu'est-ce que React ?

React est une bibliothèque JavaScript pour la construction d'interfaces utilisateur.&#x20;

Développée par Facebook, elle permet de créer des composants réutilisables offrant une gestion efficace du rendu grâce à un DOM virtuel.

### Initialiser un projet avec Create React App (CRA)

Create React App (CRA) est un outil officiel pour démarrer rapidement un nouveau projet React sans configurations complexes.

#### Étapes pour créer un projet CRA

1. Assurez-vous d'avoir Node.js et npm installés sur votre machine. Vous pouvez les télécharger à partir de [nodejs.org](https://nodejs.org/).
2.  Ouvrez votre terminal et exécutez la commande suivante pour installer Create React App globalement :

    ```
    npm install -g create-react-app
    ```
3.  Pour créer un nouveau projet, exécutez la commande suivante en remplaçant `nom-de-votre-projet` par le nom souhaité pour votre application :

    ```
    create-react-app nom-de-votre-projet
    ```
4.  Une fois l'installation terminée, accédez au répertoire du projet avec :

    ```
    cd nom-de-votre-projet
    ```
5.  Démarrez l'application en exécutant :

    ```
    npm start
    ```

    Cette commande lance le serveur de développement et ouvre automatiquement l'application dans votre navigateur.

## Structure d'un projet CRA

Une fois votre projet créé, vous verrez une structure de dossiers et de fichiers similaire à celle-ci :

```
my-app/
├── README.md
├── node_modules/
├── package.json
├── .gitignore
├── public/
│   ├── index.html
│   └── favicon.ico
└── src/
    ├── App.css
    ├── App.js
    ├── App.test.js
    ├── index.css
    ├── index.js
    ├── logo.svg
    └── serviceWorker.js
```

### Explication des principaux fichiers et dossiers

* **README.md** : Contient des informations de base sur votre projet, y compris comment le configurer et le lancer.
* **node\_modules/** : Répertoire où toutes les dépendances de votre projet sont installées.
* **package.json** : Fichier qui liste les dépendances essentielles, les scripts de commande et les métadonnées de votre projet.
* **.gitignore** : Fichier qui spécifie les fichiers et dossiers à ignorer par Git.
* **public/** : Dossier contenant les fichiers statiques. `index.html` est le fichier HTML principal, `favicon.ico` est l'icône du site.
* **src/** : Dossier principal pour les fichiers source de votre application React. Contient :
  * **App.css** : Fichier CSS pour styler votre composant App.
  * **App.js** : Composant principal de votre application React.
  * **App.test.js** : Fichier de test pour le composant App.
  * **index.css** : Feuille de style globale.
  * **index.js** : Point d'entrée de votre application. C'est ici que le composant App est rendu dans le DOM.
  * **logo.svg** : Logo React utilisé dans le composant App.
  * **serviceWorker.js** : Fichier qui aide à rendre votre application web fonctionnelle hors ligne.

## Pourquoi utiliser React aujourd'hui ?

React est devenu un choix populaire pour le développement d'applications web grâce à plusieurs avantages distincts :

* **Performance** : Le DOM virtuel de React permet de minimiser les mises à jour du vrai DOM, rendant les applications plus rapides et réactives.
* **Composants réutilisables** : La structure basée sur les composants permet de réutiliser le code, ce qui améliore la maintenabilité et la testabilité.
* **Écosystème riche** : Une vaste communauté et une multitude de bibliothèques et d'outils facilitent le développement et l'ajout de fonctionnalités.
* **Support de Facebook** : React est maintenu par Facebook, garantissant des mises à jour régulières et un support à long terme.
* **Apprentissage facile** : Une courbe d'apprentissage modérée et une bonne documentation en font un choix accessible pour les développeurs de tous niveaux.

***
