# Le prototyping

## Création d'interactions simples

### Interactions simples telles que les clics et les survols

Pour commencer à créer des interactions simples dans Figma, comme des clics et des survols, suivez ces étapes :

1. **Sélection de l'élément** : Utilisez l'outil de sélection (flèche ou V) pour choisir l'élément que vous voulez rendre interactif.
2. **Création d'un frame** : Placez l'élément sélectionné dans un frame (raccourci : F) si ce n'est pas déjà fait. Les interactions ne peuvent être définies que sur des frames.
3. **Définition de l'interaction** : Avec le frame sélectionné, accédez au panneau droit sous l'onglet 'Prototype'. Ici, vous pouvez définir les interactions. Pour un clic, choisissez 'On Click' comme déclencheur. Pour un survol, sélectionnez 'On Hover'.
4. **Déplacement et survol** : Pour créer une interaction de survol, vous pouvez ajuster la propriété 'Opacity', 'Fill', ou utiliser d'autres propriétés sous l'onglet 'Design' pour changer l'apparence de l'élément au survol.
5. **Test de l'interaction** : Utilisez le mode Présentation (icône de lecture en haut à droite) pour tester vos interactions. Assurez-vous que tout fonctionne comme prévu.

{% embed url="https://www.youtube.com/watch?v=F0Axo2Mv3kY" %}

### Options de déclenchement

Pour rendre vos prototypes interactifs dans Figma, vous pouvez définir des actions spécifiques déclenchées par les interactions de l'utilisateur.&#x20;

1. **Sélection du frame interactif** : Commencez par sélectionner le frame avec lequel l'utilisateur interagira.
2. **Accès aux paramètres de Prototype** : Dans le panneau sur la droite, cliquez sur l'onglet 'Prototype'.
3. **Choix du déclencheur** : Sous 'Interactions', choisissez le type de déclencheur pour votre interaction. Les options incluent notamment :
   * **'On Click'** : Déclenche l'action lorsque l'élément est cliqué.
   * '**On Drag'** : Déclenche l'action lorsque l'élément est glissé.
   * **'While Hovering'** : Continue de déclencher l'action tant que la souris reste au-dessus de l'élément.
   * **'On Press'** : Déclenche l'action lorsque l'élément est pressé.
4. **Définition de l'action** : Après avoir choisi un déclencheur, définissez l'action qui se produira. Cela peut être naviguer vers une autre frame, ouvrir un lien, changer l'état d'une animation, etc.
5. **Ajustement des options** : Selon l'action choisie, vous pouvez ajuster des paramètres supplémentaires comme l'animation (dissolution, glissement, etc.), la durée de l'animation, et plus encore.

### Options de destination pour guider l'utilisateur

Lors de la création de prototypes interactifs dans Figma, il est crucial de définir clairement les écrans ou les états de destination. Ces destinations déterminent où l'utilisateur est amené à la suite de ses interactions.&#x20;

Voici comment utiliser les options de destination efficacement :

1. **Définir une destination** : Après avoir configuré un déclencheur d'interaction sur un frame, vous devez choisir une destination. Cliquez sur la section 'Action' dans le panneau 'Prototype' et sélectionnez 'Navigate to' pour définir un écran de destination.
2. **Choix de l'écran de destination** : Sélectionnez l'écran ou l'état vers lequel l'utilisateur sera dirigé une fois l'action déclenchée. Vous pouvez choisir parmi les frames existants dans votre projet.
3. **Personnalisation de la transition** : Configurez la transition pour cette navigation. Figma offre plusieurs options comme 'Dissolve', 'Slide in', 'Push', et vous pouvez également ajuster la vitesse et le style de l'animation.
4. **Tester le flux d'interaction** : Utilisez régulièrement le mode Présentation pour tester et affiner le parcours utilisateur. Assurez-vous que les transitions sont fluides et que les destinations correspondent aux attentes.
5. **Itération et amélioration** : Basé sur les retours et les tests, ajustez les destinations et les transitions pour optimiser l'expérience utilisateur.

## Utilisation des transitions pour animer les interactions

Figma permet une personnalisation approfondie des transitions, vous permettant ainsi de simuler des mouvements réalistes et d'enrichir l'expérience utilisateur.&#x20;

Voici quelques étapes pour tirer le meilleur parti des transitions :

1. **Sélectionner le type de transition** : Choisir entre différentes transitions comme 'Dissolve', 'Slide in', 'Push', etc., selon l'effet désiré.
2. **Ajuster les paramètres** : Modifier la durée et la courbe d'animation pour affiner le timing et le comportement de la transition.
3. **Utiliser les transitions intelligentes** : Pour les composants dynamiques, utilisez 'Smart animate' pour créer des transitions fluides entre différents états en ajustant automatiquement les différences.
4. **Preview et ajustements** : Tester régulièrement vos transitions en mode Présentation pour évaluer l'effet visuel et ajuster les paramètres pour perfectionner l'animation.

{% embed url="https://www.youtube.com/watch?v=Web_c0GyjHw" %}

### Personnalisation des animations avec les courbes de Bézier

Les courbes de Bézier offrent un contrôle précis sur le comportement des transitions en permettant d'ajuster la vitesse et la direction de l'animation. En modifiant les points de contrôle des courbes de Bézier, vous pouvez créer des mouvements plus naturels et dynamiques. Suivez ces étapes pour exploiter leur potentiel :

1. **Accéder aux options de courbe** : Dans les paramètres de transition, sélectionnez 'Custom' dans les options de courbe d'animation.
2. **Ajuster les points de contrôle** : Modifiez les points de contrôle pour influencer la vitesse de démarrage, le milieu et la fin de l'animation.
3. **Tester et itérer** : Prévisualisez l'effet des ajustements sur l'animation et continuez à modifier les points jusqu'à atteindre l'effet désiré.

### Contrôle du timing des transitions

Pour personnaliser davantage vos transitions dans Figma, utilisez les options de durée et de retard :

#### **Durée**

Déterminez combien de temps la transition doit durer. Une durée plus longue peut rendre les mouvements plus fluides, tandis qu'une courte durée peut les rendre plus dynamiques.

#### **Délai**

Ajoutez un délai avant le début de la transition. Cela peut être utile pour créer une séquence d'animations ou pour attendre que d'autres éléments se chargent.

## Le prototyping avancé

### Utilisation des variables et des contraintes

* **Variables** : Utilisez des variables pour stocker des données clés telles que les couleurs, les dimensions et les états d'interaction. Cela permet de maintenir une cohérence dans votre design et de faciliter les ajustements globaux.
* **Contraintes** : Les contraintes permettent de définir la manière dont les composants de l'interface s'adaptent à différents écrans et orientations. En attribuant des contraintes d'échelle, d'ancrage et de proportion, vous assurez que votre design reste fonctionnel et esthétique sur toute une gamme d'appareils.

**Exemples d'Application**

* **Adaptabilité** : En appliquant des contraintes appropriées, un bouton peut se redimensionner automatiquement en fonction de la largeur de l'écran, garantissant ainsi une expérience utilisateur optimale sur mobiles et tablettes.
* **Interactivité** : Les variables peuvent être utilisées pour modifier l'apparence d'un élément (comme la couleur d'arrière-plan d'un bouton) lorsqu'il est cliqué, offrant ainsi un feedback visuel immédiat à l'utilisateur.

{% embed url="https://www.youtube.com/watch?v=LhhMpKXhRmQ" %}

{% embed url="https://www.youtube.com/watch?v=QP72d478tfE" %}
