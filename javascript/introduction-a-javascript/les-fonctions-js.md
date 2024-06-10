# Les fonctions JS

Les fonctions en JavaScript sont des blocs de code conçus pour effectuer une tâche particulière. Elles jouent un rôle crucial dans l'écriture de code modulaire et réutilisable.

## Définition d'une fonction

Une fonction se définit avec le mot-clé `function`, suivi d'un nom, d'une paire de parenthèses contenant zéro ou plusieurs paramètres, et d'un bloc de code entre accolades.

```javascript
function nomDeLaFonction(parametre1, parametre2) {
  // bloc de code à exécuter
}
```

## Invocation d'une fonction

Pour exécuter une fonction, vous l'invoquez en écrivant son nom suivi d'une paire de parenthèses. Si la fonction attend des paramètres, vous les fournissez entre les parenthèses.

```javascript
nomDeLaFonction(valeur1, valeur2);
```

### Fonction sans paramètre

Une fonction peut être créée sans paramètre. Elle effectuera une tâche spécifique à chaque appel.

```javascript
function direBonjour() {
  console.log("Bonjour à tous!");
}

direBonjour(); // Affiche : Bonjour à tous!
```

### Fonction avec paramètres

Les fonctions peuvent prendre des paramètres pour effectuer des opérations basées sur des données d'entrée.

```javascript
function additionner(nombre1, nombre2) {
  console.log(nombre1 + nombre2);
}

additionner(5, 7); // Affiche : 12
```

## Fonctions fléchées

En JavaScript ES6, une nouvelle syntaxe pour déclarer des fonctions a été introduite : la fonction fléchée. Elle offre une syntaxe plus courte et ne possède pas son propre contexte `this`.

```javascript
const multiplier = (nombre1, nombre2) => {
  return nombre1 * nombre2;
};

console.log(multiplier(3, 4)); // Affiche : 12
```

{% hint style="info" %}
Les fonctions en JavaScript sont essentielles pour structurer et organiser votre code. Elles permettent de rendre votre code plus modulaire, plus facile à lire et à maintenir.
{% endhint %}
