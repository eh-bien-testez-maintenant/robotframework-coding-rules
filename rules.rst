Règles d'écriture des tests avec Robot Framework
================================================

Définition
----------

Définition D1: Keyword

Règles sur le fond
------------------

Régle A1 : Un cas de test == une Test Suite de type fichier
   Un cas de test doit correspondre à une Test Suite de type fichier au niveau de Robot Framework (fichier .txt ou .robot).
   C'est le niveau de granularité le plus fin d'un test.

Règle A2 : Limiter le périmètre fonctionnel
   Un cas de test doit se limiter à la vérification d'un nombre minimum de fonctionnalité.
   
.. note::
   Si un test vérifie plusieurs fonctionnalités, il devra être réécrit à chaque modification d'une des fonctionnalités, augmentant ainsi le coût de maintenance.
   De plus, un test qui vérifie trop de choses risque d'être moins lisible. 

Règle A3 : Structure d'un test 
   Un test doit avoir la forme suivante ::
   
      - Setup (Keyword)
         - Test (Test Case)
      - Teardown (Keyword)

.. note::
   Ceci permet de découper un cas de test en plusieurs parties, chaque partie ayant ou non son setup et son teardown.
   Cependant, cette forme d'écriture est à éviter dans la plupart des cas si on souhaite respecter la règle A1 mais peut s'avérer utile
   dans certains cas.
 
Règle A4 : Contenu d'un test
   * Le Setup doit contenir toute l'éxécution d'un cas de test, c'est-à-dire toutes les actions à effectuer pour passer le test.
   * Le Test doit contenir les assertions permettant de vérifier si le résultat est valide ou non.
   * Le Teardown doit remettre le système sous test et les autres éléments dans leur configuration d'origine.      
 
 Corollaire A4 : Contenu d'un test
   * Le Setup et le Teardown va contenir des keywords de type "Action"
   * Le Test va contenir les keywords de type "Assertion"
 
 Règle A5 : Limitation du nombre de keyword imbriqué
   Le niveau d'imbrication des keywords doit être au maximum de 5.
 
Règles sur la forme
-------------------

Règle 1:
   Formattage

Règle 2:
   Règle de nommage


Ecriture de lib de tests
------------------------

Règle 1: 
   La librairie ne doit contenir aucune violation Pylint

   Il existe un fichier de configuration pour Pylint dans le projet qui permet d'uniformiser les résultats.

Règle 2 
   Les fonctions de type "action" présentent dans les librairies doivent lever une exception qui fait directement stopper le test.

Règle 3 
   Les fonctions de type "assertion" présentent dans les librairies doivent lever une exception qui ne fait par stopper le test.

   L'assertion utilisée dans ce cas est du type ``NonStoppingAssertionError``
