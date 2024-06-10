# Les opérateurs

PHP fournit un large éventail d'opérateurs utilisés pour effectuer des opérations arithmétiques, de comparaison, d'assignation, logiques, etc. Voici une liste des types d'opérateurs les plus couramment utilisés :

## **Opérateurs arithmétiques** <a href="#operateurs-arithmetiques" id="operateurs-arithmetiques"></a>

### Addition (+) <a href="#addition" id="addition"></a>

L'opérateur d'addition `+` en PHP est utilisé pour additionner deux nombres. Voici un exemple simple d'utilisation :

```php
$nombre1 = 5;
$nombre2 = 10;
$somme = $nombre1 + $nombre2; 
echo $somme; // 15
```

{% hint style="info" %}
Dans cet exemple, `$nombre1` et `$nombre2` sont additionnés en utilisant l'opérateur `+`, et le résultat est stocké dans la variable `$somme`. Ensuite, le résultat, 15, est affiché à l'aide de `echo`.
{% endhint %}

### **Soustraction (-)** <a href="#soustraction" id="soustraction"></a>

L'opérateur de soustraction `-` en PHP est utilisé pour soustraire un nombre d'un autre. Voici un exemple d'utilisation de l'opérateur Soustraction :

```php
$nombre1 = 15;
$nombre2 = 5;
$difference = $nombre1 - $nombre2; 
echo $difference; // 10
```

{% hint style="info" %}
Dans cet exemple, $nombre2 est soustrait de $nombre1 en utilisant l'opérateur `-`, et le résultat est stocké dans la variable $difference. Ensuite, le résultat, 10, est affiché à l'aide de echo.
{% endhint %}

### Multiplication (\*) <a href="#multiplication" id="multiplication"></a>

L'opérateur de multiplication `*` en PHP est utilisé pour multiplier deux nombres. Voici comment vous pouvez l'utiliser :

```php
$nombre1 = 10;
$nombre2 = 5;
$produit = $nombre1 * $nombre2;
echo $produit; // 50
```

{% hint style="info" %}
Dans cet exemple, `$nombre1` et `$nombre2` sont multipliés en utilisant l'opérateur `*`, et le résultat est stocké dans la variable `$produit`. Ensuite, le résultat, 50, est affiché à l'aide de `echo`.
{% endhint %}

### **Division (/)** <a href="#division" id="division"></a>

L'opérateur de division `/` en PHP est utilisé pour diviser un nombre par un autre. Ci-dessous un exemple de son utilisation :

```php
$nombre1 = 10;
$nombre2 = 2;
$quotient = $nombre1 / $nombre2;
echo $quotient; // 5
```

{% hint style="info" %}
Dans cet exemple, $nombre1 est divisé par $nombre2 à l'aide de l'opérateur `/`, et le résultat est stocké dans la variable $quotient. Ensuite, le résultat, 5, est affiché à l'aide de `echo`.
{% endhint %}

### Modulo (%) <a href="#modulo" id="modulo"></a>

Le modulo est une opération en PHP qui trouve le reste d'une division entre deux nombres. Elle est effectuée à l'aide de l'opérateur `%`. Voici comment vous pouvez l'utiliser :

```php
$nombre1 = 10;
$nombre2 = 3;
$reste = $nombre1 % $nombre2;
echo $reste; // 1
```

{% hint style="info" %}
Dans cet exemple, $nombre1 est divisé par $nombre2 et le reste de cette division (1) est stocké dans la variable `$reste`. Ensuite, le résultat est affiché avec `echo`. C'est très utile pour déterminer si un nombre est pair ou impair, ou pour toute autre nécessité de trouver un reste de division.
{% endhint %}

## **Opérateurs de comparaison** <a href="#operateurs-de-comparaison" id="operateurs-de-comparaison"></a>

### Égal à (==) <a href="#egal-a" id="egal-a"></a>

L'opérateur `==` est utilisé pour comparer deux valeurs en PHP. Si les valeurs des deux côtés de l'opérateur sont égales, l'expression retourne `true`. Sinon, cela retourne `false`. Il est important de noter que l'opérateur `==` ne vérifie pas le type de données, seulement la valeur.

```php
if (3 == "3") {
    echo "Vrai"; // Cela sera exécuté car les valeurs sont considérées comme égales
} else {
    echo "Faux";
}
```

{% hint style="info" %}
Dans l'exemple ci-dessus, même si un côté est de type entier et l'autre de type chaîne, l'expression est évaluée à `true` car les deux ont la même valeur "3".
{% endhint %}

### Strictement égal à (===) <a href="#strictement-egal-a" id="strictement-egal-a"></a>

L'opérateur `===` en PHP est utilisé pour comparer si deux valeurs sont identiques, ce qui signifie qu'il vérifie à la fois la valeur et le type de données. Si les deux valeurs sont du même type et ont la même valeur, l'expression retourne `true`. Autrement, cela retourne `false`.

```php
if (3 === 3) {
    echo "Vrai"; // Cela sera exécuté car les valeurs et les types sont identiques
} else {
    echo "Faux";
}

if (3 === "3") {
    echo "Vrai";
} else {
    echo "Faux"; // Cela sera exécuté car les types ne correspondent pas
}
```

Contrairement à `==`, l'opérateur `===` ne convertit pas les types de données pour effectuer la comparaison. C'est pourquoi il est souvent préféré pour éviter les erreurs subtiles et assurer la précision de la comparaison dans les scripts PHP.

