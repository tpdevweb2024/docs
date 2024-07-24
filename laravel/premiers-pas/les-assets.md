---
description: >-
  Comme nous l'avons vu, chaque nouvelle version apporte son lot de nouveautés,
  cette version 9 nous a apporté quant à elle le très prometteur Vite JS
---

# Les assets

## C'est quoi les assets ?

Les assets sont les ressources de style et de dynamisme que nous connaissons dans tout projet web quel qu'il soit. Ainsi nous y retrouvons les fichiers JS et CSSS habituels. Nous verrons également en bas de page comment y intégrer Sass pour plus de confort.

{% hint style="success" %}
Plusieurs raisons ont poussé à effectuer une migration de Webpack vers Vite, mais l'une des plus grosses évolutions est sans doute l'apparition du HMR, autrement dit rafraichissement automatique de la page, que les dev Frontend adorent !!! :tada:
{% endhint %}

## Lier un fichier de style CSS

Si nous prenons la documentation du MDN, lier un fichier de feuille de style CSS est simple et s'effectue comme ceci :&#x20;

```html
<link rel="stylesheet" href="css/style.css" />
```

Mais dans Laravel, comme dans une majorité de frameworks existants sur le marché, nous devrons effectuer cette démarche d'une façon différente. Reprenons notre structure de base Laravel :&#x20;

```
laracars
└─  📂 app/
└─  📂 bootstrap/
└─  📂 config/
└─  📂 database/
└─  📂 lang/
└─  📂 node_modules/
└─  📂 public/
└─  📂 resources/ 
└─  📂 routes/
└─  📂 storage/
└─  📂 tests/
└─  📂 vendor/
```

Nous allons nous concentrer sur le dossier **resources**, qui est <mark style="color:red;">**LE SEUL DOSSIER**</mark> qui vous permettra de faire des modifications de style.&#x20;

Et plus particulièrement au dossier **css**.

Une fois dans ce fichier, vous pourrez alors écrire votre code CSS comme vous en avez l'habitude. Néanmoins, Laravel n'effectue pas la liaison de manière automatique à ce fichier, nous devrons alors ajouter un @vite, directive d'association de fichier de style à notre vue courante, qui peut d'ailleurs être un layout.

Voyons ce que cela donne en termes de syntaxe :&#x20;

```php
// layouts.app

<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Laracars</title>
    // ICI NOTRE @vite qui inclut un array de fichiers CSS (un seul ci-dessous)
    @vite(['resources/css/app.css']) 
</head>
<body>
    @yield("content") // Remarquons l'ajout d'un emplacement nommé content
</body>
</html>
```

## Ajouter nos scripts

Et bien comme ci-dessus avec nos feuilles de style, il va s'agir de reproduire la même procédure, mais cette fois avec nos scripts JS, ce qui donne à notre directive @vite l'aspect suivant :&#x20;

```php
@vite([ 'resources/css/app.css', 'resources/js/app.js' ])
```

C'est aussi simple que ça ! :clap::clap::clap:

## Ajouter Sass à notre projet (facultatif)

Pour utiliser Sass et le format .scss dans notre projet, quelques manipulations vont être nécessaires :&#x20;

* **Créer le fichier app.scss** : le terme app n'a pas d'importance, vous pouvez le nommer comme vous le souhaitez
* Ajouter la balise @vite à notre vue : oui c'est vrai que nous n'avons pas encore étudié les vues mais vous trouverez le fichier de base dans le fichier **resources/views/welcome.blade.php**

```
laracars
...
└─  📂 resources/
    └─  📂 views/
        📇 welcome.blade.php
...
```

```php
<?php
// welcome.blade.php

// ...

<title>Laravel</title>
// Ligne à ajouter
@vite(['resources/scss/app.scss', 'resources/js/app.js'])

// ...
```

{% hint style="success" %}
Et voilà, notre application est désormais prêtes à utiliser le format Sass et à écouter les changements apportés par notre fichier .scss
{% endhint %}
