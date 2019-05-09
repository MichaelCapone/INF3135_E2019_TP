# Travail pratique 1

  L'objectif est de vous initier à la programmation avec le langage C, en  manipulant
  des données, des fichiers, ainsi que la gestion des arguments provenant de la ligne de commande.

  De plus, vos sources seront maintenues dans un gestionnaire de version/source de type git.
  
  Vous allez aussi vous familiariser avec la commande `make` et le fichier `Makefile` afin `d'automatiser` plusieurs tâches utiles.

# Description du travail

  Le programme doit encoder et décoder `(encrypt, decrypt)` des messages en utilisant une clé simple et un alphabet.
  
  + Une clé simple est un nombre positif ou négatif;
  + Un message (deux types) est soit : en clair (~phrase en français) ou déjà encoder (crypté);
  + Un alphabet est une chaîne de caractères;
  
  Le programme `tp1` doit (et sera) être lancé en `ligne de commande` avec toutes les combinaisons d'options possibles.
  
### Détails sur les options et arguments

*  -c `<CODE permanent>`
*  -i `<fichier source en entrée contenant le message>`
*  -o `<fichier traité en sortie après l'exécution voulue>`
*  -d | -e                               `quel est le traitement voulu : décodage ou encodage du message`
*  -k `<clé simple>`

  Le `CODE permanent` provient du fichier `cp.txt`.  Une variable nommée `CP` dans le `Makefile` doit être créée 
  pour récupérer le contenu du fichier `cp.txt`. Il est aussi possible de faire appel à un fichier `bash`
  pour l'exécution de vos tests.
  
  L'alphabet provient du fichier alphabet.txt. Le fichier sera inclus dans le fichier data.zip disponible sur le dépôt `GitHub`.

### Quelques exemples de ligne de commande valides (mais pas tous)

+ `$ ./tp1 -d -k 2 -c CODE_permanent -i nom_du_fichier_en_entree.ext > fichier_sortie.ext`
+ `$ ./tp1 -k 1 -e -c CODE_permanent`
+ `$ ./tp1 -c CODE_permanent -d -k 3 -o fichier.out`
+ `$ ./tp1 -c CODE_permanent -i nom_du_fichier_en_entree.ext -o fichier_sortie.ext -k 7 -e`
+ `$ ./tp1 -c CODE_permanent -d -k 9 < nom_du_fichier_en_entree.ext > fichier_sortie.ext`

### Vous devez réaliser le travail selon les contraintes suivantes:




## Exemples

### Un message en clair

`msg1.txt`
~~~~
Ceci est un message lisible en francais sans les accents ou caracteres complexe.
~~~~

### Un message encodé

`msg2.txt`
~~~~
Tvtz vjk le dvjjrxv czjzscv ve wiretrzj jrej cvj rttvekj fl trirtkvivj tfdgcvov.
~~~~

### La clé

~~~~
17
~~~~

### L'alphabet

`alphabet.txt`
~~~~
ABCDEFGHIJKLMNOPQRSTUVWXYZ
~~~~

# Les tests

  Les tests sont de votre responsabilité.
  
  Ce qui est fourni dans l'énoncé est à titre d'exemple. Ceci vous aide pour débuter la réflexion. 
  Votre rôle est de compléter celle-ci (la réflexion) ainsi que tout ce que vous jugez neécessaire pour obtenir un logiciel
  qui soit conforme. Il est fort possible que les tests soient plus nombreux et complets lors de la correction.

# Makefile

  Il est obligatoire d'inclure un fichier `Makefile` dans votre projet pour faciliter la compilation et la récupération 
  des données. Celui-ci doit minimalement offrir les services suivants :

- Lorsqu'on entre simplement `make`, l'exécutable `tp1` doit être produit (ou mis à jour), 
  avec les arguments suivants (obligatoire) : `-Wall -pedantic -std=c11`;

- Lorsqu'on entre `make clean`, les fichiers `.o`, `code.txt` et l'exécutable doivent être supprimés (uniquement les fichiers provenant du dépôt devraient rester);

- Lorsqu'on entre `make data`, le téléchargement des données (fichier) https://www.github.com/guyfrancoeur/INF3135_E2019_TP/raw/master/tp1/data.zip se fait
  de façon automatique. La décompression du fichier est est dirigée dans répertoire `./data`;

- Lorsqu'on entre `make test` le programme `tp1` s'exécutera séquentiellement avec les fichiers contenus dans `./data`.
  
- Lorsqu'on entre `make resultat` le fichier `note-du-tp.txt` situé à la racine du dépôt local sera poussé dans votre dépôt distant.

# Complément pour la compilation

