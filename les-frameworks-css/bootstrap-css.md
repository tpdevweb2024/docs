# Bootstrap CSS

## Introduction à Bootstrap

### Présentation du framework et de ses composants

Bootstrap est un framework CSS libre et gratuit qui permet de concevoir rapidement et facilement des interfaces web responsives et mobiles. Il contient des outils de conception HTML et CSS pour la typographie, les formulaires, les boutons, les tableaux, les grilles, la navigation, et bien plus, ainsi que des extensions JavaScript optionnelles.&#x20;

Bootstrap est compatible avec les dernières versions des principaux navigateurs et offre un système de grille flexible et facile à utiliser pour adapter vos projets web à différentes tailles d'écran et dispositifs.

### Avantages et inconvénients de Bootstrap

#### ✅ Avantages

* **Facilité d'utilisation :** Les classes préconçues de Bootstrap permettent une mise en œuvre rapide et facile sans avoir à écrire beaucoup de CSS.
* **Responsive Design :** La grille responsive de Bootstrap facilite la création de sites adaptatifs sans effort supplémentaire.
* **Personnalisable :** Bootstrap peut être personnalisé pour répondre aux besoins spécifiques de votre projet, vous permettant de n'inclure que les fonctionnalités dont vous avez besoin.
* **Populaire :** En tant que l'un des frameworks front-end les plus utilisés, Bootstrap bénéficie d'une grande communauté, offrant de vastes ressources d'apprentissage et des plugins tiers.

#### ❌ Inconvénients

* **Taille du fichier :** Un inconvénient de l'utilisation de Bootstrap peut être la taille relativement importante des fichiers CSS et JavaScript, ce qui peut affecter les performances de chargement des pages.
* **Aspect uniforme :** L'utilisation intensive de Bootstrap sans personnalisation peut conduire à un design qui semble générique ou trop similaire à d'autres sites utilisant le même framework.
* **Fonctionnalités (trop) variées :** Bien que facile à utiliser pour les débutants, maîtriser tous les aspects de Bootstrap et le personnaliser efficacement peut nécessiter un certain temps d'apprentissage.

### Installation et configuration de Bootstrap

L'installation de Bootstrap peut être réalisée de plusieurs manières, selon les besoins de votre projet :

#### **Utilisation d'un CDN**

C'est la méthode la plus rapide pour commencer. Vous ajoutez simplement les liens vers les fichiers CSS et JavaScript de Bootstrap dans votre en-tête HTML.

```html
<!-- Lien CSS de Bootstrap -->
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">

<!-- JavaScript Bundle -->
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
```

#### Installation manuelle de Bootstrap CSS

Pour installer manuellement Bootstrap CSS dans un projet web, suivez ces étapes :

1. Allez sur le site officiel de Bootstrap et téléchargez la dernière version de Bootstrap.
2. Une fois le téléchargement terminé, extrayez le fichier ZIP.
3. Copiez les fichiers CSS et JS extraits dans le dossier de votre projet. Il est recommandé de placer les fichiers CSS dans un dossier `css` et les fichiers JS dans un dossier `js`.
4. Liez le fichier CSS de Bootstrap dans le `<head>` de votre fichier HTML.
5. ```html
   <link rel="stylesheet" href="chemin/vers/le/dossier/css/bootstrap.min.css">
   ```
6. Incluez également le fichier JavaScript de Bootstrap à la fin de votre corps de page, avant la fermeture de la balise `</body>`, pour s'assurer que votre page est bien chargée avant d'exécuter le script.
7. ```html
   <script src="chemin/vers/le/dossier/js/bootstrap.bundle.min.js"></script>
   ```

#### Installation via le NPM

Pour installer Bootstrap dans votre projet en utilisant le gestionnaire de paquets npm, suivez ces étapes :

1. Ouvrez votre terminal.
2. Naviguez vers le dossier de votre projet.
3. Exécutez la commande suivante pour installer Bootstrap :
4. ```bash
   npm install bootstrap
   ```
