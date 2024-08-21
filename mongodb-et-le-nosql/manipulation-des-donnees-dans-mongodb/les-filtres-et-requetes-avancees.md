# Les filtres et requêtes avancées

## Filtres

Pour filtrer les documents dans une collection MongoDB, utilisez la méthode `find()` avec un objet de filtre.&#x20;

Par exemple, pour trouver tous les documents où le champ `age` est supérieur à 25, vous pouvez employer la syntaxe suivante :

```javascript
db.collection.find({ age: { $gt: 25 } })
```

Cette méthode permet de spécifier des critères de recherche en utilisant des opérateurs de comparaison tels que `$gt` pour "greater than" (supérieur à), `$lt` pour "less than" (inférieur à), `$gte` pour "greater than or equal to" (supérieur ou égal à), `$lte` pour "less than or equal to" (inférieur ou égal à), et bien d'autres.

Pour filtrer d'autres types de données, vous pouvez facilement ajuster l'objet de filtre.&#x20;

Par exemple, si vous souhaitez rechercher des documents où le champ `status` est égal à `"active"` et le champ `score` est inférieur à 100, la requête ressemblerait à ceci :

```javascript
db.collection.find({ status: "active", score: { $lt: 100 } })
```

{% hint style="info" %}
MongoDB propose une grande diversité d'opérateurs de requête et de mise à jour, permettant de réaliser des filtres complexifiés et adaptés à presque toutes les situations. Utilisez ces opérateurs pour construire des requêtes précises en fonction de vos besoins spécifiques.
{% endhint %}

## Requêtes avancées

Pour des requêtes plus complexes, combinez plusieurs conditions avec des opérateurs logiques.&#x20;

Par exemple, si vous souhaitez trouver tous les documents dans lesquels l'`age` est supérieur à 25 et où le `statut` est soit "célibataire" soit "marié", vous pouvez utiliser une combinaison d'opérateurs logiques. Cela permet de filtrer les résultats en s'assurant qu'ils répondent à plusieurs critères spécifiques, augmentant ainsi la granularité et la précision de vos recherches dans la base de données.

```json
db.collection.find(
{
  age: { $gt: 25 },
  status: { $in: ["single", "married"] }
}
)
```

{% hint style="success" %}
Utilisez les opérateurs `$and`, `$or`, `$not`, etc., pour affiner vos requêtes selon les besoins.
{% endhint %}
