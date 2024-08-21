---
description: >-
  Le contrôleur est en quelque sorte le point de liaison entre Model et View, et
  même si nous n'avons pas encore évoqué les models, voyons comment fonctionne
  le controller
---

# Les controllers

## Création d'un Controller

Nous y sommes, nous entrons dans une nouvelle phase de notre apprentissage, avec la création des controllers, qui comme beaucoup de fonctionnalités Laravel, se fait depuis notre [CLI](https://fr.wikipedia.org/wiki/Interface\_en\_ligne\_de\_commande).

Voici donc la commande à taper pour créer une nouveau Controller :&#x20;

### Utilisation de la CLI

```shell
php artisan make:controller CarController
```

{% hint style="success" %}
Cette action va nous générer un nouveau fichier de Classe dans le dossier \
**app/Http/Controlllers** appelé **CarController.php**
{% endhint %}

### Contenu du nouveau fichier

Allons vite voir le contenu de ce nouveau fichier :&#x20;

```php
// app/Http/Controllers/CarController.php

<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class CarController extends Controller
{
    //
}
```

Nous y remarquons une Classe PHP portant le nom choisi durant la création de celui-ci en CLI, on remarque aussi la présence d'une namespace, que l'on peut traduire comme un espace de travail propre à ce Controller, ainsi si une autre classe CarController existait dans un autre namespace, nous pourrions les utiliser indépendamment.

{% hint style="warning" %}
Tout ça c'est bien, mais il est vide non ?!!!
{% endhint %}

## On créé notre première méthode

### Le code à frapper

En effet, ce Controller est "pour l'instant" vide. C'est pourquoi nous allons ensemble créer une première [méthode PHP](https://www.php.net/manual/fr/language.oop5.basic.php), qui aura pour but d'afficher simplement l'une de nos vues, en l’occurrence notre vue **"cars",** qui à termes affichera nos véhicules.

```php
class CarController extends Controller
{
    public function index()
    {
        return view('index');
    }
}
```

### Les ajustements des routes

Qui dit utilisation d'un Controller pour afficher une vue, dit automatiquement ajout de cette route aux routes existantes.

Nous avions souvenez-vous dans les chapitres précédents, écrit ceci :&#x20;

```php
Route::get("/cars", function () {
    return view("index");
});
```

Et bien l'utilisation du Controller va nous simplifier quelque peu cette Route, voyons donc maintenant la nouvelle écriture à utiliser :&#x20;

```php
Route::get("/cars", [CarController::class, "index"]);
```

{% hint style="info" %}
Vous allez vous dire, cela fonctionne mais ça n'apporte rien de plus ? En effet, pour l'instant nous ne voyons aucunes différences et donc que peu d'utilité.
{% endhint %}

Dans le cas où votre page affiche un message d'erreur : <mark style="color:red;">**Target class \[CarController] does not exist**</mark>** :** il est alors nécessaire d'importer le controller en début de page, VS Code ou tout autre IDE devrait le faire de manière automatique, néanmoins il suffit de vérifier le présence de cette ligne avant votre première Route :&#x20;

```php
use App\Http\Controllers\CarController;
```

## Le passage de données

### Passage dans des vues

Évoquons maintenant l'avantage, et même l'intérêt d'utiliser des Controllers dans notre [pattern](broken-reference).

Revenons à notre méthode services, et passons lui des données à exploiter dans notre vue :&#x20;

```php
public function index()
{
    // On définit notre variable
    $data = "Hello, je suis les datas";
    // on passe notre variable en 2e arguement de la function view
    // dans un tableau avec clé de notre choix, ici "data"
    return view('index', [
        "data" => $data
    ]);
}
```

Allons maintenant voir côté vue :&#x20;

```php
// resources/views/index.blade.php

@extends("layouts.app")

@section("content")
    <h1>{{ $data }}</h1>
@endsection

```

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
Génial !!! nous venons de faire transiter des données entre le cœur de notre appli et la vue finale du client (internaute). :thumbsup::thumbsup::thumbsup:
{% endhint %}

### Afficher nos données au format JSON

Aussi, l'un des gros atouts de Laravel est sa polyvalence, nous pourrions par exemple vouloir récupérer nos données dans un format JSON, pour un éventuel affichage via l'API Fetch JS.

Et bien pour cela, il suffit de retourner nos datas, et ... c'est tout !!!&#x20;

Preuve en code ci-dessous, où nous allons modifier quelques instants notre méthode services du CarController :&#x20;

```php
 public function index()
{
    $data = "Hello, je suis les datas";
    return $data;
}
```

{% hint style="warning" %}
Et là vous vous dites : **le rendu est pas terrible** !
{% endhint %}

En effet il s'agit de plain text, sans style ni aucun rendu, essayons maintenant de passer un tableau à la place :&#x20;

```php
public function index()
{
    $data = [
        "firstName" => "John",
        "lastName" => "Doe",
        "age" => 25
    ];
    return $data;
}
```

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
_Beaucoup **mieux** n'est-ce pas ?_
{% endhint %}

Je vous laisse imaginer le type de tableau que nous pourrions passer à cette vue, mais surtout comment s'y prendre pour le composer.
