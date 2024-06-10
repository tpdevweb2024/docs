# SQLite

Les systèmes de gestion de bases de données relationnelles (SGBDR) sont au cœur de presque toutes les applications modernes, stockant et gérant les données de manière efficace et sécurisée.&#x20;

Parmi ces systèmes, SQLite se distingue par sa légèreté, sa simplicité et sa portabilité, offrant une solution idéale pour des applications de petite à moyenne envergure, des environnements embarqués, ou même comme fichier de stockage pour des applications client-serveur.

## Qu'est-ce que SQLite?

SQLite est un moteur de base de données relationnelle open-source, autonome, qui ne nécessite pas d'un serveur de base de données séparé pour fonctionner.&#x20;

Cela signifie que SQLite ne s'exécute pas comme un service ou un processus distinct auquel des applications se connectent, mais s'intègre directement dans les applications.&#x20;

{% hint style="info" %}
**IMPORTANT** ! Les bases de données SQLite sont stockées dans un unique fichier sur disque, ce qui facilite leur partage ou leur transfert.
{% endhint %}

## Pourquoi utiliser SQLite?

* **Légèreté et Portabilité**: SQLite ne nécessite aucune configuration ou installation séparées, ce qui le rend idéal pour des applications embarquées ou des appareils avec des ressources limitées.
* **Simplicité**: Avec une API concise et des commandes SQL standards, SQLite est facile à apprendre pour les nouveaux développeurs et suffisamment puissant pour les applications complexes.
* **Fiabilité et Durabilité**: SQLite gère avec soin les transactions et les erreurs pour assurer l'intégrité de la base de données, même en cas de pannes brutales ou de coupures de courant.
* **Compatibilité**: Supportant une grande partie du standard SQL avec des extensions propres, SQLite peut facilement interagir avec de nombreuses langues de programmation et environnements de développement.

## Cas d'usage de SQLite

* **Applications Desktop et Mobiles**: Idéal pour le stockage de données local dans des applications autonomes.
* **Sites Web**: Pour les sites à trafic léger à modéré comme un blog personnel ou un portfolio.
* **Prototypage et Test**: Rapide à mettre en place pour prototyper des applications nécessitant une gestion de bases de données.
* **Outils de Développement**: Utilisé comme moteur de base de données pour des outils et des applications logicielles.

## Comment utiliser SQLite

1.  **Installer PHP et SQLite**

    Assurez-vous que votre environnement PHP est configuré avec l'extension SQLite. La plupart des installations PHP modernes incluent cette extension par défaut.
2.  **Ouvrir une connexion à une base de données SQLite**

    Utilisez PHP pour ouvrir une connexion à votre base de données SQLite. Si le fichier de base de données n'existe pas, SQLite et PHP le créeront automatiquement.

    ```php
    <?php

        $db = new SQLite3('chemin/vers/votre/base_de_donnees.db');
        
    ?>
    ```
3.  **Exécuter des requêtes SQL**

    Vous pouvez maintenant exécuter des requêtes SQL sur votre base de données à l'aide de PHP. Voici comment créer une table et insérer des données :

    ```php
    <?php

        $db->exec("CREATE TABLE IF NOT EXISTS utilisateurs (id INTEGER PRIMARY KEY, nom TEXT, email TEXT)");
        $db->exec("INSERT INTO utilisateurs (nom, email) VALUES ('John Doe', 'john@example.com')");

    ?>
    ```
4.  **Interroger la base de données**

    Pour récupérer des données de la base de données, utilisez une requête SELECT et parcourez les résultats :

    ```php
    <?php

        $result = $db->query('SELECT * FROM utilisateurs');
        while ($row = $result->fetchArray()) {
            echo "ID: " . $row['id'] . " Nom: " . $row['nom'] . " Email: " . $row['email'] . "\n";
        }

    ?>
    ```
5.  **Fermer la connexion**

    Une fois que vous avez terminé avec votre base de données, il est bon de fermer la connexion :

    ```php
    <?php

        $db->close();
        
    ?>
    ```

En suivant ces étapes, vous pouvez intégrer SQLite dans vos applications PHP pour gérer des données de manière efficace et légère.

{% hint style="info" %}
Que vous construisiez une application mobile, un outil de bureau, ou simplement à la recherche d'un système de gestion de bases de données pour vos projets de développement, SQLite offre un bon point de départ avec la possibilité d'escalader ou de migrer vers des solutions plus robustes si le besoin se présente.
{% endhint %}
