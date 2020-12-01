# Labo 9 - Strings 

- **Durée**: 5 périodes + travail à la maison

## Objectifs
Les buts de ce laboratoire sont :
- Apprendre à choisir la structure de contrôle adaptée.
- Travailler avec des chaînes de caractère.
- Choisir les tests à faire pour valider que le programme fonctionne.

## Cahier des charges

On vous demande de concevoir puis d’écrire un programme qui permet :
- Transformer une phrase en minuscule.
- Compter le nombre de mots dans une phrase.
- Trouver la première occurrence d'un caractère dans une phrase.
- Trier les lettres (voir ci-dessous Bubble).
- Attention au paragraphe `affichage`.
- Ces fonctions doivent être implémentées par vous. L'utilisation de bibliothèque est interdite sauf pour `isspace` et `ispunc`
- Compléter le fichier de test automatique pour garantir que le programme fonctionne. **Vous devez tester tout les cas critiques**
- Respecter les règles sur le code.
- Séparer votre code en fonctions.

## Descriptif

### Lower

Cette fonction convertit une chaîne de caractère dans sa version minuscule

La ponctuation est autorisée ainsi que les espaces pour cette fonction

Uniquement les caractères `[a-z] [A-Z] et [0-9] et ponctuation` sont autorisés dans cette fonction.

Si des caractères spéciaux sont dans la chaîne, il faut retourner une erreur.

*Penser à la fonction `ispunct`*

### Find

Cherche si le caractère passé en paramètre est présent dans la chaîne.

Retourne la position de la première occurrence du caractère trouvé sinon -1.

La fonction est sensible à la casse.

Uniquement les caractères `[a-z] [A-Z] et [0-9] et ponctuation` sont autorisés comme caractère de recherche dans cette fonction.

La chaîne peut contenir n'importe quel caractère.

### Count

La fonction compte le nombre de mots dans un une phrase. 

Un mot est composé de tous les caractères qui ne sont pas une ponctuation `ispunct` ou un espace `isspace`.

Plusieurs espaces peuvent être à la suite.

N'importe quel caractère sont admis dans la chaîne.

Une phrase peut commencer ou se terminer par un espace. Cela ne change pas le nombre de mot.

### Bubble

Le tri à bulle est l'un des algorithmes de tri les plus basiques, mais pas des plus performants.

Chaque caractère est comparé au caractère suivant et si il est plus grand, il est échangé. Arrivé
à la fin de la chaîne, on recommence tant qu'au moins un caractère est échangé. Vous pouvez imaginer
que les caractères plus grands peu à peu remontent la chaîne de caractère comme des bulles dans le Champagne.

Uniquement les caractères `[a-z] [A-Z] [0-9] espace et ponctuations` sont autorisés dans cette fonction.

Utiliser la fonction `print_alphanum` pour n'afficher que les lettres et chiffre.

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

$ ./string find O "Bonjour Tout le MONDE"
18

$ ./string find , "Bonjour, tout le MONDE"
7

$ ./string bubble "Portez ce vieux whisky au juge blond qui fume"
Pabcdeeeeefghiiijklmnooqrstuuuuuvwxyz
```

## Qualité du code

La qualité du code est évaluée. Pour mémoire :

- Un **en-tête** en début de programme décrit le fonctionnement du programme.
- Les variables sont nommées de façon **appropriées**.
- La **visibilité** (*scope*) des variables est minimum.
- Les **constantes littérales** sont nommées pour une meilleure compréhension.
- Les **types** de données doivent être appropriés au contenu ciblé.
- Le programme doit être **robuste**, les cas d'exception doivent être traités.
- Le nom des fonctions doit être explicite et non trop générique
- Les fonctions **doivent** avoir un commentaire explicatif.

## Affichage

Lorsqu'il y a une erreur, aucun message n'est affiché sur `stdin`. Cela veut dire que l'on ne fait pas
de `printf`.

Pour savoir si il y a eu une erreur, on utilise le code de retour.

Il n'y a pas non plus de message lors du fonctionnement normal, comme vous pouvez le voir dans la simulation d'exécution.

## Code d'erreur

Le programme retourne les statuts de sortie suivants :

- `0` Le programme s'est terminé correctement.
- `1` Des caractères interdit sont trouvés dans le text à traîter.
- `2` Nombre d'argument.
- `3` Nom de commande inexistant.
- `4` Argument non valide.
- `5` Chaîne vide.


## Tests

Compléter le fichier de test automatique pour valider que votre programme fonctionne.

Attention la liste des tests est importantes dans ce laboratoire, une partie des points 
sera attribués en fonction du fichier de test automatique.

Ici vous avez un exemple de test

```json
{
      "name": "Test count",
      "args": ["count", "foo bar"],
      "stdout": [
        {
          "regex": "2\\b"
        }
      ],
      "exit": 2
    },
