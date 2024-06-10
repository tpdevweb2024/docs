# Les superglobales

En PHP, les variables superglobales sont des tableaux intégrés qui sont disponibles dans tous les contextes du script.

## Pourquoi des superglobales ? <a href="#pourquoi-des-superglobales" id="pourquoi-des-superglobales"></a>

Elles permettent d'accéder à des informations provenant de diverses sources comme les données du formulaire envoyées par l'utilisateur (`$_POST` et `$_GET`), les cookies (`$_COOKIE`), la session (`$_SESSION`), les informations sur le serveur et l'environnement d'exécution (`$_SERVER` et `$_ENV`), ainsi que les variables de fichier envoyées par l'utilisateur (`$_FILES`).

Ces superglobales rendent la manipulation de données externes plus simple et sécurisée, à condition de les utiliser correctement pour éviter les failles de sécurité.

## C'est quoi une superglobale ? <a href="#cest-quoi-une-superglobale" id="cest-quoi-une-superglobale"></a>

Une superglobale en PHP est un type de variable globale qui est automatiquement disponible dans toutes les portées à travers un script.

Ces variables sont fournies par PHP et contiennent des informations issues de l'environnement d'exécution du script. Elles sont accessibles de n'importe où dans le script, sans avoir besoin d'être déclarées globalement.

Les superglobales sont des tableaux associatifs qui peuvent contenir des données de formulaire, des informations de session, des données de serveur, des informations d’entrée-sortie de fichiers, et plus.

## Les différentes variables superglobales PHP <a href="#les-differentes-variables-superglobales-php" id="les-differentes-variables-superglobales-php"></a>

### `$_GET` <a href="#usd_get" id="usd_get"></a>

La superglobale `$_GET` en PHP est un tableau associatif qui contient les données envoyées au script courant via la méthode HTTP GET.

Cette méthode est couramment utilisée pour passer des paramètres à un script, généralement via l'URL. Par exemple, dans une URL comme `https://exemple.com/index.php?nom=Jean&age=25`, les données après le `?` sont des paramètres GET, ce qui signifie que `$_GET['nom']` vaudra `Jean` et `$_GET['age']` vaudra `25` dans le script `index.php`.

#### **Utilisations communes de `$_GET` :**

* **Récupération des données des formulaires** soumis via GET.
* Gestion des **paramètres de navigation** ou de filtrage dans les URL.
* **Tracking des utilisateurs** en ajoutant des paramètres spécifiques dans les liens.

#### **Exemple :**

```php
if (isset($_GET['nom'])) {
    echo "Bonjour, " . htmlspecialchars($_GET['nom']);
}
```

Cet exemple vérifie si le paramètre `nom` a été envoyé via GET et affiche un message de bienvenue. L'utilisation de `htmlspecialchars()` sert à prévenir les attaques XSS en échappant les entités HTML potentiellement dangereuses.

{% hint style="danger" %}
Il est important de valider et de nettoyer toutes les données entrantes via `$_GET` pour éviter les vulnérabilités de sécurité, notamment les injections SQL et les attaques XSS.
{% endhint %}

### `$_POST` <a href="#usd_post" id="usd_post"></a>

La superglobale `$_POST` en PHP est utilisée pour collecter les données envoyées via un formulaire HTML lorsqu'utilisant la méthode `POST`. Cette méthode est préférée pour l'envoi de données sensibles ou de grandes quantités de données, car elle ne les ajoute pas à l'URL.

#### **Exemple d'utilisation avec un formulaire HTML :**

```php
<form action="traitement.php" method="post">
  Nom: <input type="text" name="nom">
  <input type="submit">
</form>
```

Dans `traitement.php`, pour accéder aux données soumises :

```php
if (isset($_POST['nom'])) {
  echo "Bonjour, " . htmlspecialchars($_POST['nom']);
}
```

Comme pour `$_GET`, utiliser `htmlspecialchars()` avec `$_POST` est crucial pour se protéger des attaques XSS en filtrant des entrées utilisateurs.

### `$_FILES` <a href="#usd_files" id="usd_files"></a>

La superglobale `$_FILES` en PHP permet de gérer le téléchargement de fichiers depuis un formulaire HTML. Lorsqu'un utilisateur envoie un fichier via un formulaire qui utilise la méthode `post` avec l'attribut `enctype="multipart/form-data"`, les informations du fichier sont accessibles via `$_FILES`.

