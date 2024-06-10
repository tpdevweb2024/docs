# Tailwind CSS

## Introduction

### Présentation de Tailwind CSS

Tailwind CSS est un framework utilitaire de CSS hautement personnalisable qui vous permet de construire des conceptions modernes directement dans votre balisage.&#x20;

{% hint style="info" %}
Contrairement aux frameworks traditionnels tels que Bootstrap ou Foundation, Tailwind ne fournit pas de composants prédéfinis. À la place, il fournit une série de classes CSS basées sur les utilitaires qui peuvent être utilisées pour créer des interfaces utilisateur personnalisées de manière rapide et efficace.
{% endhint %}

### Avantages de l'utilisation de Tailwind CSS

* **Vitesse et efficacité** : Avec ses classes utilitaires, vous pouvez créer des interfaces sans écrire de CSS personnalisé.
* **Personnalisable** : Modifiez facilement la configuration pour répondre précisément aux besoins de votre projet.
* **Consistance** : Garantit un design uniforme à travers tout le projet.
* **Facile à apprendre** : Une fois que vous maîtrisez les conventions de nommage, il devient facile à utiliser.
* **Responsive par défaut** : Construit avec une prise en charge intégrée pour les conceptions réactives.

#### Purge automatique des classes inutilisées

L'une des fonctionnalités puissantes de Tailwind CSS est la purge automatique des classes inutilisées. Pour réduire la taille de votre fichier CSS en production, vous pouvez configurer Tailwind pour supprimer les classes inutilisées.&#x20;

Cela se fait en ajoutant les chemins de vos fichiers à la propriété `content` dans le fichier de configuration `tailwind.config.js` :

```js
module.exports = {
  // ...
  content: [
    './**/*.html',
    './src/**/*.{js,jsx,ts,tsx,vue}',
  ],
  // ...
}
```

{% hint style="success" %}
Cette purge garantit que seules les classes utilisées dans votre code seront incluses dans le fichier CSS final, optimisant ainsi les performances de votre site web.
{% endhint %}

## Installation

### Prérequis

