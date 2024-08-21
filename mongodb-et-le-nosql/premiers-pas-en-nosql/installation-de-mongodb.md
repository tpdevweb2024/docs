# Installation de MongoDB

## **Installation sur Windows**

### **Étape 1 : Télécharger MongoDB**

1. Allez sur le site officiel de MongoDB : [MongoDB Download Center](https://www.mongodb.com/try/download/community).
2. Sélectionnez la version "Community Edition".
3. Choisissez votre système d'exploitation (Windows).
4. Sélectionnez le package MSI.
5. Téléchargez le fichier.

### **Étape 2 : Installer MongoDB**

1. Exécutez le fichier MSI téléchargé.
2. Suivez les étapes de l’assistant d’installation :
   * **Setup Type** : Choisissez "Complete" pour installer tous les composants de MongoDB.
   * **Service Configuration** : Laissez les paramètres par défaut pour installer MongoDB en tant que service Windows (cela permet à MongoDB de démarrer automatiquement au démarrage de Windows).
   * **Install MongoDB Compass** : MongoDB Compass est un outil GUI pour interagir avec MongoDB. Vous pouvez cocher cette option pour l'installer également.
3. Cliquez sur "Install" pour lancer l'installation.

### **Étape 3 : Configurer les variables d’environnement**

1. Ajoutez le chemin de MongoDB aux variables d'environnement pour pouvoir l'exécuter à partir de la ligne de commande :
   * **Chemin à ajouter** : `C:\Program Files\MongoDB\Server\<version>\bin`
   * Remplacez `<version>` par le numéro de version installé.

### **Étape 4 : Lancer MongoDB**

1. Ouvrez l'invite de commande (`cmd`).
2. Tapez `mongod` pour démarrer le serveur MongoDB.
3. MongoDB utilise par défaut le répertoire `C:\data\db` pour stocker les données. Si ce dossier n'existe pas, créez-le.
4. Vous pouvez maintenant commencer à utiliser MongoDB en exécutant `mongo` dans une nouvelle fenêtre de commande.

## **Installation sur macOS**

### **Étape 1 : Installer Homebrew**

Si vous n'avez pas déjà Homebrew (un gestionnaire de paquets pour macOS), installez-le en utilisant la commande suivante dans le terminal :

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### **Étape 2 : Installer MongoDB**

1. Ouvrez le terminal.
2. Exécutez la commande suivante pour ajouter le dépôt MongoDB à Homebrew :

```bash
brew tap mongodb/brew
```

3. Installez MongoDB Community Edition avec la commande :

```bash
brew install mongodb-community
```

### **Étape 3 : Lancer MongoDB**

1. Pour démarrer MongoDB, utilisez la commande :

```bash
brew services start mongodb/brew/mongodb-community
```

2. Pour arrêter MongoDB :

```bash
brew services stop mongodb/brew/mongodb-community
```

3. Pour vérifier que MongoDB fonctionne, exécutez :

```bash
mongo
```

Cela devrait lancer le shell MongoDB.

## **3. Installation sur Linux (Ubuntu/Debian)**

### **Étape 1 : Importer la clé publique**

1. Ouvrez le terminal.
2. Exécutez la commande suivante pour importer la clé publique GPG utilisée par le système de gestion des paquets de MongoDB :

```bash
curl -fsSL https://pgp.mongodb.com/server-6.0.asc | sudo tee /etc/apt/trusted.gpg.d/mongodb.asc
```

### **Étape 2 : Créer le fichier de liste pour MongoDB**

1. Exécutez la commande suivante pour créer un fichier de liste contenant le dépôt MongoDB :

```bash
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list
```

### **Étape 3 : Mettre à jour les paquets**

1. Mettez à jour les paquets locaux avec la commande :

```bash
sudo apt-get update
```

### **Étape 4 : Installer MongoDB**

1. Installez MongoDB avec la commande :

```bash
sudo apt-get install -y mongodb-org
```

### **Étape 5 : Démarrer MongoDB**

1. Démarrez MongoDB en tant que service :

```bash
sudo systemctl start mongod
```

2. Pour vérifier l'état de MongoDB :

```bash
sudo systemctl status mongod
```

3. Pour démarrer MongoDB au démarrage du système :

```bash
sudo systemctl enable mongod
```

### **Étape 6 : Utiliser MongoDB**

1. Pour commencer à utiliser MongoDB, tapez `mongo` dans le terminal.

{% hint style="info" %}
Vous avez maintenant MongoDB installé en local sur votre machine. Vous pouvez commencer à l'utiliser pour stocker et gérer des données pour vos applications.&#x20;
{% endhint %}

{% hint style="danger" %}
N'oubliez pas de sécuriser MongoDB en production en configurant des utilisateurs avec des rôles spécifiques et en limitant l'accès à distance si nécessaire.
{% endhint %}
