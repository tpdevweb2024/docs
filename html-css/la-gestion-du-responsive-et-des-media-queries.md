# La gestion du responsive et des Media Queries

## Définition et principe des Media Queries

Les Media Queries sont des outils CSS3 permettant de créer des styles conditionnels basés sur les caractéristiques de l'appareil affichant un site web, comme la largeur de l’écran, la hauteur, la résolution, etc.&#x20;

{% hint style="success" %}
Elles sont essentielles pour le développement de design web responsive, s'adaptant aux différents appareils.
{% endhint %}

## Syntaxe et fonctionnement des Media Queries

Une Media Query se compose d'un type de média et d'une ou plusieurs expressions qui vérifient les conditions de styles. Voici un exemple basique :

```css
@media screen and (min-width: 600px) {
  /* Ici le code si la condition est vérifiée */
  body {
    background-color: lightblue;
  }
}
```

Ce code applique un arrière-plan lightblue lorsque la largeur de l'écran est d'au moins 600 pixels.

## Création de points d'arrêt (breakpoints) pour différentes tailles d'écran

Les points d'arrêt (breakpoints) sont les seuils à partir desquels la mise en page doit s'adapter pour offrir une expérience utilisateur optimale sur différents appareils. Il est important de choisir des breakpoints pertinents en fonction de la cible et du contenu du site. Voici quelques exemples de breakpoints couramment utilisés :

* Écrans mobiles : 320px, 480px, 600px
* Tablettes : 768px, 1024px
* Ordinateurs de bureau : 1200px, 1440px, 1920px

```css
/* Petits appareils (mobiles, 600px et plus) */
@media (min-width: 600px) {
  body {
    font-size: 0.9rem;
  }
}

/* Tablettes (768px et plus) */
@media (min-width: 768px) {
  body {
    font-size: 1rem;
  }
}

/* Petits ordinateurs de bureau (1024px et plus) */
@media (min-width: 1024px) {
  body {
    font-size: 1.1rem;
  }
}

/* Grands ordinateurs de bureau (1200px et plus) */
@media (min-width: 1200px) {
  body {
    font-size: 1.2rem;
  }
}
```

## Adaptation de la mise en page, des images et des typographies

Pour adapter la mise en page, les médias et les typographies, utilisez des unités relatives et flexibles, comme `em`, `rem`, `%`, et le `vw/vh`.&#x20;

* **Mise en page :** Utilisez des grilles fluides avec des pourcentages, ou encore grid et son système de template.
* **Images :** Définissez des tailles d'images en `%` ou utilisez `max-width: 100%` pour qu'elles ne dépassent pas leur conteneur. Ainsi les images respecteront la taille de leur parent, et ne créeront aucuns débordements.
* **Typographies :** Ajustez la taille des polices avec `em` ou `vw` pour qu'elles s'adaptent à la largeur de l'écran, ainsi l'affichage entre différents formats d'appareils sera compatible et respectera les normes d'accessibilité recommandées.

{% hint style="info" %}
Les Media Queries sont essentielles pour créer un site web réactif. Elles permettent d’ajuster la mise en page, la taille des éléments, et la visibilité des contenus selon les dimensions et caractéristiques de l’appareil utilisé.
{% endhint %}