5. Une fois l'installation terminée, les fichiers de Bootstrap seront ajoutés à votre dossier `node_modules`.
6. Pour utiliser Bootstrap dans votre projet, vous devez inclure les fichiers CSS et JS dans vos fichiers HTML. Vous pouvez le faire en ajoutant les lignes suivantes dans le `<head>` pour le CSS :
7.  ```html
    <link rel="stylesheet" href="node_modules/bootstrap/dist/css/bootstrap.min.css">
    ```

    Et juste avant la fermeture de la balise `</body>` pour le JavaScript :

    ```html
    <script src="node_modules/bootstrap/dist/js/bootstrap.bundle.min.js"></script>
    ```

    Cela vous permet d'utiliser toutes les fonctionnalités de Bootstrap dans votre projet.

## Utilisation de la grille Bootstrap

### Compréhension du système de grille et des classes associées

Bootstrap utilise un système de grille flexible qui permet de créer des mises en page responsives facilement. Ce système est basé sur des rangées (rows) et des colonnes (columns), où vous pouvez organiser vos contenus.

* **Rangées (`row`)** : Un conteneur horizontal qui regroupe vos colonnes. Toutes les colonnes doivent être placées à l'intérieur d'une rangée.
* **Colonnes (`col`)** : Les éléments de base de la grille qui vous permettent de placer votre contenu. Bootstrap utilise un système de grille de 12 colonnes, vous permettant de spécifier la largeur de vos colonnes selon vos besoins.

#### Classes de grille

* `col-`: s’adapte automatiquement à la largeur du contenu.
* `col-[taille]-[nombre]`: contrôle la largeur de la colonne sur différents appareils (`taille` = `sm`, `md`, `lg`, `xl`, `xxl`; `nombre` = `1` à `12`).
* `offset-[taille]-[nombre]`: ajoute un espace à gauche de la colonne, décalant ainsi la position de la colonne.

<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

### Mise en place d'une mise en page responsive avec la grille Bootstrap

Pour créer une mise en page responsive, utilisez différentes classes de grille selon la taille de l'écran. Par exemple, pour une colonne qui prend toute la largeur sur les petits écrans mais seulement la moitié sur les écrans moyens et plus grands :

```html
<div class="container">
  <div class="row">
    <div class="col-12 col-md-6">Contenu</div>
    <div class="col-12 col-md-6">Contenu</div>
  </div>
</div>
```

{% hint style="info" %}
Cette structure basique montre comment créer une mise en page responsive, avec un contenu qui s'ajuste selon la taille de l'écran.
{% endhint %}

## Classes utilitaires de base

Bootstrap fournit une série de classes utilitaires conçues pour effectuer diverses actions CSS de manière pratique.&#x20;

Ces classes simplifient le développement en évitant l'écriture de styles CSS personnalisés pour des ajustements fréquents. Voici quelques-unes des classes utilitaires de base:

### Espacement

#### Padding

Bootstrap fournit de nombreuses classes utilitaires pour définir le padding d'un élément, avec le même système de notation que pour les marges :

* `p-*` : padding sur tous les côtés
* `pt-*`, `pb-*`, `ps-*`, `pe-*` : padding sur un côté spécifique
* `px-*`, `py-*` : padding horizontal ou vertical

Les valeurs possibles sont `0`, `1`, `2`, `3`, `4`, `5` qui correspondent à des multiples du `$spacer` défini dans Sass.Exemples :

* `<div class="p-3">Padding de 3 unités sur tous les côtés</div>`
* `<div class="pt-2 pb-4">Padding vertical variable</div>`

#### Margin

De la même manière, Bootstrap propose des classes utilitaires pour définir les marges :

* `m-*` : marge sur tous les côtés
* `mt-*`, `mb-*`, `ms-*`, `me-*` : marge sur un côté spécifique
* `mx-*`, `my-*` : marge horizontale ou verticale

Les valeurs possibles sont les mêmes que pour le padding.Exemples :

* `<div class="m-5">Marge de 5 unités sur tous les côtés</div>`
* `<div class="mx-auto">Centrage horizontal</div>`

Bootstrap permet également d'utiliser des valeurs négatives pour les marges, en ajoutant un `n` avant la valeur :

* `mt-n1` : marge supérieure négative de 1 unité

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

### Alignement du texte

```html
<div class="text-start">Mon texte aligné à gauche</div>

<div class="text-center">Mon texte aligné au centre</div>

<div class="text-end">Mon texte aligné à droite</div>
```

