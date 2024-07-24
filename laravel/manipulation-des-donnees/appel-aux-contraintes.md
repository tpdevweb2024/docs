# Appel aux contraintes

Souvenez-vous des méthodes créées au sein de nos Models un peu plus tôt.

Et bien il va être temps de s'en servir, car en ayant récupérer l'intégralité de notre collection, vous ne le voyez pas encore mais nous avons bel et bien les informations liées aux clés étrangères dans celle-ci.

Changeons alors quelque peu notre vue index :&#x20;

```php
// index.blade.php

@extends("layouts.app")

@section("content")
    <h1>Toutes nos voitures</h1>
    <ul>
        @foreach($cars as $car)
            <li>{{ $car->serie->name }} {{ $car->brand->name }} 
            : {{ $car->price }}</li>
        @endforeach
    </ul>
@endsection
```

<figure><img src="../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Vous l'aurez compris, en appelant notre $car, nous allons lui demandé d'aller exploiter le tableau Brand au travers de la méthode brand() puis de saisir la colonne name, identique pour le modèle de Serie. :smile:\
Plutôt cool non ?
{% endhint %}
