---
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# MySQL

**MySQL** est un système de gestion de bases de données relationnelles. Utilisé dans le développement web, il permet de stocker et de gérer des données de manière efficace et sécurisée.

## Le fonctionnement de MySQL

MySQL fonctionne sur le principe des bases de données relationnelles, où les données sont stockées dans des tables. Les relations entre ces tables permettent d'organiser et de manipuler les données de manière complexe et flexible. MySQL utilise le langage SQL (Structured Query Language) pour la création, la manipulation et la gestion des données.

### Avantages de MySQL

* **Open Source**: MySQL est gratuit et ouvert, permettant à quiconque de l'utiliser et de contribuer à son amélioration.
* **Performances élevées**: Optimisé pour les applications web, il peut gérer une grande quantité de transactions.
* **Sécurité**: Offre des mécanismes robustes pour protéger les données.
* **Facilité d'utilisation**: Bien documenté et disposant d'une large communauté, il est accessible aux débutants.

## Utilisation de MySQL

L'utilisation de MySQL implique la création d'une base de données, la définition des tables et la manipulation des données au travers des opérations CRUD.

### Créer une base de données et des tables

```sql
CREATE DATABASE ma_base_de_donnees;
USE ma_base_de_donnees;

CREATE TABLE utilisateurs (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nom VARCHAR(100),
    email VARCHAR(100)
);
```

### Exemples de requêtes CRUD

#### **Create (Créer)**: Insérer des données.

```sql
INSERT INTO utilisateurs (nom, email) VALUES ('Jean Dupont', 'jean.dupont@email.com');
```

#### **Read (Lire)**: Sélectionner des données.

```sql
SELECT * FROM utilisateurs;
SELECT nom, email FROM utilisateurs WHERE id = 1;
```

#### **Update (Mettre à jour)**: Modifier des données existantes.

```sql
UPDATE utilisateurs SET email = 'jean.nouveau@email.com' WHERE id = 1;
```

#### **Delete (Supprimer)**: Supprimer des données.

```sql
DELETE FROM utilisateurs WHERE id = 1;
```

{% hint style="info" %}
En maîtrisant ces concepts et commandes de base, vous serez bien équipés pour démarrer dans le développement web avec MySQL. La pratique régulière et l'exploration des fonctions avancées de MySQL vous permettront de développer des applications web dynamiques et puissantes.
{% endhint %}

### Mots clés

**ORDER BY** : Permet de trier les résultats d'une requête en fonction d'une ou plusieurs colonnes, par ordre ascendant (ASC) ou descendant (DESC).

```sql
SELECT nom, age FROM utilisateurs ORDER BY age DESC;
```

**LIMIT** : Permet de limiter le nombre de résultats retournés par une requête. Utile pour la pagination.

```sql
SELECT * FROM produits ORDER BY prix DESC LIMIT 10;
```

**OFFSET** : En combinaison avec `LIMIT`, permet de sauter un nombre spécifié de lignes avant de commencer à retourner les résultats de la requête.

```sql
SELECT * FROM messages ORDER BY date_envoi DESC LIMIT 20 OFFSET 10;
```

**GROUP BY :** La déclaration `GROUP BY` permet de regrouper les lignes présentant les mêmes valeurs dans des lignes résumées pour affiner votre analyse de données. Elle est souvent utilisée avec des fonctions d'agrégation pour effectuer des calculs sur chaque groupe.

```sql
SELECT categorie, COUNT(*) FROM produits GROUP BY categorie;
```

**HAVING :** a été ajoutée à SQL parce que le mot-clé `WHERE` ne pouvait pas être utilisé avec des fonctions d'agrégation. Elle permet de spécifier des conditions qui filtrent quels résultats de groupe apparaissent dans la sortie finale.

```sql
SELECT categorie, COUNT(*) FROM produits GROUP BY categorie HAVING COUNT(*) > 10;
```

{% hint style="info" %}
Avec cette requête, vous verrez uniquement les catégories qui ont plus de 10 produits, montrant comment `HAVING` peut être utilisé pour filtrer les groupes après qu'ils aient été agrégés par \`GROUP BY
{% endhint %}

## **Les contraintes de clés étrangères**

Les contraintes de clés étrangères (foreign key constraints) sont utilisées pour assurer l'intégrité référentielle des données entre deux tables.&#x20;

Elles garantissent que les valeurs dans une colonne ou un ensemble de colonnes d'une table correspondent aux valeurs d'une colonne clé primaire dans une autre table.

#### Exemple de création de contrainte de clé étrangère :

```sql
CREATE TABLE commandes (
    id_commande INT PRIMARY KEY,
    id_client INT,
    date_commande DATE,
    FOREIGN KEY (id_client) REFERENCES clients(id_client)
);
```

_Dans cet exemple, `id_client` dans la table `commandes` doit correspondre à une valeur existante de `id_client` dans la table `clients`._