```

name :
  Le nom du test affiché dans le terminal

args :
  La ligne de commande entrée dans le programme

stdout :
  `"regex": "<val>\\b"` <val> la valeur qui doit être présent pour que le test fonctionne.

*Il est possible de tester des regex sur : `https://regex101.com/`*

exit :
  La valeur du return

Comme vous pouvez le voir dans le fichier de config, il est possible d'organiser les tests par famille avec des sous-tests.

## Bonus

Modifier la fonction `find` pour y ajouter une option pour choisir si la fonction 
est sensible à la casse ou non.

En utilisant l'option `-i` la commande ne doit plus être sensible à la casse.

```console
$ ./string find -i O "Bonjour, tout le MONDE"
1

$ ./string find -i o "Bonjour, tout le MONDE"
1

$ ./string find O "Bonjour, tout le MONDE"
18
```

## Aide

### Debug

Voici un exemple de comment lancer le programme en débug pour tester la fonction `lower`

La configuration est dans le fichier `launch.json`

```json
"args": ["lower", "AA bb, CC !"],
```

### Count

Penser sur papier comme vous faite pour compter les mots.

Je pense qu'il vous faut une machine d'état pour détecter le
début d'un mot.

### Outil commentaire

Un outil pour commenter les fonctions a été ajouté à la machine de développement que vous utilisez.

Si vous voulez ajouter automatiquement les commentaires de fonction, essayer ceci:

1. Ecrire le code de votre fonction. Ex : `int test(double value){}`
1. Juste avant la fonction entrer : `/**` 
1. Appuyer sur `enter`

L'outil va automatiquement ajouter la base de commentaire pour la fonction

### Fonctions

Voici des exemples de fonctions que vous pourriez développer et qui pourrait vous aider dans votre code.

- swap_char
- is_number
- char_to_lower
- is_valid
- is_word_separation
- ...

### Les define

En dehors de toute fonction. Comme par exemple avant le `main`, vous pouvez
ecrire
```c
#define NBR_ARG_MAX 3
```

Ensuite dans le code, partout où vous allez écrie `NBR_ARG_MAX`, le compilateur
va remplacer le text par la valeur écrite dans le `#define`.

Si vous laisser la souris sur `EXIT_SUCCESS` vous verrez que cette variable est
définie avec un `#define`.

Vous pouvez utiliser ceci par exemple pour les codes de retour
```c
#define EXIT_NBR_ARG 2
#define EXIT_TO_MANY_ARG 3

void main(void){
    if( argc < 0 ) return EXIT_NBR_ARG;
    
    return EXIT_SUCCESS;
}
```

## Liste des livrables

Mettre les fichiers suivant dans une archive **`zip`** (**pénalité pour les archives `rar`**) et la placer sur Cyberlearn
-  Code source
-  Le fichier exécutable
-  Le rapport de test

L’archive doit être déposée dans le répertoire "Labo09" de Cyberlearn (à la date
demandée sur le site INFO1 de Cyberlearn).