#### Exemple de formulaire pour télécharger un fichier :

```php
<form action="upload.php" method="post" enctype="multipart/form-data">
  Sélectionnez un fichier : <input type="file" name="monfichier">
  <input type="submit" value="Envoyer le fichier">
</form>
```

Dans `upload.php`, vous pouvez accéder aux informations du fichier comme suit :

```php
if (isset($_FILES['monfichier'])) {
    $nomFichier = $_FILES['monfichier']['name'];
    $tailleFichier = $_FILES['monfichier']['size'];
    $tmpName = $_FILES['monfichier']['tmp_name'];
    $error = $_FILES['monfichier']['error'];

    // Pour sauver le fichier uploadé
    move_uploaded_file($tmpName, "chemin/de/destination/" . $nomFichier);
}
```

#### **Points clés à retenir avec `$_FILES`**:

* Toujours utiliser `enctype="multipart/form-data"` dans votre balise `<form>` pour l'envoi de fichiers.
* Vérifiez les erreurs avec `$_FILES['nomdufichier']['error']` avant de manipuler le fichier.
* Utilisez `move_uploaded_file()` pour sauvegarder le fichier dans un répertoire de votre serveur de manière sécurisée.

## **Conseils de sécurité** :

* Vérifiez toujours le type MIME du fichier pour vous assurer qu'il correspond aux types de fichiers que vous attendez.
* Inspectez la taille du fichier pour éviter d'encombrer votre serveur avec des fichiers trop volumineux.
* Utilisez la fonction `move_uploaded_file()` pour éviter les vulnérabilités liées au téléchargement de fichiers.

### `$_SERVER` <a href="#usd_server" id="usd_server"></a>

La superglobale `$_SERVER` est un tableau contenant des informations telles que les en-têtes, les chemins et les emplacements des scripts. Elle est créée par le serveur web et peut être utilisée pour obtenir des données liées à la requête et à l'environnement d'exécution du script.

Voici quelques utilisations courantes :

* `$_SERVER['HTTP_HOST']` : Renvoie le nom de domaine de l'hôte.
* `$_SERVER['REQUEST_METHOD']` : Indique la méthode de requête utilisée pour accéder à la page (`GET`, `POST`, etc.).
* `$_SERVER['REQUEST_URI']` : Renvoie l'URI qui a été fournie pour accéder à cette page.
* `$_SERVER['SCRIPT_FILENAME']` : Le chemin absolu du script exécuté.
* `$_SERVER['REMOTE_ADDR']` : L'adresse IP du client qui demande la page.

Il est important de noter que certaines informations dans `$_SERVER` peuvent être manipulées par l'utilisateur, donc leur utilisation doit être faite avec précaution, en particulier pour des fonctionnalités de sécurité.

### `$_COOKIE` <a href="#usd_cookie" id="usd_cookie"></a>

La superglobale `$_COOKIE` en PHP est un tableau associatif contenant les cookies envoyés par le navigateur client vers le serveur. Les cookies sont des données stockées côté client et utilisées pour suivre ou identifier les utilisateurs qui reviennent sur le site web.

Les cookies peuvent améliorer l'expérience utilisateur, mais il est important de respecter la vie privée des utilisateurs et de les informer de l'utilisation des cookies sur votre site web.

### `$_SESSION` <a href="#usd_session" id="usd_session"></a>

La superglobale $\_SESSION en PHP permet de stocker des informations de session à travers diverses pages, en utilisant un identifiant de session unique. Les sessions sont un moyen de conserver les données entre les requêtes. Contrairement aux cookies, les données de session sont stockées côté serveur, ce qui les rend plus sécurisées pour stocker des informations sensibles.

Il est important de gérer les sessions de manière sécurisée en utilisant des mesures comme la régénération des ID de session après la connexion pour prévenir les attaques de session fixation, et en s'assurant de détruire la session lors de la déconnexion pour éviter les détournements de session.

## Différence entre `$_GET` et `$_POST` <a href="#difference-entre-usd_get-et-usd_post" id="difference-entre-usd_get-et-usd_post"></a>

La différence clé entre `$_GET` et `$_POST` réside dans la méthode de transmission des données : `$_GET` ajoute les données à l'URL (visible et limité en taille), tandis que `$_POST` envoie les données dans le corps de la requête (non visible dans l'URL, approprié pour des quantités de données plus importantes).
