# Le HTML avancé

## **Définition des éléments HTML avancés**

Les éléments HTML avancés sont des balises HTML qui permettent de créer des fonctionnalités plus complexes et interactives sur les sites web. Ils incluent des éléments tels que les tableaux, le Canvas, les listes déroulantes, les zones de sortie ...

{% hint style="info" %}
Ces éléments vont au-delà des fonctionnalités de base du HTML, permettant de créer des expériences utilisateur plus riches et plus dynamiques.
{% endhint %}

## Tableaux HTML

Les tableaux HTML sont utilisés pour afficher des données sous forme de table. Ils sont particulièrement utiles pour présenter des informations structurées, comme des données tabulaires, des listes de produits, des classements, etc. Les tableaux HTML sont créés en utilisant les balises `<table>`, `<tr>` (table row), `<td>` (table data), et `<th>` (table header).

### **Structure de base d'un tableau HTML**

Un tableau HTML de base est composé de lignes (`<tr>`) contenant des cellules de données (`<td>`) ou des en-têtes de colonnes (`<th>`). Voici un exemple simple :

```html
<table>
    <tr>
        <th>Nom</th>
        <th>Prénom</th>
    </tr>
    <tr>
        <td>Dupont</td>
        <td>Jean</td>
    </tr>
    <tr>
        <td>Martin</td>
        <td>Marie</td>
    </tr>
</table>
```

### **Attributs des balises de tableau**

Les balises de tableau peuvent être complétées par divers attributs pour améliorer leur fonctionnalité et leur apparence :

* **`colspan`** : Permet à une cellule de s'étendre sur plusieurs colonnes.
* **`rowspan`** : Permet à une cellule de s'étendre sur plusieurs lignes.
* **`headers`** : Associe une cellule de données à un en-tête de colonne ou de ligne, améliorant l'accessibilité.

### **Tableaux complexes**

Les tableaux peuvent être structurés de manière plus complexe en utilisant des balises `<thead>`, `<tbody>`, et `<tfoot>` pour séparer les en-têtes, le corps, et les pieds de tableau. Cela facilite la mise en forme et l'accessibilité.

```html
<table>
    <thead>
        <tr>
            <th>Nom</th>
            <th>Prénom</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Dupont</td>
            <td>Jean</td>
        </tr>
        <tr>
            <td>Martin</td>
            <td>Marie</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td colspan="2">Total : 2 personnes</td>
        </tr>
    </tfoot>
</table>
```

## Canvas HTML

Le Canvas HTML est une balise qui permet aux développeurs de dessiner des graphiques via JavaScript. Il est particulièrement utile pour créer des animations, des jeux, et des visualisations de données dynamiques. Le Canvas fournit un contexte de dessin 2D, qui peut être manipulé avec l'API Canvas pour dessiner des formes, des images, et des animations.

### **Création d'un Canvas**

Pour créer un Canvas, vous devez d'abord ajouter la balise `<canvas>` dans votre HTML, puis accéder à ce Canvas via JavaScript pour dessiner dessus. Voici un exemple simple :

```html
<canvas id="monCanvas" width="200" height="100"></canvas>
<script>
    var canvas = document.getElementById('monCanvas');
    var ctx = canvas.getContext('2d');
    ctx.fillStyle = 'red';
    ctx.fillRect(10, 10, 50, 50);
</script>
```

### **Dessiner des formes**

L'API Canvas permet de dessiner une variété de formes, comme des rectangles, des cercles, et des lignes. Voici comment dessiner un cercle :

```javascript
ctx.beginPath();
ctx.arc(100, 50, 40, 0, 2 * Math.PI);
ctx.stroke();
```

### **Dessiner des images**

Vous pouvez également dessiner des images sur le Canvas. Pour cela, vous devez d'abord charger l'image, puis la dessiner sur le Canvas :

```javascript
var img = new Image();
img.onload = function() {
    ctx.drawImage(img, 0, 0);
};
img.src = 'chemin/vers/votre/image.jpg';
```

### **Créer des animations**

Les animations sur le Canvas sont généralement créées en utilisant une boucle de dessin qui est appelée à intervalles réguliers. Voici un exemple simple d'animation :

