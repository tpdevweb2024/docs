# L'utilisation de CSS avancé

CSS (Cascading Style Sheets) est un langage de feuilles de style qui permet de définir la présentation des documents HTML.&#x20;

Au-delà des styles de base comme les couleurs, les polices et les marges, CSS offre des fonctionnalités avancées qui permettent de créer des designs plus complexes et interactifs. Nous allons donc explorer quelques-uns des concepts avancés de CSS qui sont essentiels pour les développeurs web modernes.

Flexbox, ou Flexible Box, est un modèle de mise en page CSS qui permet de disposer facilement des éléments dans une direction principale (horizontale ou verticale) et de les aligner de manière flexible. Il est particulièrement utile pour créer des mises en page réactives et flexibles, adaptées à différents types d'écrans et de tailles de contenu.

## Flexbox

Flexbox est conçu pour être une solution plus efficace et plus puissante pour la mise en page, en comparaison avec les méthodes traditionnelles comme `float` et `position`. Il permet de créer des mises en page complexes avec moins de code et de facilité.

### **Mise en place de Flexbox**

Pour utiliser Flexbox, vous devez d'abord activer le mode Flexbox sur un élément. Cela se fait en définissant la propriété `display` de cet élément à `flex` ou `inline-flex`.

```css
.container {
    display: flex;
}
```

### **Directions et Axes**

* **Direction principale** : L'axe principal est l'axe le long duquel les éléments flexibles sont disposés. La valeur par défaut est `row`, ce qui signifie que les éléments sont disposés horizontalement.
* **Direction transversale** : L'axe transversal est perpendiculaire à l'axe principal. La valeur par défaut est `column`, ce qui signifie que les éléments sont empilés verticalement.

Vous pouvez changer la direction principale en utilisant la propriété `flex-direction`.

```css
.container {
    display: flex;
    flex-direction: column; /* Les éléments sont disposés verticalement */
}
```

### **Justification et Alignement**

* **Justification** : La justification concerne l'alignement des éléments le long de l'axe principal.
* **Alignement** : L'alignement concerne l'alignement des éléments le long de l'axe transversal.

Vous pouvez utiliser les propriétés `justify-content` et `align-items` pour contrôler l'alignement des éléments.

```css
.container {
    display: flex;
    justify-content: space-between; /* Espacement égal entre les éléments */
    align-items: center; /* Alignement vertical des éléments au centre */
}
```

### **Flex Items**

Les éléments flexibles (flex items) sont les enfants directs d'un conteneur flex. Vous pouvez contrôler leur taille, leur ordre et leur alignement en utilisant différentes propriétés flex.

```css
.item {
    flex: 1; /* L'élément prendra tout l'espace disponible */
    order: 2; /* L'ordre de l'élément dans le conteneur */
}
```

### **Flex Wrap**

Par défaut, tous les éléments flexibles sont disposés sur une seule ligne. Vous pouvez changer ce comportement en utilisant la propriété `flex-wrap`.

```css
.container {
    display: flex;
    flex-wrap: wrap; /* Les éléments se déplaceront sur plusieurs lignes si nécessaire */
}
```

## Grid layout

Après avoir exploré Flexbox, le prochain concept avancé de CSS que nous allons couvrir est Grid Layout.&#x20;

Contrairement à Flexbox, qui est principalement axé sur une dimension (ligne ou colonne), Grid Layout est conçu pour gérer à la fois les lignes et les colonnes, permettant une mise en page plus complexe et structurée.

### **Introduction à Grid layout**

Grid est un modèle de mise en page CSS qui permet de créer des mises en page complexes avec des colonnes et des lignes. Il est particulièrement utile pour créer des designs de page sophistiqués et responsifs.

### **Utilisation de Grid layout**

Pour utiliser Grid Layout, vous devez d'abord activer le mode Grid sur un élément. Cela se fait en définissant la propriété `display` de cet élément à `grid` ou `inline-grid`.

```css
.container {
    display: grid;
}
```

### **Définition des colonnes et des lignes**

Avec Grid, vous pouvez définir explicitement le nombre de colonnes et de lignes, ainsi que leur taille, en utilisant les propriétés `grid-template-columns` et `grid-template-rows`.

