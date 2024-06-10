# Les types de données JS

JavaScript est un langage faiblement typé, ce qui signifie que les variables peuvent contenir différents types de données sans avoir à les déclarer explicitement. Cependant, il est important de comprendre les différents types de données pour écrire un code efficace et éviter les erreurs.&#x20;

## Les données primitives

### Nombre (Number)

Le type `Number` représente les nombres entiers et à virgule flottante. Il existe également deux valeurs spéciales : `Infinity` (infini positif) et `-Infinity` (infini négatif), ainsi que `NaN` (Not a Number).

```javascript
let x = 42; // Nombre entier
let y = 3.14; // Nombre à virgule flottante
let z = Infinity; // Infini positif
let w = -Infinity; // Infini négatif
let v = NaN; // Not a Number
```

### Chaîne de caractères (String)

Le type `String` représente les chaînes de caractères. Les chaînes peuvent être entourées de guillemets simples (`'`), de guillemets doubles (`"`), ou de backticks (\`).

```javascript
let str1 = "Bonjour"; // Guillemets doubles
let str2 = 'Monde'; // Guillemets simples
let str3 = `Salut`; // Backticks
```

### Booléen (Boolean)

Le type `Boolean` représente les valeurs logiques `true` (vrai) et `false` (faux).

```javascript
let vrai = true;
let faux = false;
```

### Null

La valeur `null` représente une valeur non existante ou invalide.

```javascript
let variable = null; // Aucune valeur
```

### Undefined

La valeur `undefined` représente une variable non initialisée ou une propriété d'objet inexistante.

```javascript
let x; // La valeur de x est undefined
```

### Symbol (ES6)

Le type `Symbol` représente des identifiants uniques et immuables. Les symboles sont principalement utilisés comme clés d'objet.

```javascript
let id = Symbol("identifiant");
```

### BigInt (ES2020)

Le type `BigInt` représente les nombres entiers de longueur arbitraire. Il est utile pour représenter des nombres entiers très grands qui ne peuvent pas être représentés avec précision par le type `Number`.

```javascript
let bigNumber = 1234567890123456789012345678901234567890n;
```

## Non-primitives

### Objet (Object)

Le type `Object` représente une collection de paires clé-valeur. Les objets peuvent contenir des propriétés (clés) et des méthodes (fonctions).

```javascript
let personne = {
  nom: "Dupont",
  age: 30,
  saluer: function() {
    console.log("Bonjour !");
  }
};
```

### Tableau (Array)

Le type `Array` représente une liste ordonnée de valeurs. Les tableaux sont un type spécial d'objet.

```javascript
let fruits = ["pomme", "banane", "orange"];
```

### Date

Le type `Date` représente une date et une heure.

```javascript
let aujourd'hui = new Date();
```

### RegExp

Le type `RegExp` représente une expression régulière, qui est un motif de recherche utilisé pour effectuer des opérations de correspondance de modèles sur des chaînes de caractères.

```javascript
let regex = /^[a-z]+$/;
```

{% hint style="info" %}
Dans ce chapitre, nous avons couvert les différents types de données en JavaScript, y compris les primitives et les non-primitives.&#x20;

Comprendre ces types de données est essentiel pour écrire un code JavaScript efficace et éviter les erreurs courantes liées aux types de données
{% endhint %}
