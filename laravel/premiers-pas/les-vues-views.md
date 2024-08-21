---
description: >-
  Il s'agit de la partie que l'on peut considérée comme interface graphique de
  notre app
---

# Les vues (views)

## Emplacement des vues

Pour retrouver l'intégralité de nos vues, il suffit de se rendre dans le répertoire **resources** puis **views** :&#x20;

```
└─  📂 resources/
    └─  📂 views/
        └─  📇 welcome.blade.php
```

{% hint style="info" %}
Toute nouvelle vue devra donc se situer dans ce dossier. Néanmoins il est toutefois possible de créer des répertoires afin de faciliter l'organisation de celles-ci.
{% endhint %}

## Le format Blade

Il s'agit d'un engine templating (moteur de template), son rôle est de compiler notre code en un format lisible _(HTML)_ par nos internautes. Sa syntaxe se veut simple et proche d'autres moteurs comme Twig par exemple.

{% hint style="info" %}
L'usage du format Blade ne doit se faire que sur des vues (Views) au sein de notre projet. Il nous permettra un peu plus tard de compiler et adapter nos données issues de notre base de données (Models)&#x20;
{% endhint %}

### La syntaxe

Les fichiers utilisant Blade se terminent forcément par l'extension \*.blade.php.

La syntaxe est proche du format HTML combiné à du PHP, mais n'utilise pas les balises habituelles. Prenons l'exemple d'une variable à afficher.

<mark style="color:red;">Ce qu'il ne faut pas faire :</mark>&#x20;

```php
<div>
    <?= $variable ?>
</div>
```

<mark style="color:green;">Ce qu'il faut plutôt faire :</mark>&#x20;

```php
<div>
    {{ $variable }}
</div>
```

## Les gabarits de page

Appelé également **Layout**, le gabarit permet de créer de véritable structure de page prédéfinie. Ainsi il nous suffira d'indiquer les contenus dits variables, et donc d'uniformiser l'aspect esthétique de notre future application.

### Créer un gabarit

Un gabarit se créé de la même façon que la création d'une vue, néanmoins par convention nous nommerons toujours notre gabarit principal **app.blade.php**, que nou sstockerons au sein d'un dossier **layouts**

```
└─  📂 resources/
    └─  📂 views/
        └─  📂 layouts/
            └─  📇 app.blade.php 
        └─  📇 welcome.blade.php
```

```php
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Laracars</title>
</head>
<body>
    @yield("content") // Remarquons l'ajout d'un emplacement nommé content
</body>
</html>
```

{% hint style="success" %}
Les layouts peuvent être multiples, et sont personnalisables à souhait
{% endhint %}

### Utiliser un gabarit

Après avoir défini un gabarit de page, nous allons donc pouvoir nous en servir sur les pages de notre choix.

Pour cela, nous allons prendre connaissance avec une autre directive fournie par Blade, il s'agit de l'héritage, que nous allons utiliser dans la vue (ou page) **services.blade.php** :&#x20;

```php
//services.blade.php

@extends("layouts.app")

@section("content")

    // Le contenu de votre page ici
    <h1>Hello les gens, je suis une vue héritant de layouts.app</h1>
    
@endsection
```

{% hint style="info" %}
Remarquons la présence de la directive [@extends](https://laravel.com/docs/9.x/blade#extending-a-layout) qui a pour but de passer en argument le nom de la vue à aller chercher, en l'occurence **app**, se situant dans le folder **layout,** que nous associons au moyen du point (.) : ("**layouts.app")**
{% endhint %}

Aussi, nous avons déterminé une zone d'emplacement, appliquée grâce à la directive @yield du layout, que nous avions appelée "content", et que nous remplissons ainsi avec l'usage de @section("content") et @endsection, tags de début et de fin de zone.

## Afficher notre nouvelle vue

Pour afficher notre vue nouvellement créée, nous allons ajouter notre route comme nous avons appris à le faire [précédemment ](broken-reference):&#x20;

```php
Route::get("/services", function () {
    return view("services");
});
```

## Les includes

Comme en PHP natif, il est tout à fait possible d'inclure des fichiers à l'intérieur d'une vue, et pour cela nous utiliserons la directive @include :&#x20;

Mais d'abord créons un fichier **header**.blade.php, se situant dans le dossier **layouts** puis **partials**, que nous allons ajouter pour l'occasion :&#x20;

```php
// layouts/partials/header.blade.php

<header>
    <nav>
        <ul>
            <li>Home</li>
            <li>About</li>
            <li>Services</li>
        </ul>
    </nav>
</header>
```

```php
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Laracars</title>
</head>
<body>
    // On y ajoute un header 
    // qui servira toutes les pages utilisant ce layout
    @include("layouts.partials.header") 
    @yield("content") 
</body>
</html>
```

<figure><img src="../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>