```css
.container {
    display: grid;
    grid-template-columns: 1fr 2fr 1fr; /* Trois colonnes de largeurs différentes */
    grid-template-rows: auto 100px; /* Deux lignes, la première s'ajuste au contenu, la seconde est de 100px */
}
```

### **Placement des éléments**

Vous pouvez placer les éléments flexibles dans des cellules spécifiques en utilisant les propriétés `grid-column` et `grid-row`.

```css
.item {
    grid-column: 2 / 3; /* L'élément occupe la deuxième colonne */
    grid-row: 1 / 3; /* L'élément occupe les deux premières lignes */
}
```

### **Espacement et alignement**

Grid offre également des propriétés pour contrôler l'espacement entre les lignes et les colonnes (`grid-gap`), ainsi que l'alignement des éléments (`justify-items`, `align-items`).

```css
.container {
    display: grid;
    grid-gap: 10px; /* Espacement de 10px entre les lignes et les colonnes */
    justify-items: center; /* Alignement horizontal des éléments au centre */
    align-items: start; /* Alignement vertical des éléments en haut */
}
```

### **Flexibilité et répétition**

Grid permet également de créer des mises en page flexibles et répétitives en utilisant les unités `fr` (fraction) et `auto`.

```css
.container {
    display: grid;
    grid-template-columns: repeat(3, 1fr); /* Trois colonnes de largeur égale */
    grid-template-rows: auto; /* Lignes qui s'ajustent au contenu */
}

```

{% hint style="info" %}
Grid est un outil puissant pour la création de mises en page complexes et structurées. En combinant les concepts de base de Grid avec ceux de Flexbox, vous pourrez créer des designs responsifs qui s'adaptent à différents types d'écrans et de contenu.
{% endhint %}

## Animations CSS

Les animations CSS sont définies à l'aide de `@keyframes`, qui spécifie les étapes de l'animation, et de la propriété `animation`, qui applique l'animation à un élément.

### **Définition d'une animation**

Pour créer une animation, vous commencez par définir les étapes de l'animation avec `@keyframes`. Chaque étape est définie par un pourcentage, qui représente le moment de l'animation.

```css
@keyframes example {
    0%      {background-color: red;}
    25%     {background-color: yellow;}
    50%     {background-color: blue;}
    100%    {background-color: green;}
}
```

{% hint style="info" %}
Dans cet exemple, l'animation change la couleur de fond de l'élément de rouge à vert en passant par le jaune et le bleu.
{% endhint %}

### **Application de l'animation**

Pour appliquer l'animation à un élément, vous utilisez la propriété `animation` et spécifiez le nom de l'animation, la durée, le timing-function (pour contrôler la vitesse de l'animation), et d'autres propriétés comme le délai et le nombre d'itérations.

```css
.animated-element {
    animation-name: example;
    animation-duration: 4s;
    animation-timing-function: linear;
    animation-delay: 2s;
    animation-iteration-count: infinite;
}
```

{% hint style="info" %}
Dans cet exemple, l'animation est appliquée à `.animated-element`, avec une durée de 4 secondes, une fonction de timing linéaire, un délai de 2 secondes avant le début de l'animation, et elle s'exécute indéfiniment.
{% endhint %}

### **Transitions CSS**

Bien que les animations CSS soient plus puissantes et flexibles, les transitions CSS sont souvent plus simples à utiliser pour des changements d'état simples. Les transitions permettent de créer des changements d'état d'un élément de manière fluide.

```css
.button {
    background-color: blue;
    color: white;
    transition: background-color 0.5s ease;
}

.button:hover {
    background-color: red;
}
```

{% hint style="info" %}
Dans cet exemple, la couleur de fond du bouton change de bleu à rouge de manière fluide lorsque l'utilisateur passe la souris dessus.
{% endhint %}

## Transitions CSS

Les transitions CSS sont utilisées pour animer les changements de propriétés CSS sur une durée spécifiée. Elles sont particulièrement utiles pour créer des effets subtils et interactifs, tels que le survol d'un bouton ou l'ouverture d'un menu déroulant.

### **Syntaxe de base**

Pour appliquer une transition à un élément, vous utilisez la propriété `transition` sur cet élément. Vous pouvez spécifier la propriété à animer, la durée de l'animation, le timing-function (pour contrôler la vitesse de l'animation), et d'autres propriétés comme le délai avant le début de l'animation.

