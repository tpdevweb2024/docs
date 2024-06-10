# NPM et les librairies

NPM (Node Package Manager) est l’un des plus grands gestionnaires de paquets pour JavaScript, utilisé principalement pour télécharger et installer des librairies de code ouvert.

## Installation de npm

Pour installer npm, il est d'abord nécessaire de procéder à l'installation de Node.js. Npm, qui est le gestionnaire de paquets de Node.js, est inclus automatiquement avec Node.js.&#x20;

Pour commencer, rendez-vous sur le site officiel de Node.js et téléchargez la version appropriée à votre système d'exploitation. Une fois le téléchargement terminé, suivez les instructions fournies pour installer Node.js sur votre machine.&#x20;

Une fois l'installation complète, vous aurez à la fois Node.js et npm installés et prêts à être utilisés.&#x20;

Maintenant, vous pouvez vérifier l'installation en utilisant les commandes `node -v` et `npm -v` dans votre terminal pour afficher les versions installées respectivement.

## Pourquoi utiliser NPM ?

NPM (Node Package Manager) est un outil puissant pour les développeurs pour plusieurs raisons :

* **La multitude de dépendances** : NPM permet d'installer, mettre à jour et supprimer facilement les packages et leurs dépendances.
* **Partage de code** : Il facilite le partage de code avec d'autres développeurs via le registre public npm.
* **Scripts automatisés** : Vous pouvez utiliser NPM pour exécuter des scripts automatisés pour des tâches courantes, telles que le développement, les tests et le déploiement.
* **Écosystème riche** : Avec des millions de packages disponibles, il offre un écosystème riche pour accélérer le développement d'applications.

## Utilisation de npm

### Initialiser un projet

Pour créer un nouveau projet, utilisez la commande suivante :

```bash
npm init
```

{% hint style="info" %}
Bon à savoir : Vous pouvez utiliser le drapeau -y pour répondre oui à toutes les questions que posera la CLI au moment de l'init : `npm init -y`
{% endhint %}

### Le fichier package.json

L'objectif de l'initialisation est de créer le fichier package.json à la rcine de notre projet. Le fichier `package.json` est essentiel pour tout projet Node.js.&#x20;

Il permet de :

* **Définir les dépendances** : Liste toutes les librairies nécessaires à votre projet.
* **Gérer les scripts** : Vous pouvez définir des commandes personnalisées pour automatiser des tâches.
* **Fournir des informations sur le projet** : Contient la version, la description, les auteurs, et d'autres métadonnées importantes.
* **Faciliter la collaboration** : Les autres développeurs peuvent cloner le projet et installer rapidement les dépendances nécessaires.

### Le fichier package-lock.json

Le fichier `package-lock.json` est automatiquement généré lors de l'installation des dépendances via npm. Il assure que les installations futures soient cohérentes en spécifiant les versions exactes des dépendances installées.

## Installer une librairie

Pour installer une librairie, par exemple, `lodash`, utilisez :

```bash
npm install lodash
```

### Utiliser une librairie

Après l'installation, vous pouvez utiliser la librairie dans votre code JavaScript :

```javascript
const _ = require('lodash');
```

{% hint style="info" %}
Il est important de comprendre qu'à ce niveau, seuls les serveurs étant utilisés avec le Runtime NodeJS sauront utiliser cette méthode. Ou alors en utilisant des bundlers comme Webpack ou encore l'excellent ViteJS.
{% endhint %}

### Les librairies populaires

#### Lodash

Lodash est une librairie JavaScript utilitaire extrêmement puissante qui simplifie et accélère le travail avec divers types de données tels que les tableaux, les nombres, les objets, les chaînes de caractères, et bien plus encore.&#x20;

Elle propose une vaste gamme de fonctions prêtes à l'emploi qui permettent de manipuler et transformer les données facilement, tout en améliorant la lisibilité et la maintenance du code.&#x20;

{% hint style="info" %}
Grâce à sa modularité, Lodash peut être utilisée aussi bien dans des projets front-end que back-end, ce qui en fait un outil incontournable pour les développeurs souhaitant gagner en productivité.
{% endhint %}

#### Exemple d'utilisation de Lodash

{% code overflow="wrap" %}
```javascript
const _ = require('lodash');

// Exemple d'utilisation de la fonction _.chunk pour diviser un tableau en sous-tableaux de taille spécifiée.
const myArray = [1, 2, 3, 4, 5, 6, 7, 8];
const chunkedArray = _.chunk(myArray, 3);
console.log(chunkedArray); 
// Résultat: [[1, 2, 3], [4, 5, 6], [7, 8]]

// Exemple d'utilisation de la fonction _.merge pour fusionner deux objets.
const object1 = { 'a': [{ 'b': 2 }, { 'd': 4 }] };
const object2 = { 'a': [{ 'c': 3 }, { 'e': 5 }] };
const mergedObject = _.merge(object1, object2);
console.log(mergedObject); 
// Résultat: { 'a': [{ 'b': 2, 'c': 3 }, { 'd': 4, 'e': 5 }] }
```
{% endcode %}

#### Express

Express est un framework web pour Node.js, rapide et minimaliste, qui facilite la création de serveurs web. Conçu pour simplifier plusieurs aspects du développement web, Express permet aux développeurs de gérer facilement les requêtes HTTP, les routes, et les middlewares.&#x20;

Grâce à sa flexibilité et à sa large adoption, il s'intègre parfaitement à d'autres modules et bibliothèques Node.js, offrant ainsi une base robuste pour construire des applications web évolutives et performantes.

#### Exemple d'utilisation d'Express

```javascript
const express = require('express');
const app = express();
const port = 3000;

// Route de base qui envoie 'Hello World!' au client
app.get('/', (req, res) => {
  res.send('Hello World!');
});

// Demarrage du serveur sur le port défini
app.listen(port, () => {
  console.log(`Serveur à l'écoute sur http://localhost:${port}`);
});
```

Ce code crée un serveur web basique avec Express qui écoute les requêtes sur le port 3000. Lorsque vous accédez à la route principale (`/`), le serveur répond avec "Hello World!".

### Gestion des dépendances

Utilisez les commandes suivantes pour gérer les dépendances :

* **Lister les dépendances** : `npm list`
* **Mettre à jour une dépendance** : `npm update <package-name>`
* **Désinstaller une dépendance** : `npm uninstall <package-name>`

{% hint style="info" %}
NPM simplifie la gestion des librairies JavaScript et leur intégration dans vos projets. En maîtrisant npm, vous pouvez facilement ajouter des fonctionnalités à vos applications et maintenance leur code efficacement.
{% endhint %}

_Pour en savoir plus, visitez la documentation officielle de npm :_ [_Docs npm_](https://docs.npmjs.com/)_._
