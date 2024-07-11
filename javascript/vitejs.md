# ViteJS

ViteJS est un outil de construction moderne pour JavaScript et TypeScript. Il offre un serveur de développement ultra-rapide et une compilation de production optimisée. Ses principales caractéristiques incluent :

* **Démarrage rapide** : Vite lance un serveur en quelques millisecondes, indépendamment de la taille de votre projet.
* **Actualisation instantanée** : Modification et rechargement immédiat sans perte d'état de l'application.
* **Compilation optimisée** : Utilise Rollup pour une production optimisée avec une configuration par défaut prête pour la production.

## Installation de Vite

### Prérequis

* Node.js (version 12.0.0 ou supérieure)

### Installation via npm

```shell
npm init vite@latest mon-projet
cd mon-projet
npm install
```

## Utilisation de Vite

### Commandes de base

*   **Démarrer le serveur de développement** :

    ```shell
    npm run dev
    ```
*   **Compiler pour la production** :

    ```shell
    npm run build
    ```
*   **Prévisualiser l'application de production** :

    ```shell
    npm run preview
    ```

### Première page avec ViteJS

Modifiez le fichier `index.html` dans le dossier racine de votre projet avec le contenu suivant :

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ma Premiere Page avec Vite</title>
</head>
<body>
    <h1>Bonjour Vite!</h1>
    <p>Ceci est ma première page avec ViteJS.</p>
    <script>
        console.log('Bienvenue sur ma première application ViteJS!');
    </script>
</body>
</html>
```

Vous pouvez maintenant démarrer le serveur de développement et voir votre application en action en exécutant :

```shell
npm run dev
```

## Les assets : JS et CSS

Pour gérer vos fichiers JavaScript et CSS avec Vite, créez un dossier `assets` à la racine de votre projet. Placez vos fichiers JavaScript dans `assets/js` et vos fichiers CSS dans `assets/css`.

### Exemple de fichier JavaScript

Créez un fichier `main.js` dans `assets/js` avec le contenu suivant :

```js
console.log('Fichier JavaScript chargé avec succès');
```

### Exemple de fichier CSS

Créez un fichier `style.css` dans `assets/css` avec le contenu suivant :

```css
body {
    font-family: Arial, sans-serif;
}
h1 {
    color: blue;
}
```

### Inclusion des assets dans index.html

Modifiez votre `index.html` pour inclure les fichiers JavaScript et CSS :

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ma Premiere Page avec Vite</title>
    <link rel="stylesheet" href="assets/css/style.css">
</head>
<body>
    <h1>Bonjour Vite!</h1>
    <p>Ceci est ma première page avec ViteJS.</p>
    <script src="assets/js/main.js"></script>
</body>
</html>
```

En suivant ces étapes, vos styles et scripts seront correctement chargés dans votre application ViteJS.

## Les librairies

### Installation d'une librairie

Pour installer des librairies supplémentaires, utilisez la commande npm install suivie du nom de la librairie :

```bash
npm install nom-de-la-librairie
```

Par exemple, pour installer la librairie canvas-confetti :

```bash
npm install canvas-confetti
```

### Utilisation des librairies

Après l'installation, vous pouvez importer et utiliser la librairie dans vos fichiers JavaScript ou TypeScript :

```javascript
import confetti from 'canvas-confetti'

confetti();
```

Vite se chargera de résoudre les imports et de distribuer les fichiers nécessaires.

### Gestion des imports non-JavaScript

Vite permet également d'importer des fichiers non-JavaScript, comme des fichiers JSON ou des images. Par exemple :

```javascript
import data from './data.json'
console.log(data) // {...}

import monImage from './monImage.jpg'
console.log(monImage) // "/assets/monImage-ahju37.jpg"
```

### Un exemple : sass

Vite supporte Sass nativement, mais vous devez installer le préprocesseur Sass :

```bash
npm install -D sass
```

#### Créer des fichiers Sass

Créez un dossier `src/styles` et ajoutez un fichier Sass, par exemple `main.scss` :

```css
// assets/css/main.scss
$primary-color: #3498db;

body {
  font-family: Arial, sans-serif;
  background-color: $primary-color;
  color: white;
}
```

#### Importer le fichier Sass

Dans votre fichier JavaScript principal (généralement `assets/js/main.js` ou `assets/ts/main.ts`), importez le fichier Sass :

```javascript
import '../assets/css/main.scss'
```

## Vite et les templates de projet

Lancez la commande de création de projet Vite :

```bash
npm init vite@latest
```

Vite vous guidera ensuite à travers un processus interactif.&#x20;

1. D'abord, il vous demandera de nommer votre projet.&#x20;
2. Entrez le nom souhaité et appuyez sur Entrée.
3. Ensuite, il vous présentera une liste de frameworks/bibliothèques à choisir. Utilisez les flèches du clavier pour naviguer et appuyez sur Entrée pour sélectionner. \
   Les options typiques incluent : Vanilla, VueJS, React, Preact, Lit, Svelte
4. Après avoir choisi le framework, Vite vous proposera généralement des variantes, comme JavaScript ou TypeScript. Sélectionnez celle qui vous convient.
5. Une fois ces choix effectués, Vite créera le projet avec la configuration choisie.
