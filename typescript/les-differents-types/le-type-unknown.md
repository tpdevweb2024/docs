# Le type unknown

Le type `unknown` est un type sécurisé pour les valeurs inconnues à la compilation. Il est similaire à `any` mais nécessite une vérification de type avant utilisation.

## Exemple de base

```typescript
let valeurInconnue: unknown;
valeurInconnue = "Hello, TypeScript";

// Nécessite une vérification de type
if (typeof valeurInconnue === "string") {
  console.log(valeurInconnue.toUpperCase());
}
```

## Utilisation sécurisée

Le code suivant démontre comment travailler avec `unknown` en toute sécurité grâce aux vérifications de type :

```typescript
function traiteValeur(valeur: unknown): void {
  if (typeof valeur === "number") {
    console.log(valeur.toFixed(2));
  } else if (typeof valeur === "string") {
    console.log(valeur.length);
  } else {
    console.log("Type inconnu");
  }
}

traiteValeur(42);        // 42.00
traiteValeur("texte");   // 5
traiteValeur(true);      // Type inconnu
```

Le type `unknown` encourage ainsi des pratiques de programmation sécurisées en TypeScript.
