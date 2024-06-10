# Les conventions en PHP

## Les conventions de nommage PHP​ <a href="#les-conventions-de-nommage-php" id="les-conventions-de-nommage-php"></a>

| Élément       | Nommage     | Exemples                                          |
| ------------- | ----------- | ------------------------------------------------- |
| La variable​  | camelCase​  | $personneAge, $userPassword, $groupSubCategory …​ |
| La constante​ | ALL\_CAPS​  | DB\_NAME, USER\_PSEUDO, OPT\_GROUP …​             |
| La fonction​  | camelCase​  | getInfoUser(), postDataClient(), …​               |
| La classe​    | PascalCase​ | HomeController, SubProduct, AdminUser …​          |

## Les conventions liées aux tableaux​ <a href="#les-conventions-liees-aux-tableaux" id="les-conventions-liees-aux-tableaux"></a>

Afin de rendre plus lisible les données liées à un tableau PHP​. Il est préférable d'utiliser un système de convention tel que ci-dessous​ :

```php
$array = [
    "Valeur 1",
    "Valeur 2",
    "Valeur 3",
    "Valeur 4",
];

// plutôt que

$array = [ "Valeur 1", "Valeur 2", "Valeur 3", "Valeur 4" ];
```

## Les commentaires (et pas qu’en PHP !)​ <a href="#les-commentaires-et-pas-quen-php" id="les-commentaires-et-pas-quen-php"></a>

~~L’usage des commentaires ​~~ => **L’abus de commentaires** est très chaudement CONSEILLE dans l’écriture du langage PHP : ils sont préfixés de « // », « # », ou encore « /\* \*/ » si commentaires de plusieurs lignes​

* Il aide à se **repérer sur des pages** composées de beaucoup de lignes de code​
* Il permet de **définir une trame des opérations à réaliser** pour obtenir un résultat ​
* Il va **simplifier la collaboration** avec les autres développeurs !​
