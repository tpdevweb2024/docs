# Sass et le SCSS

## **Introduction à Sass et SCSS**

### **Qu'est-ce que Sass ?**

#### Définition et utilisation de Sass

Sass (Syntactically Awesome Stylesheets) est un préprocesseur CSS qui permet aux développeurs de créer des stylesheets plus dynamiques et maintenables. Il étend le CSS standard en introduisant des fonctionnalités telles que les variables, les mixins, les fonctions, et l'imbrication, rendant votre feuille de style plus lisible et plus facile à gérer.

Sass a été le premier du genre, révolutionnant la manière dont les feuilles de style sont écrites et comprises. Depuis sa création, il a évolué pour inclure deux syntaxes : la syntaxe originale, simplement appelée Sass, qui utilise l'indentation pour séparer les blocs de code, et SCSS (Sassy CSS), qui utilise la syntaxe CSS standard.

#### Avantages de Sass par rapport à CSS

Les principaux avantages de Sass par rapport au CSS pur comprennent :

* **Variables** : Permettent de stocker des valeurs pour les réutiliser tout au long de votre feuille de style, facilitant la gestion des couleurs, des tailles de police, et d'autres valeurs.
* **Mixins** : Réutilisez des groupes de déclarations CSS à travers votre feuille de style sans avoir à copier et coller.
* **Imbrication** : Écrivez des sélecteurs imbriqués de manière hiérarchique, ce qui rend la structure de votre CSS plus claire et plus concise.
* **Importation** : Importez d'autres feuilles de style Sass dans votre fichier principal pour une meilleure organisation et modularité.
* **Héritage/Extends** : Partagez un ensemble de propriétés CSS d'un sélecteur à l'autre, réduisant ainsi la redondance dans votre feuille de style.

{% hint style="info" %}
En utilisant Sass, les développeurs peuvent gagner du temps, réduire les erreurs potentielles, et créer des feuilles de style plus puissantes et flexibles qui s'adaptent mieux aux projets web complexes d'aujourd'hui.
{% endhint %}

### **Qu'est-ce que SCSS ?**

SCSS (Sassy CSS) est une syntaxe de Sass qui utilise le format de fichier `.scss`. Elle est complètement compatible avec la syntaxe CSS, ce qui signifie que tout CSS valide peut être interprété par SCSS sans modification. Cela rend SCSS particulièrement attrayant pour les équipes qui migrent vers Sass mais ne veulent pas se réécrire entièrement leur CSS existant.

#### Différences entre Sass et SCSS

* **Syntaxe** : Sass utilise une syntaxe d'indentation qui ne nécessite pas de points-virgules ou d'accolades, tandis que SCSS utilise la syntaxe CSS standard.
* **Compatibilité** : SCSS est compatible avec tous les styles CSS, ce qui facilite la transition pour les équipes déjà familiarisées avec CSS.

#### Pourquoi utiliser SCSS

* **Facilité de transition** : Pour les équipes ayant une base de code CSS existante, SCSS offre une courbe d'apprentissage plus douce en raison de sa compatibilité directe avec le CSS standard.
* **Outils et communauté** : L'utilisation généralisée de SCSS signifie une grande disponibilité de ressources d'apprentissage, d'outils, et une communauté active pour le support.

## **Installation et configuration**

### Comment installer Sass ?

1. **Installer Node.js et npm** : Assurez-vous d'avoir Node.js et npm installés sur votre système. Vous pouvez les télécharger et installer depuis [le site officiel de Node.js](https://nodejs.org/).
2.  **Installer Sass** : Ouvrez votre terminal ou invite de commande et exécutez la commande suivante pour installer Sass globalement sur votre système.

    ```sh
    npm install -g sass
    ```
3.  **Vérifier l'installation** : Pour vous assurer que Sass est bien installé, tapez la commande suivante :

    ```sh
    sass --version
    ```

    Si l'installation a réussi, vous devriez voir la version de Sass s'afficher.

### Utilisation de Node.js et npm pour utiliser le Sass

Pour débuter avec Sass dans votre projet, suivez ces étapes pour configurer votre environnement de développement :

