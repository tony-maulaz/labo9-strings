# Labo 9 - Strings 

- **Durée**: 4 périodes + travail à la maison

## Objectifs
Les buts de ce laboratoire sont :
- Apprendre à choisir la structure de contrôle adaptée.
- Travailler avec des chaînes de caractère.
- Tester le programme d'une autre personne.

## Cahier des charges

On vous demande de concevoir puis d’écrire un programme qui permet :
- Transformer une phrase en majuscules.
- Transformer une phrase en minuscule.
- Compter le nombre de mots dans une phrase.
- Trouver la première occurrence d'un caractère dans une phrase.
- Trier les lettres (voir ci-dessous Bubble).
- Attention au paragraphe affichage.

## Descriptif

### Lower

Cette fonction convertit une chaîne de caractère dans sa version minuscule

La ponctuation est autorisée pour cette fonction

Uniquement les caractères `[a-z] [A-Z] et [0-9] et ponctuation` sont autorisés dans cette fonction

*Penser à la fonction `ispunct`*

### Find

Cherche si le caractère passé en paramètre est présent dans la chaîne.

Retourne la position de la première occurrence du caractère trouvé sinon -1.

Uniquement les caractères `[a-z] [A-Z] et [0-9] et ponctuation` sont autorisés dans cette fonction

### Count

La fonction compte le nombre de mots dans un une phrase. 

Un mot est composé de tous les caractères qui ne sont pas une ponctuation `ispunct` ou un espace `isspace`.

Plusieurs espaces peuvent être à la suite.

Une phrase peut commencer ou se terminer par un espace. Cela ne change pas le nombre de mot.

### Bubble

Le tri à bulle est l'un des algorithmes de tri les plus basiques, mais pas des plus performants.

Chaque caractère est comparé au caractère suivant et si il est plus grand, il est échangé. Arrivé
à la fin de la chaîne, on recommence tant qu'au moins un caractère est échangé. Vous pouvez imaginer
que les caractères plus grands peu à peu remontent la chaîne de caractère comme des bulles dans le Champagne.

Uniquement les caractères `[a-z] [A-Z] et [0-9]` sont autorisés dans cette fonction

### Commandes

Les commandes acceptées seront
- ./string lower <text>
- ./string count <text>
- ./string find <char> <text>
- ./string bubble <text>

### Simulation de fonctionnement

```console
$ ./string lower "Bonjour Tout le MONDE"
bonjour tout le monde

$ ./string count "Bonjour, Tout le   MONDE !"
4

$ ./string find a "Bonjour Tout le MONDE"
-1

$ ./string find o "Bonjour Tout le MONDE"
1

$ ./string find , "Bonjour, tout le MONDE"
7

$ ./string bubble "Portez ce vieux whisky au juge blond qui fume"
Pabcdeeeeefghiiijklmnooqrstuuuuuvwxyz
```

## Qualité du code

De plus en plus, la qualité du code est évaluée. Pour mémoire :

- Un **en-tête** en début de programme décrit le fonctionnement du programme.
- Les variables sont nommées de façon **appropriées**.
- La **visibilité** (*scope*) des variables est minimum.
- Les **constantes littérales** sont nommées pour une meilleure compréhension.
- Les **types** de données doivent être appropriés au contenu ciblé.
- Le programme doit être **robuste**, les cas d'exception doivent être traités.
- Le nom des fonctions doit être explicite et non trop générique

## Affichage

Lorsqu'il y a une erreur, aucun message n'est affiché sur `stdin`. Cela veut dire que l'on ne fait pas
de `printf`.

Pour savoir si il y a eu une erreur, on utilise le code de retour.

Il n'y a pas non plus de message lors du fonctionnement normal, comme vous pouvez le voir dans la simulation d'exécution.

## Code d'erreur

Le programme retourne les statuts de sortie suivants :

- `0` Le programme s'est terminé correctement.
- `1` Pas de chaîne de caractère.
- `2` Des caractères interdit sont trouvés dans le text à traîter.
- `3` Trop d'arguments.
- `4` Nom de commande inexistant.
- `5` Argument non valide.
- ... Vous avez le droit d'ajouter des codes d'erreur si cela vous semble pertinent.

## Liste des livrables

Mettre les fichiers suivant dans une archive **`zip`** (**pénalité pour les archives `rar`**) et la placer sur Cyberlearn
-  Code source
-  Le fichier exécutable
-  Le rapport de test

L’archive doit être déposée dans le répertoire "Labo09" de Cyberlearn (à la date
demandée sur le site INFO1 de Cyberlearn).

