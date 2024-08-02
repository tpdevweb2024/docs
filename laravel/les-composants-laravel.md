# Les composants Laravel

L'objectif des components sous Laravel est de proposer des solutions de factorisation de notre code, comme l'utilisation répétée d'une card spécifique, ou encore l'affichage de notre navbar ...

## Créer un nouveau component

Pour créer un nouveau composant Laravel, nous allons devoir ouvrir notre Terminal, puis lui indiquer la commande suivante :

```
php artisan make:component Alert
```

Cette action va nous créer une composant nommé Alert, que nous retrouverons dans notre dossier app/View/Components -> Alert.php

Mais également une view dans notre dossier resources/views, qui lui ne comprendra qu'une simple div

### Le Model de component

Notre classe Alert a bien été générée, et elle comprend le contenu suivant :

```php
<?php

namespace App\View\Components;

use Illuminate\View\Component;

class Alert extends Component
{
    /**
     * Create a new component instance.
     *
     * @return void
     */
    public function __construct()
    {
        //
    }

    /**
     * Get the view / contents that represent the component.
     *
     * @return \Illuminate\Contracts\View\View|\Closure|string
     */
    public function render()
    {
        return view('components.alert');
    }
}

```

Remarquons alors la présence d'un constructeur que nous verrons ensuite, et d'une function render() qui aura pour but de rendre notre composant avec l'utilisation d'une view, en l'occurrence celle générée par notre commande CLI dans resources/views

### Notre component view

Voici maintenant à quoi ressemble notre vue de composant :

```markup
<div>
    <!-- The only way to do great work is to love what you do. - Steve Jobs -->
</div>
```

Modifions le en :

```markup
<div style="background:green; color:white; padding:0.2rem 0.3rem; border-radius: 12px; text-align:center">
    <p>Ceci est un composant Alert</p>
</div>
```

## L'utilisation du composant

Pour utiliser notre composant à l'intérieur de nos vues, nous allons devoir utiliser une syntaxe précise :

```markup
<div class="container">
    <!--- On affiche notre composant --->
    <x-alert />
</div>
```

Vous pouvez remarquer que notre composant est parfaitement fonctionnel

## Le passage de paramètre

Pour passer des paramètres, il va alors être nécessaire de spécifier celui-ci à l'appel du composant, dans son constructeur, ainsi que dans le template du rendu

Voyons la classe :

```php
public $message;
/**
 * Create a new component instance.
 *
 * @return void
 */
public function __construct($message)
{
    $this->message = $message;
}
```

Ensuite le composant :

{% code overflow="wrap" %}
```markup
<div style="background:green; color:white; padding:0.2rem 0.3rem; border-radius: 12px; text-align:center">
    <p>{{ $message }}</p>
</div>
```
{% endcode %}

Et enfin notre page où est placé ce composant :

```markup
<h1>Welcome to Home page</h1>
<x-alert message="Ceci est un composant Alert" />
<!--- On peut alors voir que notre attribut porte le nom de notre variable 
déclarée dans noptre class et dans notre vue composant --->
```

## L'utilisation des slots

Pour utiliser un slot, nous allons changer quelque peu notre façon d'instancier notre composant :

{% code overflow="wrap" %}
```markup
<div style="background:green; color:white; padding:0.2rem 0.3rem; border-radius: 12px; text-align:center">
    {{ $slot }}
</div>
```
{% endcode %}

Ainsi pour passer des informations, mêmes écrites en HTML, dans notre composant, nous utiliserons la variable \{{ $slot \}}, puis nous passerons le contenu que l'on souhaite afficher entre une balise ouvrante fermante, ce qui nous donne :

```markup
<h1>Welcome to Home page</h1>
<x-alert>
    <div>
        <p style="color:red">Mon contenu en rouge</p>
    </div>
</x-alert>

```

{% hint style="warning" %}
Pensez à modifier votre constructeur si vous ne passez plus de variable $message, car celui-ci provoquera une erreur de paramètre non défini dans ce cas
{% endhint %}

## IMPORTANT : la casse de vos models

Imaginons que nous ayons créé **un model portant le nom de myAlert**, nous aurions alors à instancier notre composant dans nos vues de la façon suivante :

```markup
<x-my-alert />
<!--- La casse changera alors en tenant compte du camelcase 
pour remplacer chaque majuscule par un principe de tiret/minuscule --->
```
