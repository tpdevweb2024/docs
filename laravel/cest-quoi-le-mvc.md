---
description: >-
  MVC, pour Modèle-vue-contrôleur, est un motif d'architecture logicielle
  destiné aux interfaces graphiques lancé en 1978 et très populaire pour les
  applications web.
---

# C'est quoi le MVC ?

## Model / View / Controller

* Le modèle (Model) **contient les données** à afficher.
* La vue (View) contient la présentation de **l'interface graphique**.
* Le contrôleur (Controller) contient la logique concernant les **actions effectuées** par l'utilisateur.

## Principes du MVC

Tout d'abord, voyons en un schéma à qui ressemble une application MVC :&#x20;

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

On peut ainsi remarquer que à chaque page chargée sur notre application, nous aurons un cheminement identique reprenant les étapes ci-dessous :&#x20;

1. L'utilisateur va **exécuter une requête** sur une URL \
   _(ex: méthode GET sur la page https://monsite.fr/a-propos)_
2. Cette requête va être confiée au **Controller**, qui devra **vérifier son existence**, puis **exécuter les scripts** configurés en cas de correspondance
3. Ainsi, les appels (s'il y en a) à effectuer sur la **base de données** sont enclenchés et permettent une **récupération des résultats** de requête
4. Les données reçues (appelées **Model**) sont alors **renvoyées au Controller**, puis **intégrées dans la vue** prévue par le script
5. Cette vue (**View**), une fois générée et alimentée de données (Model), est alors **rendue** au format HTML à l'utilisateu