### Pourquoi utilise-t-on les clés étrangères (FK) ?

Les principales raisons d'utiliser des clés étrangères sont :

1. **Intégrité des données** : Empêcher l'insertion de données incohérentes ou orphelines.
2. **Maintenabilité** : Simplifier la gestion et la suppression de données liées.
3. **Normalisation** : Aider à organiser les données de manière structurée et éviter les redondances.

{% hint style="info" %}
En résumé, les clés étrangères sont essentielles pour maintenir la cohérence et la qualité des données dans une base de données relationnelle.
{% endhint %}

### **Les actions en cascade**

Le système de cascade dans une base de données relationnelle permet de définir des actions automatiques en cas de mise à jour ou de suppression d'une ligne parent dans une table.&#x20;

Les deux types de cascades couramment utilisés sont :

* **ON DELETE CASCADE** : Supprime automatiquement les enregistrements enfant lorsque l'enregistrement parent est supprimé.
* **ON UPDATE CASCADE** : Met à jour automatiquement les valeurs correspondantes dans les enregistrements enfant lorsqu'une valeur dans l'enregistrement parent est modifiée.

#### Exemple d'utilisation des actions en cascade

Supposons que vous avez deux tables, `orders` et `order_items`. La table `orders` contient des informations sur les commandes, tandis que la table `order_items` contient les articles correspondants à chaque commande.

{% code overflow="wrap" %}
```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    order_date DATE
);

CREATE TABLE order_items (
    item_id INT PRIMARY KEY,
    order_id INT,
    item_name VARCHAR(50),
    FOREIGN KEY (order_id) REFERENCES orders(order_id) ON DELETE CASCADE ON UPDATE CASCADE
);
```
{% endcode %}

_Dans cet exemple, si vous supprimez un enregistrement dans la table `orders`, tous les articles correspondants dans la table `order_items` seront également supprimés automatiquement grâce à `ON DELETE CASCADE`. De même, toute mise à jour du `order_id` dans `orders` sera automatiquement répercutée dans `order_items` grâce à `ON UPDATE CASCADE`._

***

## **Utilisation avancée des requêtes**

### **Les fonctions d'agrégation**

Les fonctions d'agrégation vous permettent d'effectuer un calcul sur un ensemble de valeurs pour en retourner une seule valeur. Elles sont particulièrement utiles pour les analyses statistiques.

* **COUNT()** : Compte le nombre d'éléments.
* **SUM()** : Calcule la somme d'une colonne.
* **AVG()** : Calcule la moyenne des valeurs.
* **MAX()** / **MIN()** : Trouve la valeur maximale / minimale.

Exemple :

```sql
SELECT COUNT(id), AVG(salaire) FROM employes WHERE departement = 'IT';
```

### Les fonctions de fenêtrage

Après avoir abordé les fonctions d'agrégation et avant de passer aux jointures, il est utile de mentionner les fonctions de fenêtrage. Ces fonctions fournissent un moyen d'effectuer des calculs sur un ensemble de lignes qui sont en quelque sorte liées à la ligne courante.&#x20;

Contrairement aux fonctions d'agrégation classiques qui regroupent plusieurs lignes pour donner un seul résultat par groupe, les fonctions de fenêtrage conservent les lignes distinctes tout en permettant d'effectuer des calculs à travers elles.

* **ROW\_NUMBER() :** Attribue un numéro unique à chaque ligne selon l'ordre spécifié.
* **RANK() :** Attribue un rang à chaque ligne avec des ex aequo.
* **DENSE\_RANK() :** Similaire à RANK() mais sans sauts dans la séquence des rangs.
* **LEAD() / LAG() :** Permet d'accéder à une ligne suivante ou précédente.
* **SUM() OVER() / AVG() OVER() :** Applique les fonctions d'agrégation sur un ensemble de lignes liées sans regrouper les résultats.

Exemple :

```sql
SELECT nom,
       salaire,
       AVG(salaire) OVER (PARTITION BY departement) AS moyenne_par_departement
FROM employes;
```

### **Les jointures**

La clause `JOIN` est utilisée dans les requêtes SQL pour combiner les colonnes de deux tables différentes en se basant sur une colonne clé commune.&#x20;

Cela permet de facilement récupérer et relier les données issues de plusieurs tables. Il existe différents types de jointures, chacun répondant à un besoin spécifique :

