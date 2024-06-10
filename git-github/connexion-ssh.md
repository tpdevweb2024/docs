# Connexion SSH

#### Connexion SSH avec GitHub sur macOS/Linux

1. Ouvrez votre terminal.
2.  Générez une nouvelle clé SSH (remplacez "your\_email@example.com" par votre email et nom\_choisie)&#x20;

    ```
    ssh-keygen -t rsa -b 4096 -f nom_choisie 

    ou

    ssh-keygen -t rsa -b 4096 -C "your_email@example.com" -f nom_choisie
    ```

Lorsque vous le lancez, vous verrez le message ci-dessous. Appuyez sur "Entrée" pour sauvegarder la clé dans l'emplacement par défaut (indiqué entre parenthèses) :

```
Generating public/private rsa key pair.
Enter file in which to save the key (/your_home_path/.ssh/id_rsa):
```

Ensuite, vous serez invité à saisir une phrase secrète (passphrase). Bien que cela soit optionnel, il est recommandé pour une sécurité accrue.

```
Enter passphrase (empty for no passphrase):
```

Après avoir défini une passphrase, le processus génère la clé et affiche le résumé de la clé générée, ainsi que son empreinte digitale. Vous verrez un message similaire à :

```
Your identification has been saved in /your_home_path/.ssh/id_rsa.
Your public key has been saved in /your_home_path/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx your_email@example.com
The key's randomart image is:
+---[RSA 4096]----+
|        o..      |
|       . o.o     |
|        +..o     |
|       o o= .    |
|      . S + *    |
|       . O + =   |
|        E B . o  |
|           . o   |
|                 |
+----[SHA256]-----+
```



Après avoir généré votre clé SSH, vous pouvez l'associer à votre compte GitHub pour faciliter la gestion des dépôts Git. Suivez ces étapes pour ajouter votre clé SSH à votre compte GitHub&#x20;



1.  Copiez le contenu de votre clé publique SSH dans le presse-papiers. Vous pouvez utiliser la commande suivante pour le faire :

    ```bash
    cat ~/.ssh/id_rsa.pub


    ```
2. Allez sur le site de GitHub et connectez-vous à votre compte.\

3. Cliquez sur votre photo de profil en haut à droite de la page, puis sur **Settings**.\

4. Dans la barre latérale de navigation, cliquez sur **SSH and GPG keys**.\

5. Cliquez sur le bouton **New SSH key** ou **Add SSH key**.\

6. Dans le champ "Title", ajoutez un descriptif pour la nouvelle clé, par exemple `Mon PC`.
7. Collez votre clé publique dans le champ "Key".\

8. Cliquez sur **Add SSH key**.

Une fois que vous avez ajouté votre clé SSH, vous pouvez facilement gérer vos dépôts Git sans avoir à saisir vos identifiants GitHub chaque fois que vous communiquez avec GitHub.

####