```css
.button {
    background-color: blue;
    color: white;
    transition: background-color 0.5s ease;
}

.button:hover {
    background-color: red;
}
```

{% hint style="info" %}
Dans cet exemple, la couleur de fond du bouton change de bleu à rouge de manière fluide lorsque l'utilisateur passe la souris dessus. La transition dure 0.5 seconde et utilise une fonction de timing `ease`, qui ralentit l'animation vers la fin.
{% endhint %}

### **Transition property**

La propriété `transition-property` permet de spécifier quelles propriétés CSS doivent être animées. Vous pouvez animer plusieurs propriétés en les séparant par des virgules.

```css
.button {
    transition-property: background-color, color;
    transition-duration: 0.5s;
    transition-timing-function: ease;
}
```

{% hint style="info" %}
Dans cet exemple, la couleur de fond et la couleur du texte du bouton changent de manière fluide.
{% endhint %}

### **Transition duration et Timing function**

* **Transition Duration** : La durée de l'animation, spécifiée en secondes (`s`) ou millisecondes (`ms`).
* **Transition Timing Function** : La fonction de timing contrôle la vitesse de l'animation. Les valeurs courantes incluent `linear`, `ease`, `ease-in`, `ease-out`, et `ease-in-out`.

```css
.button {
    transition-duration: 0.5s;
    transition-timing-function: ease-in-out;
}
```

{% hint style="info" %}
Dans cet exemple, l'animation commence et se termine lentement, avec une vitesse moyenne au milieu.
{% endhint %}

### **Transition delay**

La propriété `transition-delay` permet de spécifier un délai avant le début de l'animation.

```css
.button {
    transition-delay: 2s;
}
```

{% hint style="info" %}
Dans cet exemple, l'animation commence 2 secondes après que l'utilisateur ait passé la souris sur le bouton.
{% endhint %}

## Media queries

Les media queries sont utilisées pour appliquer des styles CSS conditionnellement, en fonction de certaines conditions, comme la largeur de l'écran, la hauteur de l'écran, l'orientation de l'écran, et d'autres caractéristiques de l'appareil.

La syntaxe de base d'une media query est `@media` suivie d'une condition et d'un bloc de styles CSS.

```css
@media (max-width: 600px) {
    /* Styles CSS pour les écrans de 600px ou moins */
}
```

{% hint style="info" %}
Dans cet exemple, les styles CSS à l'intérieur du bloc seront appliqués uniquement si la largeur de l'écran est de 600px ou moins.
{% endhint %}

### **Types de conditions**

* **Largeur (`width`)** : Applique les styles si la largeur de l'écran correspond à la condition.
* **Hauteur (`height`)** : Applique les styles si la hauteur de l'écran correspond à la condition.
* **Orientation** : Applique les styles si l'orientation de l'écran correspond à la condition (`portrait` ou `landscape`).
* **Resolution** : Applique les styles si la résolution de l'écran correspond à la condition.

```css
@media (orientation: portrait) {
    /* Styles pour les écrans en mode portrait */
}

@media (min-resolution: 2dppx) {
    /* Styles pour les écrans avec une résolution de 2 dots par pixel ou plus */
}
```

### **Combinaison de conditions**

Vous pouvez combiner plusieurs conditions dans une seule media query en utilisant `and`.

```css
@media (min-width: 600px) and (max-width: 1200px) {
    /* Styles pour les écrans entre 600px et 1200px de largeur */
}
```

## CSS modernes et pratiques actuelles

Après avoir exploré les concepts avancés de CSS tels que Flexbox, Grid Layout, les animations, les transitions, et les media queries, il est important de se tenir au courant des dernières tendances et pratiques en matière de CSS.&#x20;

{% hint style="info" %}
Les technologies web évoluent rapidement, et les développeurs doivent constamment s'adapter pour rester compétitifs et créer des sites web modernes et performants.
{% endhint %}

