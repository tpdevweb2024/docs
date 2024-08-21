# Le type enum

Les Enums (énumérations) en TypeScript permettent de définir un ensemble de valeurs nommées. Ils sont utiles pour représenter des collections de valeurs constantes.

```typescript
enum Couleur {
  Rouge,
  Vert,
  Bleu,
}

let couleurFavorite: Couleur = Couleur.Vert;
console.log(couleurFavorite); // Affiche 1
```

Dans cet exemple, `Couleur` est une énumération avec trois valeurs : `Rouge`, `Vert` et `Bleu`. Les valeurs par défaut commencent à `0` et augmentent de `1` pour chaque membre.

Pour modifier les valeurs par défaut d'une énumération, vous pouvez attribuer explicitement des valeurs spécifiques à ses membres.

```typescript
enum Couleur {
  Rouge = 3,
  Vert = 5,
  Bleu = 7,
}

let couleurFavorite: Couleur = Couleur.Vert;
console.log(couleurFavorite); // Affiche 5
```

Dans cet exemple, les membres de `Couleur` ont des valeurs spécifiques 3, 5, et 7.
