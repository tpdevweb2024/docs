# Le type array

<pre class="language-typescript"><code class="lang-typescript"><strong>let listeDeNombres: number[] = [1, 2, 3, 4, 5];
</strong>let listeDeNoms: string[] = ["Alice", "Bob", "Charlie"];
</code></pre>

## Utilisation de `Array<T>` générique

Une autre syntaxe que celle ci-dessus exite :&#x20;

```typescript
let listeDeBooleens: Array<boolean> = [true, false, true];
```

## Accès et manipulation des éléments

```typescript
console.log(listeDeNombres[0]); // Affiche 1
listeDeNombres.push(6); // Ajoute 6 au tableau
```

## Fonctions et méthodes courantes

```typescript
let longueur = listeDeNombres.length; // Taille du tableau
let premierElement = listeDeNoms.shift(); // Retire et renvoie le premier élément
```

## Tableaux de tableaux (Tableaux multidimensionnels)

```typescript
let grille: number[][] = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
];
```

{% hint style="info" %}
Le type `array` en TypeScript est flexible et permet de créer et manipuler des collections d'éléments de manière simple et efficace.
{% endhint %}
