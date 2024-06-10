# Sélection d'éléments

La sélection d'éléments est une opération fondamentale en JavaScript pour la manipulation du DOM (Document Object Model). Elle permet d'accéder à des éléments spécifiques dans une page web pour les lire, les modifier, ou écouter des évènements sur ces éléments.&#x20;

Voici les méthodes les plus couramment utilisées pour sélectionner des éléments dans le DOM.

## Sélection d'éléments

### getElementById

```javascript
document.getElementById('id')
```

Sélectionne un élément par son identifiant unique.

* **Utilisation :** `const element = document.getElementById('monId');`
* **Retourne :** L'élément avec l'id spécifié. Si aucun élément n'est trouvé, renvoie `null`.

### getElementsByTagName

```javascript
document.getElementsByTagName('tag')
```

Sélectionne les éléments par leur nom de balise.

* **Utilisation :** `const elements = document.getElementsByTagName('p');`
* **Retourne :** Une collection en direct des éléments correspondants trouvés dans le document.

### getElementsByClassName

```javascript
document.getElementsByClassName('class')
```

Sélectionne les éléments par leur nom de classe.

* **Utilisation :** `const elements = document.getElementsByClassName('maClasse');`
* **Retourne :** Une collection en direct des éléments correspondants trouvés dans le document.

### querySelector

```javascript
document.querySelector('selecteur')
```

Sélectionne le premier élément correspondant au sélecteur CSS.

* **Utilisation :** `const element = document.querySelector('.maClasse');`
* **Retourne :** Le premier élément qui correspond au sélecteur spécifié. Si aucun élément ne correspond, renvoie `null`.

### querySelectorAll

```javascript
document.querySelectorAll('selecteur')
```

Sélectionne tous les éléments correspondant au sélecteur CSS.

* **Utilisation :** `const elements = document.querySelectorAll('div.maClasse');`
* **Retourne :** Une NodeList statique des éléments correspondants trouvés dans le document.

{% hint style="info" %}
Ces méthodes de sélection d'éléments sont puissantes et permettent de manipuler efficacement le DOM pour créer des interactions dynamiques sur vos pages web. La compréhension de ces sélecteurs est essentielle pour tout développeur web souhaitant manipuler le contenu ou le style de la page.
{% endhint %}
