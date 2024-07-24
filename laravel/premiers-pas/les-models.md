---
description: >-
  Troisième partie de ce MVC, les Models, que l'on peut définir comme les
  données, issues d'une base ou pas, que nous allons traiter avant affichage.
---

# Les models

## C'est quoi le modèle ?

Tout comme un Controller, un modèle est en réalité une Classe PHP qui nous permettra d'instancier des Objets de type "Classe".

Ce qui sera un sacré avantage lorsque nous parlerons, un peu plus loin, de Eloquent ORM.



## Générer un nouveau modèle

En attendant, créons notre premier Model en exécutant la commande suivante :&#x20;

```
php artisan make:model Car
```

{% hint style="info" %}
Un Model **commence toujours par une majuscule,** et s'écrit toujours **au singulier**
{% endhint %}

Nous remarquons la présence d'un nouveau fichier situé dans le **répertoire app/Models/ :**&#x20;

```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class Car extends Model
{
    use HasFactory;
}

```

Rien de sensationnel pour l'instant, mais nous avons bien mis en place un nouveau modèle au sein de notre application, ce qui nous servira beaucoup dans la suite de ce tutoriel.

{% hint style="info" %}
**Bon à savoir :** \
Un modèle n'est en aucun cas l'instigateur de la table en base de données
{% endhint %}