### Titres

Bootstrap fournit des classes pour les titres de niveau 1 à 6 (`h1` à `h6`) ainsi que des classes `.h1` à `.h6` pour appliquer le même style de police à d'autres éléments.&#x20;

```html
<h1>Titre niveau 1</h1>

<p class="h2">Titre niveau 2 dans un paragraphe</p>
```

### Personnalisation des titres

Bootstrap propose également des classes pour personnaliser l'apparence des titres, comme `display-1` à `display-6` pour des titres plus imposants.

```html
<h3 class="display-4">Titre display-4</h3>
```

### Couleurs

Bootstrap fournit de nombreuses classes utilitaires pour définir la couleur du texte (`text-*`) et de l'arrière-plan (`bg-*`).&#x20;

```html
<p class="text-primary">Texte en couleur primaire</p>

<div class="bg-success p-3">Fond en couleur de succès</div>
```

### Visibilité

Des classes comme `d-none`, `d-sm-block`, `d-md-none` permettent de contrôler la visibilité des éléments sur différentes tailles d'écran. Exemples :

```html
<div class="d-none d-md-block">Visible uniquement sur grand écran</div>

<span class="d-inline-block d-sm-none">Visible uniquement sur petit écran</span>
```

{% hint style="info" %}
Ces classes visent à accélérer le développement en réduisant le besoin de styles CSS supplémentaires et en favorisant une approche cohérente de la mise en page et de l'esthétique.
{% endhint %}

## Éléments de base

### Typographie

La typographie est essentielle pour structurer et hiérarchiser l'information. Voici comment utiliser les éléments de base en Bootstrap :

#### Titres

Bootstrap permet d'appliquer des styles de titres avec les classes `.h1` à `.h6`, sans avoir à changer la balise HTML :

```html
<p class="h1">Titre de niveau 1</p>
<p class="h2">Titre de niveau 2</p>
```

Pour une personnalisation poussée, utilisez les classes `display-1` à `display-4` :

```html
<p class="display-1">Titre grand format</p>
```

#### Paragraphes

Utilisez la balise `<p>` pour les paragraphes, et ajoutez des classes `.text-*` pour ajuster l'apparence du texte (par exemple, `.text-muted` pour griser le texte) :

```html
<p class="text-muted">Ceci est un paragraphe grisé.</p>
```

#### Listes

Les listes ordonnées et non ordonnées sont stylisées par défaut, mais vous pouvez les personnaliser avec des classes CSS :

```html
<ul class="list-unstyled">
  <li>Élément 1</li>
  <li>Élément 2</li>
</ul>

<ol class="list-inline">
  <li class="list-inline-item">Premier</li>
  <li class="list-inline-item">Deuxième</li>
</ol>
```

### Boutons

Pour styliser des boutons, utilisez la classe `.btn` et ajoutez des variantes de couleurs à l'aide des classes `.btn-*`. Voici quelques exemples:

```html
<button type="button" class="btn btn-primary">Primaire</button>
<button type="button" class="btn btn-secondary">Secondaire</button>
<button type="button" class="btn btn-success">Succès</button>
<button type="button" class="btn btn-danger">Danger</button>
<button type="button" class="btn btn-warning">Avertissement</button>
<button type="button" class="btn btn-info">Info</button>
<button type="button" class="btn btn-light">Léger</button>
<button type="button" class="btn btn-dark">Sombre</button>
```

Vous pouvez aussi spécifier des états pour vos boutons, comme actif ou désactivé :

```html
<button type="button" class="btn btn-primary active">Actif</button>
<button type="button" class="btn btn-primary" disabled>Désactivé</button>
```

### Icônes

Pour intégrer des icônes dans vos éléments HTML, vous pouvez utiliser des bibliothèques tierces comme Font Awesome ou Bootstrap Icons. Voici comment vous pouvez ajouter une icône à un bouton :

**Font Awesome**

```html
<button type="button" class="btn btn-primary">
  <i class="fa fa-check"></i> Valider
</button>
```

**Bootstrap Icons**

```html
<button type="button" class="btn btn-success">
  <i class="bi bi-check-circle"></i> Succès
</button>
```

