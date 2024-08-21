# Les bases de données et les collections NoSQL

## Les base de données MongoDB

MongoDB est une base de données NoSQL orientée documents. Contrairement aux bases de données relationnelles, elle stocke les données sous forme de documents JSON (ou BSON, une version binaire de JSON), ce qui permet une grande flexibilité et évolutivité.

### Comment créer une base de données MongoDB ?

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

Pour créer une base de données directement dans MongoDB Compass, suivez ces étapes :

1. **Ouvrez MongoDB Compass** et connectez-vous à votre cluster.
2. **Cliquez sur "Create Database"** en haut à gauche.
3. **Saisissez le nom de la base de données** et le nom de la collection initiale.
4. **Cliquez sur "Create Database"** pour finaliser la création.

## Les collections&#x20;

### C'est quoi ?

Une collection dans MongoDB est un groupe de documents stockés ensemble dans une base de données. **Les collections sont l'équivalent des tables dans les bases de données relationnelles,** mais elles offrent plus de flexibilité.&#x20;

_Chaque document dans une collection peut avoir un schéma différent, ce qui permet de stocker divers types de données au sein de la même collection._

### Comment créer une collection dans MongoDB Compass ?

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

Pour créer une collection dans MongoDB Compass, suivez ces étapes :

1. **Sélectionnez la base de données** où vous souhaitez créer la collection.
2. **Cliquez sur "Create Collection"** en haut de l'interface.
3. **Entrez le nom de la collection** dans le champ désigné.
4. **Cliquez sur "Create Collection"** pour finaliser la création.

## C'est quoi un document ?

Un document dans MongoDB est une structure de données JSON stockée au sein d'une collection. Il peut contenir différents champs et valeurs, permettant une grande flexibilité dans la manière dont les données sont structurées.

### Comment créer un document dans MongoDB Compass ?

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

Pour créer un document dans MongoDB Compass, suivez ces étapes :

1. **Sélectionnez la collection** dans laquelle vous souhaitez ajouter un document.
2. **Cliquez sur "Insert Document"** en haut de l'interface.
3. **Entrez les données JSON** dans l'éditeur qui s'ouvre.
4. **Cliquez sur "Insert"** pour ajouter le document à la collection.

### Comment modifier un document dans MongoDB Compass ?

Pour modifier un document dans MongoDB Compass, suivez ces étapes :

1. **Sélectionnez la collection** contenant le document à modifier.
2. **Trouvez le document** que vous souhaitez modifier et cliquez sur l'icône d'édition (en forme de crayon).
3. **Mettez à jour les champs nécessaires** dans l'éditeur qui s'ouvre.
4. **Cliquez sur "Update"** pour enregistrer les modifications.

### Comment supprimer un document dans MongoDB Compass ?

Pour supprimer un document dans MongoDB Compass, suivez ces étapes :

1. **Sélectionnez la collection** contenant le document à supprimer.
2. **Trouvez le document** que vous souhaitez supprimer.
3. **Cliquez sur l'icône de suppression** (en forme de poubelle).
4. **Confirmez la suppression** dans la boîte de dialogue qui s'affiche.