1. **Créer un dossier de projet** : Tout d'abord, créez un dossier pour votre projet si vous ne l'avez pas déjà fait. Ceci peut être fait via l'explorateur de fichiers de votre système d'exploitation ou via la ligne de commande avec `mkdir nom_du_projet`.
2. **Initialiser Node.js** : Ouvrez un terminal dans votre dossier de projet et exécutez `npm init`. Répondez aux questions pour créer un fichier `package.json`, qui gardera une trace de vos dépendances et scripts.
3. **Créer un dossier pour les fichiers SCSS** : Créez un dossier `scss` dans votre projet pour stocker vos fichiers `.scss`. Vous pouvez le faire manuellement ou via la commande `mkdir scss`.
4. **Création d'un fichier SCSS** : Dans le dossier `scss`, créez un fichier pour votre code Sass, par exemple `style.scss`. C'est dans ce fichier que vous écrirez votre CSS en utilisant la syntaxe SCSS.
5.  **Compiler SCSS en CSS** : Pour compiler votre fichier SCSS en CSS, utilisez la commande Sass dans le terminal :

    ```sh
    sass scss/style.scss css/style.css
    ```

    Cela dit à Sass de prendre votre fichier `style.scss` et de le compiler en un fichier CSS dans un dossier `css`. Si le dossier `css` n'existe pas, Sass le créera pour vous.
6.  **Automatiser la compilation** : Pour ne pas avoir à exécuter manuellement la commande à chaque modification, vous pouvez utiliser l'option `--watch` de Sass :

    ```sh
    sass --watch scss/style.scss:css/style.css
    ```

    Cela indique à Sass de surveiller le fichier `style.scss` et de recompiler automatiquement le fichier CSS chaque fois que vous enregistrez des modifications dans le fichier SCSS.

{% hint style="info" %}
En suivant ces étapes, vous aurez un environnement de développement Sass prêt à l'emploi pour votre projet. Vous pouvez maintenant continuer à écrire votre CSS en utilisant toutes les fonctionnalités puissantes que Sass a à offrir.
{% endhint %}

<figure><img src="../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Intégrer Sass dans un nouveau projet

Pour intégrer l'usage de Sass et du SCSS dans un nouveau projet, il faut d'abord initialiser votre projet en effectuant le commande :&#x20;

```
npm init -y
```

Ensuite nous pourrons alors stocker notre commande précédente pour utiliser sass au sein d'un nouveau script du fichier package.json précédemment généré :  &#x20;

```json
{
  "name": "app",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "watch": "sass assets/scss/style.scss assets/css/style.css --watch"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}

```

Enfin, pour lancer notre script de surveillance plus facilement, il suffit d'invoquer le sass en éxécutant le script npm suivant dans un terminal :&#x20;

```
npm run watch
```

{% hint style="info" %}
Remarque : le nom du script choisi (watch dans ce cas) n'a pas d'importance réelle, mais il est préférable de donner un nom de script facilement identifiable pour d'autres éventuels collaborateurs.
{% endhint %}

## **La syntaxe SCSS**

### **Les variables**

Les variables en SCSS permettent de stocker des valeurs que vous pouvez réutiliser tout au long de votre feuille de style. Cela rend votre code plus facile à maintenir car vous pouvez définir une valeur une fois, puis la référencer partout où vous en avez besoin, ce qui est particulièrement utile pour des éléments comme les couleurs, les tailles de police, ou les espacements que vous souhaitez garder cohérents.

#### **Définir une variable**

Pour définir une variable en SCSS, vous utilisez le signe dollar (`$`) suivi du nom de la variable, et vous lui assignez une valeur :

```scss
$couleur-principale: #3498db;
$espacement-base: 16px;
```

#### **Utiliser une variable**

Une fois une variable définie, vous pouvez l'utiliser en la mentionnant par son nom dans votre code :

```scss
body {
  font-family: 'Helvetica', sans-serif;
  color: $couleur-principale;
  padding: $espacement-base;
}
```

_Ceci applique la couleur et l'espacement que vous avez définis aux éléments du `body` de votre document. Si vous décidez de changer la couleur ou l'espacement de base plus tard, vous n'aurez qu'à mettre à jour la valeur de la variable, et tous les endroits où la variable est utilisée seront automatiquement mis à jour._

### **Mixins**

Les **mixins** permettent de créer des groupes de déclarations CSS que l'on peut réutiliser dans tout notre fichier. Ceci est particulièrement utile pour les ensembles de propriétés que l'on utilise fréquemment. Pour définir un mixin, on utilise le mot-clé `@mixin` suivi du nom du mixin et de tout paramètre nécessaire. Pour l'utiliser, on emploie `@include` suivi du nom du mixin.

