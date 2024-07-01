# Slim Framework

Slim est un micro framework PHP utilisé pour créer des applications web simples mais puissantes. Il offre des fonctionnalités de base de routage, de gestion des requêtes et des réponses, très utiles pour construire une architecture RESTful.

## Installation et configuration

### Slim Package

Pour installer Slim, vous devez avoir Composer installé sur votre système. Exécutez la commande suivante pour créer un nouveau projet Slim :&#x20;

```bash
composer require slim/slim
```

Cette commande crée une structure de base pour votre application Slim avec les configurations essentielles.

### Slim Skeleton

Un équivalent plus fourni existe également et se nomme slim/slim-skeleton. Ce framework arrive avec une structure de projet complète, incluant des dossiers prédéfinis pour les modèles, les vues et les contrôleurs.&#x20;

Il propose également des fonctionnalités supplémentaires comme la gestion des dépendances via Composer, la prise en charge des middlewares, et des outils pour faciliter le développement rapide d'applications web robustes et maintenables.&#x20;

{% hint style="info" %}
Grâce à cette structure bien pensée, il devient plus facile d'organiser son code et de respecter les bonnes pratiques de développement.
{% endhint %}

Cette solution ne viens pas en complement d'un projet mais permet la création d'un nouveau projet, dont voici la commande :&#x20;

```
composer create-project slim/slim-skeleton [my-app-name]
```

## Premiers pas

Après avoir effectué un `composer init`, installons les packages suivants :&#x20;

```
composer require slim/slim
composer require slim/psr7
```

### Notre première route

Créons ensuite un dossier `public` dans lequel nous allons créer un fichier `index.php`.

```php
<?php
// public/index.php

use Psr\Http\Message\ResponseInterface as Response;
use Psr\Http\Message\ServerRequestInterface as Request;
use Slim\Factory\AppFactory;

require __DIR__ . '/../vendor/autoload.php';

$app = AppFactory::create();

$app->get('/', function (Request $request, Response $response) {
    $response->getBody()->write("Hello world!");
    return $response;
});

$app->run();
```

Ce script va créer une route à la racine de notre projet, matérialisé par le `/`, et va exécuter une function callback qui va nous créer deux paramètres-arguments, `$request` et `$response`.&#x20;

Cette réponse aura pour but de récupérer le body de notre page racine et d'y injecter un simple `Hello world!.`

Pour lancer un serveur et visualiser cette page :&#x20;

```bash
php -S localhost:8000 -t public
```

### Une seconde route : dynamique

Pour créer une route dynamique, c'est à dire capable de prendre en considération des paramètres issus de l'URL en cours, rajoutons cette route à notre fichier PHP :&#x20;

```php
$app->get('/hello/{name}', function (Request $request, Response $response, $args) {
    $name = $args['name'];
    $response->getBody()->write("Bonjour, $name");
    return $response;
});
```

{% hint style="info" %}
Nous remarquons alors l'apparition d'un troisième paramètre nommé $args, celui contient alors les informations de notre page en cours, en l'occurence $args\['name'] dans ce script.
{% endhint %}

{% hint style="success" %}
Rendez-vous alors sur la page [http://localhost:8000/hello/monde](http://localhost:8000/hello/monde) pour visualiser le rendu.
{% endhint %}

### Les réponses JSON pour créer son API

Slim facilite grandement la création de réponses JSON pour les API RESTful. Voici comment créer des réponses JSON avec Slim 4 :&#x20;

```php
$app->get('/api/data', function (Request $request, Response $response) {
    $data = ['name' => 'John', 'age' => 30];
    return $response->withJson($data);
});
```

_Ci-dessus, pour renvoyer une réponse JSON simple, vous pouvez utiliser la méthode `json()` de l'objet Response._

On peut alors optimiser le retour et faire en sorte que cette page soit parfaitement encodée :&#x20;

```php
$app->get('/api/data', function (Request $request, Response $response) {
    $data = ['name' => 'John', 'age' => 30];
    $payload = json_encode($data);
    $response->getBody()->write($payload);
    return $response
        ->withHeader('Content-Type', 'application/json')
        ->withStatus(200);
});
```

_Dans cet exemple, le type de retour sera alors en `application/json` et retournant un code HTTP 200, ce qui signifie que le retour de requête est correct._

{% hint style="success" %}
Ces méthodes vous permettent de créer facilement des réponses JSON cohérentes pour votre API RESTful avec Slim 4
{% endhint %}
