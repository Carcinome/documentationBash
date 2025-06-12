**Commandes Bash**
====================

**1. Commandes de base**
------------------------

**1.1 ./**
^^^^^^^^^^^^^^^

**Syntaxe :**

.. code-block:: bash

    ./

Permet d'exécuter des scripts bash.

*Exemple :* 

.. code-block:: bash

    ./monscript.sh
    ~/Documents/Scripts/monscript.sh

.. note::

    - S'assurer d'être dans le bon dossier, sinon pointer en dur (*chemin absolu*) vers le dossier contenant le script. 
    - Penser à se donner les droits d'exécution sur le dossier contenant les scripts. (*chmod*)

.. warning::

    Ne pas oublier la commande 

    .. code-block::

        #!/bin/bash

    En début de script, sans quoi ce dernier ne se lancera pas. Ne pas confondre avec les commentaires marqués *#*.


**1.2 #** 
^^^^^^^^^

**Syntaxe :**

.. code-block:: bash

    # en début de ligne
   

Permet de commenter le code. **Capital** pour maintenir un code à jour, propre et simple d'utilisation notamment pour les autres utilisateurs.

*Exemple :* 

.. code-block:: bash

    # ceci est un commentaire
    

.. note::

    # Utilisé pour commenter sur une ligne.


**1.3 ll / ls**
^^^^^^^^^^^^^^^

**Syntaxe :**

.. code-block:: bash
    
    ll
    ls

Permet de faire le listing des fichiers et dossiers présents dans le dossier courant. 

*Exemple :* 

.. code-block:: bash

    ls
    #resultat
    Makefile  README.md  build  env_sphinx_v1  make.bat  requirements.txt  source

    ll
    #resultat
    -rw-r--r--. 1 aicardic aicardic  638 Jun 10 15:59 Makefile
    -rw-r--r--. 1 aicardic aicardic    0 Jun 10 16:02 README.md
    drwxr-xr-x. 4 aicardic aicardic 4096 Jun 10 16:12 build
    drwxr-xr-x. 5 aicardic aicardic 4096 Jun 10 15:57 env_sphinx_v1
    -rw-r--r--. 1 aicardic aicardic  804 Jun 10 15:59 make.bat
    -rw-r--r--. 1 aicardic aicardic  952 Jun 10 15:53 requirements.txt
    drwxr-xr-x. 4 aicardic aicardic 4096 Jun 10 16:11 source

.. note::

    - *ll*, plus précis que *ls*, permet d'afficher les droits d'accès, le propriétaire, la date de la dernière modification, etc. 
    - L'utilisation du pipe *|* est possible, associé à un *grep* pour filtrer les résultats attendus via mot-clé.
    
    .. code-block:: bash

        ls /usr/bin/ | grep "chains"

    - On peut utliser *>* pour rediriger le flux généré vers un fichier. 
    - Plusieurs paramètres sont combinables. 

    .. code-block:: bash

        ls /usr/bin/ > ~/Documents/test.txt
        ll /usr/bin/ | grep "chains" > ~/Documents/test2.txt


**1.4 cp / scp**
^^^^^^^^^^^^^^^^

**Syntaxe :**

.. code-block:: bash
    
    cp <option> <fichier_à_copier> <dossier_destination>
    scp <option> <dossier_source> <dossier_destination>

    
Permet de copier des fichiers d'un endroit à un autre. *scp* permet de copier les fichiers en réseau de manière sécurisé. 

*Exemple :* 

.. code-block:: bash

    cp text.txt ~/Documents/dossierDestination
    scp aicardic@z420:/chemin/vers/repertoire/fichier.txt "~/Documents/"
    scp aicardic@z420:/chemin/vers/repertoire/fichier.txt .

.. note::

    - Concernant *scp* :
        - on peut remplacer le chemin absolu local **actuel** par un *point (.)*. 
        - La syntaxe pour la copie de ou vers un dossier distant prend le nom utisateur de l'hôte @ le nom de l'hôte (*aicardic@z420*).
        - La modification du nom du fichier copié est possible, il suffit de changer le nom à la fin du chemin de destination.
        
    - La copie de plusieurs fichiers d'un seul coup est possible, comme ceci : 

        .. code-block:: bash

            cp text1.txt text2.txt ~/Documents/dossierDestination
            scp text1.txt text2.txt aicardic@z420:/chemin/vers/repertoire

    - L'option *-r* permet de copier le repertoire indiqué de manière récursive.
    - L'option *-C* permet de compresser les fichiers transférés pour alléger leur poids.


**1.5 print**
^^^^^^^^^^^^^

**Syntaxe :**

.. code-block:: bash
    
    print("texte à afficher")
    print(f"texte à afficher contenant des {variables}.")
    
Equivalent d'`echo` ou de `printf`, permet d'afficher du texte, des charactères, variables et autre.

*Exemple :* 

.. code-block:: bash

    print("Hello world!")
    # On définit une variable en amont, age = 32.
    print(age)
    print("Je m'appelle Clément et j'ai", {age} "ans.") # Désuet, privilégier le f-string comme ci-dessous.
    print(f"Je m'appelle Clément et j'ai {age}.")

.. note::

    - Les variables sont appelées sans `""`.
    - Les chaîne de caractères (string) sont appelées avec `""`.
    - Pour l'inclusion des variables dans une string, on privilégiera le `f-string`.
    - Les accolades `{}` sont obligatoires lorsque des variables sont appelées avec des strings.

    
