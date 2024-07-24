---
description: >-
  Un mapping objet-relationnel (ORM en anglais) est un type de programme
  informatique qui se place en interface entre un programme applicatif et une
  BDD relationnelle pour simuler BDD orientée objet.
---

# C'est quoi Eloquent ORM ?

## Pour bien comprendre l'ORM

L'une des principales caractéristiques de Laravel est qu'il arrive équipé d'un ORM surpuissant : **Eloquent**

Il va **nous permettre de gérer nos liaisons entre nos modèles et nos tables stockées** dans la base de données de notre application.

Ainsi, lors d'un appel en base, la requête se calibrera sur les objets que sont nos modèles pour en extraire les data demandées dans notre script.

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

Les ressources utilisées pour un simple appel sont alors très souvent critiquées pour leur gourmandise, néanmoins Eloquent apporte **une véritable simplicité d'écriture des requêtes,** et une notion de sécurité du traitement des requêtes SQL opérées.&#x20;

## **L'utilisation de l'ORM**

Afin de comprendre comment Eloquent va nous apporter une qualité de code au sein de nos applications développées avec Laravel Framework, prenons l'exemple simple d'une requête visant à **récupérer une voiture précise grâce à son Id** dans **notre "future" table cars.**

Habituellement nous aurions utilisé PDO t nous aurions écrit ceci :&#x20;

```php
$id = 3;
// On exécute la requête
$req = $bdd->prepare("SELECT * FROM cars WHERE id = ?");
$req->execute([ $id ]);
// On récupère les données
$car = $req->fetch();
```

Avec Eloquent, et donc de ce dait dans l'univers Laravel, nous allons plutôt écrire :&#x20;

```php
use App\Models\Car;

$id = 3;
// on exécute la requête et récupère directement les données
$cars = Car::all();
$car = $cars->find($id);
```

{% hint style="info" %}
Tout ceci peut paraître un peu flou mais nous allons y revenir plus en détail ne vous inquiétez pas.
{% endhint %}
