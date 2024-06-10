# Les formulaires

## La méthode GET

### Passage de paramètres par l'URL

Nous avions vu précédemment la méthode GET sur laquelle nous allons revenir quelques instants. Cette méthode consistait à faire passer dans notre URL des paramètres, qui pourraient ainsi être transportés d'une page à l'autre, au travers d'un paramètre et de sa valeur.

> Exemple, nous pouvons récupérer un prenom de cette manière à partir de cette URL : [http://localhost:8000/index.php?prenom=Alphonse](http://localhost:8000/index.php?prenom=Alphonse)

```php
$prenom = $_GET['prenom'];
echo $prenom;
```

Rappellons par cette occasion que ce script fonction, mais qu'il est dangereux en termes de sécurité, pour le vérifier, **testez simplement de taper cette url :**&#x20;

```php
http://localhost:8000/index.php?prenom=<script>alert("hacking ok !")</script>
```

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

Voyez par vous même le résultat, **vous obtenez un superbe script JS qui va vous afficher Hacking Ok !**, c'est pas très sécurisé n'est-ce pas ?

Cette faille, **appelée communément faille XSS**, pourrait permettre de récupérer des cookies d'un autre utilisateur, et dans le cas de l'utilisation d'un utilisateur malveillant, de pourquoi pas obtenir une porte d'entrée à l'accès à des fichiers en lien avec la base de données de notre app, nous reviendrons un peu plus loin sur les différentes failles PHP.

### Passage de paramètres GET depuis un formulaire

Et oui, la méthode GET ne s'arrête pas à l'utilisation de paramètres par l'URL, **mais peut également passer différents arguments par le biais d'un formulaire**, qui serait lui même rempli par nos utilisateurs et utilisatrices de notre site web.

Pour utiliser cette méthode (method), voici l'exemple d'un formulaire créé en HTML, et envoyant des valeurs via URL :

```markup
<form>
    <input name="prenom">
    <input name="age">
    <input type="submit" value="Envoyer">
</form>
```

En saisissant les valeurs John et 24, vous obtiendrez alors une redirection vers cette même page et avec nos deux valeurs stockées dans nos paramètres tel que : [http://localhost:8000/index.php?prenom=John\&age=24](http://localhost:8000/index.php?prenom=John\&age=24)

Habillons alors quelque peu ce formulaire basique, même si nous obtiendrons le même résultat :

```markup
<form action="" method="GET">
    <input name="prenom">
    <input name="age">
    <input type="submit" value="Envoyer">
</form>
```

Regardons ensemble ce qui a changé :

> L'attribut action appliqué au formulaire est vide, ce qui lui donne l'ordre de **rediriger sur la page en cours** (la rafraichir si vous préférez), mais avec la méthode définie dans **l'attribut action, dans notre cas GET**

Ainsi il est alors possible de rediriger un utilisateur vers une autre page, avec des paramètres spécifiques. Exemple :

```markup
<form action="newPage.php" method="GET">
    <input name="prenom" value="John">
    <input name="age" value="24">
    <input type="submit" value="Envoyer">
</form>

<!-- Ce formulaire nous renverra vers la page -->
<!-- http://localhost:8000/newPage.php?prenom=John&age=24 -->
```

## La méthode POST

Dans le cas de la méthode POST, c'est un peu différent, les valeurs ne transitent pas par le biais de l'URL, mais de manière masquée (à ne pas confondre avec cryptée). Toutes ces valeurs sont alors stockés à l'intérieur d'un tableau PHP appelé $\_POST.

Testions l'envoi d'un formulaire PHP via $\_POST, puis analysons ce tableau, ainsi écrivez simplement :

```php
<?php 
    // Ce script va permettre de n'afficher le var_dump que si le tableau $_POST n'est pas vide
    if(!empty($_POST)){ 
        var_dump($_POST);
    } 
?>
<form action="" method="POST">
    <input name="prenom" value="John">
    <input name="age" value="24">
    <input type="submit" value="Envoyer">
</form>
```

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

> Au même titre que la méthode GET, il vous faudra être très attentifs aux différentes failles se présentant à vous. Ainsi, l'utilisation de la **fonction htmlspecialchars() est vivement conseillée**.

## Le traitement des champs

### Les champs classiques

Les champs de type texte, email, password, date et de type textarea sont deux champs très simples à gérer, ils ressortent une valeur de type string. Il conviendra toutefois de vérifier les contenus envoyés, malgré la présence du type dans votre formulaire HTML, pensez à l'utilisateur malveillant ...

Nous utiliserons par exemple la fonction filter\_var pour l'adresse email, et nous vérifierons le format de date envoyée pour vérifier sa correspondance en timestamp UNIX. N'hésitez pas également à effectuer un trim() sur chacun des champs.

```php
// filter_var() : fonction visant à vérifiant si il s'agit d'une adresse email valide
$email = filter_var($_POST['email'], FILTER_VALIDATE_EMAIL);
if(!$email){
    // CODE A EXECUTER SI IL NE S'AGIT PAS D'UNE ADRESSE EMAIL

}
```

```php
// trim() : fonction visant à supprimer les espaces inutiles d'une chaine de caractères
$chaine = " Mon texte avec un espace avant et un après ";
$res = trim($chaine);
echo $res;
```

Enfin, nous pouvons cumuler les fonctions PHP au sein de notre propre fonction sanitize :

```php
function sanitizeEmail($email){
    $email = trim($email);
    $email = filter_var($email, FILTER_VALIDATE_EMAIL);
    return $email;
}

var_dump( sanitizeEmail(" monadresse@moi.fr") ); 
// Nous sortira monadresse@moi.fr sans l'espace manquant en début de chaîne 

var_dump( sanitizeEmail("monadresse@moi") ); 
// Nous sortira un booléen de type false car adresse non valide
```

### Les champs plus complexes

Certains types de champs sont plus délicats à gérer, par exemple :

* le champs select
* le champs radio
* le champs checkbox
* le champs file

Voyons ensemble comment gérer ces champs si particuliers.

#### Select

Le champs Select possède une véritable particularité, à savoir l'éventuelle sélection multiple.

Prenons l'exemple d'un champs select simple :

```php
<?php 
    // Ce script va permettre de n'afficher le var_dump que si le tableau $_POST n'est pas vide
    if(!empty($_POST)){ 
        var_dump($_POST);
        // Dans ce cas le select nous sortira une valeur de type string et ayant pour valeur : 1 OU 2 OU 3
    } 
?>
<form action="" method="POST">
    <select name="selectInput">
        <option value="1">1</option>
        <option value="2">2</option>
        <option value="3">3</option>
    </select>
    <input type="submit" value="Envoyer">
</form>
```

Mais dans un champs select multiple :

```php
<?php 
    // Ce script va permettre de n'afficher le var_dump que si le tableau $_POST n'est pas vide
    if(!empty($_POST)){ 
        var_dump($_POST);
        // Dans ce cas le select nous sortira un tableau composé des valeurs selectionnées
    } 
?>
<form action="" method="POST">
    <select multiple="multiple" name="selectInput[]"> <!-- Remarquez les [] qui indiquent un array -->
        <option value="1">1</option>
        <option value="2">2</option>
        <option value="3">3</option>
    </select>
    <input type="submit" value="Envoyer">
</form>
```

#### Radio

Un champs radio est un champs, la plupart du temps avec de multiples réponses **dont une seule est cochable**. Pour qu'un utilisateur ne puisse cocher qu'une seule valeur, l'ensemble des boutons radio proposés se doivent d'avoir le même nom.

Aussi **il est conseillé de pré-cocher une des valeurs** afin de s'assurer qu'au moins une valeur sera attribué à ce champs, et de façon à ne recevoir aucun contenu $\_POST vide.

Voyons en détail la soumission d'un champs radio :

```php
<?php 
    // Ce script va permettre de n'afficher le var_dump que si le tableau $_POST n'est pas vide
    if(!empty($_POST)){ 
        var_dump($_POST);
        // Dans ce cas, si le choix n'est pas changé, $_POST['gender'] nous sortira "M"
    } 
?>
<form action="" method="POST">
    <input type="radio" name="gender" value="M" checked>Homme
    <input type="radio" name="gender" value="F">Femme
    <input type="submit" value="Envoyer">
</form>
```

> Bon à savoir : Si aucun des deux boutons radio n'était pré coché et que l'on soumet le formulaire, **$\_POST\["gender"]** nous sortirait une erreur de type **undefined**, d'où l'intérêt du pré-coché

#### Checkboxes

Assez similaire aux boutons radio, les checkboxes ont l'avantage de pouvoir capter plusieurs valeurs au sein d'une même variable, tout cela sous un format string ou array selon les cas de figures.

Tout comme nous l'avons vu avec les select, il est essentiel, dans le cas des checkboxes, de définir le nom des champs proposés identiques, et avec des crochets \[], afin de permettre à PHP de composer un nouveau tableau avec les valeurs captées.

Exemple d'un formulaire avec checkboxes multiples :

```php
<?php
    // Ce script va permettre de n'afficher le var_dump que si le tableau $_POST n'est pas vide
    if(!empty($_POST)){ 
        var_dump($_POST);
        // Dans ce cas, un tableau sera constitué avec les valeurs cochées
        // Dans le cas où aucune valeur n'est cochée, alors le tableau ne sera pas créé
    } 
?>
<form action="" method="POST">
    <input type="checkbox" name="color[]" value="Blue">Bleu
    <input type="checkbox" name="color[]" value="Green">Vert
    <input type="submit" value="Envoyer">
</form>
```

> Nous verrons un peu plus loin comment anticiper les valeurs laissées vide, qui pourraient nous entrainer des erreurs qui en réalité seraient évitables.

## L'upload de fichiers

> Le champs file est probablement **le plus vulnérable aux attaques et aux failles** de sécurité d'une appli web.

Nous allons donc détailler toutes les étapes qui vont nous permettre de vérifier si le ou les fichiers soumis lors d'un upload sont bien autorisés à être télécharger sur le serveur.

Concernant la partie html, voici le code à écrire :

```php
<?php
    if(!empty($_FILES)){ 
        var_dump($_FILES);
    } 
?>
<form action="" method="post" enctype="multipart/form-data">
    <input type="file" name="myFile">
    <input type="submit" value="Envoyer">
</form>
```

> Remarquez l'ajout d'un attribut **enctype** ayant pour valeur **multipart/form-data**, sans cet attribut : pas d'upload ! Cet attribut garantit que les données du formulaire sont codées en tant que données MIME en plusieurs parties - ce qui est nécessaire pour uploader de grandes quantités de données binaires telles que des fichiers.

Dans le traitement PHP, nous allons utiliser **la variable superglobale $\_FILES**, alors regardons ensemble ce que donne un var\_dump d'un fichier soumis :&#x20;

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

Encore une fois, PHP a transformé dans un format tableau toutes les infos correspondant au fichier envoyé, parmi les infos intéressantes :

* **sa taille**
* **son nom**
* **son type**
* un champ error, qui nous indique si le fichier a bien été uploadé, et n'a pas été recalé par le serveur PHP
* _un nom temporaire sur le serveur, il nous servira un peu plus tard **vous verrez** !_

> Il va donc falloir maintenant vérifier toutes ces informations afin de **s'assurer dans la bienveillance de ce fichier dont on ne connait rien**.

### On passe à l'action !

> Traitons ensemble notre premier formulaire ! Et pour cela créons ensemble un dossier de projet à la racine de notre www de Wamp (ou équivalent)

Concernant la structure de notre projet, nous allons la définir ainsi :

```
projet-upload
└─  📂 uploads/
└─  📃 verify.php  
└─  📃 index.php
```

Créons ensemble notre fichier index.php, il contiendra le formulaire d'upload de notre fichier :

```php
// index.php
<form action="verify.php" method="post" enctype="multipart/form-data">
    <input type="file" name="uploadFile">
    <input type="submit" value="Uploader mon fichier" name="submited">
</form>
```

Avant tout allons faire un petit tour sur la bible du développeur : le MDN ! [https://developer.mozilla.org/fr/docs/Web/HTML/Element/Input/file](https://developer.mozilla.org/fr/docs/Web/HTML/Element/Input/file)

> Que nous dit-on sur les inputs de type "file" ?

On peut d'abord remarquer l'attribut "accept", qui définiera le type de fichier attendu, il permettra à vos utilisateurs de comprendre les extensions autorisées au moment de la saisie dans leur OS. Ajoutons alors l'attribut **accept**, et nous accorderons **les fichiers de type image, par exemple les .jpg, .jpeg, .png, .svg, et .gif**.

Ainsi les fichiers de type PDF par exemple se verront grisonnés, et non pas refusés, pour les refuser, nous le ferons durant le traitement en PHP.

```php
// index.php
<form action="verify.php" method="post" enctype="multipart/form-data">
    <input type="file" name="uploadFile" accept=".jpg, .jpeg, .png, .gif, .svg">
    <input type="submit" value="Uploader mon fichier" name="submited">
</form>
```

> D'autres attributs existent tel que capture, qui utilisera la caméra de l'appareil utilisé pour enregistrer une image ou une video. Sur un appareil fixe, le champs est alors un input file classique, testez sur mobile, votre appareil photo ou votre caméra s'activera !!!

### Le traitement en PHP

Après avoir définit notre formulaire, allons faire un petit tour dans le fichier verify.php :

```php
<?php
// verify.php
var_dump($_FILES);
```

A ce niveau, nous récupérons donc globalement toutes les infos nécessaires au traitement de l'upload, mais nous allons procéder à quelques vérifications de sécurité : 1. La soumission du formulaire est bien effectué par un POST, et surtout par le biais du formulaire prévu 2. La présence d'une erreur 3. La taille du fichier 4. L'extension autorisée ou non par votre formulaire

#### 1. La soumission du formulaire

Aussi, toujours pour des raisons de sécurité, nous renommerons le fichier envoyé par nos internautes avec un nom de fichier généré par le serveur. Préparons donc ce nom généré dès chargement de notre fichier et après avoir vérifié si le formulaire a été soumis.

```php
<?php

// POUR LA VERIFICATION DU POST
// On vérifie si la méthode utilisée est bien le POST et si le formulaire soumis est bien le bon
if ($_SERVER['REQUEST_METHOD'] == 'POST' && !empty($_POST['submited'])):

    // POUR LA PARTIE CHAINE GENEREE
    $randomString = bin2hex(random_bytes(8)) . time(); 
        // Nous y ajoutons un time() afin de s'assurer que 
        // 2 fichiers ne pourraient être envoyés à la fois avec le même nom généré
        // Nous sortira quelque chose du type : 32b8a5822ebfdf421618347845

endif;
```

#### 2. La présence d'une erreur PHP

Nous allons ensuite vérifier si notre tableau composé des éléments du fichier uploadé ne comporte pas d'erreurs

Pour cela, PHP est plutôt bien fait et nous propose un élément du tableau $\_FILES pré destiné à ceci :

```php
if ($_SERVER['REQUEST_METHOD'] == 'POST' && !empty($_POST['submited'])):

    $randomString = bin2hex(random_bytes(8)) . time(); 

    // On récupère sa valeur
    $fileError = $_FILES['uploadFile']['error'];

    // On vérifie si la valeur de la clé est différente de 0
    // Si oui, on ne traite plus
    if($fileError !== 0){
        // on peut éventuellement redirigé l'User avant de die;
        die;
    }

endif;
```

#### 3. La taille du fichier

Au même titre que les autres infos, isolons d'abord la taille du fichier dans une variable $fileSize, nous pourrons ainsi la comparer à la taille maxi autorisée.

Dans notre exemple, indiquons à notre traitement de ne prendre en compte que les fichiers de moins de 5 Mo

```php
if ($_SERVER['REQUEST_METHOD'] == 'POST' && !empty($_POST['submited'])):

    $randomString = bin2hex(random_bytes(8)) . time(); 

    $fileError = $_FILES['uploadFile']['error'];
    if($fileError !== 0):
        die;
    endif;

    // On récupère la taille du fichier, et nous allons ajouter des conditions
    $fileSize = $_FILES['uploadFile']['size'];
    // Si la taille du fichier est inférieure à 1 octet OU supérieur à 5 Mo
    if( ( $fileSize < 1 ) || ( $fileSize > 5000000 ) ):
        // On ferme le traitement
        die;
    endif;

endif;
```

> Nous voici donc avec un code qui va vérifier :
>
> * Si le formulaire a été soumis
> * Si le code erreur est bien égal à 0 (NO\_ERROR)
> * Si la taille du fichier est tolérée par nos réglages

#### 4. L'extension du fichier envoyé

Il ne nous manque alors plus qu'un paramètre à analyser, et non pas des moindre, l'extension et donc de ce fait le type de fichier qui a été passé au travers de notre formulaire.

Nous avions ajouté un attribut **accept** qui permettait au moment de la saisie du formulaire de limiter (grisonner en réalité) le choix du fichier au sein de l'appareil utilisé par l'utilisateur. Celui-ci nous disait accepter les types de fichiers suivants : ".jpg, .jpeg, .png, .gif, .svg"

Faisons alors de même lors de notra traitement en PHP, en récupérant d'abord l'extension de notre fichier :

```php
if ($_SERVER['REQUEST_METHOD'] == 'POST' && !empty($_POST['submited'])):

    $randomString = bin2hex(random_bytes(8)) . time(); 

    $fileError = $_FILES['uploadFile']['error'];
    if($fileError !== 0):
        die;
    endif;

    $fileSize = $_FILES['uploadFile']['size'];
    if( ( $fileSize < 1 ) || ( $fileSize > 5000000 ) ):
        die;
    endif;

    // On récupère l'extension du fichier et son type MIME
    $fileExt = pathinfo($_FILES['uploadFile']['name'], PATHINFO_EXTENSION);
    $fileType = $_FILES['uploadFile']['type'];

    // Ainsi, si nous n'accordions que les fichiers ".jpg, .jpeg, .png, .gif et .svg"
    if( ($fileExt !== "jpg") OR ($fileExt !== "jpeg") OR ($fileExt !== "png") OR ($fileExt !== "gif") OR  ($fileExt !== "svg") ):
        // Alors ce fichier ne peut être accepté
        die;
    endif;

endif;
```

En effectuant le code ci-dessus, on peut encore améliorer un peu tout cela, et pour deux raisons :

* Nous né vérifions pas le type Mime
* Cette condition if de 5 status pourraient être simplifiée

Transoformons donc alors un peu ce morceau de code :

```php
    // On récupère l'extension du fichier et son type MIME
    $fileExt = pathinfo($_FILES['uploadFile']['name'], PATHINFO_EXTENSION);
    $fileType = $_FILES['uploadFile']['type'];

    // Ainsi, si nous n'accordions que les fichiers ".jpg, .jpeg, .png, .gif et .svg"
    if( ($fileExt !== "jpg") OR ($fileExt !== "jpeg") OR ($fileExt !== "png") OR ($fileExt !== "gif") OR  ($fileExt !== "svg") ):
        // Alors ce fichier ne peut être accepté
        die;
    endif;
```

en quelques choses de plus optimisé :

```php
    // Créons d'abord un tableau composé de nos clés / valeurs "ext" => "type
    $allowedExtensions = [
        "jpg"   => "image/jpg",
        "jpeg"  => "image/jpeg",
        "png"   => "image/png",
        "gif"   => "image/gif",
        "svg"   => "image/svg+xml"
    ];

    $fileExt = pathinfo($_FILES['uploadFile']['name'], PATHINFO_EXTENSION);
    $fileType = $_FILES['uploadFile']['type'];

    // Vérifons ensuite la présence des extensions & types dans notre tableau 
    if( ( !array_key_exists($fileExt, $allowedExtensions) ) OR ( !in_array($fileType, $allowedExtensions) ) ):
        die;
    endif;
```

> Pour connaître les types MIME : [https://developer.mozilla.org/fr/docs/Web/HTTP/Basics\_of\_HTTP/MIME\_types/Common\_types](https://developer.mozilla.org/fr/docs/Web/HTTP/Basics\_of\_HTTP/MIME\_types/Common\_types)

Ce qui nous donne finalement un fichier verify.php comme celui-ci :

```php
<?php

if ($_SERVER['REQUEST_METHOD'] == 'POST' && !empty($_POST['submited'])):

    $randomString = bin2hex(random_bytes(8)) . time();

    $fileError = $_FILES['uploadFile']['error'];
    if($fileError !== 0):
        die;
    endif;

    $fileSize = $_FILES['uploadFile']['size'];
    if( ( $fileSize < 1 ) || ( $fileSize > 5000000 ) ):
        die;
    endif;

    $allowedExtensions = [
        "jpg"   => "image/jpg",
        "jpeg"  => "image/jpeg",
        "png"   => "image/png",
        "gif"   => "image/gif",
        "svg"   => "image/svg+xml"
    ];

    $fileExt = pathinfo($_FILES['uploadFile']['name'], PATHINFO_EXTENSION);
    $fileType = $_FILES['uploadFile']['type'];

    if( ( !array_key_exists($fileExt, $allowedExtensions) ) OR ( !in_array($fileType, $allowedExtensions) ) ):
        die;
    endif;

    // OK Tout est bon on peut continuer

endif;
```

#### Mais il nous reste le nom du fichier non ?

Souveznez-vous, nous avions déclaré une chaine de caractères aléatoires un peu plus tôt :

```php
$randomString = bin2hex(random_bytes(8)) . time();
```

Et bien nous allons l'utiliser pour nommer notre nouveau fichier, ainsi la manipulation est très simple :

```php
$destFile = $randomString . "." . $fileExt;
```

> Très important, le nom du fichier ne doit absolument pas comporter le chemin d'accès et ne doit être stocké en BDD que par son nom + extension

Notre fichier final ressemble donc à ce script PHP :

```php
<?php

if ($_SERVER['REQUEST_METHOD'] == 'POST' && !empty($_POST['submited'])):

    $fileError = $_FILES['uploadFile']['error'];
    if($fileError !== 0):
        die; // Erreur lors de l'envoi en PHP
    endif;

    $fileSize = $_FILES['uploadFile']['size'];
    if( ( $fileSize < 1 ) || ( $fileSize > 5000000 ) ):
        die; // Erreur de taille de fichier
    endif;

    $allowedExtensions = [
        "jpg"   => "image/jpg",
        "jpeg"  => "image/jpeg",
        "png"   => "image/png",
        "gif"   => "image/gif",
        "svg"   => "image/svg+xml"
    ];

    $fileExt = pathinfo($_FILES['uploadFile']['name'], PATHINFO_EXTENSION);
    $fileType = $_FILES['uploadFile']['type'];

    if( ( !array_key_exists($fileExt, $allowedExtensions) ) OR ( !in_array($fileType, $allowedExtensions) ) ):
        die; // Extension non autorisée
    endif;

    // On nomme notre fichier pour intégration en BDD et dans notre dossier upload
    $randomString = bin2hex(random_bytes(8)) . time();
    $destFile = $randomString . "." . $fileExt;

endif;
```

### Cette fois-ci c'est la bonne !

Après toutes ces bonnes pratiques, déplaçons maintenant notre fichier au sein de notre ossature, plus précisement dans notre dossier upload prévu à cet effet.

Pour cela, nous allons utiliser la fonction [move\_uploaded\_file()](https://www.php.net/manual/fr/function.move-uploaded-file.php) de PHP

Pour commencer, essayons de comprendre son fonctionnement :

```php
<?php
move_uploaded_file($filename, $destination);
// @param string $filename — The filename of the uploaded file.
// @param string $destination — The destination of the moved file.
// @return bool
// If filename is not a valid upload file, then no action will occur, and move_uploaded_file will return false.
```

Nous pouvons alors comprendre que deux paramètres sont attendus :

* Le fichier source
* Le fichier distant (celui que l'on aura copié avec son nouveau nom)

> Pensez également à créer votre dossier uploads à la racine de votre projet, sous peine de récupérer un bool de type false, qui videndrait un problème de chemin introuvable

Possédant ces informations, on peut alors procéder au transfert :

```php
move_uploaded_file($_FILES['uploadFile']['tmp_name'], "uploads/". $destFile);
// $_FILES['uploadFile']['tmp_name'] => Le fichier récupéré par le serveur, et qui doit être copié
// "uploads/" . $destFile => Le repertoire et le nom du fichier généré (random) de destination
```

Notre fichier vient d'être déplacé, dans le repertoire "uploads" comme demandé, et il porte le nom généré par notre chaine aléatoire. Félicitations !!!
