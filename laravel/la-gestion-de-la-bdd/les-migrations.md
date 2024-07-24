---
description: >-
  Mais alors c'est quoi une migration, car sur le papier on peut s'attendre à un
  déplacement de quelque chose ou de quelqu'un, voyons ce qu'est une migration
  en langage Informatique.
---

# Les migrations

## Définition d'une migration

> Transformation de données, de programmes ou de logiciels afin de les rendre compatibles avec un autre environnement informatique.\
> _Source :_ [_Larousse_](https://www.larousse.fr/dictionnaires/francais/migration/51399)

### Le principe des migrations

L'usage des migrations, la plupart du temps au sein de frameworks Backend, assure une logique métier qui va nous permettre de composer notre structure de base de données, grâce notamment à la syntaxe et à la formulation des scripts.

Une migration est donc si nous **vulgarisons** la chose :&#x20;

{% hint style="info" %}
La création d'une table ainsi que de ses spécificités, dont les colonnes, le type de données attendues, ou encore les contraintes telles aque les clés étrangères.
{% endhint %}

### L'objectif des migrations

Les objectifs et l'intérêt d'instaurer les migrations au sein de notre app sont multiples :&#x20;

* La lecture facile du code se situant dans un fichier de migration, et donc la compréhension de notre base de données et de ses relations.
* Le versionning et de ce fait l'enregistrement de fichiers capables de "réinstaller" notre base de données sur un autre appareil.

{% hint style="warning" %}
&#x20;Il est toutefois recommandé d'avoir au préalable réalisé son diagramme de base de données afin de permettre à l'ensemble des utilisateurs (même si vous êtes en solo) d'avoir l'architecture de base toujours en tête.
{% endhint %}

> C'est bien, mais comment assure t'on la sauvegarde des données, car une BDD vide, c'est pas forcement utile en phase de test ?

C'est alors que les factories, intégrées dans tout projet Laravel, vont nous être utile, mais ça nous en parlerons dans le prochain chapitre.

## Création d'une migration

Afin de continuer dans notre lancée, et en ayant en tête notre application **laracars**, nous allons aloir prévoir une table qui comportera l'intégralité des voitures à afficher sur notre web app.

Mais avant de créer notre migration, petit travil de fond...

### On définit les colonnes

Prenons pour exemple cette structure de table, qui est certes optimisable, mais démarrons simple :&#x20;

```sql
id INT [ PK,  AI, UNSIGNED ]
model VARCHAR(255)
brand VARCHAR(255)
power_fisc INT [ UNSIGNED ]
power_dyn INT [ UNSIGNED ]
color VARCHAR(255)
price FLOAT [ UNSIGNED ]
```

Ce véhicule aura donc :&#x20;

* un ID auto-généré
* un modèle de type chaîne de caractères
* une marque de type chaîne de caractères
* une puissance fiscal de type entier non négatif
* une puissance dynamique de type entier non négatif
* une couleur de type chaîne de caractères
* un prix de type nombre à virgule non négatif

### Création de la table

A ce moment, nous serions tentés de créer notre table dans PhpMyAdmin par exemple, et à composer notre structure, mais non surtout pas ! C'est le rôle de Laravel et son ORM.

On va d'abord créer notre fichier de migration :&#x20;

```shell
php artisan make:migration create_cars_table
```

{% hint style="info" %}
Remarquez la convention, elle se veut commencer par le type d'action (create), puis le nom de notre future table (cars) et enfin on spécifie le type de données (table)
{% endhint %}

Cette action va générer un nouveau fichier ; et oui encore ! ; dans notre répertoire **database** puis **migrations.** On peut aisément comprendre l'utilité de cette migration de part son nom.

```
laracars
└─  📂 app/
└─  📂 bootstrap/
└─  📂 config/
└─  📂 database/
    └─  📂 migrations/
        └─  📇 2022_07_13_070942_create_cars_table.php
└─  📂 lang/
└─  📂 node_modules/
└─  📂 public/
└─  📂 resources/
└─  📂 routes/
└─  📂 storage/
└─  📂 tests/
└─  📂 vendor/
```

On ouvre alors ce fichier :&#x20;

```php
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('cars', function (Blueprint $table) {
            $table->id();
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('cars');
    }
};

```

{% hint style="info" %}
On remarque cette fois-ci que dans la méthode up(), une création de Schema est prévue, avec par défaut un id, puis des timestamps (en l’occurrence _created\_at_ et _updated\_at_)
{% endhint %}

### On ajoute les colonnes

C'est alors ici que nous allons ajouter nos colonnes définies un peu plus haut :&#x20;

```php
public function up()
{
    Schema::create('cars', function (Blueprint $table) {
        $table->id();

        // On ajoute nos nouvelles colonnes
        // grâce aux fonctions de notre Model Laravel
        $table->string("model");
        $table->string("brand");
        $table->integer("power_fisc")->unsigned();
        $table->integer("power_dyn")->unsigned();
        $table->string("color");
        $table->float("price")->unsigned();

        $table->timestamps();
    });
}
```

Puis nous allons tenter une nouvelle migration pour vérifier si tout fonctionne.

```shell
php artisan migrate
```

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

Au delà de la création de plusieurs tables, puisque plusieurs fichiers de migration, le rendu de cette nouvelle table **cars** est le suivant :&#x20;

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
:tada: Félicitations, vous venez de **comprendre le principe des migrations !!!**
{% endhint %}

Toutefois, il ne s'agit que d'une table simple, nous devons absolument comprendre comment fonctionnent les contraintes de clé étrangères.

## Les relations dans les migrations

> Nous savons maintenant créer nos tables, qu'en est-il de nos **éventuelles clés étrangères ?**

### Le principe de clé étrangère

Vous l'aurez compris, toute notre interface de travail est Orientée Objet. Ainsi, le FrameWork est donc capable de comprendre facilement les relations au travers des objets <mark style="color:red;">**(nos Models !)**</mark>**.**

Revoyons notre application en revisitant notre base de données. Nous pourrions alors penser à ce type de structure :&#x20;

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

Avec cette vue, nous identifions quelques changements à opérer :&#x20;

* le model devient une foreign key "serie\_id" s'appuyant sur la table series
* la brand elle se veut maintenant "brand\_id" qui elle s'appuie sur brands

Le choix d'appeler nos modèles de voiture "series" consiste à éviter les conflits de classe entre les Model natif de Laravel et le Model éventuel de voiture. Nous pourrions, et aurions rencontrer une erreur du type :&#x20;

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

Cela va donc nous obliger à créer 2 tables supplémentaires. Je vous propose avant de continuer cette documentation d'essayer de votre côté de générer les fichiers de migrations de ces deux tables. :smile::smile::smile:

{% hint style="info" %}
Ci-dessous la création des deux tables en ligne de commande (CLI)
{% endhint %}

### On créé les clés étrangères

Il est tout à fait faisable, et même conseillé de créer la globalité des éléments nécessaires en une seule commande :&#x20;

```shell
php artisan make:model Serie -mcr
# On remarquera l'application des flags -mcr à notre noueau model
# Cela va nous générer la migration (m) ainsi que le 
# controller (c) ainsi que ses resources (r) que nous allons voir ensuite
```

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

La création de notre migration reprend les conventions définies un peu plus haut dans cette page, notre Controller a bien été généré et notre Model bien entendu créé.

Allons maintenant modifier notre migration pour la rendre opérationnel et à nôtre goût.

```php
// ******_create_series_table.php
 Schema::create('series', function (Blueprint $table) {
  $table->id();
  $table->string("name")->unique(); 
  // On applique ci-dessus un unique pour éviter les doublons
  // $table->timestamps(); On supprime cette ligne car inutile
});
```

Faisons ensuite les mêmes manipulations avec le Model Brand :&#x20;

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

```php
// ******_create_brands_table.php
Schema::create('brands', function (Blueprint $table) {
    $table->id();
    $table->string("name")->unique();
    // $table->timestamps(); On supprime cette ligne car inutile
});

```

{% hint style="info" %}
Nous possédons dorénavant l'intégralité des tables nécessaires à la création de foreign keys, il ne nous reste qu'à indiquer à notre model Car qu'il doit tenir compte des deux autres que sont Serie et Brand.
{% endhint %}

#### Attention aux timestamps !

{% hint style="danger" %}
**IMPORTANT :** Le fait de commenter les timestamps de nos migrations n'est plus suffisant, il est également nécessaire de préciser à Laravel, et surtout à nos Models que nous ne souhaitons plus les avoir dans nos requêtes.
{% endhint %}

Voici donc la marche à suivre pour les désactiver sur un Model, prenons l'exemple de **Brand :**&#x20;

```php
class Brand extends Model
{
    public $timestamps = false; // ICI cette ligne à ajouter

    use HasFactory;
}
```

Pour cela retournons voir notre migration "cars", et remplaçons les valeurs souhaitées :&#x20;

```php
// ******_create_cars_table.php
public function up()
{
    Schema::create('cars', function (Blueprint $table) {
        $table->id();

        // $table->string("model");
        $table->foreignId("serie_id")->constrained();
        // $table->string("brand");
        $table->foreignId("brand_id")->constrained();
        
        $table->integer("power_fisc")->unsigned();
        $table->integer("power_dyn")->unsigned();
        $table->string("color");
        $table->float("price")->unsigned();

        $table->timestamps();
    });
}
```

Une fois cette modification effectuée, on relance un php artisan migrate, mais quelque peu différent, avec un refresh qui va recréer l'intégralité de nos tables :&#x20;

```
php artisan migrate:refresh
```

Et là, c'est le DRAME !

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

Il s'agit d'une erreur courante avec les migrations, nous demandons à notre table **cars** de référencer **serie\_id** sur la base de la table **series**, qui elle n'est pas encore créée, eh oui regardez bien !!! :joy::joy::joy:

Nous allons donc effectuer un petit ajustement, demander à Laravel de ne créé la table cars qu'après création des deux autres, et la solution est très rudimentaire :&#x20;

{% hint style="warning" %}
Nous allons renommer notre fichier de migration cars de façon à ce qu'il se situe en fin de file de notre dossier migrations, car en effet, Laravel **traite les fichiers par ordre alphabétique !**
{% endhint %}

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

On va lancer la commande suivante pour vider l'existant, et réinitialiser le tout :&#x20;

```
php artisan migrate:fresh
```

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Nos tables sont maintenant créées et nos foreign keys valides ! **FELICITATIONS !** :tada:
{% endhint %}

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

### Les fonctions liées aux contraintes

Après avoir défini nos contraintes au travers des migrations, nous allons également avoir besoin, pour nos futurs requêtes en BDD, de créer une liaison de nos différents modèles entre eux. En effet les contraintes MySQL ne sont là que pour des raisons liées à la sécurité et aux relations, et il va donc falloir réfléchir CRUD.

Le fonctionnement :&#x20;

Au vu de notre future web app, nous pouvons aisément dire "qu'une voiture aura **UNE** marque et **UNE** série". Traduisons maintenant ceci en langage Model. Et pour cela, rendons nous dans notre modèle Car :&#x20;

```php
// Car.php

class Car extends Model
{
    use HasFactory;

    public function serie()
    {
        return $this->belongsTo(Serie::class);
    }

    public function brand()
    {
        return $this->belongsTo(Brand::class);
    }
}
```

{% hint style="info" %}
Notre véhicule n'ayant qu'une marque, remarquons la méthode **brand indiquée au singulier,** idem pour la méthode **serie qui est également au singulier** puisque notre voiture ne possède qu'une série.
{% endhint %}

Allons maintenant faire l'inverse dans nos Model Brand et Serie :&#x20;

```php
// Brand.php

class Brand extends Model
{
    public $timestamps = false;

    use HasFactory;

    public function cars()
    {
        return $this->hasMany(Car::class);
    }
}
```

```php
// Serie.php

class Serie extends Model
{
    public $timestamps = false;

    use HasFactory;

    public function cars()
    {
        return $this->hasMany(Car::class);
    }
}
```
