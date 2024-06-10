# GitHub actions

## Qu'est-ce que GitHub Actions ?

GitHub Actions est un système d'automatisation intégré à GitHub qui permet aux développeurs de créer des workflows personnalisés pour automatiser et simplifier leur pipeline de développement logiciel. Avec GitHub Actions, vous pouvez déclencher des workflows en réponse à des événements spécifiques sur GitHub tels que des push, des pull requests ou des issues. Ces workflows peuvent inclure des tâches comme la construction du code, le test, le déploiement sur divers environnements, et bien plus, directement au sein de vos dépôts GitHub.

GitHub Actions utilise le format YAML (.yml ou .yaml) pour la définition des workflows. Ce format est choisi pour plusieurs raisons :

* **Lisibilité :** YAML est conçu pour être facile à lire et à comprendre par les humains.
* **Simplicité :** Il permet de définir des structures de données complexes (comme des listes et des dictionnaires) de manière concise.
* **Interopérabilité :** YAML est largement utilisé et supporté par de nombreux outils de développement, ce qui facilite l'intégration avec d'autres systèmes et services.
* **Flexibilité :** Il offre la capacité d'exprimer des workflows complexes tout en restant simple pour les cas d'utilisation de base.

Exemple :&#x20;

```yaml
name: Example Workflow

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Run a command
      run: echo Hello, world!
    - name: Run a multi-line script
      run: |
        echo Add other commands
        echo This is a multi-line script
```

### Explication des éléments du workflow GitHub Actions

Voici une explication des principaux éléments de la définition d'un workflow GitHub Actions :

*   **name:** Ceci définit le nom du workflow qui apparaîtra dans l'interface GitHub Actions.

    ```yaml
    name: Example Workflow
    ```
*   **on:** Cet élément spécifie les événements qui déclencheront le workflow. Dans cet exemple, le workflow est déclenché par un `push`.

    ```yaml
    on: [push]
    ```
*   **jobs:** Les jobs sont une série d'actions que GitHub Actions exécute. Chaque job peut contenir plusieurs étapes.

    ```yaml
    jobs:
      build:
    ```
*   **build:** Ceci est un exemple de job. Vous pouvez lui donner un nom descriptif pour indiquer ce que ce job fait.

    ```yaml
      build:
    ```
*   **runs-on:** Cet élément spécifie l'environnement dans lequel le job doit être exécuté. Par exemple, `ubuntu-latest` indique que le job doit s'exécuter sur une machine virtuelle Ubuntu.

    ```yaml
      runs-on: ubuntu-latest
    ```
*   **steps:** Les étapes sont des tâches individuelles exécutées par le job.

    ```yaml
      steps:
    ```
*   **- uses:** Cette ligne indique qu'une action prédéfinie de la communauté GitHub est utilisée. Par exemple, `actions/checkout@v2` permet de cloner le dépôt.

    ```yaml
      - uses: actions/checkout@v2
    ```
*   **- name:** Vous pouvez spécifier un nom pour chaque étape afin de la décrire.

    ```yaml
      - name: Run a command
    ```
*   **run:** Spécifie la commande Shell unique à exécuter.

    ```yaml
        run: echo Hello, world!
    ```
*   **run (multi-line script):** Permet l'exécution de plusieurs commandes dans une seule étape.

    ```yaml
        run: |
          echo Add other commands
          echo This is a multi-line script
    ```

### Trouver vos workflows GitHub Actions

Pour accéder et gérer vos workflows GitHub Actions, suivez ces étapes :

1. **Naviguez vers votre dépôt GitHub** : Ouvrez le dépôt où vous avez configuré vos workflows.
2. **Cliquez sur l'onglet "Actions"** : Situé en haut de la page du dépôt, entre les onglets "Pull requests" et "Projects".
3. **Explorer les workflows** : Sur la page "Actions", vous verrez une liste de tous les workflows de votre dépôt, organisés par leurs noms. Vous pouvez cliquer sur un workflow spécifique pour voir plus de détails, y compris l'historique des exécutions, le statut de chaque exécution, et les journaux.
4. **Filtrer et rechercher** : Utilisez les filtres disponibles pour affiner les résultats par branche, état d'activité (ex: en cours, réussi, échoué), et même par auteur. La barre de recherche peut également être utilisée pour trouver des workflows spécifiques par mots-clés.

Ces étapes vous permettront de naviguer facilement parmi vos workflows, d'examiner leur réussite ou échec, et de débugger en cas de besoin.
