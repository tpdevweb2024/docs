# L'utilisation du driver PDO

Pour interagir avec des bases de données en PHP, PDO (PHP Data Objects) est une extension qui offre une interface légère et cohérente.

## Connexion avec PDO

```php
<?php

$server = "localhost"; // Nom du serveur de bases de données - Ajouter le port si différent de 3306 -> Exemple : "localhost:3308"
$dbname = "dbname"; // Nom de notre base de données
$user = "root"; // Nom d'utilisateur pour éccder au serveur
$pwd = "root"; // Mot de passe pour accéder au serveur - Laisser vide pour les users Mac OS

try {
    $bdd = new PDO("mysql:host=$server;dbname=$dbname", $user, $pwd); // Connexion à la bdd exercicepdo
    $bdd->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION); // Activation du mode d'erreur amélioré
} catch (PDOException $e) {
    echo "Échec de la connexion : " . $e->getMessage(); // Affichage de l'erreur en cas d'erreur
}
```

La tentative de connexion est encapsulée dans un bloc `try` pour gérer les exceptions potentielles. Si la connexion à la base de données échoue, une `PDOException` est capturée et le message d'erreur est affiché en utilisant `echo "Erreur de connexion : " . $e->getMessage();`.

## Création d'une instance PDO

La ligne `$pdo = new PDO($dsn, $utilisateur, $mot_de_passe);` tente de créer une nouvelle instance de PDO. Cet objet est utilisé pour effectuer des opérations sur la base de données.

### Identifiants de la base de données

Les variables `$utilisateur` et `$mot_de_passe` représentent le nom d'utilisateur (`root`) et le mot de passe (\`\`) pour la connexion à la base de données.&#x20;

{% hint style="danger" %}
Dans un environnement de production, vous les remplaceriez par des **identifiants sécurisés.**
{% endhint %}

### Nom du serveur de données (DSN)

La variable `$dsn` contient les informations de connexion.&#x20;

Dans ce cas, elle spécifie :&#x20;

* le type de base de données (`mysql`)
* l'hôte (`localhost`)
* le nom de la base de données (`nom_de_la_base`)
* le jeu de caractères (`utf8`).&#x20;

{% hint style="info" %}
Ces informations indiquent à PDO comment se connecter à la base de données.
{% endhint %}
