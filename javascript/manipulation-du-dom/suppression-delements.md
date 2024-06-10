# Suppression d'éléments

Pour supprimer des éléments du DOM en JavaScript, vous pouvez utiliser plusieurs méthodes. Voici les plus courantes :&#x20;

## Supprimer des éléments en JS

### `removeChild()`

Pour supprimer un élément enfant spécifique d'un élément parent :

```javascript
var element = document.getElementById("element-a-supprimer");
element.parentNode.removeChild(element);
```

### `remove()`

Depuis les versions modernes de JavaScript, il est aussi possible d'utiliser la méthode `remove()` directement sur l'élément à supprimer :

```javascript
document.getElementById("element-a-supprimer").remove();
```

## Suppression d'éléments par Sélecteur

Pour supprimer plusieurs éléments répondant à un certain critère, vous pouvez combiner `querySelectorAll` avec une boucle :

```javascript
document.querySelectorAll(".classe-a-supprimer").forEach(e => e.remove());
```
