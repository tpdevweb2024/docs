# Les sessions et les cookies

## Les sessions PHP

### Objectifs des sessions PHP

Les sessions en PHP constituent le moyen de **conserver des variables sur les différentes pages de votre application** / site web. Elles sont associées à l'utilisateur actuel, et il n'est donc pas nécessaire de les passer au travers d'un formulaire pour les "emmener avec nous". Véritable alternative, et même plus que ça, il s'agit de la solution idéale à utiliser dans de multiples cas de figures.

Une session correspond à une manière de stocker des données de chacun des utilisateurs visiteurs, en utilisant un identifiant de session unique. La quantité de données stockées est illimité.

Les identifiants de session sont envoyés au navigateur via des cookies de session et vont servir à récupérer les données actuelles de la session.

### Cas d'utilisation des sessions

Parmi les cas dans lesquels nous utiliserons les sessions, nous pouvons retrouver :

* Faire transiter un mot de passe ou une donnée sensible d'une page à l'autre
* Récupérer des informations entre deux pages non consécutives
* Garder un contenu de variable en "mémoire" sans le stocker dans un cookie (plus sécurisé)
* Mettre en place un système d'authentification global dans une application, ce qui rendra limité l'accès à certaines pages

### Comment ça marche ?

A la différence des cookies, les variables de sessions sont quant à elles stockées côté serveur ! Ce qui rend la **confidentialité des données nettement plus efficace et mieux sécurisée.**

Nous retiendrons **3 étapes essentielles** dans la mise en place de variables de session :

1. Un visiteur se connecte sur votre site, **ce qui va lui créer une session unique**, et attribuée par le serveur. Ce numéro une simple "random string" du style b76hdvejdhgdgev656dedey612hbhd, **il s'agit d'un « ID de session » (PHPSESSID)**. PHP le transmet automatiquement de page en page, en utilisant un cookie.
2. Une fois la session générée, on va alors **pouvoir stocker des datas au sein de cette superglobale**, tout un tas d'informations en tout genre. On peut alors créer une variable  $\_SESSION\['firstName']  qui contiendra le prénom du visiteur,  $\_SESSION\['loginDate']  qui contient le datetime de sa connexion, ... Le serveur conservera alors ces variables même lors de nos changements de page, il **suffira alors sur chaque page d'appeler les informations** stockées que l'on souhaite.
3. Lorsque le visiteur se déconnecte de votre site, ou lorsqu'il ferme son navigateur (enfin pas tout à fait), **la session est alors fermée** et PHP va se charger de supprimer les données associées. Pour revenir à la fermeture du navigateur, PHP n'est (heureusement pour notre vie privée) pas capable de savoir si nous avons fermé Chrome ou Firefox, alors **un système de Timeout a été pensé** pour, au delà d'un délai définit par le serveur, déconnecté l'utilisateur par sécurité.

Egalement, deux fonctions essentielles à connaître :

* **session\_start()**, pour démarrer une session
* **session\_destroy()**, pour supprimer ou détruire une session en cours (démarrée)

### Usage des sessions en PHP

Nous l'avons dit précédemment, les informations de session sont stockées au sein de la superglobale $\_SESSION, qui est comme souvent en PHP un tableau prêt à accepter tous types de valeurs :

* string
* int
* float
* bool
* array
* ...

La syntaxe pour définir des valeurs au sein de la variable est donc identique à l'intégration de données au sein d'un tableau, à savoir :

```php
// index.php
$_SESSION['userFirstName'] = "John";
$_SESSION['userLastName'] = "Doe";
```

Pour afficher ces données, il est alors facile d'utiliser la clé demandée :

```php
// user.php
echo $_SESSION['userFirstName']; // Nous affichera John
```

> Bon à savoir : **Une session se doit toujours d'être générée afin de pouvoir stocker et afficher des éléments** contenus dans $\_SESSION, c'est donc à ce moment que nous allons utiliser notre fonction session\_start(). Il faut absolument appelé session\_start() avant même le début du chargement de votre page (tout en haut de la page), soit avant le doctype et la déclaration de la balise html.

```php
// index.php
session_start();
$_SESSION['userFirstName'] = "John";
$_SESSION['userLastName'] = "Doe";
```

```php
// user.php
session_start();
echo $_SESSION['userFirstName']; // Nous affichera John
```

#### Créer des variables de session

```php
index.php
<?php
// On démarre la session en haut de page
session_start();

// On déclare des variables
$_SESSION['userFirstName'] = 'John';
$_SESSION['userLastName'] = 'Doe';
$_SESSION['userAge'] = 32;
?>

<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8" />
        <title>Index page</title>
    </head>
    <body>
    <p>
        Coucou <?php echo $_SESSION["userFirstName"]; ?> !<br />
        Tu es sur la page index.php. Cliques sur le lien ci-dessous pour accéder à une autre page.
    </p>
    <p>
        <a href="autre-page.php">Lien vers une autre page</a><br />
    </p>
    </body>
</html>
```

