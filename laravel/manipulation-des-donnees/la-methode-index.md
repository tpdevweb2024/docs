# La méthode index()

Reprenons alors notre méthode index, et cherchons à récupérer notre collection de voitures !

En temps normal, nous aurions effectuer ce type de requête (après avoir instancié PDO) :&#x20;

```php
$req = $bdd->prepare("SELECT * FROM cars");
$req->execute();
$cars= $req->fetchAll();
```

### La requête

Et bien, j'ai une très bonne nouvelle pour vous, **ceci n'est plus nécessaire !** :smile:

Avec Laravel, voici la procédure :&#x20;

```php
$cars = Car::all();
```

{% hint style="success" %}
C'est **TOUT !**
{% endhint %}

### Compréhension

Comme nous l'avons évoqué plus tôt, Laravel est un framework PHP Orienté Objet. Nos Models sont l'essence même de notre projet, et sont avants tout les points d'accroches de Eloquent ORM.

Cela signifie que sur simple utilisation d'un Model, des méthodes statiques prédéfinies sont accessibles et permettent un "requêtage" immédiat sans déclaration, et ci-dessus nous avons utilisé **la méthode all() qui a bien entendu pour but de récupérer l'intégralité des données** _(de notre collection Car)_

### Visualiser nos résultats

Maintenant que nous avons stocké dans notre variable $cars toute notre collection, voyons comment l'utiliser au sein de notre vue.

```php
// CarController.php
// ...

public function index()
{
    $cars = Car::all();
    return $cars; // Nous retourne nos résultats au format JSON
}
```

<figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
Mais c'est pas du tout ce qu'on veut ! ??? Ca dépends, mais là non nous allons les passer au travers de notre vue index.
{% endhint %}

```php
// CarController.php
// ...

public function index()
{
    $cars = Car::all();
    return view("index", [
        "cars" => $cars
    ]);
    // Ci-dessus nous indiquons à notre vue, que des données isolées dans une clé
    // "cars" ont pour valeur $cars (notre collection)
    // Ainsi nous allons récupérer une variable $cars dans notre vue Blade
}
```

Allons du côté de notre vue :&#x20;

```php
// index.blade.php

@extends("layouts.app")

@section("content")
    <h1>{{ $cars }}</h1> // On pense à remettre $cars au lieu de $data
@endsection

```

{% hint style="info" %}
Et le résultat ? NO COMMENT ! **BEURK !!!**
{% endhint %}

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

Et oui le résultat n'est pas terrible, mais il réponds à notre demande, afficher notre collection (complète) dans notre vue. C'est à ce moment que nos connaissances de PHP vont venir nous aider, souvenez-vous que lorsque nous récupérons un tableau de données, il est nécessaire de les boucler !

Allez on revisite notre vue :&#x20;

```php
// index.blade.php

@extends("layouts.app")

@section("content")
    <h1>Toutes nos voitures</h1>
    <ul>
        @foreach($cars as $car)
            <li>{{ $car->serie_id }} _ {{ $car->brand_id }} 
            : {{ $car->price }}</li>
        @endforeach
    </ul>
@endsection
```

{% hint style="info" %}
Remarquez **l'utilisation de @foreach**, une directive Blade qui reprends le système de boucle PHP foreach habituelle.
{% endhint %}

**C'est beaucoup mieux !** Pas super lisible, mais en tous les cas fonctionnel :clap::clap::clap:

<figure><img src="../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>
