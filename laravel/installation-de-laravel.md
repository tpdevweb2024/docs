# Installation de Laravel

## Initialisation d'un projet Laravel

Il existe deux façons de créer une application Laravel :

* En utilisant le programme d'installation de Laravel
* En installant le package Laravel et en utilisant composer et la commande create-project.

### Installation Windows

Il est complètement faisable, et conseillé d'utiliser l'installateur Laravel, qui est accessible au moyen d'une ligne de script en CLI :&#x20;

```shell
composer global require "laravel/installer"
```

Cette commande va installer globalement _(sur votre poste)_ l'installateur Laravel, ce qui aura pour but de faciliter la commande d'installation d'une nouvelle instance.

Profitons-en pour créer notre nouveau projet :&#x20;

```shell
laravel new laracars
```

### Installation Mac OS

{% hint style="danger" %}
Dans l'environnement Mac OS, le programme d'installation Laravel n'est pas disponible et l'utilisation de composer est alors la seule issue.
{% endhint %}

Voyons alors comment initialiser notre projet avec composer :&#x20;

```shell
composer create-project --prefer-dist laravel/laravel laracars
```

## La base de données

Pour utiliser Laravel comme il se doit, nous aurons besoin d'une base de données, et nous choisirons plutôt MySQL pour une question de connaissances des bases.

{% hint style="info" %}
_Laravel fonctionne aussi parfaitement avec PostgreSQL si vous le souhaitez_
{% endhint %}

Ainsi il nous **suffit de créer au sein de notre SGBD** (PhpMyAdmin par exemple), une **nouvelle** bases de données au format utf-8, que nous nommerons **laracars**&#x20;

## Après l'installation

Cette action aura pour but de nous créer un nouveau dossier appelé **laracars,** qui contiendra l'ensemble de notre structure.

{% hint style="warning" %}
Remarquons la présence d'un fichier package.json, vous savez ce que cela veut dire, il y a probablement des dépendances à installer, alors **exécutons les commandes** : \
\
cd laracars\
npm install
{% endhint %}
