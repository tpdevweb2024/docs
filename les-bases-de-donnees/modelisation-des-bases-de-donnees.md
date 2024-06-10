# Modélisation des bases de données

**Rappel** : une base de données est un ensemble de données structurées. Pour structurer ces données, il est nécessaire de **concevoir un modèle**.

Une technique reconnue pour concevoir une base de données consiste à réaliser successivement :

* un **modèle conceptuel de données (MCD)** (ou encore entités-associations)
* un **modèle logique de données (MLD)** (ou encore modèle relationnel)
* puis enfin un **modèle physique de données (MPD)**

## Modèle Conceptuel de Données (MCD)

Le Modèle Conceptuel de Données, également connu sous le nom d'entités-associations, est la première étape dans la conception d'une base de données. Il décrit de manière abstraite les données en identifiant les entités principales et les relations entre elles.&#x20;

C'est une représentation à haut niveau qui ne se préoccupe pas des détails de mise en œuvre.

**Principaux composants du MCD :**

* **Entités** : Objets ou concepts avec des données stockées à leur sujet.
* **Associations** : Relations entre les entités indiquant comment elles interagissent.
* **Attributs** : Propriétés ou caractéristiques des entités (et parfois des associations).

### Exemple de MCD

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

#### Entités et Associations

* **Propriétaire**
  * ID\_Personne (Clé Primaire)
  * Nom
* **Voiture**
  * ID\_Voiture (Clé Primaire)
  * Marque
* **Possède** (Association entre Propriétaire et Voiture)

## Modèle Logique de Données (MLD)

Après avoir défini le MCD, l’étape suivante consiste à développer le Modèle Logique de Données ou modèle relationnel. Le MLD traduit le MCD en une structure qui peut être implémentée dans une base de données relationnelle.&#x20;

Il définit les tables (représentant les entités et associations), les clés primaires (identifiant unique des enregistrements dans les tables) et les clés étrangères (assurant les relations entre les tables).

**Transformation du MCD au MLD :**

* Chaque **entité** devient une **table**.
* Chaque **attribut** d'une entité devient une **colonne** dans la table correspondante.
* Les **associations** mènent souvent à des **relations** implémentées à travers des clés étrangères.

### Exemple de MLD

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

#### Modèle Logique de Données (MLD)

Pour concevoir notre base de données relationnelle concernant les voitures et leurs propriétaires, il est essentiel de définir les tables et les associations entre ces tables. Voici le MLD requis :

**Tables**

* **Proprietaires**
  * _ID\_Proprietaire_ : Clé primaire, INT
  * _Nom_ : VARCHAR
  * _Prenom_ : VARCHAR
  * _Adresse_ : VARCHAR
  * _DateDeNaissance_ : DATE
* **Voitures**
  * _ID\_Voiture_ : Clé primaire, INT
  * _Marque_ : VARCHAR
  * _Modele_ : VARCHAR
  * _Annee_ : INT
  * _ID\_Proprietaire_ : Clé étrangère vers Proprietaires(ID\_Proprietaire)

**Associations**

* **Une association de type Un à Plusieurs** entre `Proprietaires` et `Voitures` : Un propriétaire peut posséder plusieurs voitures, mais une voiture spécifique est associée à un seul propriétaire. Cette association est réalisée via l'attribut `ID_Proprietaire` dans la table `Voitures` faisant référence à `ID_Proprietaire` dans la table `Proprietaires`.

{% hint style="info" %}
Ce modèle logique peut ensuite être transformé en Modèle Physique de Données pour implémentation.
{% endhint %}

## Modèle Physique de Données (MPD)

Le Modèle Physique de Données est l’étape finale de la conception de base de données. C'est à ce niveau que la base de données est réellement construite.&#x20;

Le MPD peut inclure tous les éléments techniques nécessaires pour la création de la base de données, tels que le type de données exact (par exemple, VARCHAR pour les textes, INT pour les nombres entiers), la longueur des champs, les contraintes (comme NOT NULL), et des détails spécifiques du système de gestion de base de données utilisé (par exemple, MySQL, Oracle, etc.).

**Préoccupations du MPD :**

* **Définition précise des tables** incluant types de données et longueurs.
* **Indexation** pour améliorer les performances des requêtes.
* **Intégration des contraintes** pour garantir l'intégrité des données.

{% hint style="info" %}
Ce processus itératif assure que la structure de la base de données est bien conçue pour stocker les données de manière efficace et pour faciliter l'accès et la manipulation des données selon les besoins de l'application.
{% endhint %}

### Exemple de MPD

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

#### Table `owners`

* `id` : INT, Clé primaire
* `last_name` : VARCHAR(255)
* `first_name` : VARCHAR(255)
* `address` : VARCHAR(255)
* `birth_date` : DATE

#### Table `cars`

* `id` : INT, Clé primaire
* `brand` : VARCHAR(255)
* `model` : VARCHAR(255)
* `year` : INT
* `owner_id` : INT, Clé étrangère vers `owners(id)`

#### Associations

* Une association de type **Un à Plusieurs** entre `owners` et `cars` est établie, indiquant qu'un propriétaire peut posséder plusieurs voitures, mais une voiture est spécifiquement associée à un seul propriétaire.&#x20;
* Cette association est concrétisée par l'attribut `owner_id` dans la table `cars`, faisant référence à `id` dans la table `owners`.

{% hint style="info" %}
Cette structure de base de données permet de stocker de manière efficace les informations relatives aux livres et aux clients, tout en facilitant l'accès et la manipulation des données pour diverses opérations telles que l'achat de livres, la gestion des stocks, et la communication avec les clients.
{% endhint %}
