# Les bases de Github

## Création de Compte GitHub

Pour créer un compte GitHub, suivez ces étapes simples :

1. Allez sur le site officiel de [GitHub](https://github.com).
2. Cliquez sur le bouton **Sign up** en haut à droite de la page.
3. Remplissez le formulaire avec votre nom d'utilisateur, adresse e-mail, et mot de passe.
4. Choisissez un plan d'abonnement. (Il y a une option gratuite qui convient à la plupart des utilisateurs.)
5. Suivez les instructions pour compléter la création de votre compte.

### Docs :

[Set up Git - GitHub Docs](https://docs.github.com/en/get-started/getting-started-with-git/set-up-git?email\_source=welcome)



### Créer un dépôt git avec Github

* Créer un dépôt sur Github
* Cloner ce dépôt sur votre disque dur (`git clone`)
* Y ajouter un fichier (`git add`, `git commit`), puis mettre à jour le dépôt distant (`git push`)

Le but est de retrouver ce fichier dans la page du dépôt sur Github, ainsi que le commit correspondant.

#### **Notes importantes**

* À savoir: “dépôt” se traduit “repository”, en Anglais.
* Nous avons besoins de l’utilisation d’un terminal (aussi appelé “shell”, “console” ou “invite de commandes”).
  * Si vous êtes sous macOS ou linux: il suffit d’utiliser le terminal fourni. Si macOS vous propose d’installer “XCode Command Line Tools”, acceptez. Vous aurez peut-être besoin de redémarrer ensuite votre terminal.
  * Si vous êtes sous Windows, utilisez Ubuntu (cf [procédure d’installation](https://docs.microsoft.com/fr-fr/windows/wsl/install-win10)).
* Le signe dollar (`$`) permet d’indiquer que la commande qui suit sera à saisir dans le terminal. Pour que la commande fonctionne, il ne faut pas copier le `$` dans le terminal, seulement la commande qui suit.
* Si jamais vous ne reconnaissez plus l’invite de commandes de votre terminal et/ou que vous n’arrivez plus à exécuter des commandes, pressez les touches `Ctrl-C` pour revenir à l’invite de commandes.
* Si jamais vous êtes bloqué(e) dans l’editeur de texte `vi`, tapez la séquence de touches `:q` et présser la touche `entrer`pour quitter et revenir à l’invite de commandes.war

#### **Étapes**

1. Vérifier dans le terminal que `git` est bien installé: `$ git version`. Si ce n’est pas le cas, installez-le en suivant les recommandations de votre système d’exploitation où en le téléchargeant depuis [git-scm.com/downloads](https://git-scm.com/downloads), puis redémarrez votre terminal.\

2. Vérifier dans le terminal que vous êtes identifié(e): `$ git config user.email` doit afficher votre adresse email. Si ce n’est pas le cas, suivez les instructions de la section “Votre identité” de [Paramétrage à la première utilisation de Git](https://git-scm.com/book/fr/v2/D%C3%A9marrage-rapide-Param%C3%A9trage-%C3%A0-la-premi%C3%A8re-utilisation-de-Git).\

3. Ouvrir l’interface web Github\

4.  Toujours depuis de l’interface de Github, créez un dépôt:

    *   Cliquer sur “+” → “new repository”

        * Donner un nom de projet concis, en minuscules, et séparé par des tirets



        <figure><img src="../.gitbook/assets/Capture_decran_2024 03 24_a_23.13.36.png" alt=""><figcaption></figcaption></figure>
    * Choisissez “public”, afin que le dépôt soit accessible en lecture aux autres.


5. Dans le terminal:
   * Téléchargez le dépôt sur votre disque-dur (en local) : `$ git clone <url>` (remplacer `<url>` par l’adresse HTTPS de votre dépôt, celle qui finit par `.git`)
   * puis entrez dans le dossier de ce dépôt: `$ cd nom_du_dépôt`\

6. Créer un commit:
   * `$ echo "Bonjour" > README.md` pour créer un fichier `README.md` contenant le texte “Bonjour”
     * ou Clic droit créé un fichier `README.md` contenant le texte “Bonjour”
   * `$ git status` (optionnel) pour constater qu’un fichier a été créé mais pas encore ajouté dans le dépôt
   * `$ git add README.md` pour ajouter le fichier `README.md` dans l’espace de staging (index)
   * `$ git status` (optionnel) pour afficher le contenu actuel de l’espace de staging (index)
   * `$ git commit -m "ajout du fichier README.md"` pour créer un commit à partir de l’espace de staging. Notez que le texte fourni entre guillemets est libre. Similairement à l’objet d’un email, ce message permet d’expliquer de manière concise quelles modifications sont apportées au dépôt par votre commit.
   * `$ git status` (optionnel) pour constater que l’espace de staging a été réinitialisé et qu’aucun fichier n’a été modifié depuis votre commit
   * `$ git push` pour uploader votre commit sur votre dépôt distant, hébergé sur le serveur Github.



Le fichier `README.md` devrait maintenant être visible depuis la page web du dépôt, sur hithub.