#### **Définition d'un mixin**

```scss
@mixin reset-list {
  margin: 0;
  padding: 0;
  list-style: none;
}
```

#### **Utilisation d'un mixin**

```scss
ul {
  @include reset-list;
}
```

#### **Exemple d'un mixin avec paramètres**

Les mixins peuvent également prendre des paramètres pour rendre le style plus flexible.

```scss
@mixin theme-color($color) {
  background-color: $color;
  color: white;
}

.button {
  @include theme-color(blue);
}
```

### **Les fonctions**

Les fonctions personnalisées en SCSS permettent de réaliser des calculs et des manipulations de chaînes de caractères, couleurs, nombres, etc., afin de générer des styles dynamiques.

#### **Définition d'une fonction**

Pour déclarer une fonction, utilisez le mot-clé `@function` suivi du nom de la fonction, puis des parenthèses contenant les paramètres, et enfin des accolades pour inclure le corps de la fonction.

```scss
@function calculate-padding($multiplier) {
  @return 10px * $multiplier;
}
```

#### **Utilisation d'une fonction**

Utilisez le nom de la fonction où vous souhaitez appliquer son retour, en passant les arguments nécessaires.

```scss
.container {
  padding: calculate-padding(2);
}
```

{% hint style="success" %}
Dans cet exemple, la fonction `calculate-padding` est utilisée pour calculer le padding d'un élément `.container`, où le résultat sera `20px` (10px \* 2).
{% endhint %}

### **Les boucles**

Les boucles et conditions permettent d'automatiser et de personnaliser votre CSS. Voici comment vous pouvez les utiliser :

#### **La boucle `@for`**

Utilisez `@for` pour répéter des styles un certain nombre de fois.

```scss
@for $i from 1 through 3 {
  .item-#{$i} { width: 100px * $i; }
}
```

#### **La boucle `@each`**

`@each` est utilisé pour appliquer des styles à une liste de valeurs.

```scss
$colors: blue, red, green;

@each $color in $colors {
  .#{$color}-text { color: $color; }
}
```

### **Les conditions**

La directive `@if` vous permet d'appliquer des styles basés sur des conditions.

```scss
$theme: dark;

body {
  @if $theme == dark { background-color: black; color: white; }
  @else { background-color: white; color: black; }
}
```

### **Nesting**

Le nesting est une fonctionnalité de SCSS qui vous permet d'écrire vos sélecteurs CSS de manière hiérarchique, reflétant ainsi la structure HTML de votre page. Cela simplifie beaucoup la maintenance et la lisibilité de votre code CSS.

#### Exemple de Nesting

Sans nesting, vous écririez vos sélecteurs CSS comme ceci :

```scss
nav {
  background-color: blue;
}

nav ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

nav ul li {
  display: inline-block;
}

nav ul li a {
  text-decoration: none;
  color: white;
  padding: 10px;
}
```

Avec le nesting en SCSS, vous pouvez structurer votre CSS de manière plus logique :

```scss
nav {
  background-color: blue;
  
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
    
    li {
      display: inline-block;
      
      a {
        text-decoration: none;
        color: white;
        padding: 10px;
      }
    }
  }
}
```

#### Quelques règles à suivre

* [x] Évitez un nesting trop profond, car il peut rendre le code difficile à lire et peut également entraîner une spécificité CSS élevée qui est difficile à maintenir.
* [x] Utilisez le nesting pour refléter la structure HTML et non pour regrouper tous les styles d'un composant, ce qui pourrait rendre votre CSS plus difficile à comprendre.
* [x] Profitez de l'opérateur `&` pour combiner le sélecteur parent avec des pseudos-classes, des pseudos-éléments ou des modificateurs.

## **Les techniques avancées**

### **Partials et importation**

Les partials sont des fichiers Sass dont le nom commence par un underscore (\_), comme `_variables.scss`. L'underscore indique à Sass qu'il s'agit d'un fichier partiel, un fichier qui peut être importé dans d'autres fichiers Sass plutôt que prévu pour être compilé en un fichier CSS.

#### **Création de partials**

