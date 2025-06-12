**Commandes Bash**
====================

**1. Commandes de base**
------------------------


**1.1 ./**
^^^^^^^^^^

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
    - Penser à se donner les droits d'exécution sur le dossier contenant les scripts. (`chmod`)

.. warning::

    Ne pas oublier la commande 

    .. code-block::

        #!/bin/bash

    En début de script, sans quoi ce dernier ne se lancera pas. Ne pas confondre avec les commentaires marqués `#`.


**1.2 #** 
^^^^^^^^^

**Syntaxe :**

.. code-block:: bash

    # en début de ligne
   

Permet de commenter le code. **Capital** pour maintenir un code à jour, propre et simple d'utilisation notamment pour les autres utilisateurs.

*Exemple :* 

.. code-block:: bash

    # ceci est un commentaire
    

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

    - `ll`, plus précis que `ls`, permet d'afficher les droits d'accès, le propriétaire, la date de la dernière modification, etc. 
    - L'utilisation du pipe `|` est possible, associé à un `grep` pour filtrer les résultats attendus via mot-clé.
    
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
    
    cp <option> <fichier_a_copier> <dossier_destination>
    scp <option> <dossier_source> <dossier_destination>

    
Permet de copier des fichiers d'un endroit à un autre.  `scp` permet de copier les fichiers en réseau de manière sécurisé. 

*Exemple :* 

.. code-block:: bash

    cp test.txt ~/Documents/dossierDestination
    scp aicardic@z420:/chemin/vers/repertoire/fichier.txt "~/Documents/"
    scp aicardic@z420:/chemin/vers/repertoire/fichier.txt .

.. note::

    - Concernant `scp` :
        - on peut remplacer le chemin absolu local **actuel** par un point "`.`". 
        - La syntaxe pour la copie de ou vers un dossier distant prend le nom utisateur de l'hôte @ le nom de l'hôte (*aicardic@z420*).
        - La modification du nom du fichier copié est possible, il suffit de changer le nom à la fin du chemin de destination.
        
    - La copie de plusieurs fichiers d'un seul coup est possible, comme ceci : 

        .. code-block:: bash

            cp test1.txt test2.txt ~/Documents/dossierDestination
            scp test1.txt test2.txt aicardic@z420:/chemin/vers/repertoire

    - L'option `-r` permet de copier le repertoire indiqué de manière récursive.
    - L'option `-C` permet de compresser les fichiers transférés pour alléger leur poids.


**1.5 mv**
^^^^^^^^^^

**Syntaxe :**

.. code-block:: bash

    # Dans le répertoire courant    
    mv <fichier_a_deplacer> <dossier_destination>

    # Hors du répertoire courant
    mv <dossier_source> <dossier_destination>
    
Permet de couper/coller des fichiers, peut aussi être utilisé pour renommer des fichiers.

*Exemple :* 

.. code-block:: bash

    # Dans le répertoire courant
    mv test.txt ~/dossierDestination/copie_test.txt

    # Hors du répertoire courant
    mv ~/DossierSource/test.txt ~/DossierDestination/

.. warning::

    - Le fait de renommer un fichier n'est possible que si le fichier en question se trouve dans le repertoire courant. 
    - **Dans Linux, un dossier est un fichier.** >> https://fr.linkedin.com/learning/linux-les-disques-et-le-stockage/comprendre-le-concept-du-tout-est-fichier


**1.6 rm**
^^^^^^^^^^

**Syntaxe :**

.. code-block:: bash

    # Dans le répertoire courant    
    rm <option> <fichier_a_supprimer>

    # Hors du répertoire courant
    rm <option> <dossier_source>
    
Permet de supprimer fichiers et dossiers. 

*Exemple :* 

.. code-block:: bash

    # Dans le répertoire courant
    rm -f test.txt

    # Hors du répertoire courant
    rm -rf ~/dossierSource/dossier_a_supprimer 

.. note:: 

    - L’option `-r` permet la récursivité de la commande, supprimant ainsi dossier et sous-dossier.
    - L’option `-f` permet de forcer la suppression sans requête utilisateur.
    - L’option `-i` permet de demander une confirmation supplémentaire à chaque suppression.
    - L’option `-v` permet d’indiquer l’action en cours de réalisation.

.. warning::

    **Commande puissante, éviter le plus possible l'option `-rf` à moins d'être sûr de soi.** (Bien que faire `rm -rf /*` sur le pc des copains à l'école était assez drôle).


**1.5 man / help**
^^^^^^^^^^^^^^^^^^

**Syntaxe :**

.. code-block:: bash

    man
    help

Permet de consulter l'aide d'une commande.

*Exemple :* 

.. code-block:: bash

    man lsblk
    help mapfile

.. note::

    - La commande `man` est utilisée pour obtenir de l'aide sur des programmes ou commandes externes au shell bash.
    - La commande `help` est utilisée pour obtenir de l'aider sur les commandes et fonctions internes au shell bash.
    
