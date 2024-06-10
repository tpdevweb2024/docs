# Fonctionnalités avancées

PDO (PHP Data Objects) offre une interface uniforme pour accéder à différentes bases de données. Au-delà des opérations de base, PDO propose plusieurs fonctionnalités avancées améliorant la performance, la sécurité et la flexibilité de vos applications PHP. Dans ce chapitre, nous explorerons ces capacités avancées.

## Transactions

Les transactions permettent de grouper plusieurs opérations en une seule unité de travail, qui sera soit entièrement exécutée, soit entièrement annulée. Cela assure l'intégrité des données en cas d'erreur.

```php
try {
    $pdo->beginTransaction();
    $pdo->exec("UPDATE comptes SET solde = solde - 100 WHERE id = 1");
    $pdo->exec("UPDATE comptes SET solde = solde + 100 WHERE id = 2");
    $pdo->commit();
} catch (Exception $e) {
    $pdo->rollBack();
    echo "Erreur : " . $e->getMessage();
}
```

## Liaison de Colonnes

La liaison de colonnes associe directement les colonnes d'un résultat de requête à des variables PHP, permettant un traitement plus efficace des données.

```php
$stmt = $pdo->prepare("SELECT nom, email FROM utilisateurs");
$stmt->execute();
$stmt->bindColumn(1, $nom);
$stmt->bindColumn(2, $email);
while ($stmt->fetch(PDO::FETCH_BOUND)) {
    echo "Nom: $nom, Email: $email<br>";
}
```

## Attributs de Connexion

PDO fournit des attributs modifiables qui influencent le comportement de la connexion. Par exemple, pour activer les exceptions en cas d'erreur :

```php
$pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
```