### Différent de (!=) <a href="#different-de" id="different-de"></a>

L'opérateur `!=` en PHP est utilisé pour vérifier si deux valeurs sont différentes. Si les valeurs comparées n'ont pas la même valeur, l'expression retourne `true`. Si elles ont la même valeur, indépendamment de leur type, l'expression retourne `false`. Cet opérateur ne prend pas en compte le type de données lors de la comparaison.

```php
if (3 != "3") {
    echo "Faux"; // Ne sera pas exécuté car les valeurs sont considérées comme égales
} else {
    echo "Vrai";
}

if (3 != 4) {
    echo "Vrai"; // Cela sera exécuté car les valeurs sont différentes
} else {
    echo "Faux";
}
```

### Supérieur à (`>`) <a href="#superieur-a-greater-than" id="superieur-a-greater-than"></a>

L'opérateur `>` en PHP est utilisé pour comparer deux valeurs. Il vérifie si la valeur à gauche de l'opérateur est supérieure à celle à droite. Si la condition est vraie, il renvoie `true`; sinon, il renvoie `false`.

```php
if (5 > 3) {
    echo "Vrai"; // Cela sera exécuté car 5 est supérieur à 3
} else {
    echo "Faux";
}

if (3 > 5) {
    echo "Vrai";
} else {
    echo "Faux"; // Cela sera exécuté car 3 n'est pas supérieur à 5
}
```

### Inférieur à (<) <a href="#inferieur-a-less-than" id="inferieur-a-less-than"></a>

L'opérateur `<` en PHP est utilisé pour comparer deux valeurs. Il vérifie si la valeur à gauche de l'opérateur est inférieure à celle à droite. Si c'est le cas, l'expression renvoie `true`; sinon, elle renvoie `false`.

```php
if (2 < 3) {
    echo "Vrai"; // Cela sera exécuté car 2 est inférieur à 3
} else {
    echo "Faux";
}

if (4 < 2) {
    echo "Vrai";
} else {
    echo "Faux"; // Cela sera exécuté car 4 n'est pas inférieur à 2
}
```

## **Opérateurs d'assignation** <a href="#operateurs-dassignation" id="operateurs-dassignation"></a>

### Incrémentation (+=) <a href="#incrementation" id="incrementation"></a>

Dans cet exemple, `$x` contient initialement la valeur `5`. En utilisant l'opérateur `+=`, nous ajoutons `3` à `$x`, ce qui résulte en `8`, qui est ensuite réassigné à `$x`.

```
$x = 5;
$x += 3; // Équivalent à $x = $x + 3;
echo $x; // Affiche : 8
```

L'opérateur `+=` en PHP est une abréviation permettant de réaliser une addition et une affectation en une seule étape. Il ajoute l'opérande de droite à l'opérande de gauche et assigne le résultat à l'opérande de gauche.

### Décrémentation (-=) <a href="#decrementation" id="decrementation"></a>

`-=` est un opérateur de soustraction suivi d'une assignation en programmation. Il soustrait la valeur de droite à celle de la variable de gauche, puis assigne le résultat à la variable de gauche. Par exemple, `x -= y` équivaut à \`x = x - y

## **Opérateurs logiques** <a href="#operateurs-logiques" id="operateurs-logiques"></a>

### Opérateur logique `&&` (ET) <a href="#operateur-logique-and-and-et" id="operateur-logique-and-and-et"></a>

L'opérateur `&&` est un opérateur logique 'ET' utilisé pour combiner deux conditions. Il ne retourne `true` que si les deux opérandes sont vraies. Si l'une des conditions (ou les deux) est fausse, l'expression complète retournera `false`. Cet opérateur est souvent utilisé pour tester si plusieurs conditions sont remplies simultanément.

```php
$isAdult = true;
$hasPermission = true;

if ($isAdult && $hasPermission) {
    echo "Accès autorisé";
} else {
    echo "Accès refusé";
}
```

{% hint style="info" %}
Dans cet exemple, l'accès est autorisé uniquement si les deux variables `$isAdult` et `$hasPermission` sont `true`.
{% endhint %}

### Opérateur logique || (OU) <a href="#operateur-logique-or-or-ou" id="operateur-logique-or-or-ou"></a>

L'opérateur logique `||` représente l'opérateur OR (OU). Dans une expression logique, il renvoie `true` si au moins l'une des conditions qu'il compare est vraie. Si les deux conditions sont fausses, alors il renvoie `false`. Il est souvent utilisé pour vérifier plusieurs conditions dans une instruction de décision.

### **Opérateur logique ! (NON)** <a href="#operateur-logique-non" id="operateur-logique-non"></a>

L'opérateur logique `!` est connu sous le nom de NOT (NON). Il est utilisé pour inverser le résultat d'une condition. Si la condition est `true`, l'application de l'opérateur `!` la transformera en `false`, et vice versa. C'est un moyen efficace de tester l'inverse d'une condition donnée.

Voici un exemple d'utilisation :

```php
$isMinor = !true; // équivaut à false

if ($isMinor) {
    echo "Accès refusé";
} else {
    echo "Accès autorisé";
}
```

Dans cet exemple, `$isMinor` est défini comme l'inverse de `true`, ce qui signifie qu'il est `false`. Par conséquent, l'accès est autorisé.

{% hint style="info" %}
Chaque opérateur effectue une action spécifique sur ses opérandes et retourne un résultat, permettant de construire des expressions complexes et de contrôler le flux d'un programme.
{% endhint %}