* [x] Connaissance de base en HTML et CSS
* [x] Compréhension des concepts de responsive design
* [x] Node.js et npm installés sur votre système (pour l'installation via npm)

### Les méthodes d'installation

#### CDN

Vous pouvez inclure Tailwind CSS directement via un CDN. Ajoutez simplement la ligne suivante dans votre fichier HTML :

```html
<link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
```

#### npm

Pour installer Tailwind CSS via npm ou yarn, exécutez la commande suivante :

```bash
npm install tailwindcss
```

Ensuite, créez votre fichier de configuration en utilisant la commande suivante :

```bash
npx tailwindcss init
```

## Configuration Initiale

Pour personnaliser votre configuration Tailwind CSS, éditez le fichier `tailwind.config.js` généré. Vous pouvez y définir vos propres palettes de couleurs, typographies, tailles, espacements, et bien plus.

#### Personnalisation des couleurs

Ajoutez vos couleurs personnalisées sous la clé `theme.extend.colors` :

```javascript
// tailwind.config.js

module.exports = {
  theme: {
    extend: {
      colors: {
        primary: '#1E40AF',
        secondary: '#F59E0B',
      },
    },
  },
  variants: {},
  plugins: [],
}
```

#### Personnalisation des typographies

Ajoutez vos polices personnalisées sous la clé `theme.extend.fontFamily` :

```javascript
// tailwind.config.js

module.exports = {
  theme: {
    extend: {
      fontFamily: {
        sans: ['Inter', 'system-ui', 'sans-serif'],
        serif: ['Merriweather', 'serif'],
      },
    },
  },
  variants: {},
  plugins: [],
}
```

## Utilisation des Classes Utilitaires

Tailwind CSS fournit une syntaxe simple et intuitive pour appliquer des styles directement dans votre HTML via des classes utilitaires. Voici quelques exemples :

### **Flexbox**

Tailwind CSS fournit plusieurs utilitaires pour gérer le flex layout. Voici un résumé des principales fonctionnalités :

#### Flex Container

* `flex` pour activer le flex layout sur un conteneur.
* `flex-row` pour aligner les éléments flex horizontalement.
* `flex-col` pour les aligner verticalement.
* `flex-row-reverse` et `flex-col-reverse` pour inverser l'ordre.

#### Flex Items

* `flex-1` pour permettre à un élément de prendre tout l'espace disponible.
* `flex-auto` pour qu'un élément grandisse et rétrécisse en fonction de sa taille initiale.
* `flex-initial` pour qu'un élément rétrécisse mais ne grandisse pas.
* `flex-none` pour empêcher un élément de grandir ou rétrécir.
* `flex-grow` pour permettre à un élément de grandir.
* `flex-grow-0` pour empêcher un élément de grandir.
* `flex-shrink` pour permettre à un élément de rétrécir.
* `flex-shrink-0` pour empêcher un élément de rétrécir.
* `flex-basis-*` pour définir la taille initiale d'un élément flex (ex: `flex-basis-1/4`).

```html
<div class="flex flex-row justify-around items-center h-screen">
  <div class="flex-none bg-blue-500 text-white p-4 rounded">Item 1</div>
  <div class="flex-1 bg-green-500 text-white p-4 mx-4 rounded">Item 2</div>
  <div class="flex-none bg-red-500 text-white p-4 rounded">Item 3</div>
</div>
```

### **Grid**

Tailwind CSS fournit également des utilitaires pour créer facilement des mises en page grid. Voici un résumé des principales fonctionnalités :

#### Grid Container

* `grid` pour activer le grid layout sur un conteneur.
* `grid-cols-*` pour définir le nombre de colonnes de la grille (ex: `grid-cols-3`).
* `grid-rows-*` pour définir le nombre de lignes (ex: `grid-rows-4`).
* `gap-*` pour définir l'espacement entre les cellules de la grille.

#### Grid Items

* `col-start-*` et `col-end-*` pour positionner un élément sur les colonnes de la grille.
* `row-start-*` et `row-end-*` pour le positionner sur les lignes.
* `col-span-*` pour faire s'étendre un élément sur plusieurs colonnes.
* `row-span-*` pour l'étendre sur plusieurs lignes.

Exemple de grille 3x3 avec un élément s'étalant sur 2 colonnes et 2 lignes :

```html
<div class="grid grid-cols-3 grid-rows-3 gap-4">
  <div class="col-start-1 row-start-1 ...">1</div>
  <div class="col-start-3 row-start-1 ...">2</div>
  <div class="col-start-2 col-span-2 row-span-2 ...">3</div>
  <div class="col-start-1 row-start-3 ...">4</div>
  <div class="col-start-3 row-start-3 ...">5</div>
</div>
```

\


### **Typographie**

Tailwind CSS fournit des utilitaires pour gérer la typographie, tels que la taille de police, le poids, le style et l'espacement des lignes.

#### **Taille de police**

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption><p>Source : <a href="https://tailwindcss.com/docs/font-size">https://tailwindcss.com/docs/font-size</a></p></figcaption></figure>

{% hint style="info" %}
`text-x` permet de modifier la taille d'un texte
{% endhint %}

#### **Poids de police**

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p>Source : <a href="https://tailwindcss.com/docs/font-weight">https://tailwindcss.com/docs/font-weight</a></p></figcaption></figure>

{% hint style="info" %}
`font-x` sert à définir la graisse de votre police de texte
{% endhint %}

#### **Style de police**

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption><p>Source : <a href="https://tailwindcss.com/docs/font-style">https://tailwindcss.com/docs/font-style</a></p></figcaption></figure>

{% hint style="info" %}
Ces classes permettent d'ajouter ou retirer le style italique à un texte
{% endhint %}

#### **Transformation de texte**

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption><p>Source : <a href="https://tailwindcss.com/docs/text-transform">https://tailwindcss.com/docs/text-transform</a></p></figcaption></figure>

{% hint style="info" %}
Ces classes définissent la casse des élements
{% endhint %}

#### **Espacement des lignes**

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption><p>Source : <a href="https://tailwindcss.com/docs/line-height">https://tailwindcss.com/docs/line-height</a></p></figcaption></figure>

{% hint style="info" %}
`leading-x` définit l'espacement de ligne
{% endhint %}

**Exemples**: `leading-none`, `leading-tight`, `leading-snug`, `leading-normal`, `leading-relaxed`, `leading-loose`.

### **Couleurs**

Tailwind CSS fournit une palette de couleurs par défaut, ainsi que des utilitaires pour définir les couleurs de texte et d'arrière-plan.

<figure><img src="../.gitbook/assets/image (6).png" alt="" width="331"><figcaption><p><a href="https://tailwindcss.com/docs/customizing-colors">https://tailwindcss.com/docs/customizing-colors</a></p></figcaption></figure>

#### **Couleurs de texte et d'arrière-plan**

Pour définir les couleurs dans votre document, utilisez les classes `bg-*` pour la couleur d'arrière-plan et `text-*` pour la couleur du texte.

Les couleurs disponibles par défaut sont

* black
* white
* gray-\*
* red-\*
* yellow-\*
* green-\*
* blue-\*
* indigo-\*
* purple-\*
* pink-\*

### **Bordures**

Tailwind CSS propose une variété d'utilitaires pour travailler avec les bordures.

#### **Types de bordures**

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption><p>Source : <a href="https://tailwindcss.com/docs/border-width">https://tailwindcss.com/docs/border-width</a></p></figcaption></figure>

{% hint style="info" %}
`border-*`: Définit la largeur de la bordure.
{% endhint %}

Exemples : `border`, `border-2`, `border-4`, `border-8`.

#### **Couleurs de bordures**

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption><p>Source : <a href="https://tailwindcss.com/docs/border-color">https://tailwindcss.com/docs/border-color</a></p></figcaption></figure>

{% hint style="info" %}
`border-color-*`: Définit la couleur de la bordure.
{% endhint %}

Exemples : `border-black`, `border-white`, `border-gray-500`, `border-red-500`.

#### **Radius de bordures**

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption><p>Source : <a href="https://tailwindcss.com/docs/border-radius">https://tailwindcss.com/docs/border-radius</a></p></figcaption></figure>

{% hint style="info" %}
`rounded-*`: Ajuste le rayon de la bordure (bordure arrondie).
{% endhint %}

Exemples : `rounded-none`, `rounded-sm`, `rounded`, `rounded-lg`, `rounded-full`.
