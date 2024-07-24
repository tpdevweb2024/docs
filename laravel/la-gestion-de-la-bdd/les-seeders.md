---
description: >-
  L'utilisation des Seeders est une des fonctionnalités les plus intéressantes
  de Laravel et de Eloquent, il s'agit là de peupler notre base de données de
  contenus plus ou moins proche du réel.
---

# Les seeders

## C'est quoi un Seeder ?

Le Seeder dans Laravel est le meilleur ami des factories, il permet d'effectuer la liaison entre chaque factory précédemment créée et la base prête à les recevoir.

Par défaut, Laravel nous donne accès à un Seeder appelé DatabaseSeeder :

```php
<?php

namespace Database\Seeders;

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
        // \App\Models\User::factory(10)->create();
    }
}

```

Celui-ci ne comporte pas spécialement d'informations, si ce n'est qu'une méthode **run** est d'ores et déjà définie et nous montre, de manière commenté, l'appel à une éventuelle factory.

{% hint style="info" %}
Dans l'exemple ci-dessus, nous voyons alors que le Seeder, si nous décommentons la ligne User::factory, va utiliser notre factory 10 fois consécutivement, et dans chaque boucle nous créer une instance de modèle de type User.&#x20;

Pour résumer, **cet appel nous créera 10 lignes dans notre table users**.  Magique non ?
{% endhint %}

Pas tant que ça en réalité, car **il a fallut paramétrer notre factory** pour lui permettre la création.

## Envoyer une Factory au Seeder

Comme indiqué ci-dessus, pour créer à la volée des lignes dans nos différentes tables, notre Seeder va nous réclamer une "Factory" type, et s'appuiera sur celle-ci pour exécuter sa tâche.

Nous avions précédemment créer une factory appelée CarFactory, et nous avions utilisé le Faker de Laravel pour générer des dummy datas, utilisons alors cette fabrique pour créer une trentaine d'annonces.

Pour cela, modifions directement notre DatabseSeeder.php :

```php
<?php

namespace Database\Seeders;

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
        // \App\Models\User::factory(10)->create();
        \App\Models\Car::factory(30)->create();
    }
}

```

{% hint style="success" %}
Remarquez la présence de cette nouvelle ligne Car::factory, qui vient **s'appuyer sur notre Model Car et utiliser la factory AnnonceFactory** pour générer 30 annonces sur la base des réglages préétablis. \
Admirez maintenant le résultat en base de données.
{% endhint %}
