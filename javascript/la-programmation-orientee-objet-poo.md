# La programmation Orientée Objet (POO)

La Programmation Orientée Objet (POO) est un paradigme qui permet de structurer le code d'une manière modulaire et réutilisable.&#x20;

Elle est essentielle pour gérer des projets complexes et favorise la maintenance du code.&#x20;

## Les Bases de la POO

### Classes et Objets

**Classe**: Schéma ou modèle définissant les propriétés et méthodes.

**Objet**: Instance de la classe.

```javascript
class Voiture {
  constructor(marque, modele) {
    this.marque = marque;
    this.modele = modele;
  }
  démarrer() {
    console.log(`${this.marque} ${this.modele} démarre.`);
  }
}

const maVoiture = new Voiture('Toyota', 'Corolla');
maVoiture.démarrer();
```

### Attributs et Méthodes

* **Attribut**: Caractéristique ou propriété de la classe.
* **Méthode**: Fonction définie dans la classe.

### Avantages et Applications

#### Facilité de Maintenance

La facilité de maintenance est une caractéristique essentielle pour toute base de code bien conçue. Un code bien maintenu permet aux développeurs de repérer et de corriger plus facilement les bugs, d'ajouter des fonctionnalités et de rendre la base de code plus robuste au fil du temps.&#x20;

Cela inclut l'écriture de tests unitaires, l'utilisation de bonnes pratiques en matière de documentation et l'adhésion à des conventions de codage claires.

#### Modularité

La modularité est le concept de diviser une base de code en segments indépendants ou semi-indépendants. Chaque module gère une partie spécifique de la fonctionnalité et peut être développé, testé et maintenu séparément.&#x20;

Cela permet non seulement de réutiliser du code dans différents projets, mais également de faciliter la maintenance et l'évolution des systèmes logiciels complexes.

#### Réutilisabilité du Code

La réutilisabilité du code fait référence à la capacité de certains segments de code à être utilisés dans différents contextes sans modification ou avec des modifications minimales.&#x20;

Cela permet d'économiser du temps et des ressources, car les développeurs peuvent tirer parti de solutions existantes plutôt que de réinventer la roue à chaque projet. \
Une bonne conception modulaire et une documentation adéquate sont essentielles pour garantir une réutilisabilité efficace du code.

## Principes Fondamentaux

### Encapsulation

L'encapsulation consiste à regrouper les données (attributs) et les méthodes (fonctions) qui les manipulent au sein d'une seule classe. Cela permet de protéger l'intégrité des données en limitant leur accès direct depuis l'extérieur de la classe. Seules les méthodes de la classe peuvent accéder et modifier les attributs, garantissant ainsi une meilleure maîtrise des données.

```javascript
class CompteBancaire {
  constructor(solde) {
    let _solde = solde; // Attribut privé

    this.deposer = function(montant) {
      if (montant > 0) {
        _solde += montant;
      }
    };

    this.retirer = function(montant) {
      if (montant > 0 && montant <= _solde) {
        _solde -= montant;
      }
    };

    this.consulterSolde = function() {
      return _solde;
    };
  }
}

const compte = new CompteBancaire(100);
compte.deposer(50);
console.log(compte.consulterSolde()); // 150
```

_Par exemple, dans la classe `CompteBancaire`, l'attribut `_solde` est privé et ne peut être modifié que via les méthodes `deposer` et `retirer`, assurant ainsi la sécurité des opérations bancaires._

### Héritage

L'héritage permet à une classe de dériver les propriétés et méthodes d'une autre classe.

```javascript
class Véhicule {
  constructor(type) {
    this.type = type;
  }
}

class Moto extends Véhicule {
  constructor(marque) {
    super('Moto');
    this.marque = marque;
  }
}
```

### Polymorphisme

Le polymorphisme permet d'utiliser des objets de différentes classes de manière interchangeable en utilisant une interface commune. Par exemple, si vous avez une méthode `afficherDetails` qui fonctionne sur des objets de types différents, vous pouvez appeler cette méthode sur n'importe quel objet qui implémente cette interface, indépendamment de sa classe spécifique.

```javascript
class Vehicule {
  afficherDetails() {
    console.log("Détails du véhicule");
  }
}

class Voiture extends Vehicule {
  afficherDetails() {
    console.log("Détails de la voiture");
  }
}

class Moto extends Vehicule {
  afficherDetails() {
    console.log("Détails de la moto");
  }
}

let vehicules = [new Voiture(), new Moto()];
vehicules.forEach(v => v.afficherDetails());
```

_Dans cet exemple, la méthode `afficherDetails` peut être appelée sur des instances de `Voiture` et `Moto` grâce au polymorphisme._

{% hint style="info" %}
La Programmation Orientée Objet en JavaScript est une compétence essentielle pour les développeurs modernes. Elle permet de créer des applications robustes et évolutives. Expérimentez avec les exemples fournis et intégrez ces concepts dans vos projets pour améliorer votre code.
{% endhint %}
