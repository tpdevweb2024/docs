---
description: >-
  Nous allons commencer par nous intéresser au Routing, il s'agit de la première
  étape qui s'enclenchera lors de l'appel d'une URL, et ce peu importe la
  méthode.
---

# Le routing

## Fonctionnement

Pour comprendre le fonctionnement des routes, allons faire un petit tour du côté de notre fichier web.php situé dans le dossier routes :&#x20;

```
laracars
└─  📂 routes/
|   |   └─ 📇 web.php
```

Puis direction la première ligne de code commençant par Route, et décryptons ensemble ce que tout cela signifie.&#x20;

```php
<?php
// routes/web.php

use Illuminate\Support\Facades\Route;

/*
|--------------------------------------------------------------------------
| Web Routes
|--------------------------------------------------------------------------
|
| Here is where you can register web routes for your application. These routes are loaded by the RouteServiceProvider within a group which
| contains the "web" middleware group. Now create something great!
|
*/

Route::get('/', function () {
    return view('welcome');
});
```

Ce bloc nous fait comprendre qu'une instance d'objet Route, passée via paramètre GET et possédant l'URL demandée "/" (la racine du domaine), doit nous retourner une méthode s'appelant view, et passant en paramètre la vue "welcome".

## Créer une nouvelle route

Pour créer une nouvelle route, nous aurons besoin d'utiliser l'instance Route, lui attribuer une méthode et l'URL qui viendra à déclencher son usage, puis enfin définir une action à exécuter en cas de correspondance.

### Sans utilisation d'une vue

```php
Route::get("/ma-route", function() {
    return "<h1>Hello World</h1>";
});
```

Ce qui nous donne :&#x20;

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

### Avec utilisation d'une vue

Pour créer une route utilisant une vue, il est alors possible d'utiliser la méthode **view** native dans Laravel, en y précisant le nom de la vue à exploiter :&#x20;

On commence par écrire notre code :&#x20;

```php
Route::get("/ma-route-avec-vue", function () {
    return view("ma-vue"); // On y passe le nom de la vue à utiliser
});
```

Puis nous allons créer notre vue :&#x20;

```
laracars
└─  📂 resources/
       └─  📂 views/
              └─ 📇 welcome.blade.php
              └─ 📇 ma-vue.blade.php
```

Ce qui nous donnera :&#x20;

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

### Avec utilisation d'un Controller

Nous n'avons pas encore compris ce qu'est un controller, mais il est bon de savoir malgré tout qu'il s'agit de l'utilisation la plus courante des Routes au sein des frameworks MVC.

La syntaxe est elle un peu particulière :&#x20;

```php
Route::get("/ma-route-avec-controller", [ MyController::class, "about-us" ]);
```

Dans ce cas de figure, il est très conseillé de nommer vos routes, en y combinant la méthode name().

```php
Route::get("/ma-route-avec-controller", [ MyController::class, "about-us" ])
    ->name("route.name");
```
