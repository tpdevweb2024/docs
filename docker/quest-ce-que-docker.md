# Qu'est-ce que Docker ?

Docker fourni des conteneurs, ils consistent à créer des environnements isolés pour l'exécution d'applications. Cette isolation de processus système permet à une application de fonctionner de manière étanche aux autres conteneurs ou applications du système hôte. Les conteneurs Docker sont conçus pour fournir un environnement d'exécution autonome et portable pour les applications, ce qui permet de les déployer facilement sur différents systèmes et plateformes.

Les processus exécutés dans un conteneur Docker n'ont pas accès aux autres processus du système hôte. Chaque conteneur a son propre espace de noms pour le système de fichiers, le réseau, les utilisateurs et les groupes, ce qui garantit que les processus exécutés dans un conteneur ne peuvent pas interférer avec les autres processus du système hôte. Cependant, les conteneurs Docker partagent le noyau du système hôte, ce qui leur permet d'utiliser les fonctionnalités du noyau sans avoir à les installer dans chaque conteneur.

En résumer, les conteneurs Docker offrent une isolation de processus système tout en partageant le noyau du système hôte, ce qui permet de déployer des applications de manière portable et sécurisée sur différents environnements.



### Docker versus machine virtuel (vm)

La distinction principale entre Docker (conteneurs) et les machines virtuelles (VM) repose sur leur approche d'isolation et de virtualisation. Voici quelques différences clés :

* **Surcharge système :** Les conteneurs Docker sont plus légers que les VM car ils partagent le noyau du système hôte et ne nécessitent pas un système d'exploitation complet pour chaque conteneur. Les VM, cependant, incluent un système d'exploitation complet pour chaque instance, ce qui requiert plus de ressources système.
* **Démarrage :** Les conteneurs peuvent démarrer presque instantanément, car il suffit de lancer le processus dans le conteneur. Les VM prennent plus de temps à démarrer puisqu'il faut amorcer un système d'exploitation complet.
* **Isolation :** Bien que Docker fournisse une isolation au niveau du processus, les VM offrent une isolation complète au niveau du système, y compris le matériel virtuel, ce qui les rend plus sécurisées pour des environnements nécessitant une isolation forte.
* **Utilisation des ressources :** Les conteneurs Docker sont plus efficaces en termes d'utilisation des ressources puisqu'ils partagent certaines parties du système hôte. Les machines virtuelles, en revanche, doivent émuler l'ensemble du matériel et exécuter un système d'exploitation distinct, ce qui augmente la consommation des ressources.
* **Mobilité :** Les conteneurs sont hautement portables. Le même conteneur Docker peut fonctionner sans modification sur n'importe quel système supportant Docker. Les VM nécessitent souvent une configuration spécifique pour s'adapter aux besoins du système hôte.

En conclusion, bien que Docker et les VM servent des objectifs d'isolation et de déploiement d'applications, leur approche et leur efficacité diffèrent sensiblement, rendant Docker plus adapté aux environnements nécessitant une flexibilité, une portabilité et une meilleure utilisation des ressources, tandis que les VM sont privilégiées pour une isolation complète et une sécurité renforcée.



### Avantages de l'utilisation de Docker

***

#### développeur  :

* Un environnement d'exécution propre et portable
* Plus de problèmes de dépendances logicielles : le développeur choisit les bibliothèques à embarquer dans le conteneur.&#x20;
* La possibilité d’exécuter plusieurs conteneurs avec des versions différentes d’une même application, et ce, complètement isolé.
* Partage facile des images grâce à la registry Docker.

#### Opérateurs :

* Eliminer l’inconsistance entre les différents environnements.
* Améliore le cycle de vie de l’application.
* Améliore la rapidité du déploiement.
* Permet le déploiement continu.
* Améliore la sécurité.



### Installation de Docker

{% embed url="https://www.docker.com/products/docker-desktop/" %}
Docker desktop pour Windows / Mac / Linux
{% endembed %}

**Explication de Docker Desktop**

Docker Desktop est une application qui simplifie le développement de logiciels en permettant aux développeurs de construire, tester et déployer des applications dans des conteneurs Docker. Les conteneurs Docker fournissent un environnement de runtime cohérent, peu importe où l'application s'exécute, ce qui élimine le célèbre problème "ça marche sur mon ordinateur". Docker Desktop inclut non seulement le moteur Docker, mais aussi Docker Compose pour la gestion de plusieurs conteneurs, permettant ainsi une facilité d'utilisation accrue et une meilleure intégration dans l'environnement de développement du développeur.

* **Pour Windows:** Docker Desktop utilise WSL 2 (Windows Subsystem for Linux version 2) pour une intégration et des performances optimales.
* **Pour Mac:** Docker Desktop utilise une machine virtuelle sous-jacente pour exécuter Docker dans un environnement macOS.
* **Pour Linux:** Docker Desktop offre une interface graphique pour gérer les conteneurs Docker, facilitant ainsi la vie des développeurs habitués à une expérience plus visuelle.

Grâce à Docker Desktop, les développeurs peuvent facilement construire et partager des images Docker et collaborer avec leur équipe dans le cadre de la phase de développement d'applications.



### Le Registre Docker

Un registre Docker est un système de stockage et de distribution pour les images Docker. Il permet aux utilisateurs de téléverser, stocker et télécharger des images Docker, facilitant le partage d'images dans différents environnements et équipes. Docker Hub est un exemple populaire de registre Docker public, mais les utilisateurs peuvent également configurer des registres privés pour un usage interne.



### Dockerfile & Images Docker

Un **Dockerfile** est un fichier texte qui contient toutes les commandes qu’un utilisateur peut appeler sur la ligne de commande pour assembler une image Docker. En utilisant un Dockerfile, on définie l'environnement dans lequel le code va s'exécuter, en spécifiant explicitement quel logiciel doit être installé et comment le système doit être configuré. Cela assure que l'application s'exécute de manière consistante dans n'importe quel environnement Docker.

Après avoir créé un Dockerfile, les utilisateurs peuvent construire une image Docker en exécutant la commande `docker build`. Cette image peut ensuite être exécutée dans un conteneur Docker. Les images construites peuvent être stockées localement ou téléversées sur un registre Docker pour être partagées.

#### Docker Hub

[Docker Hub](https://hub.docker.com/) est le service de registre Docker officiel qui offre à la fois des repos publics pour partager des images Docker avec la communauté et des repos privés pour une utilisation privée. Docker Hub s'intègre profondément avec Docker Desktop, permettant aux développeurs de télécharger facilement leurs images sur Docker Hub et de les partager avec leur équipe ou la communauté globale. En plus de stocker des images Docker, Docker Hub offre des fonctionnalités de gestion des versions, des webhooks pour les notifications automatiques, et l'intégration avec des outils de CI/CD comme GitHub et Bitbucket.

Pour utiliser Docker Hub, les utilisateurs doivent créer un compte, puis ils peuvent commencer à pousser (`docker push`) et tirer (`docker pull`) des images vers et depuis leurs dépôts. Ceci facilite grandement le partage d'images Docker et la collaboration au sein des équipes de développement.

