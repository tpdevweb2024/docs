# Le CRUD

Pour effectuer ces opérations, vous devrez alors vous dirigez vers le shell de MongoDB, accessible depuis votre terminal, ou encore depuis Compass.

## Lire (Read)

```javascript
db.collection.find({ "nom": "Dupont" });
```

La commande ci-dessus récupère les documents de la collection nommée **"collection"** qui ont le champ "nom" avec une valeur strictement égale à "Dupont".&#x20;

En d'autres termes, elle sélectionne uniquement les documents dont le champ "nom" correspond exactement à "Dupont" sans distinction de casse ou de variations supplémentaires. Cette opération est essentielle pour filtrer les résultats et obtenir uniquement les enregistrements désirés dans la base de données.

## Créer (Create)

```javascript
db.collection.insertOne({ "nom": "Dupont", "age": 30 });
```

Cette commande insère un nouveau document dans la collection avec les informations suivantes:

* **Nom**: "Dupont"
* **Âge**: 30 ans

Le document sera ajouté à la collection de manière à ce que les informations fournies soient enregistrées et indexées correctement. Utilisez cette commande pour maintenir une base de données organisée et mise à jour.

## Mettre à jour (Update)

<pre class="language-javascript"><code class="lang-javascript"><strong>db.collection.updateOne({ "nom": "Dupont" }, { $set: { "age": 31 } });
</strong></code></pre>

Cela met à jour le champ "age" à 31 pour le document où le "nom" est "Dupont". Cette opération est particulièrement utile lorsque vous souhaitez modifier les informations personnelles d'un individu spécifique dans la base de données.&#x20;

En procédant ainsi, vous assurerez que l'âge de Monsieur Dupont reflète correctement sa dernière date de naissance ou toute autre mise à jour administrative nécessaire.&#x20;

{% hint style="warning" %}
Veillez à exécuter cette action avec précaution pour éviter toute erreur dans les données sensibles.
{% endhint %}

## Supprimer (Delete)

```javascript
db.collection.deleteOne({ "nom": "Dupont" });
```

Cette commande supprime le premier document où le "nom" est "Dupont" de la collection, à ne pas confondre avec deleteMany, qui supprimera toutes les occurences.

```javascript
db.collection.deleteMany({ "nom": "Dupont" });
```

{% hint style="danger" %}
Cette commande supprime tous les documents où le "nom" est "Dupont" de la collection. Il est essentiel de l'utiliser avec prudence pour éviter de supprimer des données par inadvertance.
{% endhint %}
