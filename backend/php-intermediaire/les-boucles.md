# Les boucles

En PHP, les boucles sont utilisées pour exécuter le même bloc de code un nombre spécifié de fois. PHP fournit plusieurs types de boucles.

## Pourquoi utiliser les boucles en PHP ? <a href="#pourquoi-utiliser-les-boucles-en-php" id="pourquoi-utiliser-les-boucles-en-php"></a>

Les boucles en PHP sont essentielles pour effectuer des tâches répétitives sans avoir besoin de rédiger le même code plusieurs fois.

Que ce soit pour parcourir les éléments d'un tableau, exécuter une opération un nombre défini de fois, ou continuer l'exécution d'un bloc de code tant qu'une condition spécifiée est vraie, les boucles offrent une méthode efficace et flexible pour augmenter la productivité du développement.

Elles jouent un rôle crucial dans la manipulation de données, le traitement des formulaires, l'accès aux bases de données, et dans de nombreuses autres opérations backend, rendant le code plus propre, plus lisible, et plus facile à maintenir.

## Les types de boucles <a href="#les-types-de-boucles" id="les-types-de-boucles"></a>

Chaque type de boucle offre des caractéristiques uniques, les rendant plus adaptés à des situations spécifiques, fournissant ainsi flexibilité et efficacité dans les tâches de répétition de code.

**foreach :** Adaptée pour itérer sur chaque élément d'un tableau.

**for :** Optimal pour les scénarios où le nombre d'itérations est prédéterminé.

**do-while :** Similaire à `while`, mais assure que le bloc de code est exécuté au moins une fois.

**while :** Exécute le bloc de code tant que la condition reste vraie.

PHP fournit une gamme de boucles pour faciliter le contrôle du flux de programme, permettant l'exécution répétitive de blocs de code sous des conditions variables.

### foreach <a href="#foreach" id="foreach"></a>

La boucle `foreach` est spécialement conçue pour parcourir les éléments d'un tableau en PHP, offrant une manière simple et intuitive de traiter chaque élément individuellement. Elle est particulièrement utile pour les tableaux associatifs où chaque élément peut être accédé via sa clé et sa valeur.

La syntaxe de base est la suivante :

```php
foreach ($tableau as $valeur) {
    // Code à exécuter pour chaque élément
}
```

Pour les tableaux associatifs, vous pouvez également obtenir la clé de chaque élément :

```php
foreach ($tableau as $cle => $valeur) {
    // Code à exécuter pour chaque clé/valeur
}
```

Cette structure de contrôle simplifie grandement le parcours des tableaux, rendant le code plus lisible et facile à maintenir.

```php
$listeFruits = [
    "pomme" => 150,
    "banane" => 120,
    "cerise" => 10
];

foreach ($listeFruits as $fruit => $poids) {
    echo "Le poids de la $fruit est $weight grammes."; 
}

// Ouput :
// Le poids de la pomme est 150 grammes.
// Le poids de la banane est 120 grammes.
// Le poids de la cerise est 10 grammes.
```

### for <a href="#for" id="for"></a>

La boucle `for` en PHP est un moyen efficace de répéter des instructions un nombre spécifique de fois. La syntaxe de base `for (initialisation; condition; incrémentation)` permet de démarrer avec une valeur initiale, de continuer la boucle tant que la condition est vraie, et d'incrémenter ou modifier la valeur à chaque itération.

Cette structure permet de parcourir des tableaux indexés numériquement ou d'effectuer des tâches répétitives précises.

Voici un exemple simple :

```php
for ($i = 0; $i <= 10; $i++) {
    echo "Ligne numéro $i\n";
}
```

Dans cet exemple, le script affichera les numéros de ligne de 0 à 10, démontrant comment une boucle `for` peut être utilisée pour générer des séquences répétitives de manière concise et claire.

### do-while <a href="#do-while" id="do-while"></a>

La boucle `do-while` en PHP est similaire à la boucle `while`, mais avec une différence clé : dans une boucle `do-while`, le corps de la boucle est exécuté au moins une fois avant que la condition ne soit testée.

Cela signifie que le code à l'intérieur de la boucle `do-while` s'exécutera toujours au moins une fois, même si la condition est fausse dès le début. La syntaxe générale est `do { /* instructions */ } while (condition);`.

```php
do {
    echo "Ceci est exécuté au moins une fois.";
} while (false);
```

{% hint style="info" %}
C'est un choix efficace quand vous voulez que le code s'exécute au moins une fois et ensuite, continue à s'exécuter tant que la condition spécifiée est vraie.
{% endhint %}

### while <a href="#while" id="while"></a>

Les boucles `while` sont utiles lorsque vous ne savez pas à l'avance combien de fois vous devez exécuter un bloc de code. Par exemple, lire des lignes d'un fichier jusqu'à atteindre la fin.

Dans cet exemple, la boucle continue de s'exécuter tant que `$count` est inférieur ou égal à 5. À chaque itération, la valeur actuelle de `$count` est imprimée, puis `$count` est incrémenté de 1. Lorsque `$count` devient 6, la condition devient fausse, et la boucle se termine.

```php
$count = 1;
while ($count <= 5) {
    echo "Le nombre est : $count \n";
    $count++;
}
```

La syntaxe d'une boucle `while` en PHP est la suivante :

```php
while (condition) {
    // code à exécuter
}
```

Dans la boucle `while`, la condition est évaluée avant l'exécution du corps de la boucle. Si la condition évalue à `true`, le corps de la boucle est exécuté. Cela est répété tant que la condition reste vraie. Si la condition évalue à `false`, la boucle est terminée et le contrôle passe à l'instruction immédiatement suivante de la boucle.

{% hint style="info" %}
La boucle `while` en PHP est une instruction de contrôle de flux qui permet d'exécuter du code de manière répétée sur la base d'une condition booléenne donnée. La boucle `while` peut être considérée comme une instruction `if` répétitive.
{% endhint %}
