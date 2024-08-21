# Le type string

Le type `string` en TypeScript est utilisé pour représenter des chaînes de caractères. Voici un exemple d'utilisation :

```typescript
let message: string = "Bonjour, TypeScript!";
```

Les chaînes de caractères peuvent être concaténées en utilisant l'opérateur `+` :

```typescript
let greeting: string = "Bonjour";
let target: string = "monde";
let fullGreeting: string = greeting + ", " + target + "!";
```

Vous pouvez aussi utiliser les templates littéraux pour des chaînes multi-lignes et l'interpolation de variables :

```typescript
let name: string = "Alice";
let welcomeMessage: string = `Bienvenue, ${name}!`;
```