```javascript
function dessiner() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    ctx.fillStyle = 'blue';
    ctx.fillRect(x, 0, 50, 50);
    x += 1;
    if (x > canvas.width) {
        x = 0;
    }
    requestAnimationFrame(dessiner);
}
var x = 0;
dessiner();
```

{% hint style="info" %}
Le Canvas HTML est un outil puissant pour créer des graphiques et des animations sur le web. En maîtrisant les concepts de base de l'API Canvas, vous pouvez créer des visualisations de données dynamiques, des jeux, et des animations.
{% endhint %}

## Select HTML

La balise Select HTML est utilisée pour créer des listes déroulantes dans les formulaires HTML. Elle permet aux utilisateurs de sélectionner une ou plusieurs options à partir d'une liste prédéfinie. La balise `<select>` est utilisée pour définir la liste déroulante, tandis que chaque option est définie par la balise `<option>`.

### **Conception d'une liste déroulante simple**

Pour créer une liste déroulante simple, vous devez d'abord ajouter la balise `<select>` dans votre HTML, puis ajouter des balises `<option>` pour chaque option de la liste. Voici un exemple simple :

```html
<select name="fruits">
    <option value="apple">Pomme</option>
    <option value="banana">Banane</option>
    <option value="cherry">Cerise</option>
</select>
```

### **Liste déroulante avec sélection multiple**

Pour permettre la sélection de plusieurs options, vous pouvez ajouter l'attribut `multiple` à la balise `<select>`. Cela transforme la liste déroulante en une liste de cases à cocher.

```html
<select name="fruits" multiple>
    <option value="apple">Pomme</option>
    <option value="banana">Banane</option>
    <option value="cherry">Cerise</option>
</select>
```

### **Grouper les options**

Vous pouvez grouper les options dans une liste déroulante en utilisant la balise `<optgroup>`. Cela permet d'organiser les options de manière logique et d'améliorer l'expérience utilisateur.

```html
<select name="fruits">
    <optgroup label="Fruits">
        <option value="apple">Pomme</option>
        <option value="banana">Banane</option>
    </optgroup>
    <optgroup label="Légumes">
        <option value="carrot">Carotte</option>
        <option value="tomato">Tomate</option>
    </optgroup>
</select>
```

{% hint style="info" %}
La balise Select HTML est un élément essentiel pour créer des listes déroulantes dans les formulaires HTML. En utilisant des listes déroulantes, vous pouvez faciliter la saisie de données par les utilisateurs et améliorer l'expérience utilisateur sur vos sites web.
{% endhint %}

## Datalist HTML

Le Datalist HTML est une balise qui permet de créer des listes déroulantes avec des suggestions automatiques pour les champs de formulaire. Cela améliore l'expérience utilisateur en fournissant des options de saisie prédéfinies, ce qui peut réduire les erreurs de saisie et faciliter la navigation.

### **Création d'un Datalist**

Pour créer un Datalist, vous devez d'abord ajouter la balise `<datalist>` dans votre HTML, puis associer cette liste à un champ de formulaire (`<input>`) en utilisant l'attribut `list`. Voici un exemple simple :

```html
<input list="browsers" name="browser">
<datalist id="browsers">
    <option value="Internet Explorer">
    <option value="Firefox">
    <option value="Chrome">
    <option value="Opera">
    <option value="Safari">
</datalist>
```

### **Utilisation du Datalist**

Lorsque l'utilisateur commence à taper dans le champ de formulaire associé au Datalist, les navigateurs affichent une liste déroulante des options correspondantes. L'utilisateur peut alors sélectionner une option de la liste ou continuer à taper pour filtrer les suggestions.

### **Personnalisation du Datalist**

Vous pouvez personnaliser le comportement du Datalist en utilisant JavaScript. Par exemple, vous pouvez filtrer les options de la liste déroulante en fonction de la saisie de l'utilisateur, ou ajouter des options dynamiquement.

{% hint style="info" %}
En utilisant des listes déroulantes avec des options prédéfinies, vous pouvez réduire les erreurs de saisie, faciliter la navigation, et rendre vos formulaires plus conviviaux.
{% endhint %}

## Gestion des fichiers et images

La gestion des fichiers dans les applications web permet aux utilisateurs de télécharger des fichiers sur le serveur ou de les télécharger depuis le serveur. Cela peut inclure des documents, des images, des vidéos, etc.

### **Upload de fichiers**

