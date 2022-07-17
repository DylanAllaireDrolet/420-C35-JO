Les technologies de l’information consistent à stocker, traiter, et générer des données. On estime qu’en 2025, leur nombre atteindra 175 zettaoctets. Et à notre époque, certaines valent leur pesant d’or.

Pour être stockées, traitées, et générées par des machines, les données sont numérisées. C’est-à-dire que peu importe le type de leur valeur, elles seront toutes transformées en valeur numérique.

Mais ces valeurs numériques peuvent aussi s’exprimer de plusieurs façons, ce que l’on nomme des systèmes de numération.

# Système de numération

Certains systèmes de numération sont particulier, tel le système romain. Dans un contexte informatique, ayant comme principaux besoins de représenter et traiter de l’information par une machine, un système de numération plus adapté aux mathématiques et à l’électronique est nécessaire.

## Décimal

Le fait que nous ayons 10 doigts n'est probablement pas étranger au système décimal, système de numération additif à base 10. On nomme « chiffre » les 10 symboles de cette numération, généralement représentés par:

![Décimal](Images/Decimal.png)

Le nombre décimal 123456 peut être décomposé de façon suivante:

![Décomposition](Images/DecimalDecomposition.png)

Et puisqu'il s'agit d'un nombre à base 10, il peut être représenté de façon suivante:

![Base 10](Images/DecimalBase.png)

## Binaire

La base de la logique informatique repose sur le système binaire, un système de numération à base 2. On nomme « bit » les 2 symboles de cette numération, généralement représentés par:

![Binaire](Images/Binary.png)

Et on nomme « octet » un groupe de 8 bits, qui consistent en l’unité de base en informatique:

![Octet](Images/Byte.png)

L’utilisation de ce système, plutôt que le système décimal, s’explique par la facilité de représenter des données et effectuer des opérations avec l’électricité; puisque soit le courant passe (1), soit il ne passe pas (0).

### Conversions

Malgré ça base minimaliste, le fonctionnement du système binaire est équivalent à celui du système décimal:

![Décomposition](Images/BinaryDecomposition.png)

La même logique peut donc être utilisée avec la base 2:

![Décomposition](Images/BinaryBase.png)

#### Décimal à Binaire

Plutôt que de multiplier par la base, c'est la division entière qui est utilisée pour effectuer la conversion. Le reste à cette division est ajouté au résultat, de droite à gauche, jusqu'à ce que le nombre entier décimal soit 0:

![Conversion](Images/DecToBin.png)

### Signe

Les valeurs entières étant représentées par le système binaire en mémoire centrale, celles-ci ne peuvent qu'être positives puisqu’il n’y a pas de signe dans ce système, que des 0 et des 1.

Le bit le plus fort est donc utilisé afin d'indiquer si la valeur est positive (0) ou négative (1). Mais cette façon de faire comporte des problématiques: il y a deux 0 (un positif et un négatif) et les résultats d'opérations arithmétiques ne sont plus valides lorsque des valeurs négatives sont impliquées:

*[Image]*

#### Complément à deux

Pour pallier ces problèmes, le complément à deux est utilisé pour effectuer la négation, c'est-à-dire que tous les bits sont inversés, puis 1 est ajouté. Donc, pour représenter la valeur négative -2, nous devons appliquer le complément à deux sur la valeur 2:

*[Image]*

Donc chaque fois que le bit le plus fort est 1, c'est que la valeur est encodée avec le complément à deux:

*[Image]*

## Hexadécimal

Ce système de numération est régulièrement utilisé en informatique afin de représenter de grandes valeurs de façon plus concise.

...
