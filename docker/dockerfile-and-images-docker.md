# Dockerfile &  Images Docker

## Utilisation de Docker

#### Démarrer avec Docker

Une fois Docker installé, vous pouvez tester son fonctionnement en exécutant le commandement suivant dans un terminal:

```
docker run hello-world
```

Cette commande télécharge une image de test et exécute un conteneur à partir de celle-ci, affichant un message de bienvenue.

#### Créer une image Docker

Pour créer votre propre image Docker, vous devez définir un `Dockerfile`. Un Dockerfile est un script contenant les instructions nécessaires pour construire l'image. Voici un exemple basique de Dockerfile:

```
# Définir l'image de base
FROM ubuntu:latest

# Installer nginx
RUN apt-get update && apt-get install -y nginx

# Définir le port que le conteneur doit exposer
EXPOSE 80

# Lancer nginx
CMD ["nginx", "-g", "daemon off;"]
```

Pour construire l'image à partir de ce Dockerfile, utilisez la commande suivante dans le même répertoire que le Dockerfile:

```
docker build -t mon-image-nginx .
```

#### Exécuter un conteneur Docker

Pour lancer un conteneur à partir de votre image, utilisez la commande:

```
docker run -d -p 80:80 mon-image-nginx
```

Cela démarre un conteneur en mode détaché (`-d`) et mappe le port 80 du conteneur sur le port 80 de votre hôte.

En suivant ces étapes, vous pouvez commencer à utiliser Docker pour faciliter le déploiement et la gestion de vos applications.



### Commandes de base :

***

Voici quelques commandes de base pour utiliser Docker :

* **`docker run`** : permet de créer et de démarrer un conteneur à partir d'une image Docker.
* **`docker ps`** : permet d'afficher la liste des conteneurs en cours d'exécution.
* **`docker stop`** : permet d'arrêter un conteneur en cours d'exécution.
* **`docker rm`** : permet de supprimer un conteneur arrêté.
* **`docker images`** : permet d'afficher la liste des images Docker disponibles sur le système.
* **`docker pull`** : permet de télécharger une image Docker à partir d'un registre Docker.
* **`docker push`** : permet de publier une image Docker sur un registre Docker.



### DockerHub

***

DockerHub est un registre Docker public qui permet de stocker, partager et distribuer des images Docker. Les utilisateurs peuvent rechercher et télécharger des images Docker à partir de DockerHub, ainsi que publier leurs propres images Docker pour les partager avec d'autres utilisateurs.



### Dockerfile

***

* Un Dockerfile est un fichier texte qui contient les instructions nécessaires pour construire une image Docker. Une image Docker est un modèle utilisé pour créer des conteneurs Docker.
* Le Dockerfile définit les différentes étapes nécessaires pour construire l'image Docker. Chaque étape est définie par une instruction dans le fichier. Les instructions les plus courantes sont **`FROM`**, **`RUN`**, **`COPY`**, **`WORKDIR`**, **`EXPOSE`** et **`CMD`**.
*   Voici une brève description de chaque instruction :

    * **`FROM`** : spécifie l'image de base à utiliser pour construire l'image Docker.
    * **`RUN`** : exécute une commande dans le conteneur et crée une nouvelle couche dans l'image Docker.
    * **`COPY`** : copie des fichiers ou des répertoires du système hôte vers le conteneur.
    * **`WORKDIR`** : définit le répertoire de travail dans le conteneur.
    * **`EXPOSE`** : spécifie les ports que le conteneur écoutera.
    * **`CMD`** : définit la commande à exécuter lorsque le conteneur démarre.

    Le Dockerfile est utilisé par la commande **`docker build`** pour construire l'image Docker. La commande **`docker build`** lit le Dockerfile et exécute chaque instruction pour créer l'image Docker.



### Commande de gestion des images et des conteneurs

***

