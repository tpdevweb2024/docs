# Envoyer des emails

Envoyer un email depuis Laravel peut s'avérer très intéressant, lors de la création d'un compte, envoi d'un message automatique, notification à l'admin ...

Voyons comment mettre en place un système de mail dans Laravel :

## Définir les paramètres d'envoi

Pour définir les paramètres d'envoi de mails dans Laravel, vous devez configurer votre fichier `.env`. Ajoutez ou modifiez les lignes suivantes selon votre service de mail :

```
MAIL_MAILER=smtp
MAIL_HOST=smtp.example.com
MAIL_PORT=587
MAIL_USERNAME=votre_nom_utilisateur
MAIL_PASSWORD=votre_mot_de_passe
MAIL_ENCRYPTION=tls
MAIL_FROM_ADDRESS=adresse@example.com
MAIL_FROM_NAME="${APP_NAME}"
```

{% hint style="info" %}
Ces paramètres permettent à Laravel de se connecter à votre service de messagerie et d'envoyer des emails.
{% endhint %}

## Créer une classe mail de Laravel

Tout comme il existe des classes de type Controller, ou de type Model, ou autres … Il existe également des classes de type Mailable.

Pour créer une nouvelle classe d'Email sous Laravel, nous allons entrer la commande :

```
php artisan make:mail productInsertedMail
```

{% hint style="warning" %}
Cette action va nous créer un nouveau dossier Mail au sein de notre dossier app.
{% endhint %}

## Modifier notre modèle d'email

Nous pouvons alors remarquer une structure simple :

```php
<?php

namespace App\Mail;

use Illuminate\Bus\Queueable;
use Illuminate\Contracts\Queue\ShouldQueue;
use Illuminate\Mail\Mailable;
use Illuminate\Queue\SerializesModels;

class productInsertedMail extends Mailable
{
    use Queueable, SerializesModels;

    /**
     * Create a new message instance.
     *
     * @return void
     */
    public function __construct()
    {
        
    }

    /**
     * Build the message.
     *
     * @return $this
     */
    public function build()
    {
        return $this->view('myview');
    }
}

```

Nous allons alors comprendre deux choses, notre constructeur, qui pour l'heure ne réclame aucun paramètre, va nous permettre de passer des informations.&#x20;

La function build va quant à elle nous permettre de définir le gabarit ou template de l'email à utiliser, il sera alors nécessaire de créer une view dans notre répertoire resources/views.

### La méthode build()

Modifions quelque peu cette fonction build() :

```php
public function build()
{
    return $this->from('no-reply@monsite.fr')
                        ->subject("Un email qui confirme l'ajout d'un produit")
                        ->view('emails.product.inserted');
}
```

### Le constructeur

Si nous souhaitions passer des informations dans notre modèle d'email, c'est dans ce constructeur que nous allons ajouter des variables, et nous préférerons généralement un array()

```php
 public $user = [];

 /**
  * Create a new message instance.
  *
  * @return void
  */
 public function __construct(array $user)
 {
     $this->user = $user;
 }
```

### La vue du gabarit

Une fois ces informations $user passées, elles sont maintenant directement utilisables dans notre vue précédemment définie, ce code permettra d'afficher notamment son nom (si il s'avère défini) :

```php
{{ $user['name'] }}
// Nous mettons la clé sous crochet puisque s'agit d'un tableau et non un objet
```

## Modification du Controller

Maintenant que nous avons créé notre modèle d'email ainsi que son contenu, il va alors s'avérer intéressant de l'intégrer à notre Controller, et notamment la méthode store() par exemple :

```php
 public function store(Request $request)
 {
     $user = [ "email" => "user@example.com", "name" => "John Doe"];
     Mail::to($user['email'])->send(new productInsertedMail($user));
     return redirect()->route('homepage');
 }
```

Nous pouvons noter deux choses, l'appel du model Mail, qui est étendu de Mailable, expliqué un peu plus haut, et le passage de deux méthode :

* la méthode to() qui définira le ou les destinataire(s), si plusieurs alors utilisation d'un array
* la méthode send(), qui nous demandera de créer une instance de notre Model de Mail, ainsi que les informations à passer dans son constructeur.

{% hint style="info" %}
Pour exécuter l'envoi de l'email, il suffira d'appeler la méthode dans lequel le Mail::to se situe bien évidemment.
{% endhint %}