```php
autre-page.php
<?php
session_start(); // On démarre la session
?>

<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8" />
        <title>Une autre page</title>
    </head>
    <body>
    <p>Re-bonjour !</p>
    <p>
        Coucou <?php echo $_SESSION['userFirstName'] . ' ' . $_SESSION['userLastName']; ?> !<br />
        Et tu as exactement <?php echo $_SESSION['userAge']; ?> ans.
    </p>
    </body>
</html>
```

#### Supprimer des variables de session

Pour supprimer une seule variable de session, la superglobale étant un tableau, il suffit alors d'appeler la fonction unset()

```php
unset($_SESSION['userAge']); // Supprimera la variable age de la session en cours
```

Pour supprimer une session de manière globale, c'est à dire le tableau $\_SESSION et toutes ses infos

```php
session_start();
session_destroy();
```

> Il est très important de ne pas oublier d'initialiser une session pour pouvoir la supprimer, sans quoi PHP ne saurait pas quel élément il doit lui même retirer de son serveur.

Nous reverrons également les variables de session lorsque nous évoquerons l'authentification d'utilisateurs au sein d'une application web.

## Les cookies PHP

La gestion des cookies est quelque peu similaire à l'utilisation des sessions, à quelques petites différences.

1. La première étant, comme évoqué un peu plus tôt, le **stockage s'effectuant côté client et non côté serveur**.
2. La **conservation des cookies et sa durée de stockage**, selon la façon selon laquelle l'utilisateur travaille avec son navigateur.
3. La **visibilité des données** contenus à l'intérieur des cookies.
4. La **quantité de données** d'un cookie est naturellement limitée, puisque basée sur l'idée de stocker côté client. (nous parlons de quelques Ko)

Mais c'est quoi un cookie ? C'est avant tout un petit gâteau ! mais pas seulement ... C'est un **fichier stocké dans l'ordinateur client** (internaute), et qui nous permettra dès sa venue suivante sur notre site, de récupérer un contenu précédemment stocké.

### Objectifs des cookies PHP

Les cookies ont très souvent une mauvaise image, les associant à du remarketing, ou encore de la force de vente poussée à l'extrême. Et les réglements mis en place ces dernières années laissent à supposer qu'il s'agit de fichiers malveillants.

Ceci n'est pas tout à fait vrai. Même si beaucoup de sites se servent de cookies pour mémoriser vos habitudes de navigation, ou encore vos produits recherchés, préférés ... **Les cookies peuvent aussi avoir un aspect fonctionnel**, il faut d'ailleurs savoir les dissocier pour entrer en règlementation avec le RGPD et la CNIL.

> Par convention, nous **associerons plutôt une seule valeur dans un seul cookie**.

### Fonctionnement des cookies

Comme vu lors de la déclaration de variable, un cookie possède un nom ainsi qu'une valeur. Par exemple, **le cookie pseudo pourrait avoir la valeur johndoe**. Nous viendrons ajouter alors un troisième élément INDISPENSABLE : sa durée de validité, qui est en réalité un datetime au format timestamp UNIX.

#### Ecrire un cookie

Pour écrire (déclarer) un cookie, c'est super simple :

```php
<?php 
    // On créé le cookie avec la fonction setcookie(), 
    // suivie de 3 paramètres (nom, valeur et timestamp)

    // Dans notre exemple : time() + 365*24*3600 va créé une validité d'un an
    setcookie('pseudo', 'johndoe', time() + 365*24*3600); 
?>
```

Analysons quelque peu cette fonction setcookie() :

```php
setcookie ( 
    string $name , // le nom du cookie
    string $value = "" ,  // la valeur (facultatif)
    int $expires = 0 , // sa date d'expiration
    string $path = "" , // le dossier (facultatif) sur lequel le cookie sera appelé
    string $domain = "" , // Le domaine  (facultatif) sur lequel le cookie est fonctionnel
    bool $secure = false , // L'utilisation du cookie en mode https uniquement
    bool $httponly = false // L'utilisation des cookies que sur requetes http (conseillé)
) : bool
```

Ré-écrivons alors notre création de cookie :

```php
setcookie('pseudo', 'johndoe', time() + 365*24*3600, "", "", false, true);
```

Pour afficher un cookie :

```php
echo $_COOKIE['pseudo']; // Nous donnera johndoe
```

#### Pour modifier un cookie

Un simple appel nouveau de setcookie permettra d'écraser le cookier précédent :

```php
// Nous réduisons une expiration à 230 jours plus loin qu'aujourd'hui
setcookie('pseudo', 'johndoe', time() + 230*24*3600, "", "", false, true);
```

#### Pour supprimer un cookie

Tout comme pour créer ou modifier un cookie, pour le supprimer nous ferons un setcookie(), et oui c'est dingue ! Passons lui simplement cette fois ci une valeur négative et le navigateur comprendra ainsi que ce cookie n'est plus actif, et donc le supprimera, c'est magique non ?

```php
setcookie('pseudo', '', time()-3600, "", "", false, false);
```