Pour permettre l'upload de fichiers, vous devez utiliser un champ de formulaire de type `file` dans votre HTML. Lorsque le formulaire est soumis, le fichier peut être traité côté serveur en utilisant le langage de programmation approprié (comme PHP, Node.js, etc.).

N'oubliez surtout pas d'ajouter `enctype="multipart/form-data"` afin de rendre votre formulaire opérationnel quant à l'utilisation de l'input file.

```html
<form action="/upload" method="post" enctype="multipart/form-data">
    <input type="file" name="myFile">
    <input type="submit" value="Upload">
</form>
```

### **Téléchargement de fichiers**

Pour permettre le téléchargement de fichiers, vous pouvez créer un lien vers le fichier sur le serveur. Cela peut être fait en utilisant la balise `<a>` avec l'attribut `href` pointant vers l'emplacement du fichier.

```html
<a href="/path/to/your/file.pdf" download>Télécharger le fichier</a>
```

### **Affichage d'images**

Les images peuvent être affichées dans les applications web en utilisant la balise `<img>`. Vous devez spécifier l'attribut `src` pour indiquer l'emplacement de l'image.

```html
<img src="/path/to/your/image.jpg" alt="Description de l'image">
```

{% hint style="success" %}
Avec JavaScript, vous pouvez manipuler des images côté client, par exemple en redimensionnant, en filtrant, ou en ajoutant des effets. Cela peut être réalisé en utilisant l'API Canvas ou des bibliothèques JavaScript spécialisées.
{% endhint %}

## Les images adaptives

L'attribut `srcset` est utilisé dans les balises `<img>` pour spécifier différentes images à charger en fonction de la résolution de l'écran de l'utilisateur. Cela permet d'optimiser le chargement des images sur les appareils mobiles et de bureau, en chargeant uniquement l'image la plus appropriée pour la résolution de l'écran.

### **Syntaxe de l'attribut `srcset`**

L'attribut `srcset` contient une liste d'images et leurs résolutions associées, séparées par des virgules. Chaque image est spécifiée par son chemin d'accès et sa résolution, séparés par un espace.

```html
<img 
    src="image-300w.jpg" 
    srcset="image-300w.jpg 300w, image-600w.jpg 600w, image-1200w.jpg 1200w" 
    alt="Description de l'image"
    >
```

_Dans cet exemple, trois images sont spécifiées avec leurs résolutions (300w, 600w, 1200w). Le navigateur choisira l'image la plus appropriée en fonction de la résolution de l'écran de l'utilisateur._

### **Utilisation de `srcset` avec `sizes`**

Pour une gestion plus précise du chargement des images, vous pouvez combiner `srcset` avec l'attribut `sizes`. L'attribut `sizes` permet de spécifier la taille de l'image en fonction des différentes conditions de mise en page.

```html
<img 
    src="image-300w.jpg" 
    srcset="image-300w.jpg 300w, image-600w.jpg 600w, image-1200w.jpg 1200w" 
    sizes="(max-width: 600px) 300px, 600px" 
    alt="Description de l'image"
>
```

_Dans cet exemple, si la largeur de la fenêtre du navigateur est inférieure ou égale à 600px, l'image de 300px de large est chargée. Sinon, l'image de 600px de large est chargée._

## Le lazy loading

### C'est quoi le lazy loading ?

Le lazy loading est une technique qui permet de retarder le chargement des images jusqu'à ce qu'elles soient nécessaires, c'est-à-dire jusqu'à ce qu'elles soient visibles dans la fenêtre de visualisation de l'utilisateur.&#x20;

{% hint style="success" %}
Cela peut améliorer les performances de chargement des pages, en particulier pour les sites web avec de nombreuses images.
{% endhint %}

### **Utilisation de l'attribut `loading`**

L'attribut `loading` est une fonctionnalité native de HTML qui permet d'activer le lazy loading des images. En ajoutant `loading="lazy"` à une balise `<img>`, vous indiquez au navigateur de retarder le chargement de l'image jusqu'à ce qu'elle soit nécessaire.

```html
<img src="image.jpg" loading="lazy" alt="Description de l'image">
```

#### Bon à savoir

{% hint style="info" %}
Il est également possible de définir un lazy loading manuel, sans utiliser les attributs HTML natifs, mais pour cela nous devrons faire appel à Javascript et sa manipulation du DOM.
{% endhint %}
