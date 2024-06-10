# Les tableaux en PHP

Un tableau PHP, appelé plus communément Array est une variable composée de multiples valeurs qui peuvent être organisées, si on le souhaite, par un système de clé.​

Il est important de comprendre qu’une variable de type Array ne peut être affichée globalement via un simple « echo », mais nécessitera l’utilisation des clés citées précédemment​

Dans le cas où aucune clé n’a été définie, un système de clé ordonnée par sa position est alors utilisé, en commençant par l’index 0, suivi de la clé 1, 2, 3 … On utilisera alors les boucles.​

## Déclarer un tableau <a href="#declarer-un-tableau" id="declarer-un-tableau"></a>

Pour déclarer un nouveau tableau, deux méthodes (syntaxes) existent et peuvent être utilisée.​

```php
// Méthode n°1
$array = array();

// Méthode n°2
$array = [];
```

## Composition d’un tableau​ <a href="#composition-dun-tableau" id="composition-dun-tableau"></a>

### Les tableaux indexés <a href="#les-tableaux-indexes" id="les-tableaux-indexes"></a>

```php
<?php

$monTableau = [
    "Valeur 1",
    "Valeur 2",
    "Valeur 3",
    "Valeur 4"
];
```

### Les tableaux associatifs <a href="#les-tableaux-associatifs" id="les-tableaux-associatifs"></a>

```php
<?php

$monTableau = [
    0 => "Valeur 1",
    1 => "Valeur 2",
    2 => "Valeur 3",
    3 => "Valeur 4"
]

// équivaut à

$monTableau = [
    "Clé 1" => "Valeur 1",
    "Clé 2" => "Valeur 2",
    "Clé 3" => "Valeur 3",
    "Clé 4" => "Valeur 4"
]; 
```

### Les tableaux avec quelques clés​ <a href="#les-tableaux-avec-quelques-cles" id="les-tableaux-avec-quelques-cles"></a>

```php
<?php

$monTableau = [
    "Clé 1" => "Valeur 1", // "Clé 1" => "Valeur 1"
    4,                     //  0 => 4
    true,                  //  1 => true
    "Clé 4" => "Valeur 4"  // "Clé 4" => "Valeur 4"
];
```

## Ajouter une valeur à un tableau​ <a href="#ajouter-une-valeur-a-un-tableau" id="ajouter-une-valeur-a-un-tableau"></a>

Pour ajouter une valeur à un tableau, il existe deux possibilités :​

### Méthode 1 <a href="#methode-1" id="methode-1"></a>

```php
<?php

$monTableau = [
    "John",
    "Jack",
    "Jim",
    "Jude"
];
array_push($monTableau, "Jerry");
var_dump($monTableau);
```

### Méthode 2 <a href="#methode-2" id="methode-2"></a>

```php
<?php

$monTableau = [
    "John",
    "Jack",
    "Jim",
    "Jude"
];
$monTableau[] = "Jerry";
var_dump($monTableau);
```

## Ajouter une clé et une valeur <a href="#ajouter-une-cle-et-une-valeur" id="ajouter-une-cle-et-une-valeur"></a>

Pour ajouter une clé ainsi que sa valeur à un tableau :​

```php
<?php

$monTableau = [
    "prenom"  => "John",
    "nom"     => "Doe",
    "age"     => 34,
    "taille"  => 176
];

$monTableau['equipe'] = "Lakers";
```

## Supprimer une valeur d’un tableau​ <a href="#supprimer-une-valeur-dun-tableau" id="supprimer-une-valeur-dun-tableau"></a>

```php
<?php

$monTableau = [
    "prenom" => "John",
    "nom" => "Doe",
    "age" => 34,
    "taille" => 176,
    "equipe" => "Lakers"
];

unset($monTableau["taille"]);​
```

Dans le cas d’un tableau sans clé, précisez simplement l’index.

```php
<?php

$monTableau = [
    "John",
    "Doe",
    34,
    176,
    "Lakers"
];

unset(monTableau[3]);
```

## Afficher une valeur précise d'un tableau <a href="#afficher-une-valeur-precise-dun-tableau" id="afficher-une-valeur-precise-dun-tableau"></a>

Pour afficher une valeur, il suffit alors de spécifier la clé correspondant à la valeur demandée.​

* Prenons l’exemple de la **taille** de John Doe​
* Puis de son **équipe** de basket-ball préférée​

```php
<?php

$monTableau = [
    "prenom" => "John",
    "nom" => "Doe",
    "age" => 34,
    "taille" => 176,
    "equipe" => "Lakers"
];

echo $monTableau['taille']; // affichera 176
echo $monTableau['equipe']; // affichera Lakers|
```

Nous verrons un peu plus loin que des fonctions liées aux tableaux PHP vont nous permettre d’effectuer des manipulations, ajouts, méthodes de tris, … beaucoup plus simplement que vu précédemment.​

## Les tableaux multidimensionnels​ <a href="#les-tableaux-multidimensionnels" id="les-tableaux-multidimensionnels"></a>

Un tableau multidimensionnel est un tableau ne s’arrêtant ​pas à un seul niveau de récursivité.​

Autrement dit, un tableau peut contenir un ou plusieurs tableaux, qui peuvent contenir également d’autres tableaux, qui peuvent …​ et ainsi de suite.

```php
<?php

$monArrayMulti = [
    "infos" => [
        "first_name" => "John",
        "last_name"  => "Doe",
        "children" => [
            "Jack" =>  [
                "age" => 12
            ],
            "Emily" => [
                "age" => 8
            ]
        ]
    ],
    "coords" = [
        "address"     => "12 avenue des lombards",
        "postal_code" => "10000",
        "city"        => "Troyes"
    ]
]; 
```

{% hint style="info" %}
Dans ce tableau, nous nous rendons compte de la multi-dimension apportée, avec des systèmes de sectorisation et d'héritage
{% endhint %}
