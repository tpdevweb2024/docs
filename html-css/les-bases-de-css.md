# Les bases de CSS

## Introduction à CSS

### Qu'est-ce que CSS ?

CSS (Cascading Style Sheets) est un langage de feuille de style utilisé pour décrire l'apparence et la mise en forme d'un document écrit en HTML ou en XML. Il permet de séparer le contenu (HTML) de la présentation (CSS), ce qui facilite la maintenance et l'adaptation du design.

### Comment CSS est utilisé dans le développement web.

CSS est utilisé pour styliser les éléments HTML, définir la mise en page, contrôler les couleurs, les polices, les animations, et bien plus encore. Il est généralement inclus dans un fichier séparé (`.css`) et lié au document HTML via une balise `<link>` dans l'en-tête du document.

## Les différents types de sélecteurs CSS.

* **Sélecteurs d'élément** : Ciblent les éléments HTML par leur nom de balise.

```css
p {
   color: blue;
}
```

* **Sélecteurs de classe** : Ciblent les éléments HTML qui ont une classe spécifique.

```css
.highlight {
   background-color: yellow;
}
```

* **Sélecteurs d'ID** : Ciblent un élément HTML unique par son ID.

```css
#unique {
   font-size: 24px;
}
```

* **Sélecteurs universels** : Ciblent tous les éléments HTML.

```css
* {
   margin: 0;
   padding: 0;
}
```

* **Sélecteurs d'attribut** : Ciblent les éléments HTML qui ont un attribut spécifique.

```css
input[type="text"] {
   border: 1px solid black;
}
```

* **Sélecteurs de pseudo-classes** : Ciblent des éléments HTML basés sur leur état ou leur position.

```css
a:hover {
   color: red;
}
```

* **Sélecteurs de pseudo-éléments** : Ciblent des parties spécifiques d'un élément HTML.

```css
p::first-letter {
   font-size: 2em;
}
```

## Les propriétés CSS et leurs valeurs.

Les propriétés CSS définissent les aspects spécifiques de la mise en forme, comme la couleur du texte, la taille de la police, la marge, le rembourrage (padding), etc. Chaque propriété peut avoir différentes valeurs, qui déterminent comment l'élément HTML sera stylisé.

## Sélecteurs CSS

Les sélecteurs CSS sont utilisés pour cibler des éléments HTML spécifiques afin de leur appliquer des styles. Voici comment utiliser chaque type de sélecteur :

### Sélecteurs d'élément

Cible les éléments HTML par leur nom de balise.

```css
h1 {
 color: red;
}
```

### Sélecteurs de classe

Cible les éléments HTML qui ont une classe spécifique.

```css
.important {
 font-weight: bold;
}
```

#### Sélecteurs d'id

Cible un élément HTML unique par son ID.

```css
#unique-element {
 background-color: lightblue;
}
```

#### Sélecteurs universels

Cible tous les éléments HTML.

```css
* {
 box-sizing: border-box;
}
```

#### Sélecteurs d'attribut

Cible les éléments HTML qui ont un attribut spécifique.

```css
input[type="email"] {
 border: 2px solid green;
}
```

#### Sélecteurs de pseudo-classes

Cible des éléments HTML basés sur leur état ou leur position.

```css
a:visited {
 color: purple;
}
```

#### Sélecteurs de pseudo-éléments

Cible des parties spécifiques d'un élément HTML.

```css
p::first-letter {
 font-size: 2em;
}
```

## Propriétés CSS

Les propriétés CSS définissent les aspects spécifiques de la mise en forme des éléments HTML. Voici quelques exemples de propriétés et comment les utiliser :

### Propriétés de texte

* **font-family** : Définit la police du texte.

```css
p {
   font-family: Arial, sans-serif;
}
```

* **font-size** : Définit la taille du texte.

```css
h1 {
   font-size: 24px;
}
```

* **color** : Définit la couleur du texte.

```css
p {
   color: #333;
}
```

* **text-align** : Définit l'alignement du texte.

```css
p {
   text-align: center;
}
```

### Propriétés de mise en page

* **margin** : Définit l'espace extérieur autour d'un élément.

```css
div {
   margin: 10px;
}
```

* **padding** : Définit l'espace intérieur autour du contenu d'un élément.

```css
button {
   padding: 5px 10px;
}
```

* **display** : Définit le type de boîte de l'élément (block, inline, flex, etc.).

```css
img {
   display: block;
}
```

* **position** : Définit la position de l'élément (static, relative, absolute, etc.).

```css
.header {
   position: fixed;
   top: 0;
}
```

### Propriétés de bordure

* **border** : Définit la bordure d'un élément.

```css
div {
   border: 1px solid black;
}
```

* **border-radius** : Définit le rayon des coins d'une bordure.

```css
img {
   border-radius: 50%;
}
```

### Propriétés de couleur

* **background-color** : Définit la couleur de fond d'un élément.

```css
body {
   background-color: #f0f0f0;
}
```

* **opacity** : Définit l'opacité d'un élément.

```css
.transparent {
   opacity: 0.5;
}
```

### Propriétés de transition et d'animation

* **transition** : Définit la transition entre deux états d'un élément.

La propriété `transition` est un raccourci pour définir plusieurs propriétés de transition en une seule déclaration. Elle permet de contrôler la manière dont une propriété change d'une valeur à une autre. Voici comment vous pouvez l'utiliser :

```css
button:hover {
   background-color: blue;
   transition: background-color 0.5s ease;
}
```

{% hint style="info" %}
Dans cet exemple, la propriété `transition` est utilisée pour animer la couleur de fond d'un bouton lorsqu'il est survolé. La transition dure 0.5 seconde et utilise la fonction d'accélération `ease`, qui commence lentement, accélère au milieu, puis ralentit à nouveau vers la fin.
{% endhint %}

* **animation :** Définit l'animation en contrôlant les images clés

Les animations CSS permettent de créer des animations complexes en contrôlant les images clés d'une animation. Voici comment vous pouvez définir une animation :

```css
@keyframes monAnimation {
    from {
        background-color: red;
    }
    to {
        background-color: yellow;
    }
}

button {
    animation: monAnimation 2s infinite;
}

```

{% hint style="info" %}
Dans cet exemple, une animation nommée `monAnimation` est définie avec `@keyframes`. L'animation change la couleur de fond d'un bouton de rouge à jaune. L'animation est appliquée au bouton avec la propriété `animation`, qui spécifie le nom de l'animation, sa durée (2 secondes) et indique que l'animation doit se répéter indéfiniment (`infinite`).
{% endhint %}
