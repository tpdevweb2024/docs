# Les requêtes avec PDO

PDO (PHP Data Objects) est une extension qui fournit une interface unifiée pour l'accès aux bases de données dans PHP. Elle permet aux développeurs de réaliser des requêtes SQL de façon sécurisée et efficace, indépendamment du type de base de données utilisé.

## Avantages de PDO

* **Abstraction de la base de données** : PDO permet de travailler avec n'importe quel type de base de données supporté sans changer la manière de faire les requêtes.
* **Sécurité** : En utilisant les requêtes préparées, PDO aide à prévenir les injections SQL.
* **Flexibilité** : PDO offre une grande flexibilité dans le traitement des données.

## Réaliser une requête simple

Pour exécuter une requête SQL simple, vous pouvez utiliser la méthode `query`.

```php
$sql = 'SELECT * FROM votre_table';
foreach ($pdo->query($sql) as $row) {
    echo $row['votre_colonne'] . "\n";
}
```

## Utilisation des requêtes préparées avec PDO

Les requêtes préparées offrent une meilleure sécurité et améliorent la performance, particulièrement lors de l'exécution répétée de la même requête avec de petits changements dans les valeurs des paramètres.

### Avantages des requêtes préparées

* **Sécurité accrue**: Elles permettent d'éviter les attaques par injection SQL car les valeurs sont liées à des paramètres et non intégrées directement dans la requête.
* **Meilleure performance**: La requête est compilée une fois et peut être exécutée plusieurs fois avec des valeurs différentes.

### Préparation d'une requête

Pour préparer une requête, utilisez la méthode `prepare` de l'objet PDO.

```php
$stmt = $pdo->prepare('SELECT * FROM votre_table WHERE votre_colonne = :valeur');
```

Une fois que le paramètre est lié à la requête préparée, vous pouvez exécuter la requête avec la méthode `execute`.

```php
$stmt->execute();
```

**Autres méthodes pour lier des valeurs**

En plus de `bindParam`, il existe d'autres méthodes pour lier des valeurs à une requête préparée :

*   **bindValue**: Cette méthode est similaire à `bindParam`, mais au lieu de lier une variable au paramètre, elle lie une valeur. Cela peut être utile si vous n'avez pas une variable mais une valeur directe à lier.

    ```php
    $stmt->bindValue(':valeur', 'valeur_directe');
    ```
*   **Passage direct de paramètres à `execute`**: Vous pouvez également passer un tableau de valeurs directement à la méthode `execute` sans utiliser `bindParam` ou `bindValue`.

    ```php
    $stmt->execute([':valeur' => $valeur]);
    ```

### Liaison des paramètres

Liez les valeurs aux paramètres spécifiés dans la requête préparée avec la méthode `bindParam`.

```php
$stmt->bindParam(':valeur', $valeur);
```

* `:valeur` est le nom du paramètre dans la requête SQL.
* `$valeur` est la variable contenant la valeur à associer au paramètre.

### Exécution de la Requête

Une fois les paramètres liés, vous pouvez exécuter la requête préparée.

```php
$stmt->execute();
```

{% hint style="info" %}
Les requêtes préparées sont un moyen efficace de travailler avec des bases de données en PHP, offrant une combinaison précieuse de sécurité, de performance et de flexibilité.
{% endhint %}

## Récupération de résultats avec PDO

Lorsque vous travaillez avec des bases de données en PHP, PDO offre un mécanisme souple pour exécuter des requêtes et récupérer des résultats. Une fois que vous avez préparé et exécuté votre requête, vous pouvez récupérer les résultats en utilisant différentes méthodes telles que `fetch()` ou `fetchAll()`. Ces méthodes permettent de travailler avec les données retournées de manière efficace.

### **Utilisation de `fetch()`**

La méthode `fetch()` récupère la prochaine ligne à partir du jeu de résultats de votre requête. Vous pouvez spécifier le mode de récupération des données, par exemple, sous forme de tableau associatif.

```php
// Exécution de la requête préparée
$stmt->execute();

// Récupération d'une ligne sous forme de tableau associatif
$resultat = $stmt->fetch(PDO::FETCH_ASSOC);
```

**Parcours des résultats**

Pour traiter plusieurs lignes, vous pouvez boucler sur les résultats retournés par `fetch()`.

### **Utilisation de `fetchAll()`**

```php
# Préparation de la requête
$stmt = $pdo->prepare('SELECT * FROM votre_table WHERE votre_colonne = :valeur');

# Liaison des paramètres
$stmt->bindParam(':valeur', $valeur);

# Exécution de la requête
$stmt->execute();

# Récupération des résultats
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {
    echo $row['nom_de_la_colonne'] . "\n";
}
```

{% hint style="info" %}
Pour récupérer toutes les lignes d'un coup, vous pouvez utiliser la méthode `fetchAll()`. Cette méthode retourne un tableau contenant toutes les lignes du jeu de résultats, ce qui peut être pratique si vous devez passer les données à une autre partie de votre application.
{% endhint %}

```php
// Exécution de la requête préparée
$stmt->execute();

// Récupération de toutes les lignes
$resultats = $stmt->fetchAll(PDO::FETCH_ASSOC);

// Affichage des résultats
foreach ($resultats as $row) {
    echo $row['nom_de_la_colonne'] . "\n";
}
```

L'usage de `fetch()` ou `fetchAll()` dépend de vos besoins spécifiques, notamment du volume de données attendu et de la manière dont vous souhaitez les traiter dans votre application.
