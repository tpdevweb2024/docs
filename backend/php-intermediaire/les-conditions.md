# Les conditions

Dans le développement web avec PHP, les conditions jouent un rôle central, permettant à votre code de prendre des décisions et d'agir différemment en fonction des données ou des situations. Les structures conditionnelles les plus utilisées en PHP sont : `if`, `else`, `elseif`, et le commutateur `switch`.

## La structure `if` <a href="#la-structure-if" id="la-structure-if"></a>

La structure `if` exécute une portion de code si une condition spécifiée est vraie.

```php
if (condition) {
  // code à exécuter si la condition est vraie
}
```

### Utilisation de `else` <a href="#utilisation-de-else" id="utilisation-de-else"></a>

`else` complète une instruction `if` pour exécuter du code lorsque la condition `if` n'est pas vraie.

```php
if (condition) {
  // code à exécuter si la condition est vraie
} else {
  // code à exécuter si la condition est fausse
}
```

### La structure `elseif` <a href="#la-structure-elseif" id="la-structure-elseif"></a>

`elseif` permet de définir une nouvelle condition si la condition `if` précédente est fausse.

```php
if (condition1) {
  // code à exécuter si condition1 est vraie
} elseif (condition2) {
  // code à exécuter si condition2 est vraie
} else {
  // code à exécuter si les conditions précédentes sont fausses
}
```

## Le commutateur `switch` <a href="#le-commutateur-switch" id="le-commutateur-switch"></a>

Le commutateur `switch` exécute différents blocs de code basés sur différentes conditions.

```php
switch (variable) {
  case valeur1:
    // code à exécuter si variable=valeur1
    break;
  case valeur2:
    // code à exécuter si variable=valeur2
    break;
  default:
    // code à exécuter si variable ne correspond à aucun cas
}
```

{% hint style="info" %}
Les structures conditionnelles en PHP offrent une flexibilité et un contrôle précis du flux d'exécution de votre code, permettant ainsi de créer des applications dynamiques et réactives.
{% endhint %}

### L'expression `match` <a href="#lexpression-match" id="lexpression-match"></a>

L'expression `match` est une version plus puissante et flexible du commutateur `switch` qui a été introduite dans PHP 8. Elle permet de comparer une expression à plusieurs valeurs de manière concise, et contrairement à `switch`, elle retourne une valeur.

```php
$resultat = match (variable) {
    valeur1 => 'resultat pour valeur1',
    valeur2 => 'resultat pour valeur2',
    default => 'resultat par défaut',
};
```

Avec `match`, chaque branche est une expression qui renvoie une valeur, et il est inutile d'utiliser `break`.
