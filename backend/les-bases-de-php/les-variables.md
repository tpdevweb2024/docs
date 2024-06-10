# Les variables

## C'est quoi une variable ? <a href="#cest-quoi-une-variable" id="cest-quoi-une-variable"></a>

### Définition et bonnes pratiques <a href="#definition-et-bonnes-pratiques" id="definition-et-bonnes-pratiques"></a>

Une variable sert à stocker une info de façon temporaire. et n’existe que durant le temps de l’exécution d’un script (page).​

Selon la documentation PHP :​

* les variables démarrent par le signe dollar ($) et sont suivies d’une lettre ou d’un \_ (underscore), et ne démarrent pas par un chiffre ni un tiret !​
* On y associe ensuite le nom souhaité de la variable​
* Le nom est sensible à la casse ($mavariable est différent de $maVariable)​
* Il ne faut surtout pas utiliser la variable protégée $this pour en créer une nouvelle, puisque comme son nom l'indique elle est "protégée​"

### Pourquoi utiliser les variables ? <a href="#pourquoi-utiliser-les-variables" id="pourquoi-utiliser-les-variables"></a>

* Une variable peut être assimilée à un carton sur lequel est ​collée une étiquette portant un nom (le nom de la variable). ​
* A l'intérieur de ce colis se trouve un nombre de chaises (la valeur) d’un type précis (le type de la variable). ​
* Quand nous souhaitons obtenir cette valeur (nombre de chaises), nous ne nous adressons pas directement à elle mais nous y faisons référence en sélectionnant le carton par son nom, celui qui est sur l’étiquette.​

<figure><img src="https://doc.tpdev.fr/~gitbook/image?url=https%3A%2F%2F3371530675-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-x-prod.appspot.com%2Fo%2Fspaces%252F3EOGBDKYVP8bySgXKz0o%252Fuploads%252FUHnvd2GdTNwNXE8f5Htm%252FPHP%2520-%2520Variables.png%3Falt%3Dmedia%26token%3D229278e3-21f5-43cf-a527-3d636978770f&#x26;width=768&#x26;dpr=4&#x26;quality=100&#x26;sign=55a9dfc3b05dda463096e3e5ce2525aebb22865060d1e0a857cf6f27cd33fa45" alt=""><figcaption></figcaption></figure>

Une variable en PHP est un espace de mémoire nommé dans lequel vous pouvez stocker des valeurs. Ces valeurs peuvent être de différents types, comme des chaînes de caractères, des nombres entiers, des nombres décimaux, des tableaux, etc.

### Les différents types de variables​ <a href="#les-differents-types-de-variables" id="les-differents-types-de-variables"></a>

* string (**string**) : Les chaînes de caractères​
* integer (**int**) : Les nombres entiers​
* float (**float**) : Les nombres décimaux​
* bool (**bool**) : Un booléen qui nous retournera true ou false​
* **double** : Alias de float​ ​
* **array** : Utilisation des tableaux​
* **object** : Utilisation des propriétés

### **Déclarer une variable**

Créons ensemble un personnage​

* Nous définissons ensemble une variable **$prenom** ayant pour valeur **« John »​**
* Suivie d’une variable **$age** avec pour valeur **34**.​

Nous allons maintenant afficher ces deux variables au sein d’un paragraphe.​

```php
<?php 
$prenom = "John";
$age = 34;

<p>Le personnage <?php echo $prenom; ?> a <?php echo $age; ?> ans.
<p>Le personnage <?= $prenom ?> a <?= $age; ?> ans.

// Ce qui donnera : "Le personnage John a 34 ans.
```

### **Écraser la valeur d'une variable**

* Le fait de déclarer de nouveau une variable avec la même taxonomie lui attribuera d’office une nouvelle valeur.​
* Prenons l’exemple d’une variable $var qui par défaut a une valeur de « Lorem » et attribuons lui ensuite la valeur « Ipsum »​
* Utilisons la fonction echo pour afficher les résultats​

```php
<?php

$var = "Lorem"; 
echo $var; // Output : "Lorem" 
$var = "Ipsum"; 
echo $var; // Output : "Ipsum" 
```

### **Concaténer deux variables**

Pour ajouter du contenu supplémentaire à une variable, il suffit de les séparer par un simple . (point).​

{% hint style="warning" %}
**ATTENTION** : la concaténation ne comprends pas l’espace qui est lui-même considéré comme un caractère HTML.​
{% endhint %}

```php
<?php 

$var1 = "Tant va la cruche à l'eau";
$var2 = "qu'à la fin elle se brise";

$res = $var1 . $var2; 
var_dump($res);
// Output : 'Tant va la cruche à l'eauqu'à la fin elle se brise'

$res = $var1 . " " . $var2;
var_dump($res) ; 
// Output : 'Tant va la cruche à l'eau qu'â la fin elle se brise'
```

## Analyse des variables PHP <a href="#analyse-des-variables-php" id="analyse-des-variables-php"></a>

Lorsqu'une chaîne de caractères est spécifiée entre guillemets doubles ou en Heredoc, les variables qu'elle contient sont interprétées.

Il existe 2 types de syntaxes : une simple et une complexe. La syntaxe simple est la plus commune et la plus pratique. Elle fournit une façon d'embarquer une variable, une valeur de tableau, ou une propriété d'objet dans une chaîne de caractères avec un minimum d'effort.

La syntaxe complexe se reconnaît à l'utilisation d'accolades autour de l'expression.

```php
<?php

$juice = "pomme";
echo "Il a bu du jus de $juice." . PHP_EOL;

// Non souhaité. "s" est un caractère valide pour un nom de variable, 
// ainsi ceci fait référence à $juices, et non à $juice.
echo "Il a bu du jus constitué de $juices." . PHP_EOL;
// Spécifiez explicitement la fin du nom de la variable en plaçant 
// la référence entre accolades.
echo "Il a bu du jus constitué de ${juice}s.";
```

## Les variables constantes <a href="#les-variables-constantes" id="les-variables-constantes"></a>

* Une constante est un nom / identifiant unique qui représente une valeur simple. ​
* Cette valeur ne peut jamais être modifiée durant l'exécution du script (sauf les constantes magiques). ​

Par convention, les constantes sont toujours en majuscule.​

```
<?php

define("MA_CONSTANTE", "valeur");

var_dump (MA_CONSTANTE);
```
