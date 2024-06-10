# Les bases de GIT

### Qu'est-ce que Git ?

Git est un système de contrôle de version décentralisé gratuit et open source, conçu pour gérer des projets de toutes tailles avec rapidité et efficacité. Il permet aux développeurs de suivre et de coordonner les modifications du code source tout au long du processus de développement logiciel. Git est réputé pour sa robustesse, sa flexibilité et sa capacité à enregistrer l'historique complet des versions d'un projet, facilitant ainsi la collaboration entre les membres d'une équipe.



### Bases de Git&#x20;

Pour commencer à utiliser Git, vous devez d'abord l'installer sur votre ordinateur. Voici les étapes pour télécharger et installer Git :

1. **Visitez le site Web officiel de Git** : Allez à [https://git-scm.com](https://git-scm.com) pour trouver les dernières versions de Git pour différentes plateformes.
2. **Choisissez votre système d'exploitation** : Sur la page d'accueil, vous verrez des options pour télécharger Git pour Linux, macOS, et Windows. Sélectionnez celle qui correspond à votre système d'exploitation.
3. **Téléchargez et installez** : Suivez les instructions spécifiques à votre plateforme pour télécharger et installer Git. Sous Windows, vous lancerez le fichier `.exe` téléchargé et suivrez l'assistant d'installation. Sous macOS, vous pouvez utiliser le package d'installation ou installer Git via Homebrew (`brew install git`). Sous Linux, vous utiliserez généralement votre gestionnaire de paquets, par exemple `sudo apt-get install git` pour les distributions basées sur Debian.
4. **Vérifiez l'installation** : Pour vous assurer que Git est correctement installé, ouvrez un terminal ou une invite de commande et saisissez `git --version`. Votre version de Git devrait s'afficher, confirmant ainsi l'installation réussie.

Avec Git installé, vous êtes prêt à configurer votre environnement et à commencer à travailler sur vos projets de développement.



### Commande de base de git&#x20;

> #### `git init`

Initialise un nouveau dépôt Git dans le répertoire courant. Cette commande crée un nouveau sous-répertoire nommé `.git` qui contient tous les fichiers nécessaires pour suivre les modifications du projet.

```bash
git init

```



> `git clone <url>`

Clone un dépôt Git distant dans le répertoire courant. Cette commande permet de récupérer une copie complète d'un dépôt Git existant, y compris l'historique des commits.

```bash
git clone <https://github.com/utilisateur/mon-projet.git>


```



> `git add <fichier>`

Ajoute un fichier à l'index Git pour le suivi des modifications. Cette commande permet de sélectionner les fichiers que l'on souhaite inclure dans le prochain commit.

```bash
git add mon-fichier.txt

```



> `git commit -m "message"`

Crée un nouveau commit avec les modifications apportées aux fichiers suivis par Git. Le message de commit doit décrire brièvement les modifications apportées. Cette commande permet de sauvegarder les modifications dans l'historique du dépôt Git.

```bash
git commit -m "Ajout d'un nouveau fichier"

```



> `git remote add origin https://......`

La commande "git remote add origin \[url]" est utilisée pour ajouter un dépôt distant à votre dépôt local. Le dépôt distant est une copie de votre projet stockée sur un serveur distant. L'URL du dépôt distant est spécifiée après l'option "origin", qui est le nom par défaut donné au dépôt distant principal.

```bash
git remote add origin [url] 

```



> `git push`

Envoie les commits locaux vers le dépôt Git distant. Cette commande permet de partager les modifications avec d'autres personnes et de sauvegarder les modifications sur un serveur distant.

```bash
git push

```



> `git pull`

Récupère les dernières modifications du dépôt Git distant et les fusionne avec les modifications locales. Cette commande permet de mettre à jour le dépôt local avec les modifications des autres contributeurs.

```bash
git pull

```



> `git branch`

Affiche la liste des branches locales du dépôt Git. Cette commande permet de visualiser les différentes branches du projet et de savoir sur quelle branche on se trouve actuellement.

```bash
git branch 

```



> `git branch ma-branche`

Cette commande créera une nouvelle branche nommée "ma-branche" mais vous resterez sur la branche actuelle.

```bash
git branch ma-branche

```



> `git checkout <branche>`

Bascule vers une branche spécifique du dépôt Git. Cette commande permet de changer de branche pour travailler sur une autre partie du projet.

```bash
git checkout ma-branche

```



> `git branch -b ma-branche`

Cette commande créera une nouvelle branche nommée "ma-branche" et basculera automatiquement sur cette branche. Vous pouvez ensuite apporter des modifications à cette branche sans affecter la branche principale du projet.

```bash
git branch -b ma-branche

```



> `git merge <branche>`

Fusionne les modifications d'une branche spécifique dans la branche actuelle. Cette commande permet de combiner les modifications de deux branches distinctes en une seule.

```bash
git merge ma-branche

```



> `git status`

Affiche l'état actuel du dépôt Git, y compris les fichiers suivis et non suivis, ainsi que les modifications en attente de commit. Cette commande permet de savoir où on en est dans le processus de développement et de détecter les éventuels conflits.

```bash
git status

```



> `git log`

Affiche l'historique des commits du dépôt Git, avec des informations sur l'auteur, la date et le message de chaque commit. Cette commande permet de visualiser l'évolution du projet dans le temps et de retrouver des versions antérieures de fichiers.

```bash
git log

```



> `Le dernier recour.`

à la racine de votre dossier dans votre teminal.

linux, mac,

```bash
rm -rf .git

```

Windows,

```bash
rm -force .git

```

La commande **`rm -rf .git`** sur Linux et macOS, et **`rm -force .git`** sur Windows, permet de supprimer le répertoire **`.git`** à la racine de votre dossier de projet.

Le répertoire **`.git`** est un répertoire caché qui contient toutes les informations de contrôle de version de votre projet Git. Lorsque vous supprimez ce répertoire, vous supprimez l'historique de votre projet Git et toutes les informations de contrôle de version associées.

La suppression du répertoire **`.git`** peut être utile dans certaines situations, par exemple si vous souhaitez supprimer l'historique de votre projet Git ou si vous rencontrez des problèmes avec votre dépôt Git et que vous souhaitez **recommencer à zéro**. Cependant, vous devez être prudent lorsque vous utilisez cette commande, car elle **supprime définitivement toutes les informations de contrôle de version de votre projet Git**. Assurez-vous de sauvegarder toutes les modifications importantes avant de supprimer le répertoire **`.git`**.



## Manipulation&#x20;

**Apprendre le Branchement Git**

:computer: [Learn Git Branching](https://learngitbranching.js.org/?locale=fr\_FR) :octopus:

Une application web interactive conçue pour enseigner les concepts fondamentaux et avancés de Git à travers une expérience pratique. Les utilisateurs peuvent apprendre et comprendre les opérations et les stratégies de branchement Git en participant à des exercices pratiques.





## forker un projet&#x20;

Forker un projet sur GitHub permet de créer une copie du dépôt (repository) original sur votre compte GitHub. Cette opération est souvent utilisée pour proposer des modifications ou développer de nouvelles fonctionnalités sans affecter le projet d'origine. Voici les étapes pour forker un projet :

1. **Rendez-vous sur le dépôt GitHub** que vous souhaitez forker.
2. **Cliquez sur le bouton "Fork"** situé en haut à droite de la page. GitHub créera une copie du dépôt dans votre compte.
3. **Clonez le fork sur votre machine locale** pour commencer à travailler dessus. Utilisez la commande `git clone <URL de votre fork>`.

Après avoir apporté vos modifications, vous pouvez les pousser vers votre fork sur GitHub. Si vous souhaitez que ces modifications soient intégrées au projet original, soumettez une **Pull Request (PR)** au dépôt original à partir de votre fork.

<figure><img src="../.gitbook/assets/Capture d’écran 2024-04-07 à 12.43.33.png" alt=""><figcaption></figcaption></figure>

### Git Mirror

Git Mirror est une fonctionnalité permettant de créer une réplique exacte (miroir) d'un dépôt git sur un autre serveur. Cette opération est utile pour les sauvegardes, la migration de projets, ou la synchronisation entre plusieurs dépôts. Pour mettre en place un miroir, utilisez la commande suivante :

```bash
git clone --mirror <URL dépôt source> <dossier local>
cd <dossier local>
git push --mirror <URL dépôt destination>
```

Cela clonera l'intégralité du dépôt source (y compris toutes les branches et tags) dans un dossier local, puis poussera un miroir complet sur le dépôt de destination.



## A découvrir

***

_**Pistes**_

Pour aller plus loin avec git et le monde open source:

* Gestion de tickets (issues)
* Tags et gestion de versions
* Déploiement sur Heroku
* Licences open source

_**Ressources**_

* Exerciseur interactif (pour pratiquer): [Apprenez Git Branching](https://learngitbranching.js.org/?locale=fr\_FR)
* OpenClassrooms: [Gérez votre code avec Git et GitHub](https://openclassrooms.com/fr/courses/7162856-gerez-du-code-avec-git-et-github)
* Guide récapitulatif: [git - petit guide - no deep shit!](http://rogerdudler.github.io/git-guide/index.fr.html)

_**Exemples de dépôts open source sur GitHub:**_

* [Linux (système d'exploitation)](https://github.com/torvalds/linux)
