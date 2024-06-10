# Include et require

En PHP, `include` et `require` sont des instructions utilisées pour insérer le contenu d'un fichier PHP dans un autre durant l'exécution. La principale différence entre les deux réside dans leur comportement lorsqu'une erreur survient.

Utilisant `include`, le script émettra un avertissement si le fichier spécifié ne peut pas être trouvé, mais il continuera à exécuter le reste du script.

D'autre part, `require` produira une erreur fatale lorsque le fichier n'existe pas ou est illisible, arrêtant immédiatement l'exécution du script.

Il existe également des variantes `include_once` et `require_once` qui assurent qu'un fichier est inclus uniquement une fois, évitant une inclusion ou une exigence répétitive.

## Différences entre include et require​ <a href="#differences-entre-include-et-require" id="differences-entre-include-et-require"></a>

Les principales différences entre `include` et `require` en PHP sont résumées ci-dessous :

* **Comportement en cas d'erreur :** Si le fichier ciblé est introuvable ou illisible :
  * `include` génère un avertissement (`E_WARNING`), mais le script continue de s'exécuter.
  * `require` produit une erreur fatale (`E_COMPILE_ERROR`) et arrête l'exécution du script immédiatement.
* **Utilisation :**
  * `include` est idéal pour les fichiers optionnels, dont l'absence n'interrompt pas le fonctionnement global du script.
  * `require` est utilisé pour les fichiers essentiels, sans lesquels l'exécution du script ne peut se poursuivre.

## Utilisation de include et require <a href="#utilisation-de-include-et-require" id="utilisation-de-include-et-require"></a>

### include & include\_once​ <a href="#include-and-include_once" id="include-and-include_once"></a>

`include` et `include_once` sont deux instructions utilisées en PHP pour insérer le contenu d'un fichier dans un autre fichier avant que le serveur n'exécute celui-ci. Voici un aperçu de leur utilisation :

Utilisez `include` lorsque vous souhaitez inclure et exécuter le contenu d'un fichier spécifié. Si le fichier n'est pas trouvé, PHP génère un avertissement, mais le script continue de s'exécuter. Cela est utile pour inclure des fichiers tels que des en-têtes, des pieds de page, ou des éléments de menu qui sont utilisés sur plusieurs pages, mais dont l'absence n'arrête pas l'exécution du script.

```php
<?php
    include 'header.php';
?>
```

La directive `include_once` fonctionne de la même manière que `include`, mais elle vérifie d'abord si le fichier spécifié a déjà été inclus. _**Si c'est le cas, il ne sera pas inclus de nouveau. Cela évite notamment les problèmes de redéfinition de fonctions, classes ou variables si le même fichier est inclus plusieurs fois.**_

```php
<?php
    include_once 'init.php';
?>
```

Utilisez `include_once` principalement pour inclure des fichiers qui contiennent des déclarations de fonctions, des classes, ou des instructions d'initialisation qui ne doivent être exécutées qu'une seule fois.

### require & require\_once <a href="#require-and-require_once" id="require-and-require_once"></a>

La directive `require` en PHP est similaire à `include`, mais elle est plus stricte : si le fichier spécifié est introuvable, elle provoque une erreur fatale et arrête l'exécution du script. Cela la rend utile pour inclure des fichiers essentiels au fonctionnement de l'application.

```php
<?php
require 'config.php';
?>
```

`require_once` agit de la même manière que `require`, mais comme `include_once`, elle vérifie si le fichier a déjà été inclus et, dans ce cas, ne le réinclut pas.

Elle est particulièrement utile pour les fichiers contenant des déclarations de classes ou des fichiers d'initialisation qui ne doivent être exécutés qu'une seule fois.

```php
<?php
require_once 'setup.php';
?>
```

Tout comme `include_once`, utiliser `require_once` est une bonne pratique lorsque vous avez besoin de vous assurer que le fichier est inclus une seule fois pour éviter les erreurs de redéfinition.

## Cas pratique d'utilisation <a href="#cas-pratique-dutilisation" id="cas-pratique-dutilisation"></a>

### **Intégration des fichiers partiels dans une page PHP**

L'utilisation de `include` ou `require` pour intégrer des fichiers partiels, comme les en-têtes (headers) et pieds de page (footers), est une pratique courante qui aide à structurer et à maintenir le code plus facilement. Voici comment vous pouvez procéder dans une page `index.php`:

```php
<?php
// Inclut le fichier d'en-tête
include "partials/header.php";

// Votre contenu principal ici
echo "<h1>Bienvenue sur ma page d'accueil</h1>";

// Inclut le fichier de pied de page
include "partials/footer.php";
?>
```

En utilisant `include`, si le fichier spécifié n'est pas trouvé, PHP générera un avertissement mais continuera l'exécution du script.

**Si vous souhaitez arrêter l'exécution du script lorsque le fichier n'est pas trouvé**, utilisez `require` à la place de `include`.

```php
<?php
// Inclut le fichier d'en-tête
require "partials/header.php";

// Votre contenu principal ici
echo "<h1>Bienvenue sur ma page d'accueil</h1>";

// Inclut le fichier de pied de page
require "partials/footer.php";
?>
```

{% hint style="info" %}
Cette méthode assure que vos pages web restent cohérentes en termes de présentation tout en facilitant la maintenance de vos fichiers d'en-tête et de pied de page puisque tout changement dans ces fichiers se répercute automatiquement sur toutes les pages qui les incluent.
{% endhint %}
