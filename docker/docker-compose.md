# Docker Compose

### Docker Compose

Docker Compose est un outil permettant de définir et de gérer des applications multi-conteneurs Docker. Avec Docker Compose, vous pouvez utiliser un simple fichier YAML pour spécifier les services, les réseaux et les volumes nécessaires à votre application. Il simplifie la gestion des dépendances et le processus de déploiement en regroupant les configurations en un seul fichier lisible.

#### Commandes de base de Docker Compose détaillées

* `docker-compose up` : Lance et exécute les conteneurs définis dans le fichier `docker-compose.yml`.
* `docker-compose down` : Arrête et supprime les conteneurs, les réseaux, les volumes et les images créés par `up`.
* `docker-compose build` : Reconstruit les images Docker si le code source ou les configurations ont changé.
* `docker-compose logs` : Affiche les logs des conteneurs en cours d'exécution.
* `docker-compose ps` : Liste tous les conteneurs gérés par Docker Compose.
* `docker-compose stop` : Arrête les conteneurs sans les supprimer.
* `docker-compose restart` : Redémarre les conteneurs.



#### Exemple d'un fichier docker-compose.yml

```yaml
version: '3.8' # optionnel

services:
  web:
    image: nginx:latest # Utilise l'image nginx pour le service web
    ports:
      - "80:80" # Expose le port 80 de l'hôte au port 80 du conteneur
    volumes:
      - ./src:/usr/share/nginx/html # Monte le répertoire local 'src' dans le conteneur

  app:
    build: ./app # Utilise les instructions Dockerfile situées dans le répertoire 'app'
    volumes:
      - ./app:/usr/src/app # Monte le répertoire local 'app' dans le conteneur
    environment:
      - NODE_ENV=development # Définit l'environnement applicatif en mode développement

  db:
    image: postgres:latest # Utilise l'image PostgreSQL pour le service base de données
    environment:
      POSTGRES_DB: exampledb # Nom de la base de données à créer
      POSTGRES_USER: user # Nom d'utilisateur par défaut
      POSTGRES_PASSWORD: password # Mot de passe pour l'utilisateur décrit ci-dessus
    volumes:
      - db_data:/var/lib/postgresql/data # Stockage persistant des données de la base de données

volumes:
  db_data:
```



En complément de Docker Compose, plusieurs outils peuvent vous aider à gérer et optimiser vos environnements conteneurisés :

* **Portainer** : Une interface utilisateur pour gérer vos conteneurs Docker, réseaux et volumes. Portainer facilite la gestion et la surveillance des ressources Docker.
* **Docker Swarm** : Pour le déploiement d'environnements de production, Docker Swarm permet d'orchestrer et de gérer des clusters de conteneurs Docker.
* **Kubernetes** : Une autre option d'orchestration de conteneurs qui propose des fonctionnalités avancées telles que l'autoscaling, le déploiement canari et les migrations de bases de données.
* **Docker Compose Override** : Utilisez des fichiers `docker-compose.override.yml` pour personnaliser ou étendre les configurations sans modifier le fichier principal. Cela est particulièrement utile pour les environnements de développement et de test.

#### Dépannage

Lorsque vous travaillez avec Docker Compose, il est possible que des problèmes surviennent. Voici quelques conseils pour le dépannage :

* **Logs** : Utilisez `docker-compose logs` pour examiner les journaux des services et identifier les erreurs.
* **Reconstruction d'Images** : Si vous apportez des modifications aux configurations ou aux Dockerfiles, assurez-vous de reconstruire les images avec `docker-compose build`.
* **Volumes** : Si des problèmes de stockage persistent, essayez de supprimer et de recréer les volumes avec `docker-compose down -v` suivi de `docker-compose up`.
* **Conflits de Ports** : Si un service ne peut pas démarrer en raison d'un conflit de port, vérifiez et modifiez les ports mappés dans le fichier `docker-compose.yml`.

#### Ressources Utiles

Pour en savoir plus et approfondir vos connaissances sur Docker Compose, consultez les ressources suivantes :

* [Documentation Officielle Docker Compose](https://docs.docker.com/compose/)
* [Tutoriels Docker Compose sur Docker Hub](https://hub.docker.com/search?q=\&type=tutorial)

Ces ressources offrent des guides détaillés, des exemples et des meilleures pratiques pour vous aider à maîtriser Docker Compose et à l'utiliser efficacement dans vos projets.



