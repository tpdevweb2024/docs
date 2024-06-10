# Bonnes pratiques et sécurité

## Utiliser les statements préparés

Pour prévenir les injections SQL, utilisez toujours des _prepared statements_ avec PDO. Cela permet de séparer clairement les instructions SQL de vos données.

```php
$stmt = $pdo->prepare("SELECT * FROM users WHERE email = :email");
$stmt->execute(['email' => $userInput]);
```

## Activer les exceptions PDO

Activez les exceptions PDO pour mieux gérer les erreurs. Cela permet de détecter immédiatement les problèmes dans vos requêtes SQL.

```php
$pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
```

## Utiliser des transactions

Les transactions garantissent que toutes vos modifications de la base de données sont exécutées avec succès ou annulées en cas d'erreur.

```php
try {
    $pdo->beginTransaction();
    // Vos requêtes SQL ici
    $pdo->commit();
} catch (Exception $e) {
    $pdo->rollBack();
}
```

## Limiter les droits de l'utilisateur de la base de données

N'utilisez pas un utilisateur de base de données avec des droits d'administration complets. Attribuez uniquement les permissions nécessaires pour les opérations prévues.

## Utiliser une connexion sécurisée

Si votre application nécessite une connexion à distance à la base de données, assurez-vous d'utiliser une connexion sécurisée, comme SSH ou VPN, pour prévenir les écoutes indiscrètes.

{% hint style="info" %}
En respectant ces pratiques, vous augmentez considérablement la sécurité de vos applications PHP en utilisant PDO.
{% endhint %}