### **Les variables CSS**

Les variables CSS permettent de stocker des valeurs spécifiques pour une utilisation ultérieure. Elles peuvent être utilisées pour stocker des couleurs, des tailles de police, des espacements, et d'autres valeurs réutilisables, ce qui rend le code plus propre et plus facile à maintenir.

```css
:root {
    --main-color: #06c;
    --secondary-color: #f06;
}

body {
    background-color: var(--main-color);
    color: var(--secondary-color);
}
```

### **CSS Grid et Flexbox ensemble**

Bien que Flexbox et Grid Layout soient souvent utilisés séparément, ils peuvent être combinés pour créer des mises en page complexes et flexibles. Par exemple, vous pouvez utiliser Grid pour la mise en page globale et Flexbox pour les éléments internes.

```css
.container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
}

.item {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

### **CSS Custom Properties**

Les CSS Custom Properties, également connues sous le nom de variables CSS, permettent de stocker des valeurs spécifiques pour une utilisation ultérieure.&#x20;

Elles peuvent être utilisées pour stocker des couleurs, des tailles de police, des espacements, et d'autres valeurs réutilisables, ce qui rend le code plus propre et plus facile à maintenir.

```css
:root {
    --main-color: #06c;
    --secondary-color: #f06;
}

body {
    background-color: var(--main-color);
    color: var(--secondary-color);
}
```

### **Utilisation de `calc()`**

La fonction `calc()` permet de réaliser des calculs directement dans les feuilles de style CSS. Cela peut être particulièrement utile pour les calculs de taille, de positionnement, et d'autres valeurs qui dépendent de variables ou de valeurs dynamiques.

```css
.container {
    width: calc(100% - 20px);
}
```

### Les préfixes

Les préfixes de fournisseurs sont des extensions de propriétés CSS spécifiques à un navigateur, utilisées pour assurer la compatibilité entre les navigateurs lors de l'utilisation de certaines propriétés CSS qui ne sont pas encore standardisées ou qui sont encore en cours de développement.&#x20;

Chaque navigateur a son propre préfixe :&#x20;

* `-webkit-` pour Chrome et Safari
* `-moz-` pour Firefox
* `-ms-` pour Internet Explorer et Edge
* `-o-` pour Opera.

Par exemple, si vous souhaitez utiliser une propriété CSS qui n'est pas encore standardisée, vous devrez l'ajouter avec le préfixe approprié pour chaque navigateur que vous souhaitez prendre en charge. Attention, cela peut rendre le code CSS plus encombrant et plus difficile à gérer.

```css
.element {
    -webkit-transform: rotate(30deg); /* Pour Chrome et Safari */
    -moz-transform: rotate(30deg); /* Pour Firefox */
    -ms-transform: rotate(30deg); /* Pour Internet Explorer et Edge */
    -o-transform: rotate(30deg); /* Pour Opera */
    transform: rotate(30deg); /* Pour les navigateurs qui supportent la propriété sans préfixe */
}

```

### **Exemple pratique**

Voici un exemple pratique de l'utilisation de plusieurs de ces pratiques modernes de CSS :

```css
:root {
    --main-color: #06c;
    --secondary-color: #f06;
}

.container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
}

.item {
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: var(--main-color);
    color: var(--secondary-color);
}

.item:hover {
    background-color: var(--secondary-color);
    color: var(--main-color);
}
```

{% hint style="info" %}
Dans cet exemple, nous utilisons des variables CSS pour les couleurs, Grid Layout pour la mise en page, et Flexbox pour l'alignement des éléments. Nous avons également ajouté une interaction de survol pour changer les couleurs.
{% endhint %}

{% hint style="success" %}
Les pratiques modernes de CSS, telles que l'utilisation de variables CSS, la combinaison de Grid et Flexbox, et l'utilisation de `calc()`, permettent de créer des designs plus flexibles, plus maintenables, et plus performants. En restant à jour avec les dernières tendances et en utilisant des outils comme Autoprefixer, vous pouvez créer des sites web qui sont à la fois modernes et compatibles avec une large gamme de navigateurs.
{% endhint %}