Pour créer un partial, il suffit de préfixer le nom du fichier avec un underscore. Par exemple:

* `_reset.scss` pour un fichier contenant un reset CSS.
* `_variables.scss` pour stocker des variables globales.
* `_mixins.scss` pour définir des mixins réutilisables.

#### **Importation de partials**

Pour utiliser les styles définis dans un partial, vous devez importer ce fichier dans un autre fichier Sass en utilisant la directive `@import`. Par exemple:

```scss
// Importation du partial de variables
@import 'variables';

// Importation du partial de mixins
@import 'mixins';
```

{% hint style="danger" %}
Notez que lors de l'utilisation de la directive `@import`, on omet l'underscore et l'extension `.scss` du nom du fichier. Sass résout automatiquement le nom correct du fichier partial.
{% endhint %}

{% hint style="info" %}
L'importation de fichiers permet une meilleure organisation du code en séparant les styles en différents fichiers selon leur fonctionnalité, simplifiant ainsi la maintenance et la réutilisation des styles.
{% endhint %}

### Différence entre mixins et placeholders

Les **mixins** et **placeholders** sont deux fonctionnalités puissantes de Sass qui permettent la réutilisation de styles. Alors qu'ils semblent servir un but similaire, ils ont des applications et des avantages distincts.

**Mixins**

Les **mixins** permettent d'inclure un groupe de déclarations CSS dans plusieurs sélecteurs. Ils sont particulièrement utiles pour les ensembles de styles qui nécessitent des paramètres dynamiques. Un mixin est défini avec le mot-clé `@mixin` et peut être inclus dans un sélecteur avec le mot-clé `@include`.

```scss
@mixin border-radius($radius) {
  border-radius: $radius;
}

.box {
  @include border-radius(10px);
}
```

#### Avantages des mixins :

* Acceptent des arguments, permettant la personnalisation des styles inclus.
* Facilitent la maintenance en centralisant les styles communs.

#### **Placeholders**

Les **placeholders** sont des sélecteurs spéciaux qui n'engendrent pas de CSS par eux-mêmes mais peuvent être étendus dans d'autres sélecteurs avec le mot-clé `@extend`. Ils sont utiles pour partager un ensemble commun de propriétés CSS sans dupliquer le style dans le fichier compilé.

```scss
%button-shared {
  padding: 10px;
  border: none;
  cursor: pointer;
}

.button-primary {
  @extend %button-shared;
  background-color: blue;
  color: white;
}

.button-secondary {
  @extend %button-shared;
  background-color: grey;
  color: black;
}
```

#### Avantages des placeholders :

* Ne génèrent du CSS que lorsqu'ils sont étendus, réduisant potentiellement la taille du fichier final.
* Favorisent un CSS plus sec en évitant la répétition des propriétés communes.

{% hint style="success" %}
Les mixins sont idéaux pour les styles dynamiques avec des paramètres variables, tandis que les placeholders conviennent pour partager des ensembles de styles statiques. Choisir entre eux dépend de la spécificité des besoins en termes de réutilisation de styles dans votre projet.
{% endhint %}

### **Le scope d'une variable**

**Scope**

Le scope d'une variable détermine où elle peut être utilisée. Sass dispose de deux principaux types de scope:

* **Global Scope**: Les variables définies au plus haut niveau de votre document sont accessibles partout dans votre feuille de style.
* **Local Scope**: Les variables définies à l'intérieur d’une règle ou d'un bloc ne sont accessibles que dans ce contexte.

**Exemple de scope local :**

```scss
.container {
  $local-color: green;
  color: $local-color; // Fonctionne ici
}
// $local-color n'est pas accessible ici
```

**Conversion de scope local à global :**

Vous pouvez rendre une variable locale globale en utilisant le mot-clé `!global`.

```scss
.container {
  $local-color: green !global;
}
// $local-color est maintenant accessible partout
```

**Bonnes pratiques**

* Préférez l’utilisation de variables locales pour éviter les conflits et maintenir un code propre et facile à maintenir.
* Utilisez des noms de variables descriptifs pour améliorer la lisibilité de votre code.

Sass introduit également la notion de **variable par défaut** avec le flag `!default`, qui permet de définir une valeur par défaut pour une variable qui peut être écrasée si nécessaire :

```scss
$font-size: 16px !default; // La valeur peut être redéfinie ailleurs
```
