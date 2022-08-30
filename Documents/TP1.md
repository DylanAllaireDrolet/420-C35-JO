# Travail 1

Ce travail consiste à développer un programme, en ligne de commande, permettant d'afficher une suite de données d'un fichier.

## Fichier à accès aléatoire

Il sera nécessaire de manipuler des fichiers à accès aléatoire, et par conséquent, il faudra aussi gérer les exceptions qui pourraient se produire avec ceux-ci. Les classes ci-dessous doivent donc être importées:

![Importations](Images/TP1Imports.png)

Le constructeur de la classe « RandomAccessFile » permet d'ouvrir un fichier selon un mode, en lecture seule dans ce contexte:

![Fichier à accès aléatoire](Images/TP1RandomAccessFile.png)

Cette classe offre des méthodes afin de manipuler les données d'un fichier à accès aléatoire:

Méthode         | Description
----------------|-------------------------------------------------------------
void close()    | Fermeture de fichier.
long length()   | Obtention de la taille, en octets, du fichier.
int read()      | Obtention de l'octet à la position actuelle dans le fichier.
void seek(long) | Positionnement dans le fichier à l'octet passé en paramètre.

## Procédures

La procédure principale devra récupérer les arguments possibles:

- -o (facultatif, valeur par défaut: 0)
- -l (facultatif, valeur par défaut: taille du fichier - le décalage)
- -f (obligatoire)

Elle devra aussi les valider:

- La valeur du décalage (-o) doit être >= 0 et < que la taille du fichier.
- La valeur de la taille (-l) doit être > 0 et < que la taille du fichier - le décalage.
- La valeur du nom du fichier (-f) doit être valide.

![Fonction principale](Images/TP1Main.png)

Si les arguments sont valides et le fichier ouvert, la procédure « printData » doit être appelée afin d'afficher les données demandées:

![Données](Images/TP1PrintData.png)

Sinon, pour toutes exceptions ou mauvaise utilisation, la procédure « printUsage » doit être appelée afin d'afficher les indications d'utilisation:

![Indications](Images/TP1PrintUsage.png)

## Arguments

Il est possible de passer des arguments lors de l'exécution d'un programme. Par exemple, sous l'éditeur « IntelliJ IDEA », les arguments peuvent être spécifiés en éditant la configuration de compilation:

![Configuration](Images/TP1IDEAConfiguration.png)

![Arguments](Images/TP1IDEAArguments.png)

La procédure principale comporte un paramètre « args », qui consiste en un tableau de chaînes de caractères, dans lequel sont stockés automatiquement les arguments passés au programme. Il serait possible de les afficher de cette façon:

![Arguments](Images/TP1Args.png)

## Exemples

À partir d'un fichier texte nommé « texte.txt » ayant comme contenu:

```
Contenu d'un fichier texte
afin de tester mon premier atelier
du cours de Programmation III
de Techniques de l'Informatique.
```

Le résultat avec l'argument « -f texte.txt » sera:

![Exemple](Images/TP1Exemple.png)

Le résultat avec les arguments « -o 76 -l 17 -f texte.txt » sera:

![Exemple](Images/TP1ExempleA.png)

Et le résultat avec les arguments « -o 98 -l 28 -f texte.txt » sera:

![Exemple](Images/TP1ExempleB.png)

*Il est à noter, dans la section ASCII, que les caractères de contrôle (les sauts de ligne par exemple) doivent être remplacés par le caractère '.'.*

### Affichage formaté

Plutôt que d'utiliser « print » et « println », la méthode « printf » permet de formater l'affichage.

![printf](Images/TP1Printf.png)

**Consultez les documentations à son sujet! Sa maîtrise vous permettra de réduire de beaucoup les traitements nécessaires à l'affichage, et réduira considérablement le temps nécessaire à la réalisation de ce travail.**

### Couleurs

Il est possible, en ligne de commande, de modifier la couleur d'affichage des caractères à l'aide d'une balise spéciale:

![Couleurs](Images/TP1Colors.png)

## Chaînes de caractères

Il est possible, à l'aide du programme développé dans ce travail, de déterminer le mot de passe du programme « [CrackMe.exe](Files/CrackMe.exe) ».

Un argument -s (facultatif, valeur par défaut: 4) pourrait permettre d'afficher les chaines de caractères du fichier, plutôt que ses données, selon la taille minimum passée en paramètre.

![Chaînes de caractères](Images/TP1PrintStrings.png)

Par exemple, le résultat avec les arguments « -l 534 -f CrackMe.exe -s » sera:

![Chaînes de caractères](Images/TP1Strings.png)

*Il est à noter que dans l'exemple ci-haut, les caractères de contrôle des chaînes de caractères (le retour de chariot et le saut de ligne par exemple) sont remplacés par leur balise en programmation. Mais il est permis de les ignorer afin de réduire le temps de développement de ce travail.*

## Format

Il est possible, à l'aide du programme développé dans ce travail, de déterminer le système d'exploitation et le processeur cible des programmes « ProgrammeX.exe »:

- [ProgrammeA.exe](Files/ProgrammeA.exe)
- [ProgrammeB.exe](Files/ProgrammeB.exe)
- [ProgrammeC.exe](Files/ProgrammeC.exe)
- [ProgrammeD.exe](Files/ProgrammeD.exe)

Outre les fichiers texte, le contenu de fichiers binaires est, pour la grande majorité, structuré selon le type de contenu, ce que l'on nomme « format ». Dans le contexte de la programmation, ce sont principalement des fichiers exécutables qui sont produits, et, tout comme les autres, ceux-ci sont structurés selon un format particulier.

Un argument -i (facultatif, aucun paramètre) pourrait permettre d'afficher des informations sur un exécutable (et d'autres types si vous désirez).

![Format](Images/TP1PrintFormat.png)

Par exemple, le résultat avec les arguments « -f ProgrammeA.exe -i » sera:

![Format](Images/TP1Format.png)

*Il est à noter que la section concernant le « boutisme » n'est pas à négliger pour les valeurs de certaines structures.*

## Barème

|Évaluation|Pondération|
|:---------|:---------:|
|Gestion des arguments et paramètres|/ 2|
|Gestion du fichier|/ 2|
|Utilisation de « printf »|/ 1|
|Affichage des données|/ 5|
|Affichage des chaînes de caractères|/ 3|
|Affichage d'informations du format|/ 2|
| |**/ 15**|
