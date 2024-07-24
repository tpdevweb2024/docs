# La gestion de la BDD

Bien que Laravel puisse fonctionner sur PostgreSQL ou même en SQLite, nous allons (bien évidemment) axer notre documentation vers MySQL, qui est au delà du plus conseillé, le service le plus adapté à Laravel.

## La création de notre base

Comme vu un peu plus tôt dans cette doc, il est nécessaire de créer une base de données (vide) via l'outil de votre choix : PhpMyAdmin, HeidiSQL, TablePlus, DBeaver ou encore la CLI mysql.

Il faut alors veiller à bien vérifier si notre configuration du fichier .env est bonne, pour rappel :&#x20;

```
// Veillez à remplacer vos identifiants de connexion à votre BDD
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laracars
DB_USERNAME=root
DB_PASSWORD=
```

Puis nous allons vérifier la liaison en exécutant un script dans notre terminal :&#x20;

```shell
php artisan migrate
```

Cette commande va récupérer les fichiers de migration et les transformer en tables dans notre BDD.&#x20;

{% hint style="warning" %}
**Les migra... quoi ?**\
Les migrations, un formidable outil que nous allons découvrir dans le chapitre suivant.
{% endhint %}

Si le retour de votre commande n'émet aucune erreur, alors nous sommes bons pour passer à la suite. :clap::clap::clap:

## Supprimer toutes les données d'une base

Il n'est pas possible de supprimer la Base de données depuis Laravel, mais la vider de la globalité des datas est out à fait possible en revanche, pour cela une nouvelle commande :&#x20;

```shell
php artisan db:wipe
```

{% hint style="info" %}
**IMPORTANT** : Depuis la version 11, Laravel propose l'initialisation d'une BDD de type SQLite par défaut sur son installation de base, ce qui nous évite une configuration initiale si ce type de solution nous correspond.
{% endhint %}