* **INNER JOIN** : Permet de sélectionner les enregistrements qui ont des valeurs correspondantes dans les deux tables. Si un enregistrement de la table A a une correspondance dans la table B, cet enregistrement sera retourné dans notre résultat.
* **LEFT JOIN** / **RIGHT JOIN** : Le `LEFT JOIN` retourne tous les enregistrements de la table de gauche (A) ainsi que les enregistrements correspondants de la table de droite (B). Les enregistrements de la table A qui n'ont pas de correspondance dans la table B sont tout de même retournés, avec des valeurs NULL pour les colonnes de la table B. Le `RIGHT JOIN` fonctionne de la même manière mais en inversant les rôles des tables.
* **FULL JOIN** : Cette jointure combine les caractéristiques du `LEFT JOIN` et du `RIGHT JOIN`. Elle retourne tous les enregistrements lorsqu'il y a une correspondance dans l'une des tables, laissant des valeurs NULL pour les colonnes sans correspondances dans l'autre table.

Exemple d'utilisation d'un `INNER JOIN` :

```sql
SELECT employes.nom, departements.nom
FROM employes
INNER JOIN departements ON employes.departement_id = departements.id;
```

_Ce type de jointure est extrêmement utile pour lier des données cohérentes entre diverses entités dans une base de données relationnelle._

### **Les conditions**

Les conditions dans les requêtes SQL permettent de filtrer les résultats retournés par une requête. Elles sont généralement utilisées avec `WHERE`, `HAVING` (quand on applique des fonctions d'agrégation), et des clauses conditionnelles comme `AND`, `OR`.

* `WHERE` sert à filtrer les lignes retournées par une requête selon une condition spécifiée. Par exemple, `SELECT * FROM employes WHERE age > 30;` retourne tous les employés âgés de plus de 30 ans.
* `AND` et `OR` peuvent être utilisés pour combiner plusieurs conditions. Si vous voulez retrouver des employés âgés de plus de 30 ans mais de moins de 50 ans, vous pouvez utiliser `SELECT * FROM employes WHERE age > 30 AND age < 50;`.
* `HAVING` est utilisé de manière similaire à `WHERE`, mais pour filtrer des données qui utilisent des fonctions d'agrégation. Par exemple, si vous souhaitez compter le nombre d'employés dans chaque département ayant un salaire moyen supérieur à un certain montant, vous pourriez utiliser `SELECT departement_id, AVG(salaire) AS salaire_moyen FROM employes GROUP BY departement_id HAVING salaire_moyen > 5000;`.

{% hint style="info" %}
En maîtrisant l'usage des conditions, vous pouvez affiner vos requêtes pour extraire précisément les données qui vous intéressent.
{% endhint %}

### Les triggers&#x20;

Les triggers, ou déclencheurs en français, sont des procédures stockées qui se lancent automatiquement lorsqu'un événement spécifique survient dans la base de données. Ces événements peuvent être des insertions, des mises à jour, ou des suppressions de lignes dans une table. Les triggers permettent d'automatiser certaines tâches comme la vérification de la cohérence des données ou le maintien d'un historique des modifications.

Voici un exemple simple de trigger dans MySQL :

```sql
CREATE TRIGGER after_employee_update 
AFTER UPDATE ON employee
FOR EACH ROW 
BEGIN
   INSERT INTO employee_audit
   SET action = 'update',
       employee_id = OLD.employee_id,
       changed_at = NOW();
END;
```

Cet exemple crée un trigger nommé `after_employee_update` qui s'exécute après chaque mise à jour dans la table `employee`. Il insère un enregistrement dans une table `employee_audit` pour tenir un historique des mises à jour effectuées sur les employés.

{% hint style="warning" %}
Les triggers peuvent grandement améliorer l'intégrité et la fiabilité des données dans votre base. Toutefois, ils doivent être utilisés avec prudence, car ils peuvent rendre le débogage plus complexe et réduire les performances si leur logique est trop lourde ou appelée fréquemment.
{% endhint %}

### Les procédures stockées

Les procédures stockées dans MySQL sont des blocs de code SQL qui sont enregistrés et stockés pour être exécutés ultérieurement. Elles peuvent être utilisées pour encapsuler des logiques complexes, effectuer des opérations répétitives et améliorer la performance en réduisant le nombre d'appels à la base de données.&#x20;

Les procédures permettent également une meilleure sécurisation en centralisant la logique d'accès aux données.

Voici un exemple basique de création et d'appel d'une procédure dans MySQL :

```sql
DELIMITER //

CREATE PROCEDURE GetAllEmployees()
BEGIN
  SELECT * FROM employee;
END //

DELIMITER ;

CALL GetAllEmployees();
```

Dans cet exemple, une procédure nommée `GetAllEmployees` est créée pour sélectionner tous les enregistrements de la table `employee`. L'utilisation du délimiteur `//` permet de définir clairement où la procédure commence et se termine, facilitant sa création. L'appel de la procédure se fait ensuite via la commande `CALL GetAllEmployees();`.

{% hint style="success" %}
Pratiquer ces concepts avancés augmentera votre capacité à manipuler et à interpréter des données dans MySQL, ouvrant la voie à des analyses plus riches et des applications web plus dynamiques.
{% endhint %}
