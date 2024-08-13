# L.A.M.P avec Docker Compose

## Guide de Configuration Docker Compose pour un serveur L.A.M.P

### Objectifs d'Apprentissage

Ce guide vise à fournir une compréhension approfondie de la mise en place d'un environnement de développement LAMP (Linux, Apache, MySQL, PHP) en utilisant Docker Compose. Il détaille comment configurer chaque service pour une application web, une base de données, et un outil de gestion de base de données via une interface graphique.

### Prérequis

* Une application PHP
* Une base de données MySQL
* **Docker**: Installez Docker en suivant les instructions sur [Docker Hub](https://hub.docker.com/).
* **Docker Compose**: Assurez-vous que Docker Compose est installé. Les instructions d'installation sont disponibles sur la [documentation officielle de Docker Compose](https://docs.docker.com/compose/install/).

### Configuration avec Docker Compose

#### 1. Préparation

```bash
serve-php/
│
├── docker-compose.yml
│
├── code/
│    ├── index.php # exemple : <?php echo 'Hello'; ?>
│    └── ...
│
└── Dockerfile
```

L'arborescence de votre projet est essentielle pour organiser les différentes parties de votre application. Voici une brève explication des éléments présents dans cette arborescence :

* `docker-compose.yml` : Ce fichier définit les services nécessaires à votre environnement de développement, y compris les conteneurs pour PHP, Apache, MySQL, etc.
* `code/` : Ce répertoire contient le code source de votre application PHP.
  * `index.php` : Un exemple de fichier PHP simple qui sert de point d'entrée pour votre application.
* `Dockerfile` : Ce fichier contient les instructions pour construire l'image Docker personnalisée pour votre service PHP.



C'est partie Créez un dossier pour votre projet et initialisez votre fichier `Dockerfile` :

dans votre terminal :

```bash
mkdir serve-php # créer un dossier mkdir
cd serve-php # ce déplacer dans le dossier serve-php
```

#### 2. Création du Dockerfile

Créez un fichier `Dockerfile` dans le même dossier pour définir l'image personnalisée :

```bash
touch Dockerfile #création du fichier Dockerfile
```

**Contenu du Dockerfile** :

```dockerfile
# Utilise l'image officielle PHP avec Apache
FROM php:8.2-apache

RUN apt-get update && apt-get install -y

# Installe les extensions PHP nécessaires
RUN docker-php-ext-install mysqli pdo pdo_mysql && docker-php-ext-enable mysqli pdo pdo_mysql

EXPOSE 80
```

**Explication** :

* **FROM** : Utilise l'image `php:8.2-apache` comme image de base.
* **RUN docker-php-ext-install** : Installe les extensions PHP nécessaires.
* **EXPOSE** : expose le port 80

***

### Création du fichier `docker-compose.yml`

Vous pouvez créer le fichier `docker-compose.yml` à l'aide du terminal en exécutant les commandes suivantes :

```sh
touch docker-compose.yml
```

Pour configurer les services et orchestrer plusieurs conteneurs Docker, nous avons besoin du fichier `docker-compose.yml`.

#### **3. Configuration des Services**

Chaque service dans le fichier `docker-compose.yml` est défini avec des attributs spécifiques tels que `container_name`, `ports`, et `volumes` pour assurer une configuration et une gestion efficaces des conteneurs.



**Service Apache avec PHP**

```yaml
services:
  php-apache:
    container_name: php-apache
    ports:
      - 8000:80
    volumes:
      - ./code:/var/www/html
    build:
      context: .
      dockerfile: Dockerfile
```

**Explication**:

* **services**: Définit les services individuels qui composeront l'application.
* **Image**: Utilise l'image `php:8.2-apache` qui inclut PHP et le serveur web Apache.
* **Container Name**: Nomme le conteneur `php-apache` pour une identification facile.
* **Ports**: Mappe le port 8000 de l'hôte au port 80 du conteneur, rendant l'application accessible via `localhost:8000`.
* **Volumes**: Montage du dossier local `./code` sur `/var/www/html` dans le conteneur. Ce volume permet une synchronisation en temps réel du code entre l'hôte et le conteneur.\
  \
  **doc de l'image** [**php de docker**](https://hub.docker.com/\_/php)



**Service MySQL**

```yaml
  database:
    image: mysql:8.0
    container_name: mysql8
    command: --default-authentication-plugin=mysql_native_password
    ports:
      - 3307:3306
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: docker_DB
      MYSQL_USER: user
      MYSQL_PASSWORD: pass
```

**Explication**:

* **Image**: Utilise `mysql:8.0`, une version stable et populaire de MySQL.
* **Container Name**: Nomme le conteneur `mysql8`.
* **Command**: Configure MySQL pour utiliser le plugin d'authentification `mysql_native_password` pour une compatibilité accrue.
* **Ports**: Mappe le port 3307 de l'hôte au port 3306 du conteneur.
* **Environment**: Définit les variables d'environnement pour la configuration initiale de MySQL, incluant le mot de passe root, le nom de la base de données, l'utilisateur, et le mot de passe.\
  \
  **doc de l**[**'image de MySql** ](https://hub.docker.com/\_/mysql)



**Service phpMyAdmin**

```yaml
  phpmyadmin:
    image: phpmyadmin/phpmyadmin
    container_name: phpmyadmin
    environment:
      - PMA_ARBITRARY=1
      - PMA_HOST=mysql8
      - PMA_USER=user
      - PMA_PASSWORD=pass
    ports:
      - "8888:80"
```

**Explication**:

* **Image**: `phpmyadmin/phpmyadmin` fournit une interface web pour la gestion de MySQL.
* **Container Name**: Nomme le conteneur `phpmyadmin`.
* **Environment**: Configure phpMyAdmin pour se connecter à MySQL en utilisant les détails fournis.
* **Ports**: Mappe le port 8888 de l'hôte au port 80 du conteneur, rendant phpMyAdmin accessible via `localhost:8888`.\
  \
  **Doc de** [**l'image de PhpMyAdmin**](https://hub.docker.com/\_/phpmyadmin)



### fichier `docker-compose.yml` complet :

```yaml
# docker-compose.yml
version: "3.8" #optionnel

services:
  php-apache:
    container_name: php-apache
    ports:
      - 8000:80
    volumes:
      - ./code:/var/www/html
    build:
      context: .
      dockerfile: Dockerfile

  database:
    image: mysql:8.0
    container_name: mysql8
    command: --default-authentication-plugin=mysql_native_password
    ports:
      - 3307:3306
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: docker_DB
      MYSQL_USER: user
      MYSQL_PASSWORD: pass

  phpmyadmin:
    image: phpmyadmin/phpmyadmin # image
    container_name: phpmyadmin # nom du conteneur
    environment: # variables d'environnement
      - PMA_ARBITRARY=1 # autorisation d'accès
      - PMA_HOST=mysql8 # nom du conteneur
      - PMA_USER=user # utilisateur
      - PMA_PASSWORD=pass # mot de passe de l'utilisateur
    ports: # port d'accès
      - 8888:80

```

### **Adaptation de l'Application**

Pour adapter votre application afin de tirer parti de l'environnement Docker, assurez-vous que votre application peut se connecter à la base de données MySQL en utilisant les variables d'environnement définies dans `docker-compose.yml`. Par exemple, configurez votre application pour utiliser `mysql8` comme hôte de base de données, avec les informations d'utilisateur et de mot de passe fournies.

#### Rappel des informations pour la connexion :

* **Host**: mysql8
* **User**: user
* **Password**: pass
* **Database**: mydb

### Lancement de l'Environnement

Démarrez vos services en exécutant :

```bash
docker-compose up -d
```

Pour arrêter et nettoyer les services, utilisez :

```bash
docker-compose down
```

### Gestion des Services

Pour démarrer individuellement les services sans reconstruire les conteneurs, utilisez :

```bash
docker-compose start
```

Pour arrêter les services sans les supprimer, utilisez :

```bash
docker-compose stop
```

### Accès aux Services

* **Application Web**: Accédez à votre application PHP en ouvrant `http://localhost:8000`.
* **phpMyAdmin**: Gérez votre base de données MySQL via `http://localhost:8888`.

### Bonnes Pratiques de Sécurité

* Assurez-vous de ne pas exposer le port MySQL sur une interface publique.
* Utilisez des mots de passe forts pour les utilisateurs de bases de données.
* Gardez vos images Docker à jour pour bénéficier des correctifs de sécurité.
