Un débordement de tampon (buffer overflow) consiste à écrire plus de données que l'espace réservé en mémoire pour les contenir.

# Langage C

Les langages de programmation de bas niveau ont comme objectif d'être performant en étant le plus près que possible du matériel. Par conséquent, il y a très peu de validation et on tient pour acquis que les programmeurs savent ce qu'ils font... ce qui n'est, malheureusement, pas toujours le cas.

## Morris

En 1988, le premier maliciel autorépliquant voit le jour sous le nom de « Morris ».

*[Image]*

Pour s'autorépliquer, le ver Morris utilisait, entre autre, une faille de type débordement de tampon. Celle-ci se trouvait dans l'outil réseau, bien connu du monde Unix, « finger », programmé en langage C. Ce service permettait de connaître les utilisateurs connectés au poste de travail, mais aussi de demander de l'information à propos d'un utilisateur en particulier.

Pour traiter la requête, la fonction « gets » était utilisée pour stocker le nom de l'utilisateur dans un tampon de 512 octets. Normalement, aucun nom d'utilisateur respectable ne contient 512 caractères, donc la taille du tampon peut sembler suffisante, voir même exagérer. Malgré tout, ce tampon reste vulnérable puisque la fonction « gets » ne prend aucun paramètre de validation concernant sa taille, ce que Robert Tappan Morris a su exploiter.

![Robert Tappan Morris](Images/RobertTappanMorris.png)

Les développeurs du langage C ont réalisés le problème, et dans la révision des spécifications 1999 la fonction « gets » a été dépréciée, tandis que dans la mise à jour 2011 elle a été entièrement retirée. Mais ce genre de faille expose bien les risques d'utiliser des langages de bas niveau sans bien en connaître les fonctionnements internes.

# Preuve de concept

Démonstration d'une faille logicielle par un programme qui la met en évidence.

Le programme suivant attend la saisie d'une chaîne de caractères, puis la compare à une autre chaîne de caractères, et finalement affiche un succès si elles sont identiques, sinon un échec:

*[Image]*

Le lieur nous donne déjà un bon indice... si on prend soin de lire les avertissements:

*[Image]*

Quelques tests sommaires permettent de rapidement constater la faille:

*[Image]*

Si les deux premières tentatives semblent bien fonctionner, la troisième expose la problématique.

# Exploitation

Lorsqu'un programme est exécuté, il est préalablement chargé en mémoire centrale selon plusieurs sections, dont certaines que pour les données.

À l'aide de points d'arrêt aux lignes 9 et 12, il est possible de consulter l'état des variables avant et après la saisie:

*[Image]*

Il y a une différence de 31 octets (3F - 20) entre le début du tampon et la variable booléenne. Donc si 32 caractères sont saisis, le dernier viendra altérer le contenu de la variable booléenne.

Il est donc pratiquement possible d'altérer toutes les données d'un programme qui sont déclarées après un tampon utilisé par la fonction « gets ».

# Prévention

Prévention
Les compilateurs de langages de programmation offrent maintenant certaines options de préventions en matière de sécurité logicielle.

La première prévention consiste à utiliser des fonctions considérées sécuritaires par le compilateur. Dans le contexte actuel, la fonction « gets_s » aurait dû être utilisée plutôt que la fonction « gets ».

La grande majorité des fonctions utilisant un tampon ont été révisées et de nouvelles fonctions, dont leurs identifiants se terminent par « _s » (pour « safe »), ont été créées. Comme exemples: « printf » devient « printf_s », « scanf » devient « scanf_s », etc.

Une autre prévention consiste à utiliser certaines options lors de la compilation. Par exemple, inspectons la différence en utilisant l'option de compilation « stack-protector »:

*[Image]*

On peut constater qu'avec l'option de prévention, le compilateur a déplacé la déclaration de la variable « isValid » en mémoire centrale. Le tampon se trouvant maintenant à la suite de la variable « isValid », il ne pourra l'affecter, même en débordant.