+ `-std=c99` indique au compilateur de traiter le code selon le standard C99 (et donc de rejeter certaines extensions comme celles de GNU par exemple);
+ `-std=c11` indique au compilateur de traiter le code selon le standard C11 (2011); 
+ `-pedantic` permet de signaler les avertissements, ou warnings, selon la norme ISO;
+ `-Wall` permet de signaler un grand nombre d’autres warnings décrit dans le man gcc.

En effet, la grande permissivité de C réduit l’aide (la verbosité) du compilateur (sans option)
pour traquer certaines erreurs et les mauvaises pratiques de programmation.

# README.md

  En plus du code source nommé `tp1.c` et du fichier nommé `Makefile`, votre projet doit contenir
  un fichier nommé `README.md` qui décrit le contenu et qui **respecte le format Markdown**.
  Il doit minimalement contenir les informations ci-bas :

~~~~
   # Travail pratique 1

   ## Description

   <description du projet en quelques phrases>
   <mentionner le contexte (cours, sigle, université, etc.)>

   ## Auteur

   <prénom et nom> (<code permanent>)

   ## Fonctionnement

   <expliquez brièvement comment faire fonctionner votre projet, en inscrivant
   au moins deux exemples d'utilisation (commande lancée et résultat affiché)>

   ## Contenu du projet

   <décrivez brièvement chacun des fichiers contenus dans le projet (une phrase
   par fichier)>

   ## Références

   <citez vos sources ici>

   ## Statut

   <indiquez si le projet est complété ou s'il y a des bogues>
~~~~

# Contrainte

- Les `#include` standard au langage C sont tous permis. Tel que `#include <stdio.h>`;
- Vous ne pouvez pas utiliser des librairies (entêtes et implémentations binaire) `#include "autre.h"` d'un tiers;
- Le travail pratique 1 est à faire individuellement. Donc chacun doit initialiser son propre dépôt (git) distant privé;

# Remise

  La totalité de votre travail doit être remis au plus tard le **18 juin 2019** à **00h01**. 
  À partir de minuit, une pénalité de **5 points par jour** de retard sera appliquée.

  La remise se fait **obligatoirement** par l'intermédiaire de l'une des plateformes de gestion de version suivantes :
  + `GitHub https://github.com/`___;
  + `GitLab https://gitlab.com/`___.
  
  **Aucune remise par courriel ne sera acceptée** (le travail sera considéré comme non remis).

  Le nom de votre projet doit être `inf3135-e2019-tp1` (en minuscules). Vous devez donner un accès 
  en mode **lecture/écriture** (pas **admin**) à l'utilisateur `guyfrancoeur` (moi-même). Ceci me 
  permettra de déposer directement dans vos projets votre note pour le travail ainsi que mes commentaires si nécessaire.
  
  La branche `master` sera celle `clonée` et sera celle qui sera évaluée.

  Votre projet devrait minimalement contenir les fichiers suivants :

- Un fichier `cp.txt` contenant votre code permanent en majuscule et complet (requis pour la publication des résultats);
- Un fichier `tp1.c` contenant le code source de votre projet, ainsi que votre fonction `main`;
- Un fichier `README.md` avec le titre du projet, les auteurs, les exemples, etc;
- Un fichier nommé `Makefile` supportant les appels `make`, `make clean`, `make data`, `make test` et `make resultat`;
- Un fichier ``.gitignore``. Ça aide beaucoup;
- Aucune structure de répertoire nécessaire.

# Correction et évaluation

Les travaux seront corrigés sur le serveur Java. Vous devez donc vous assurer que votre programme
fonctionne **sans modification** sur celui-ci.
  
Votre travail sera évalué de façon automatisée.  Ce qui implique que vos dépôts seront clonés
et un pull sera effectué de façon automatique. Un `pull` par jour pendant 5 jours.
Il n'y aura pas d'humain pour faire fonctionner le programme. 
Votre travail sera soumis à plusieurs cas et les résultats seront évalués par un script `bash`.
Assurez-vous de bien lire toutes les directives et les requis.

> > Les fichiers seront soumis au détecteur de plagiat.

# Barème de correction (a faire)

| Critère | Sous-critère | Points |
| ------- |:------------ | ------:|
| Fonctionnabilité  | 5 à 10 tests seront lancés (comparaison binaire) | 6.0 |
| Compilation       | sans avertissement ni erreur                     | 1.0 |
| Git clone         | récupération (droit lecture, écriture)  | 1.0 |
| Qualité           | temps d'exécution (performance) et code | 2.0 |
| Directives        | création de code.txt                    | 0.5 |
| Makefile          | <ul><li>make</li><li>make clean</li><li>make data</li><li>make test</li><li>make resultat</li></ul> | <ul><li>1.0</li><li>0.5</li><li>1.0</li><li>0.5</li><li>0.5</li></ul> |
| Markdown          | README.md                               | 1.0 |
| **Total**         |                                         | 25 |
