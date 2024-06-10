# Introduction à Javascript

## Histoire et importance de JavaScript

JavaScript a été créé en 1995 par Brendan Eich chez Netscape Communications Corporation.&#x20;

À l'origine, il était connu sous le nom de LiveScript, mais a été renommé JavaScript pour des raisons marketing. Bien que son nom puisse prêter à confusion, JavaScript n'a aucun lien direct avec le langage de programmation Java.JavaScript est devenu un langage incontournable pour le développement web.&#x20;

Il permet d'ajouter de l'interactivité aux pages web, de valider des formulaires, de créer des animations et bien plus encore. Avec l'avènement des applications web modernes, JavaScript est également utilisé pour le développement d'applications côté client et serveur grâce à des environnements d'exécution comme Node.js.

## Syntaxe de base de JavaScript

### Variables

Les variables sont utilisées pour stocker des valeurs. En JavaScript, les variables sont déclarées avec les mots-clés `var`, `let` ou `const`.

```javascript
var x = 5; // Variable avec portée de fonction
let y = 10; // Variable avec portée de bloc
const z = 15; // Constante (valeur immuable)
```

### Types de données en JavaScript

JavaScript prend en charge plusieurs types de données, notamment :

* **Number** : représente les nombres entiers et à virgule flottante.
* **String** : représente les chaînes de caractères.
* **Boolean** : représente les valeurs logiques `true` ou `false`.
* **Undefined** : représente une variable non initialisée.
* **Null** : représente une valeur non existante.
* **Object** : représente une collection de paires clé-valeur.
* **Array** : représente une liste ordonnée de valeurs.

### Opérateurs

JavaScript prend en charge les opérateurs arithmétiques, d'affectation, de comparaison, logiques et bien d'autres.

```javascript
let a = 5 + 3; // Addition
let b = a * 2; // Multiplication
let c = b % 4; // Modulo
```

### Structures de contrôle

Les structures de contrôle permettent d'exécuter du code de manière conditionnelle ou en boucle.

```javascript
if (condition) {
  // Code à exécuter si la condition est vraie
} else {
  // Code à exécuter si la condition est fausse
}

for (let i = 0; i < 5; i++) {
  // Code à exécuter pour chaque itération
}
```

### Fonctions

Les fonctions sont des blocs de code réutilisables qui peuvent accepter des paramètres et retourner une valeur.

```javascript
function addNumbers(a, b) {
  return a + b;
}

let result = addNumbers(3, 5); // result vaut 8
```
