# Manipulation du DOM

## Concept du DOM (Document Object Model)

Le DOM (Document Object Model) est une interface de programmation qui représente la structure d'une page web sous forme d'un arbre d'objets. Chaque élément HTML (balises, attributs, texte, etc.) est représenté par un nœud dans cet arbre. Le DOM permet aux langages de script, comme JavaScript, d'accéder et de manipuler dynamiquement le contenu, la structure et le style d'un document web.

## Sélection et modification d'éléments HTML avec JavaScript

JavaScript fournit plusieurs méthodes pour sélectionner et modifier les éléments HTML d'une page web.

### Sélection d'éléments

* `document.getElementById('id')` : Sélectionne un élément par son identifiant unique.
* `document.getElementsByTagName('tag')` : Sélectionne les éléments par leur nom de balise.
* `document.getElementsByClassName('class')` : Sélectionne les éléments par leur nom de classe.
* `document.querySelector('selecteur')` : Sélectionne le premier élément correspondant au sélecteur CSS.
* `document.querySelectorAll('selecteur')` : Sélectionne tous les éléments correspondant au sélecteur CSS.

### Modification d'éléments

* `element.textContent` : Accède ou modifie le contenu textuel d'un élément.
* `element.innerHTML` : Accède ou modifie le contenu HTML d'un élément.
* `element.setAttribute('attribut', 'valeur')` : Modifie la valeur d'un attribut d'un élément.
* `element.style.propriete = 'valeur'` : Modifie le style CSS d'un élément.
* `element.classList.add('classe')` : Ajoute une classe CSS à un élément.
* `element.classList.remove('classe')` : Supprime une classe CSS d'un élément.

### Création et suppression d'éléments dynamiquement

JavaScript permet de créer et de supprimer des éléments HTML dynamiquement.

### Création d'éléments

* `document.createElement('tag')` : Crée un nouvel élément HTML.
* `element.appendChild(nouveauElement)` : Ajoute un nouvel élément comme dernier enfant d'un élément parent.
* `element.insertBefore(nouveauElement, elementExistant)` : Insère un nouvel élément avant un élément existant.

### Suppression d'éléments

* `element.removeChild(enfant)` : Supprime un élément enfant d'un élément parent.
* `element.remove()` : Supprime l'élément lui-même du DOM.
