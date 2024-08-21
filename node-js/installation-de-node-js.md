# Installation de Node JS

## **Installation sur Windows**&#x20;

* Rendez-vous sur le site officiel de Node.js : [nodejs.org](https://nodejs.org/).
* Téléchargez la version recommandée pour la plupart des utilisateurs (LTS - Long Term Support).
* Exécutez le fichier d'installation (.msi) téléchargé.
* Suivez les instructions de l'installateur (les paramètres par défaut conviennent généralement).
* Après l'installation, ouvrez l'invite de commande (`cmd`) ou PowerShell pour vérifier l'installation.

## **Installation sur macOS**&#x20;

* Vous pouvez utiliser le gestionnaire de paquets Homebrew pour installer Node.js.
*   Ouvrez le terminal et exécutez la commande suivante pour installer Homebrew (si ce n'est pas déjà fait) :

    ```bash
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
    ```
*   Ensuite, installez Node.js en utilisant la commande suivante :

    ```bash
    brew install node
    ```
* Pour ceux qui préfèrent, il est aussi possible de télécharger directement le package d'installation depuis [nodejs.org](https://nodejs.org/) et de suivre les instructions.

## **Installation sur Linux**&#x20;

*   Pour les distributions basées sur Debian/Ubuntu :

    ```bash
    sudo apt update
    sudo apt install nodejs
    sudo apt install npm
    ```
*   Pour les distributions basées sur Red Hat/Fedora :

    ```bash
    sudo dnf install nodejs
    sudo dnf install npm
    ```
*   Une autre méthode universelle consiste à utiliser `nvm` (Node Version Manager), qui permet de gérer plusieurs versions de Node.js :

    ```bash
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
    source ~/.bashrc
    nvm install --lts
    ```

## Vérification de l'installation

### **Vérifier la version de Node.js**&#x20;

*   Ouvrez votre terminal (ou invite de commande sur Windows) et tapez :

    ```bash
    node -v
    ```
* Cela devrait afficher la version de Node.js installée (par exemple, `v18.16.0`).

### **Vérifier la version de npm**&#x20;

*   Dans le même terminal, tapez :

    ```bash
    npm -v
    ```
* Vous devriez voir la version de npm installée (par exemple, `9.5.0`).
