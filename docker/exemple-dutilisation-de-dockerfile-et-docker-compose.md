# Exemple d'utilisation de Dockerfile et Docker-compose

## Chat Application avec ViteJS et Docker



Cette application est construite avec ViteJS et JavaScript Vanilla. Elle utilise un conteneur Docker pour exécuter une interface de chat qui communique avec une IA sur Ollama.

### Objectif

1. **Créer une image Docker votre application ViteJS.**
2. **Utiliser Docker Compose pour orchestrer deux conteneurs : l'application ViteJS et l'IA Ollama.**
3. **Entrer en commande `ollama run qwen2:0.5b` ou avec le Docker Desktop afin de télécharger ia d'ollama**

* à l'aide de la commande `docker exec -it nom_du_container ollama run qwen2:0.5b`

### Étapes de développement

#### 1. Créer une image Docker pour l'application ViteJS

1.  **Installer les dépendances et lancer le serveur de développement :**

    Utilisez les commandes suivantes pour installer les dépendances et lancer le serveur de développement :&#x20;

    ```
    npm install
    npm run dev
    ```

    \
    `npm run dev` démarre l'application en mode développement, permettant de voir les modifications en temps réel.\

2.  **Construire l'application pour la production :**

    Une fois satisfait du développement, construisez l'application pour la production :

    ```
    npm run build
    ```

    Cette commande crée un répertoire `dist` contenant les fichiers statiques optimisés.\

3.  **Créer une image Docker :**

    Créez un fichier `Dockerfile` à la racine de votre projet avec le contenu suivant :\


    ```
    # Utilise l'image de base Nginx
    FROM nginx:latest

    # Copie les fichiers de l'application dans le répertoire Nginx

    COPY ./dist/ /usr/share/nginx/html

    # Copie le fichier de configuration Nginx personnalisé

    COPY nginx.conf /etc/nginx/conf.d/default.conf

    # Expose le port 80 pour Nginx

    EXPOSE 80
    ```

    \
    Pour construire l'image Docker :

    ```
    docker build -t my-vite-app .
    ```

    \
    Remplacez `my-vite-app` par le nom souhaité pour votre image Docker. Ainsi vous avez créer l'image docker de votre application.

#### 2. Utiliser Docker Compose pour orchestrer les conteneurs

Docker Compose permet de définir et de gérer plusieurs conteneurs.

1.  **Créer un fichier `docker-compose.yml` :**

    À la racine de votre projet, créez un fichier `docker-compose.yml` avec le contenu suivant :

    ```
    services:
      web-app:
        image: chat-app:v0.1
        build: .
        ports:
          - "80:80"

      ollama:
        image: ollama/ollama
        ports:
          - "11434:11434"
    ```

* **`web`** : Définit le service pour votre application ViteJS.
* **`ollama`** : Définit le service pour l'IA Ollama.

2. **Lancer Docker Compose :**

Exécutez la commande suivante pour démarrer les services définis dans `docker-compose.yml` :

```
docker-compose up -d
```

Cette commande construit et lance les conteneurs définis dans le fichier compose.

3.  **Faire la commande dans le container afin de télécharger l'ia d'ollama  souhaitée ici ce sera qwen2:0.5b pour l'exemple:**\


    Exécutez les commandes suivante :

    ```
    # rechercher le nom de votre container ollama, il utilise l'image ollama/ollama
    docker ps

    docker exec -it nom_du_container ollama run qwen2:0.5b
    ```

    \
    une fois l'installation fini apres "success" après les >>> fait un **/bye** dans votre terminal.

Si vous souhaitez d'autres modèles, consultez [la bibliothèque d'Ollama](https://ollama.com/library). Pour plus d'informations, vous pouvez également vous référer à [la documentation d'Ollama](https://github.com/ollama/ollama/tree/main/docs).



Votre application est maintenant en cours d'exécution. Pour la visualiser, ouvrez votre navigateur web et entrez l'adresse suivante dans la barre d'adresse : localhost:80.



#### Résumé

Vous avez maintenant une application ViteJS s'exécutant dans un conteneur Docker, avec une interface de chat communiquant avec une IA Ollama, également exécutée dans un conteneur Docker. Utilisez Docker Compose pour gérer ces conteneurs, facilitant ainsi le déploiement et l'orchestration de votre application.

{% embed url="https://github.com/lolopook/ia-docker-compose" %}
Exemple d'utilisation de docker avec ollama
{% endembed %}



