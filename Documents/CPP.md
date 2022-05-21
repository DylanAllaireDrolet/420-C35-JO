Évolution du langage C, ajoutant principalement la prise en charge du paradigme orienté objet.

# Historique

En 1979, Bjarne Stroustrup travaille à son doctorat et trouve de nombreuses fonctionnalités intéressantes au langage Simula. Mais il n’était pas aussi performant que le langage C, qui lui, était de trop bas niveaux.

<br>![Bjarne Stroustrup](../Images/BjarneStroustrup.png)

En 1980, dans les laboratoires Bell d'AT&T, Stroustrup commence à améliorer le langage C en lui ajoutant la prise en charge de classe, de dérivation, du polymorphisme, etc. Bref, en lui faisant supporter le paradigme orienté objet. D’ailleurs, son nom de code était : « C with classes » mais, en 1983, il fut nommé « C++ », faisant un clin d’oeil à la syntaxe du langage.

> Il est facile de se tirer dans le pied avec le langage C; c’est plus difficile avec le langage C++ mais, lorsque vous y arrivez, c’est la jambe en entier qui explose.
>
> \- Bjarne Stroustrup

# Classe

Les classes sont les entités de bases du paradigme orienté objet.

## U.M.L.

La notation UML permet de visualiser rapidement et simplement la déclaration d'une classe:

<br>![UML](../Images/UMLClass.png)

## Déclaration

Le mot-clé « class » permet de déclarer une classe avec l'identificateur de notre choix:

<br>![Déclaration](../Images/ClassDeclaration.png)

### Modificateurs d'accès

Les modificateurs d'accès permettent de rendre une classe robuste en limitant l'accès aux membres sensibles:

| Accès   | Symbole | Description                                                      |
|---------|:-------:|------------------------------------------------------------------|
|private  |    -    | Accessible que de l'implémentation de la classe.                 |
|public   |    +    | Accessible de l'implémentation de la classe et de ses instances. |

Un modificateur d'accès s'applique à tout ce qui le suit:

<br>![Déclaration](../Images/ClassAccessModificators.png)

*« private » est appliqué par défaut si aucun modificateur d'accès n'est déclaré.*

## Implémentation

L'implémentation d'une classe se fait dans son bloc de code.

### Données membres

On nomme donnée membre les variables déclarées à l'intérieur d'une classe:

<br>![Donnée membre](../Images/ClassDataMember.png)

### Méthodes

On nomme méthode les fonctions déclarées à l'intérieur d'une classe:

<br>![Méthode](../Images/ClassMethod.png)

### Constructeur

Méthode particulière puisqu'elle est appelée automatiquement lors de l'instanciation.

Puisqu'il s'agit d'une méthode que le compilateur doit différencier des autres méthodes, sa syntaxe comporte quelques exigences:

- Aucun type de retour
- Même identificateur que la classe

<br>![Constructeur](../Images/ClassConstructor.png)

Le constructeur est principalement utilisé pour initialiser les données membres:

<br>![Constructeur](../Images/Constructor.png)

*Pour différencier les données membres des paramètres, le mot-clé « this », représentant l'instance de la classe, peut être utilisé.*

#### Défaut

S'il n'a aucun paramètre, on le nomme « constructeur par défaut ».

#### Copie

S'il contient qu'un seul paramètre étant une référence du même type que la classe, on le nomme « constructeur de copie » puisqu'il permet de déterminer comment une instance est dupliquée.

### Destructeur

Mêmes exigences que le constructeur, mais l'identificateur doit être précédé du caractère « ~ ». Et est appelée automatiquement lors de la libération.

# Instance

...

## Instanciation

L'instanciation consiste à allouer l'espace nécessaire en mémoire centrale et initialiser son contenu:

<br>![Instanciation](../Images/instanciation.png)

1. Allocation d'un espace en mémoire centrale pour stocker l'instance.
2. Appel du constructeur de l'instance.
3. Retour de l'adresse de l'instance en mémoire centrale.

## Libération

delete

1. Appel du destructeur.
2. Libération de l'instance en mémoire centrale.