* **`docker images`** : affiche la liste des images Docker disponibles sur le système.
* **`docker pull <image>`** : télécharge une image Docker depuis un registre Docker.
* **`docker rmi <image>`** : supprime une image Docker du système.
* **`docker build -t <image> .`** : construit une image Docker à partir d'un Dockerfile dans le répertoire courant.
* **`docker ps`** : affiche la liste des conteneurs Docker en cours d'exécution.
* **`docker ps -a`** : affiche la liste de tous les conteneurs Docker, y compris ceux qui ne sont pas en cours d'exécution.
* **`docker run -p <hôte-port>:<conteneur-port> <image>`** : crée et démarre un conteneur Docker à partir d'une image et mappe le port du conteneur sur le port de l'hôte.
* **`docker stop <conteneur>`** : arrête un conteneur Docker en cours d'exécution.
* **`docker rm <conteneur>`** : supprime un conteneur Docker du système.
*   **`docker exec -it <conteneur> <commande>`** : exécute une commande dans un conteneur Docker en cours d'exécution.

    Ces commandes sont les plus courantes pour gérer les images et les conteneurs Docker. Il en existe d'autres pour gérer les réseaux, les volumes, etc. Vous pouvez utiliser la commande **`docker --help`** pour obtenir une liste complète des commandes disponibles.



### Exercice de compréhension Docker et à créer un conteneur avec Nginx servant un fichier `index.html` et un fichier `style.css`.



**Étape 1 : Créer les fichiers `index.html` et `style.css`**

Tout d'abord, créez un répertoire pour votre projet :

```bash
mkdir docker-nginx # création d'un dossier de votre choix
cd docker-nginx # ce déplacer dans le dossier docker-nginx
```

Ensuite, créez un fichier `index.html` avec le contenu suivant :

<pre class="language-html"><code class="lang-html"><strong># créer un fichier HTML, soyez libre et créatif
</strong>&#x3C;!DOCTYPE html>
&#x3C;html lang="fr">
&#x3C;head>
    &#x3C;meta charset="UTF-8">
    &#x3C;meta name="viewport" content="width=device-width, initial-scale=1.0">
    &#x3C;title>My Docker Web App&#x3C;/title>
&#x3C;/head>
&#x3C;body>
    &#x3C;h1>Bienvenue sur ma première application web avec Docker!&#x3C;/h1>
&#x3C;/body>
&#x3C;/html>
</code></pre>

Créez également un fichier `style.css` avec le contenu suivant :

```css
body {
    background-color: #f0f0f0;
}

h1 {
    color: blue;
}
```



**Étape 2 : Créer le `Dockerfile`**

Créez un fichier nommé `Dockerfile` dans le même répertoire que vos fichiers `index.html` et `style.css`. Ajoutez le contenu suivant :

```Dockerfile
# Utiliser l'image officielle nginx comme base
FROM nginx:latest

# Copier le contenu du répertoire courant 
# dans le répertoire /usr/share/nginx/html du conteneur
COPY . /usr/share/nginx/html

# Exposer le port 80 du conteneur
EXPOSE 80
```



**Étape 3 : Construire l'image Docker**

Utilisez la commande `docker build` pour créer une image Docker à partir de votre `Dockerfile` :

```bash
docker build -t mon-image-nginx .
```



**Étape 4 : Lancer le conteneur Docker**

Utilisez la commande `docker run` pour lancer un conteneur à partir de votre image :

```bash
docker run -d -p 8080:80 mon-image-nginx
```

Cette commande lance le conteneur en arrière-plan (`-d`) et redirige le port 8080 de votre machine vers le port 80 du conteneur (`-p 8080:80`).



**Étape 5 : Vérifier le résultat**

Ouvrez votre navigateur et accédez à `http://localhost:8080`. Vous devriez voir votre page web avec le style CSS appliqué.

Félicitations, vous venez de créer et de lancer un conteneur Docker avec Nginx !



:tada: Bravo ! Vous avez réussi à créer votre première image Docker. Cela marque une étape importante dans votre parcours d'apprentissage avec Docker ! :whale2:



### Conclusion

Comme vous l'avez vu, Docker simplifie grandement le processus de capture d'une configuration et du code dans une image immuable. Cela vous permet de partager et de déployer vos applications avec une grande facilité, tout en vous assurant qu'elles fonctionneront de manière cohérente dans différents environnements. Continuez à explorer les possibilités offertes par Docker pour améliorer vos flux de travail de développement et de déploiement.