Assurez-vous d'inclure les fichiers CSS correspondant à la bibliothèque d'icônes de votre choix dans votre projet pour que les icônes s'affichent correctement.

### Images et médias

#### Images et médias

Pour créer des images adaptatives qui s'ajustent à la largeur de leur conteneur, utilisez la classe `.img-fluid`. Cette classe applique `max-width: 100%;` et `height: auto;` aux images pour s'assurer qu'elles ne dépassent jamais leur conteneur.

**Exemple d'image avec arrondis :**

Pour ajouter des arrondis aux images, Bootstrap propose plusieurs classes telles que `.rounded`, `.rounded-circle` pour une bordure totalement arrondie, et `.rounded-0` pour supprimer les arrondis.

**Exemple d'image responsive :**

En ce qui concerne l'intégration de vidéos ou d'iframes (comme des vidéos YouTube ou des cartes Google Maps), il est recommandé d'utiliser la classe `.embed-responsive` combinée à un specifique ratio classe comme `.embed-responsive-16by9` ou `.embed-responsive-4by3` pour conserver le ratio de l'élément tout en le rendant responsive.

**Exemple d'iframe responsive :**

```html
<div class="embed-responsive embed-responsive-16by9">
  <iframe class="embed-responsive-item" src="url-de-votre-iframe" allowfullscreen></iframe>
</div>
```

## Composants Bootstrap

### Barres de navigation

Les barres de navigation sont des composants clés pour la navigation dans les applications web. Bootstrap offre une facilité de création et de personnalisation de ces barres avec la classe `.navbar`.&#x20;

Voici une manière simplifiée de mettre en œuvre une barre de navigation responsive et esthétique :

* **Classe `.navbar`** pour créer une barre de navigation.
* **Personnalisation** avec des classes telles que `.navbar-expand-*` pour contrôler le comportement responsive, `.navbar-light` ou `.navbar-dark` pour le thème de couleur, et bien d'autres options pour un design sur mesure.
* **Inclusion de divers éléments** tels que des marques (logo ou nom), des menus déroulants, des formulaires de recherche, des liens, et des icônes pour une navigation complète.

{% hint style="info" %}
Cet agencement assure non seulement une navigation intuitive pour l'utilisateur mais renforce également l'identité visuelle de l'application web.
{% endhint %}

### Alertes

Pour informer ou alerter l'utilisateur de certaines actions ou informations importantes, Bootstrap propose le composant d'alerte. Voici comment l'utiliser :

* **Classe `.alert`** pour créer des boîtes d'alerte.
* **Variantes de couleurs** avec `.alert-*` (par exemple, `.alert-success` pour un message de succès, `.alert-warning` pour un avertissement).
* **Possibilité d'ajouter des boutons de fermeture** en utilisant le composant de bouton avec la classe `.btn-close` pour permettre aux utilisateurs de fermer l'alerte.

### Badges

Pour intégrer des badges à votre application, utilisez la classe `.badge`. Ces badges peuvent être ajoutés à d'autres éléments, tels que les boutons, pour fournir des informations supplémentaires ou attirer l'attention sur des éléments spécifiques.

* **Ajout de badges** : Utilisez la classe `.badge` suivie d'une classe de couleur pour personnaliser l'apparence. Par exemple, `.badge-primary` pour un badge bleu.
* **Combinaison avec des boutons** : Placez un badge dans un bouton pour indiquer des informations telles que le nombre de notifications. Exemple : `<button class="btn btn-primary">Notifications <span class="badge bg-secondary">4</span></button>`.
* **Personnalisation** : Les badges peuvent être personnalisés en tenant compte des couleurs, de la taille et d'autres styles CSS pour s'adapter au mieux à votre design.

Cette fonctionnalité enrichit la communication visuelle au sein de l'application en permettant de catégoriser ou de mettre en évidence des informations clés.

### Cartes

* Classe `.card` pour créer des cartes
* Sections divisées en l'en-tête (`card-header`), le corps (`card-body`), le pied de page (`card-footer`)
* Possibilité d'ajouter des images, des boutons, et d'autres éléments au sein de la carte

