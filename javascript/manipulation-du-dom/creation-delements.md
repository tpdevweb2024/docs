# Création d'éléments

Pour manipuler et interagir avec le DOM en JavaScript, il est essentiel de savoir créer et insérer de nouveaux éléments dans la page web.&#x20;

Voici quelques méthodes fondamentales :&#x20;

## Créer un élément

```javascript
document.createElement('tag') 
```

Cette fonction crée un nouvel élément HTML. Remplacez `'tag'` par le nom de la balise de l'élément que vous souhaitez créer, par exemple `'div'`, `'span'`, etc.

## Ajouter un nouvel élément

```javascript
element.appendChild(nouveauElement)
```

Elle permet d'ajouter `nouveauElement` comme dernier enfant d'un élément parent spécifié. Cela signifie que `nouveauElement` sera placé après tous les autres enfants existants de l'élément parent.

## Ajouter un nouvel élément avent un autre

```javascript
element.insertBefore(nouveauElement, elementExistant)
```

Cette méthode insère `nouveauElement` avant `elementExistant` dans la liste des enfants de leur parent commun. C'est utile pour placer un nouvel élément à un endroit spécifique parmi les enfants d'un élément parent.
