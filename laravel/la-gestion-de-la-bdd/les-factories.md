---
description: >-
  Les factories, que nous traduirons par usines en français, vont nous permettre
  de fabriquer une certaines quantités de données, et ce rapidement, voyons cela
  !
---

# Les factories

## Pourquoi des factories ?

Le Framework Laravel est en général utilisé pour créer des applications web modernes de manière ultra-rapide, et il paraît logique que **la seule création des tables de notre base de données ne permet pas de tester correctement notre code** et nos composants.

C'est pourquoi les factories vont nous être grandement utiles, elles vont nous **permettre de générer de fausses données (dummy datas) et de peupler avec une quantité de notre choix** le nombre de lignes dans chacune des tables configurées.

Imaginez un instant qu'en une seule ligne de commande, **quelques 20 voitures, 3 marques et 4 séries seraient** alors déjà intégrées à notre table dédiée aux **annonces.**

{% hint style="info" %}
Il s'agit bien de la promesse de Laravel avec l'usage de ses factories, ajouter du contenu en masse en une seule ligne de code. _Enfin une ligne pas tout à fait ..._
{% endhint %}

## **Création d'une factory**

Comme a son habitude, Laravel nous propose de créer manuellement une factory, ou alors de la générer depuis notre CLI, ce que nous allons bien évidemment choisir comme solution.

```shell
php artisan make:factory BrandFactory
```

Cette action va nous générer un nouveau fichier dsiponible dans **database/factories :**&#x20;

```php
// database/factories/BrandFactory.php
<?php

namespace Database\Factories;

use Illuminate\Database\Eloquent\Factories\Factory;

/**
 * @extends \Illuminate\Database\Eloquent\Factories\Factory<\App\Models\Brand>
 */
class BrandFactory extends Factory
{
    /**
     * Define the model's default state.
     *
     * @return array<string, mixed>
     */
    public function definition()
    {
        return [
            //
        ];
    }
}

```

Remarquons alors la présence de **l'importation de notre class Brand en ligne 9**, qui permettra de **vérifier la concordance des colonnes** avec les données que nous allons soumettre.

## Préparation des données

Ajoutons maintenant les contenus envisagés dans notre zone de retour :&#x20;

```php
public function definition()
{
    return [
        // L'id est autoincrémenté donc pas nécessaire
        // Nous définissons ensuite grâce au Faker le type de données souhaitées
        "name" => $this->faker->words(rand(1,2), true)
        // Il s'agira donc d'une chaine de caractères de 1 ou 2 mots
    ];
}
```

{% hint style="info" %}
Vous pouvez bien entendu faire de même avec SerieFactory
{% endhint %}

Enfin, occupons-nous de la partie la plus importante, la CarFactory qui elle possède plus de colonnes :&#x20;

```php
<?php

namespace Database\Factories;

use App\Models\Brand;
use App\Models\Serie;
use Illuminate\Database\Eloquent\Factories\Factory;

/**
 * @extends \Illuminate\Database\Eloquent\Factories\Factory<\App\Models\Car>
 */
class CarFactory extends Factory
{
    /**
     * Define the model's default state.
     *
     * @return array<string, mixed>
     */
    public function definition()
    {
        return [
            "power_dyn" => $this->faker->numberBetween(60, 450),
            "power_fisc" => $this->faker->numberBetween(4, 25),
            "color" => $this->faker->colorName(),
            "price" => $this->faker->randomFloat(2, 7_500, 150_000),
            "serie_id" => Serie::all()->random()->id,
            "brand_id" => Brand::all()->random()->id,
        ];
    }
}

```

Beaucoup de points à aborder concernant ce code !

* Tout d'abord, Faker nous propose une solution globale de fausses datas, et sa documentation est accessible ici : [https://github.com/fzaninotto/Faker](https://github.com/fzaninotto/Faker)
* Ensuite, nous pouvons remarquer l'appel au hasard (random), d'un id provenant des Brands et Series existantes
* Enfin, pour utiliser les random de Brands et Series, il est nécessaire d'ajouter les **use en début de page** afin de fournir leur namespace&#x20;

{% hint style="success" %}
Nous en avons terminé avec la création des fausses données, nous allons donc demander au Seeder (tiens un nouveau jouet !) d'éxécuter la création de fausses données
{% endhint %}

## Utilisation du Seeder

Avant tout, nous pouvons remarquer un 3e dossier situé dans le répertoire **database**, il s'agit du dossier **seeders, qui ne contient qu'un DatabaseSeeder.php.**

C'est à cet endroit que vous allez donner l'ordre de créer tant de Cars, ou de Series, ou encore de Brands.

**Ouvrons ce fichier** et effectuons quelques modifications :&#x20;

```php
<?php

namespace Database\Seeders;

use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;

class DatabaseSeeder extends Seeder
{
    /**
     * Seed the application's database.
     *
     * @return void
     */
    public function run()
    {
        \App\Models\Brand::factory(3)->create();
        \App\Models\Serie::factory(4)->create();
        \App\Models\Car::factory(20)->create();
    }
}

```

Dans l'exemple ci-dessus, nous allons lui demander de créer :&#x20;

* 3 Marques (Brand)
* 4 Séries (Serie)
* 20 Véhicules (Car)

{% hint style="warning" %}
**ATTENTION :** Tout comme dans les migrations, l'ordre des demandes de création est capital si on ne veut pas rencontrer d'erreur, il est donc important de **créer les marques et séries avant de les associer à un véhicule**
{% endhint %}

Pour envoyer nos données à notre base de données, une commande pour changer :&#x20;

```shell
php artisan db:seed
# qui lancera le DatabaseSeeder.php
```

{% hint style="success" %}
**FELICITATIONS :** Vous avez créé une base de données complètes et remplies de data à exploiter. On peut maintenant retourner voir nos Controllers !&#x20;
{% endhint %}
