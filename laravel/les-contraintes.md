# Les contraintes

## La déclaration des FK

### foreignId

Créez une migration pour les tables, par exemple `cars` et `owners`.

```
php artisan make:migration create_cars_table
php artisan make:migration create_owners_table
```

Dans la migration `create_owners_table`, définissez les colonnes.

```php
Schema::create('owners', function (Blueprint $table) {
    $table->id();
    $table->string('name');
    $table->timestamps();
});
```

Dans la migration `create_cars_table`, définissez les colonnes et la clé étrangère.

```php
Schema::create('cars', function (Blueprint $table) {
    $table->id();
    $table->string('model');
    $table->unsignedBigInteger('owner_id');
    $table->foreign('owner_id')->references('id')->on('owners')->onDelete('cascade');
    $table->timestamps();
});
```

Exécutez les migrations.

```
php artisan migrate
```

{% hint style="info" %}
Cela met en place une relation entre les tables `cars` et `owners` avec une contrainte de clé étrangère.
{% endhint %}

### foreignIdFor

Utilisez `foreignIdFor` pour créer automatiquement une colonne de clé étrangère basée sur une relation de modèle définie, il prend alors le nom de la table jointe en la mettant au singulier suivie du suffixe `_id`.&#x20;

Par exemple, dans la migration `cars`, au lieu de définir manuellement `owner_id` et la clé étrangère correspondante :

```php
$table->foreignIdFor(Owner::class)->constrained()->onDelete('cascade');
```

{% hint style="success" %}
Cela simplifie la déclaration des clés étrangères et assure une meilleure lisibilité.
{% endhint %}

## Les méthodes à modifier

Pour définir une relation entre les modèles, vous devez ajouter des méthodes spécifiques dans vos classes de modèle.&#x20;

Par exemple, pour définir une relation entre les modèles `Car` et `Owner` :

**Relation BelongsTo** : Ajoutez cette méthode dans le modèle `Car` pour indiquer qu'une voiture appartient à un propriétaire.

```php
class Car extends Model
{
    public function owner()
    {
        return $this->belongsTo(Owner::class);
    }
}
```

**Relation HasMany** : Ajoutez cette méthode dans le modèle `Owner` pour indiquer qu'un propriétaire peut avoir plusieurs voitures.

```php
class Owner extends Model
{
    public function cars()
    {
        return $this->hasMany(Car::class);
    }
}
```

{% hint style="info" %}
Ces méthodes permettent à Eloquent de comprendre la manière dont les différents modèles sont liés entre eux et simplifient les requêtes jointes et les opérations sur les relations.
{% endhint %}

## Afficher des données en jointure

Pour afficher les données d'un modèle avec ses jointures, vous pouvez utiliser Eloquent et les méthodes `with` ou `load` pour eager loading.&#x20;

Par exemple, pour afficher les données d'une voiture avec son propriétaire :

```php
$cars = Car::with('owner')->get();
foreach ($cars as $car) {
    echo $car->name . ' belongs to ' . $car->owner->name;
}
```

{% hint style="warning" %}
Il est important de comprendre que `owner` dans ce cas fait référence à la méthode créée précédemment dans le modele `Car`, lui meme appelé en début de ligne.&#x20;
{% endhint %}

{% hint style="success" %}
Cela récupère les voitures ainsi que leurs propriétaires en une seule requête optimisée.
{% endhint %}
