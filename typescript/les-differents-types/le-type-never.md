# Le type never

Le type `never` représente les valeurs qui ne se produisent jamais. Il est souvent utilisé pour les fonctions qui lèvent des exceptions ou qui ne terminent jamais leur exécution.

## **Exemple de fonction jetant une erreur :**

```typescript
function throwError(message: string): never {
  throw new Error(message);
}
```

## **Exemple de fonction avec une boucle infinie :**

```typescript
function infiniteLoop(): never {
  while (true) {}
}
```
