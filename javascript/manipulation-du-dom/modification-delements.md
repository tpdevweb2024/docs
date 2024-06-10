# Modification d'éléments

Le JavaScript offre plusieurs façons de modifier les éléments d'une page web. Cela peut être utile pour ajouter de l'interactivité à vos pages web.&#x20;

Voici quelques méthodes clés pour la modification d'éléments dans le DOM (Document Object Model).

## Accès et Modification du contenu

### textContent

```javascript
element.textContent
```

* **Utilisation :** Accéder ou modifier le contenu textuel d'un élément.
* **Exemple :** `element.textContent = "Nouveau texte";`

### innerHTML

```javascript
element.innerHTML
```

* **Utilisation :** Accéder ou modifier le contenu HTML d'un élément.
* **Exemple :** `element.innerHTML = "<p>Nouveau paragraphe</p>";`

## Modification d'attributs

### setAttribute

```javascript
element.setAttribute('attribut', 'valeur')
```

* **Utilisation :** Modifie la valeur d'un attribut d'un élément.
* **Exemple :** `element.setAttribute('id', 'nouvelID');`

## Modification de style

### Propriété de style

```javascript
element.style.propriete = 'valeur'
```

* **Utilisation :** Modifie le style CSS d'un élément.
* **Exemple :** `element.style.backgroundColor = 'blue';`

## Manipulation de classes CSS

### Ajouter une classe CSS

```javascript
element.classList.add('classe')
```

* **Utilisation :** Ajoute une classe CSS à un élément.
* **Exemple :** `element.classList.add('nouvelleClasse');`

### Supprimer une classe CSS

```javascript
element.classList.remove('classe')
```

* **Utilisation :** Supprime une classe CSS d'un élément.
* **Exemple :** `element.classList.remove('ancienneClasse');`

### Alterner une classe CSS

```javascript
element.classList.toggle('classe')
```

* **Utilisation :** Alterne l'ajout et la suppression d'une classe CSS. Si l'élément possède déjà la classe spécifiée, elle est retirée ; sinon, elle est ajoutée.
* **Exemple :** `element.classList.toggle('classeActive');`

{% hint style="info" %}
En utilisant ces méthodes de manière combinée, vous pouvez dynamiquement changer le contenu, la présentation et l'apparence des éléments de votre page web, offrant ainsi une expérience utilisateur plus riche et interactive.
{% endhint %}
