# Évènements et interactions

## Le principe&#x20;

Le `addEventListener` est une méthode très puissante et flexible utilisée pour attacher des gestionnaires d'événements à des éléments spécifiques d'une page web.&#x20;

### Types d'évènements

Cette méthode permet de spécifier le type d'événement que l'on souhaite écouter, comme par exemple `click`, `mouseover`, `keydown`, `resize`, et bien d'autres.&#x20;

En réponse à cet événement, une fonction préalablement définie sera exécutée, ce qui permet de créer une interactivité dynamique et riche sur les pages web.

### La composition

Le premier paramètre de la méthode `addEventListener` est toujours une chaîne représentant le type d'événement. Le deuxième paramètre est la fonction de rappel (callback) qui sera exécutée lorsque l'événement spécifié se produit.&#x20;

Il est également possible de passer un troisième paramètre optionnel, qui est un objet contenant des propriétés de contrôle supplémentaires, comme `capture`, `once`, et `passive`.

Voici un exemple simple d'utilisation de `addEventListener`:

```javascript
const button = document.getElementById('myButton');
button.addEventListener('click', function(event) {
  alert('Bouton cliqué !');
});
```

{% hint style="info" %}
Dans cet exemple, nous attachons un gestionnaire d'événements `click` à un élément bouton avec l'ID `myButton`. **Lorsque ce bouton est cliqué, une alerte apparaîtra avec le message "Bouton cliqué !**"**.**&#x20;
{% endhint %}

Cette flexibilité permet aux développeurs de facilement ajouter des fonctionnalités interactives qui répondent à diverses actions des utilisateurs sur la page web, améliorant ainsi l'expérience utilisateur.

```javascript
element.addEventListener('click', function() {
    // Code à exécuter lors du clic sur l'élément
});
```

### Le comportement par défaut

La méthode `preventDefault` est une fonction essentielle en JavaScript qui est utilisée pour empêcher le comportement par défaut d'un événement. Par exemple, lorsque vous soumettez un formulaire sur une page web, le comportement par défaut est de rafraîchir la page et de procéder à la soumission du formulaire au serveur.&#x20;

En utilisant `preventDefault`, vous pouvez intercepter cet événement et empêcher le rechargement de la page, ce qui est particulièrement utile si vous souhaitez valider les données en JavaScript ou effectuer des requêtes AJAX sans recharger la page.&#x20;

Cela offre une plus grande flexibilité et un meilleur contrôle sur le comportement des événements dans vos applications web.

{% code overflow="wrap" %}
```javascript
form.addEventListener('submit', function(event) {
    event.preventDefault();
    // Code à exécuter lors de la soumission du formulaire, 
    // celui-ci (formulaire) ne sera en revanche pas soumis
});
```
{% endcode %}

{% hint style="info" %}
Cela permet de gérer les validations et autres logiques avant d'effectuer l'action par défaut.
{% endhint %}