```html
<div class="card" style="width: 250px">
  <img src="card-img-top" alt="Card image cap">
  <div class="card-body">
    <h5 class="card-title">Mon titre</h5>
    <p class="card-text">Un contenu de type texte dans ma card.</p>
    <a href="#" class="btn btn-primary">CTA</a>
  </div>
</div>
```

### Modales

* Classe `.modal` pour créer des fenêtres modales
* Contrôle de l'ouverture/fermeture avec JavaScript
* Personnalisation du contenu et de l'apparence

Les modales sont des fenêtres qui s'affichent au-dessus de la page principale, permettant de capturer l'attention de l'utilisateur pour des informations supplémentaires ou des actions. Elles sont utiles pour des formulaires, des avertissements ou tout contenu nécessitant une interaction explicite de l'utilisateur.

#### Exemple Basique

```html
<!-- Bouton déclencheur -->
<button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModal">
  Lancer la modale
</button>

<!-- Modale -->
<div class="modal fade" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">Titre de la modale</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Fermer">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body">
        Contenu de la modale.
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal">Fermer</button>
        <button type="button" class="btn btn-primary">Sauvegarder les changements</button>
      </div>
    </div>
  </div>
</div>
```

Ce code crée une modale de base pouvant être déclenchée par un bouton. Les classes de Bootstrap gèrent l'aspect visuel, tandis que les attributs `data-toggle` et `data-target` associés au bouton servent à contrôler l'affichage de la modale. La fermeture se fait via le bouton avec `data-dismiss="modal"` ou en cliquant hors de la modale.

### Accordéons

Les accordéons sont un moyen efficace d'organiser le contenu de manière compacte. Ils permettent aux utilisateurs de révéler l'information section par section. Voici comment implémenter un accordéon simple :

#### Création d'un Accordéon

```html
<div class="accordion" id="accordionExample">
  <div class="accordion-item">
    <h2 class="accordion-header" id="headingOne">
      <button class="accordion-button" type="button" data-bs-toggle="collapse" data-bs-target="#collapseOne" aria-expanded="true" aria-controls="collapseOne">
        Accordéon Item #1
      </button>
    </h2>
    <div id="collapseOne" class="accordion-collapse collapse show" aria-labelledby="headingOne" data-bs-parent="#accordionExample">
      <div class="accordion-body">
        Contenu de l'Accordéon Item #1.
      </div>
    </div>
  </div>
  <div class="accordion-item">
    <h2 class="accordion-header" id="headingTwo">
      <button class="accordion-button collapsed" type="button" data-bs-toggle="collapse" data-bs-target="#collapseTwo" aria-expanded="false" aria-controls="collapseTwo">
        Accordéon Item #2
      </button>
    </h2>
    <div id="collapseTwo" class="accordion-collapse collapse" aria-labelledby="headingTwo" data-bs-parent="#accordionExample">
      <div class="accordion-body">
        Contenu de l'Accordéon Item #2.
      </div>
    </div>
  </div>
</div>
```

Pour le contrôle, l'attribut `data-bs-toggle="collapse"` est utilisé pour manipuler l'ouverture et la fermeture des items, et `data-bs-target` spécifie l'élément à contrôler. Ajouter des icônes ou des boutons supplémentaires dans chaque item ou en-tête pour enrichir l'interactivité et la présentation de l'accordéon.

### Carrousels

#### Création d'un Carrousel

Pour créer un carrousel d'images adaptable et interactif, utilisez Bootstrap et sa classe `.carousel`. Ce composant permet de faire défiler automatiquement ou manuellement des éléments comme des images ou du texte.

**Éléments requis :**

1. **Classe `.carousel`**: L'élément de base pour la création du carrousel.
2. **Data Attributes**:
   * `data-bs-ride="carousel"`: Permet de lancer le défilement automatique à la charge de la page.
   * `data-bs-slide-to`: Indique à quel slide se déplacer lorsque l'on clique sur un indicateur.
3. **Contrôles de Navigation**: Pour naviguer manuellement d'un slide à l'autre.
4. **Indicateurs**: Points en bas du carrousel permettant de naviguer vers un slide spécifique.

**Exemple de Carrousel**

