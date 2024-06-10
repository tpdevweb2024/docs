# Le fonctionnement des BDD

Les bases de données sont basées sur une architecture 3-Tiers

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

Les opérations pouvant être exécutées sont les suivantes :

* **Create**
* **Read**
* **Update**
* **Delete**

On entendra donc souvent dans la création d'application **le terme de CRUD**, qui laissera pense à l'utilisation d'un SGBD, et de l'appel à des requêtes en BDD.

## Les différents types de bases

Il est à noter deux types principaux de bases de données :

* Les bases de données relationnelles _appelées également SGBDR_
* Les bases de données non relationnelles _et majoritairement le NoSQL (not only SQL)_

> Intéressons nous d'abord aux bases de données relationnelles

## Comment accéder à une base de données

Il existe 3 solutions pour accéder à une BDD :

* Par une **application de visualisation** telle que PhpMyAdmin
* Par ligne de commande (**CLI**)
* Par la programmation **en développant** des composants d'accès
