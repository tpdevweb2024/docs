# Les tableaux en JS

Les tableaux en JavaScript sont des collections ordonnées, également connus sous le nom d'arrays, qui peuvent contenir différents types de valeurs telles que des nombres, des chaînes de caractères et même d'autres tableaux. Ils sont incroyablement utiles pour stocker et manipuler des ensembles de données.

## Création d'un Tableau

Pour créer un tableau en JavaScript, vous pouvez utiliser la syntaxe des crochets `[]`.

```javascript
let monTableau = [1, 2, 3, 4, 5];
```

### Accéder aux Éléments d'un Tableau

Pour accéder à un élément d'un tableau, utilisez la syntaxe des crochets avec l'index de l'élément (commençant à 0).

```javascript
let premierElement = monTableau[0]; // Accède au premier élément, qui est 1
```

### Modifier un Élément

Vous pouvez modifier un élément spécifique en utilisant son index.

```javascript
monTableau[0] = 9; // Change le premier élément à 9
```

## Longueur d'un Tableau

La propriété `.length` vous permet de savoir combien d'éléments sont contenus dans le tableau.

```javascript
let taille = monTableau.length; // Renvoie la taille du tableau
```

## Méthodes Utiles

JavaScript propose plusieurs méthodes pour manipuler les tableaux, notamment :

* `push()` pour ajouter un élément à la fin.
* `pop()` pour retirer le dernier élément.
* `shift()` pour retirer le premier élément.
* `unshift()` pour ajouter un élément au début.

## Parcourir un Tableau

Pour parcourir les éléments d'un tableau, vous pouvez utiliser une boucle `for` ou la méthode `forEach()`.

### Utilisation de for

```javascript
for (let i = 0; i < monTableau.length; i++) {
  console.log(monTableau[i]);
}
```

### Utilisation de forEach

```javascript
monTableau.forEach(function(element) {
  console.log(element);
});
```

{% hint style="info" %}
Les tableaux en JavaScript sont des structures de données flexibles et puissantes qui permettent de stocker et manipuler facilement des collections de données. En maitrisant la création, l'accès aux éléments, la modification, et la navigation dans les tableaux, vous pouvez gérer efficacement des données complexes dans vos applications JavaScript.
{% endhint %}