```html
<div id="monCarrousel" class="carousel slide" data-bs-ride="carousel">
  <div class="carousel-indicators">
    <button type="button" data-bs-target="#monCarrousel" data-bs-slide-to="0" class="active" aria-current="true" aria-label="Slide 1"></button>
    <button type="button" data-bs-target="#monCarrousel" data-bs-slide-to="1" aria-label="Slide 2"></button>
    <button type="button" data-bs-target="#monCarrousel" data-bs-slide-to="2" aria-label="Slide 3"></button>
  </div>
  <div class="carousel-inner">
    <div class="carousel-item active">
      <img src="chemin_vers_image1.jpg" class="d-block w-100" alt="...">
    </div>
    <div class="carousel-item">
      <img src="chemin_vers_image2.jpg" class="d-block w-100" alt="...">
    </div>
    <!-- Ajoutez plus de slides ici -->
  </div>
  <!-- Contrôles Précédent & Suivant -->
  <button class="carousel-control-prev" type="button" data-bs-target="#monCarrousel" data-bs-slide="prev">
    <span class="carousel-control-prev-icon" aria-hidden="true"></span>
    <span class="visually-hidden">Précédent</span>
  </button>
  <button class="carousel-control-next" type="button" data-bs-target="#monCarrousel" data-bs-slide="next">
    <span class="carousel-control-next-icon" aria-hidden="true"></span>
    <span class="visually-hidden">Suivant</span>
  </button>
</div>
```

Personnalisez ce carrousel en ajoutant ou en retirant des slide, et en ajustant les options de contrôle et d'indicateurs selon vos besoins pour offrir une expérience utilisateur optimale.

## Personnalisation et thématisation

### Utilisation des variables Sass

Bootstrap utilise un système de variables Sass qui permet de personnaliser facilement les styles de base. En remplaçant ces variables, vous pouvez donner à votre projet une apparence unique tout en conservant la cohérence et la fonctionnalité de Bootstrap. Voici quelques exemples de variables couramment utilisées :

* `$spacer`: Contrôle l'espace de marge et de padding à travers le framework.
* `$enable-rounded`: Active ou désactive les arrondis des composants.
* `$primary`: Définit la couleur principale utilisée dans divers composants (boutons, liens, etc.).

Pour surcharger ces variables, définissez-les avant d'importer les fichiers Sass de Bootstrap dans votre fichier principal Sass :

```scss
// Personnalisation des variables de Bootstrap
$primary: #007bff;
$enable-rounded: false;

// Importation de Bootstrap
@import "node_modules/bootstrap/scss/bootstrap";
```

Cette méthode vous permet de créer une apparence personnalisée pour vos applications web en ajustant les éléments de base offerts par Bootstrap à vos propres spécifications de design.

### Surcharge des styles par défaut

Pour surcharger les styles par défaut de Bootstrap, après avoir défini vos variables personnalisées et importé Bootstrap, vous pouvez ajouter des règles CSS ou Sass supplémentaires pour ajuster davantage les styles à vos besoins. Cela permet une personnalisation plus fine au-delà des variables et des cartes Sass.

```scss
// Personnalisation approfondie
body {
  font-family: "Votre police préférée", sans-serif;
}

.btn-primary {
  background-color: $primary;
  border-radius: 0; // Si `$enable-rounded` est false
}

// Ajoutez d'autres styles personnalisés ici
```

Ces surcharges doivent être placées après l'importation de Bootstrap pour s'assurer qu'elles prennent la priorité sur les styles par défaut.

### Création d'un thème personnalisé

Pour créer un thème personnalisé avec Bootstrap, modifiez les cartes Sass fournies. Par exemple, pour personnaliser les couleurs principales, ajustez la carte `$theme-colors` :

```scss
// Définir vos couleurs personnalisées
$your-primary: #007bff; // bleu
$your-success: #28a745; // vert

// Utiliser vos couleurs dans la carte des couleurs du thème
$theme-colors: (
  "primary": $your-primary,
  "success": $your-success,
  // Ajoutez ou modifiez d'autres couleurs ici
);
```

Ensuite, utilisez ces variables dans votre projet pour maintenir la cohérence du thème. Bootstrap appliquera automatiquement ces couleurs à divers composants, tels que les boutons et les liens, permettant ainsi une personnalisation globale et cohérente du thème.
