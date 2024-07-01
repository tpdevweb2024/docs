# Composer et les packages

Composer est un gestionnaire de dépendances pour PHP. Il permet de gérer les packages nécessaires à votre projet de façon simple et efficace.

### Pourquoi utiliser Composer ?

* **Facilité de gestion des dépendances** : Installez et mettez à jour les packages facilement.
* **Autoloading** : Charge automatiquement les classes sans nécessiter d'inclusion manuelle.
* **Versioning** : Maintenez des versions compatibles des packages.
* **Communauté** : Accès à une large variété de packages de qualité.

### Installation

**Windows**

1. Téléchargez l'installateur de Composer depuis le site officiel [getcomposer.org](https://getcomposer.org/).
2. Exécutez l'installateur et suivez les instructions à l'écran.
3. Vérifiez l'installation en ouvrant une invite de commande et en tapant `composer`.

**Linux**

1. Ouvrez un terminal.
2.  Téléchargez Composer en exécutant :

    ```
    php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
    php composer-setup.php
    php -r "unlink('composer-setup.php');"
    ```

#### Mac

1. Ouvrez un terminal.
2.  Installez Composer en utilisant [Homebrew](https://brew.sh/) :

    ```sh
    brew install composer
    ```

## L'utilisation de Composer

Après avoir installé Composer, vous pouvez créer un fichier `composer.json` pour définir les dépendances de votre projet :

```json
{
    "require": {
        "monolog/monolog": "^2.0"
    }
}
```

Ensuite, exécutez la commande suivante pour installer les dépendances :

```sh
composer install
```

Cela créera un dossier `vendor` contenant toutes les bibliothèques nécessaires à votre projet. Pour ajouter d'autres dépendances, utilisez :

```sh
composer require {vendor}/{package}
```

Pour mettre à jour les dépendances, utilisez :

```sh
composer update
```

## L'autoload et le PSR

L'autoloading est une fonctionnalité clé de Composer, permettant de charger automatiquement les classes PHP nécessaires à votre projet **sans avoir à les inclure manuellement**.&#x20;

Pour configurer l'autoloading, vous pouvez spécifier les namespaces et les chemins associés dans le fichier `composer.json` de votre projet.

Voici un exemple de configuration d'autoloading utilisant le standard PSR-4 :

```json
{
    "autoload": {
        "psr-4": {
            "App\\": "src/"
        }
    }
}
```

Après avoir ajouté cette configuration, vous devez exécuter la commande suivante pour que Composer génère les fichiers nécessaires :

```sh
composer dump-autoload
```

{% hint style="info" %}
Cela permettra à Composer de générer un fichier `vendor/autoload.php` que vous pouvez inclure dans votre projet pour charger automatiquement les classes selon votre configuration.
{% endhint %}

## La librairie officielle

La librairie officielle des packages de Composer se trouve sur [Packagist](https://packagist.org/). Packagist est le dépôt central qui contient les informations de tous les paquets disponibles pour Composer. Vous pouvez y rechercher des paquets, consulter leurs versions, dépendances et lire la documentation associée.

Lorsque vous trouvez un package que vous souhaitez utiliser, vous pouvez l'ajouter à votre projet en exécutant la commande suivante dans votre terminal, en remplaçant `vendor/package` par le nom du package souhaité :

```sh
composer require vendor/package
```

Cela mettra à jour votre fichier `composer.json` et téléchargera le package et ses dépendances dans le répertoire `vendor`.

## L'objectif de Composer, la collaboration

L'objectif principal de Composer est de faciliter la gestion des dépendances dans les projets PHP, mais il va au-delà en permettant une meilleure collaboration entre les développeurs. En utilisant Composer, les équipes peuvent :

* Assurer la cohérence des dépendances dans différents environnements de développement.
* Partager facilement les configurations de projet à travers le fichier `composer.json`.
* Maintenir des versions stables grâce à la gestion des versions stricte de Composer.
* Intégrer et utiliser des bibliothèques tierces de manière simple et contrôlée.

{% hint style="success" %}
Utiliser Composer non seulement rationalise le processus de développement, mais améliore également la productivité et réduit le risque de conflits de version, facilitant ainsi une collaboration plus efficace entre les membres de l'équipe.
{% endhint %}
