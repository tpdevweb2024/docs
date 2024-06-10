# L'accès aux données et PHP

### Connexion aux bases de données

La force de PHP réside dans sa capacité à interagir avec divers systèmes de gestion de bases de données (SGBD), tels que MySQL, PostgreSQL et SQLite. Cela permet aux développeurs de récupérer, stocker et manipuler des données de manière efficace.

```php
<?php
$servername = "localhost";
$username = "username";
$password = "password";
$dbname = "myDB";

// Création de la connexion
$conn = new mysqli($servername, $username, $password, $dbname);

// Vérification de la connexion
if ($conn->connect_error) {
    die("Échec de la connexion : " . $conn->connect_error);
} 
echo "Connexion réussie";
?>
```

{% hint style="warning" %}
Remarquons l'usage de mysqli, qui est à ce jour une méthode quasi dépréciée, et qui a laissé sa place au driver PDO, que nous verrons dans les étapes suivantes.
{% endhint %}

### Interrogation de la base de données

PHP permet d'exécuter des requêtes SQL à travers son interface, ce qui rend le traitement des données simple et efficace.

```php
$sql = "SELECT id, nom, email FROM utilisateurs";
$result = $conn->query($sql);

if ($result->num_rows > 0) {
    // Affichage des données de chaque ligne
    while($row = $result->fetch_assoc()) {
        echo "id: " . $row["id"]. " - Nom: " . $row["nom"]. " " . "Email: " . $row["email"]. "<br>";
    }
} else {
    echo "0 résultats";
}
```

{% hint style="info" %}
La facilité avec laquelle PHP se connecte à des bases de données rend ce langage extrêmement utile pour le développement de sites web dynamiques. Sa flexibilité et sa large base d’utilisateurs font de lui un choix incontournable pour les développeurs web.
{% endhint %}
