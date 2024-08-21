# L'agrégation

L'agrégation est une technique puissante pour manipuler et analyser des données dans des bases de données NoSQL comme MongoDB. Elle permet de regrouper, filtrer, et transformer les données de manière efficace, ce qui est essentiel pour extraire des informations utiles à partir de grands ensembles de données.

MongoDB utilise un **framework de pipeline d'agrégation** qui fonctionne de manière similaire aux opérations pipe (`|`) en UNIX.&#x20;

Ce framework permet de faire passer les documents d'une collection à travers une série d'étapes où chaque étape transforme les données avant de les transmettre à l'étape suivante. Ce processus est linéaire et permet de réaliser des opérations complexes, telles que le regroupement, le tri, la projection de champs spécifiques, et bien plus encore.

## **Exemple de pipeline de base**

Voici un exemple de pipeline d'agrégation simple dans MongoDB :

```javascript
db.orders.aggregate([
  { $match: { status: "completed" } },
  { $group: { _id: "$productId", totalQuantity: { $sum: "$quantity" } } },
  { $sort: { totalQuantity: -1 } }
])
```

Dans cet exemple :

* **`$match`** : Cette étape filtre les documents pour ne conserver que ceux où le champ `status` est égal à `"completed"`. Cela réduit la quantité de données à traiter par les étapes suivantes du pipeline.
* **`$group`** : Les documents filtrés sont ensuite regroupés par le champ `productId`. Pour chaque groupe, la somme des quantités (`$quantity`) est calculée et stockée dans un champ `totalQuantity`. Le champ `_id` représente la clé de regroupement, ici définie par `productId`.
* **`$sort`** : Enfin, les documents regroupés sont triés en fonction de `totalQuantity` en ordre décroissant, mettant en tête les produits les plus vendus.

## Utilisation de plusieurs étapes

Les pipelines d'agrégation peuvent inclure plusieurs étapes pour effectuer des transformations complexes. Voici un autre exemple :

```javascript
db.sales.aggregate([
  { $match: { year: { $gt: 2020 } } },
  { $group: { _id: "$region", totalSales: { $sum: "$amount" } } },
  { $project: { _id: 0, region: "$_id", totalSales: 1 } }
])
```

Dans cet exemple :

* **`$match`** : L'étape initiale filtre les documents pour ne conserver que ceux où le champ `year` est supérieur à 2020, ciblant ainsi les ventes récentes.
* **`$group`** : Les documents sont ensuite regroupés par `region`. Pour chaque région, le total des ventes (`$amount`) est calculé et stocké dans le champ `totalSales`.
* **`$project`** : Cette étape reformate le résultat final. Le champ `_id`, qui contient maintenant la région, est renommé en `region` et l'identifiant `_id` est exclu des résultats, ne laissant que les champs `region` et `totalSales`.

## Importance de l'Agrégation

L'agrégation est un outil crucial pour manipuler et analyser de grandes quantités de données dans MongoDB.&#x20;

{% hint style="info" %}
Elle permet non seulement de réaliser des calculs complexes comme des totaux, des moyennes, ou des comptages, mais aussi de transformer et d'organiser les données d'une manière qui facilite leur analyse et leur visualisation.&#x20;
{% endhint %}

Les pipelines d'agrégation permettent d'optimiser ces opérations en réduisant la charge de traitement au fur et à mesure que les données avancent dans le pipeline. Cela en fait une méthode essentielle pour toute application nécessitant une analyse de données robuste et performante.
