# Les concepts avancés

A présent, explorons les concepts clés de la Programmation Orientée Objet (POO) en PHP, en mettant l'accent sur l'héritage, le polymorphisme, et l'encapsulation.

Ces principes fondamentaux vous permettront de concevoir des applications plus modulaires, réutilisables et faciles à maintenir.

## L'Héritage <a href="#lheritage" id="lheritage"></a>

L'héritage est un mécanisme qui permet à une classe de ‘hériter’ des propriétés et méthodes d'une autre classe.

La classe qui hérite est appelée **"classe enfant"**, tandis que la classe dont les caractéristiques sont héritées est connue sous le nom de **"classe parent"**.

```php
// Classe parent
class Voiture {

  public $marque;
  
  public function demarrer() {
    echo "La voiture démarre";
  }
  
}

// Classe enfant
class Porsche extends Voiture {

  public $modele = "911";
  
  public function afficherModele() {
    echo "Le modèle est " . $this->modele;
  }
  
}
```

_Dans l'exemple de code fourni pour illustrer l'héritage en PHP, nous avons deux classes: `Voiture` et `Porsche`._

La classe `Voiture` définit une propriété publique `$marque` et une méthode `demarrer()` qui affiche un message lorsque la voiture démarre.

La classe `Porsche` hérite de la classe `Voiture` (comme indiqué par l'extension `extends Voiture`) et introduit une propriété supplémentaire `$modele` avec une valeur par défaut de `"911"`.

Elle fournit également une méthode `afficherModele()` qui affiche le modèle de la Porsche.

Cet exemple illustre comment l'héritage permet à une classe enfant d'utiliser les propriétés et les méthodes de la classe parent, tout en ajoutant ou en modifiant des fonctionnalités selon ses besoins spécifiques.

## Le Polymorphisme <a href="#le-polymorphisme" id="le-polymorphisme"></a>

Le polymorphisme permet à des classes différentes d'être traitées via une interface commune ou à des méthodes d'être redéfinies pour des comportements spécifiques. Ce concept facilite la flexibilité et la réutilisabilité du code.

```php
interface Forme {
  public function aire();
}

class Cercle implements Forme {
  private $rayon;
  public function __construct($rayon) {
    $this->rayon = $rayon;
  }
  public function aire() {
    return pi() * pow($this->rayon, 2);
  }
}

class Carre implements Forme {
  private $cote;
  public function __construct($cote) {
    $this->cote = $cote;
  }
  public function aire() {
    return pow($this->cote, 2);
  }
}
```

_Le code PHP ci-dessus illustre le principe du polymorphisme grâce à l'implémentation de l'interface `Forme` par deux classes différentes : `Cercle` et `Carre`._

Les deux classes respectent l'interface `Forme` en implémentant la méthode `aire`, qui calcule la surface de la forme. Cependant, chaque classe propose sa propre mise en œuvre de cette méthode, démontrant ainsi la capacité du polymorphisme à gérer différents objets via une interface commune.

La classe `Cercle` calcule la surface en se basant sur le rayon, en utilisant la formule mathématique ( \pi r^2 ), tandis que la classe `Carre` calcule la surface comme étant le carré de son côté. Cette approche améliore non seulement la flexibilité et la réutilisabilité du code, mais souligne également la nature polymorphique de la programmation orientée objet en permettant à la même interface de répondre à différentes fonctionnalités.

## L'Encapsulation <a href="#lencapsulation" id="lencapsulation"></a>

L'encapsulation est une technique qui consiste à restreindre l'accès aux composantes d'un objet. Cela est généralement réalisé à l'aide des niveaux de visibilité: public, protected, et private.

* **public** : Accessible de partout.
* **protected** : Accessible seulement dans la classe elle-même et par les classes qui en héritent.
* **private** : Accessible uniquement dans la classe elle-même.

```php
class CompteBancaire {
  private $solde;

  public function __construct($montantInitial) {
    $this->solde = $montantInitial;
  }

  public function deposer($montant) {
    $this->solde += $montant;
  }

  public function retirer($montant) {
    if ($montant <= $this->solde) {
      $this->solde -= $montant;
    } else {
      echo "Solde insuffisant";
    }
  }

  public function getSolde() {
    return $this->solde;
  }
}
```

Le code ci-dessus définit une classe `CompteBancaire` en PHP qui illustre l'encapsulation, l'un des piliers de la programmation orientée objet (POO). Voici comment le code fonctionne et ses composants clés :

**Classe `CompteBancaire`**

**Propriétés**

* `private $solde;` : Une propriété privée qui stocke le solde du compte. L'attribut privé garantit que le solde ne peut pas être modifié directement de l'extérieur de la classe, préservant ainsi l'intégrité des données.

**Méthodes**

* `__construct($montantInitial)` : C'est le constructeur de la classe. Il initialise le solde du compte avec un montant initial fourni lors de la création de l'objet `CompteBancaire`.
* `deposer($montant)` : Cette méthode publique permet d'ajouter un montant spécifié au solde actuel du compte. Étant publique, elle peut être appelée de n'importe où, à l'extérieur de la classe.
* `retirer($montant)` : Permet de retirer un montant spécifié du compte si le solde est suffisant. Si le montant demandé est supérieur au solde, un message "Solde insuffisant" est affiché. Cette logique garantit la sécurité de la transaction.
* `getSolde()` : Une méthode publique qui retourne le solde actuel du compte. Elle permet un accès contrôlé à l'information du solde, respectant le principe d'encapsulation.

Cette classe est un exemple de comment encapsuler et protéger les données, tout en fournissant une interface publique pour interagir avec ces données de manière sécurisée.

Exemple d'instanciation et d'application des méthodes aux propriétés :

```php
// Création d'un nouvel objet CompteBancaire avec un solde initial de 1000
$compte = new CompteBancaire(1000);

// Dépôt de 500
$compte->deposer(500);

// Retrait de 200
$compte->retirer(200);

// Affichage du solde actuel : 1300
echo "Le solde actuel est de ".$compte->getSolde()." euros.";
```
