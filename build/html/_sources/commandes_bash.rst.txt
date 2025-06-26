**1. Commandes Bash**
=====================

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

    - *Options connues :*
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

.. note:: *options connues :*

    - L’option `-r` permet la récursivité de la commande, supprimant ainsi dossier et sous-dossier.
    - L’option `-f` permet de forcer la suppression sans requête utilisateur.
    - L’option `-i` permet de demander une confirmation supplémentaire à chaque suppression.
    - L’option `-v` permet d’indiquer l’action en cours de réalisation.

.. warning::

    **Commande puissante, éviter le plus possible l'option `-rf` à moins d'être sûr de soi.** (Bien que faire `rm -rf /*` sur le pc des copains à l'école était assez drôle).


**1.7 man / help**
^^^^^^^^^^^^^^^^^^

**Syntaxe :**

.. code-block:: bash

    man <commande>
    help <commande>

Permet de consulter l'aide d'une commande.

*Exemple :* 

.. code-block:: bash

    man lsblk
    help mapfile

.. note::

    - La commande `man` est utilisée pour obtenir de l'aide sur des programmes ou commandes externes au shell bash.
    - La commande `help` est utilisée pour obtenir de l'aider sur les commandes et fonctions internes au shell bash.
    

**1.8 sudo su - / su -**
^^^^^^^^^^^^^^^^^^^^^^^^

**Syntaxe :**

.. code-block:: bash

    sudo su -
    sudo <commande>
    su -

Permet l'élévation des privilèges ou la connexion en *root*.

*Exemple :* 

.. code-block:: bash

    sudo dnf install python3
    su - 
    # Remplir la demande de login utilisateur root. 

.. note::

    Il se peut que le compte root soit désactivé pour des raisons de durcissement,dans ce cas là seul l'élévation de privilège via `sudo` ou `sudo su -` fonctionnera.


**1.9 vi / vim**
^^^^^^^^^^^^^^^^

**Syntaxe :**

.. code-block:: bash

    vi <fichier>
    vim <fichier>

Permet d'éditer des fichiers textuels. `vim` est une version améliorée de `vi`, les deux fonctionnent de la même façon. C'est en quelque sorte un éditeur de texte en ligne de commande.

**Outil puissant à manipuler avec précaution.** 

*Exemple :* 

.. code-block:: bash

    vim ~/Documents/Documentation/bash/requirements.txt
    vim ~/Documents/Documentation/bash/conf.py
    
.. note::

    - Tout type de fichiers textuels peuvent être édités par `vi / vim` (`.py`, `.sh`, `.cfg`..).
    - L'éditeur dispose de son propre langage : 
        
        .. code-block::
            
            i # Permet de modifier le fichier.
            x # Permet de supprimer le caractère sous le curseur.
            dw # Permet de supprimer un mot. 
            dd # Permet de supprimer une ligne.
            yy # Permet de copier la ligne actuelle.
            p # Permet de coller après le curseur.
            u # Permet d'annuler la dernier commande. 
            :w # Permet de sauvegarder les modifications.
            :wq # Permet de sauvegarder les modifications et quitter l'éditeur de texte.
            :q # Permet de quitter l'éditeur de texte.
            :q! # Permet de quitter l'éditeur de texte sansa sauvegarder les modifications.


**1.10 dnf**
^^^^^^^^^^^^

**Syntaxe :**

.. code-block:: bash

    dnf <option> <package>

Permet l'installation et la manipulation de rpm, de packages, de repository et leur gestion.

*Exemple :* 

.. code-block:: bash

    sudo dnf install python3
    sudo dnf provides /usr/bin/fichier
    dnf search NetworkManager

.. note:: *options connues :*

    - L'option `install` permet d'installer des rpm. 
    - L'option `provides` permet d'identifier quel package fournit une fonctionnalité, un fichier ou une capacité spécifique. 
    - L'option `upgrade` permet de mettre à jour un package ou la distribution.
    - L'option `search` permet de faire une recherche via mot-clé.
    - L'option `repolist` permet d'afficher les repository configurés. `--all` pour tous les afficher.
    - L'option `config-manager` permet de gérer les repository présents, permet de les activer avec `enable` et les désactiver avec `disable`.
    - L'option `clean all` permet de vider le cache dnf. 

    **NB :** La commande `rpm -qa` permet de lister tous les packages rpm installés. 


**1.11 lsblk**
^^^^^^^^^^^^^^

**Syntaxe :**

.. code-block:: bash

    lsblk <option>

Permet d'optenir la liste et les caractéristiques des disques et de leurs partitions.

*Exemple :* 

.. code-block:: bash

    lsblk 
    lsblk -f

.. note:: *options connues :*

    - L'option `-f` permet d'afficher la liste complète.

.. note::

    - La valeur MOUNTPOINTS est le chemin monté du disque ou de la partition en question.


**1.12 dd** 
^^^^^^^^^^^

**Syntaxe :**

.. code-block:: bash

    dd <inputFile> <outputFile> <option>
   

Permet de créer un support bootable à partir d'un fichier .iso.

*Exemple :* 

.. code-block:: bash

    sudo dd if=home/aicardic/isoTest.iso of=/dev/sda status=progress

    # if = inputFile, l'iso à implémenter.
    # of = outputFile, le support à flasher.
    # status=progress = permet d'afficher la progression du flash.

.. note::

    On privilégiera l'utilisation d'outils tiers comme Ventoy. 


**1.13 checkisomd5 / sha256sum** 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Syntaxe :**

.. code-block:: bash

    checkisomd5 <fichier_iso>
    sha256sum <option> <fichier>
   

Permet de vérifier l'intégrité des fichiers *.iso* pour l'algorithme `checkisomd5` et de n'importe quel type de fichiers pour `sha256sum`.

*Exemple :* 

.. code-block:: bash

   checkisomd5 ~/Documents/moniso.iso

   sha256sum ~/Documents/monfichier
   # permet de générer la somme SHA-256 du fichier. 

   sha256sum -c ~/Documents/checksum_monfichier
   # permet de vérifier les sommes hachées dans le fichier spécifié (généralement un .sha256)

.. note:: *options connues :*

    - L'option `--quiet` permet de réduire la sortie, utile par exemple lors des vérifications.
    - L'option `--status` permet d'utiliser les codes de sortie pour indiquer le succès ou l'échec.
    - L'option `--tag` permet de formater la sortie pour inclure de balises comme dans les fichiers checksum par exemple.
    - L'option `-c` permet de lancer un contrôle complet.

.. warning::

    On doit se trouver dans le dossier concerné pour la commande `sha256sum`.


**1.14 chown** 
^^^^^^^^^^^^^^

**Syntaxe :**

.. code-block:: bash

    chown <user:group> <file>
   # Le duo utilisateur-groupe n'est pas forcément nécessaire, cela peut être l'un ou l'autre.

Permet de changer le propriétaire d'un dossier ou d'un fichier.

*Exemple :* 

.. code-block:: bash

    sudo chown aicardic:aicardic /run/media/aicardic/SSK-EXT4/


.. note::

    - `aicardic:aicardic` correspond en premier à la valeur utilsateur et en second à la valeur groupe utilisateur.
    - Chaque valeur est optionnelle, cela peut être un groupe qui devient propriétaire ou juste un seul utilisateur.


**1.15 chmod** 
^^^^^^^^^^^^^^

**Syntaxe :**

.. code-block:: bash

     chmod <option> <mode> <file>
   

Permet de modifier les autorisations d'accès à un fichier ou dossier.

*Exemple :* 

.. code-block:: bash

    chmod 700 ~/Documents/fichier
    chmod -R 664 ~/Documents/dossierTest
    # ici en mode octal.
    chmod ugo+rw ~/Documents/fichier
    # ici en mode setuid/setgid.

.. note::

    Concernant les modes *setuid/setgid*, les types d'autorisations appliquables sont les suivants :

        - `r` : lecture.
        - `w` : écriture.
        - `x` : exécution (ou parcours pour les répertoires).
        - `X` : exécuction dans le cas où le fichier est un répertoire ou si il a déjà une autorisation d'exécution par une catégorie d'utilisateur.
        - `s` : utiliser l'ID du propriétaire ou du groupe propriétaire du fichier lors de son exécution. 
        - `t` : permet d'indiquer que seul le propriétaire du repértoire ou du fichier en question peut supprimer cedit fichier. 
        - `u` : définit les droits utilisateur.
        - `g` : définit les droits groupe.
        - `o` : définit les droits pour "autre".

.. note:: *options connues :*

    - L'option `-R` permet d'appliquer les modifications de manière récursive.
    - L'option `-c` permet de ne décrire que les fichiers dont les permissions ont réllement changé.
    - L'option `-v` permet d'afficher les modifications apportées.


**1.16 grep** 
^^^^^^^^^^^^^

**Syntaxe :**

.. code-block:: bash

    grep <option> <pattern> <fichier>
   

Permet de chercher des motifs et des chaînes de caractères.

*Exemple :* 

.. code-block:: bash

    ls /usr/bin/ | grep "chains" > ~/Documents/testv2.txt

    # if = inputFile, l'iso à implémenter.
    # of = outputFile, le support à flasher.
    # status=progress = permet d'afficher la progression du flash.

.. note::

    Très souvent utilisé en complément d'autres commandes. 


**1.17 tee** 
^^^^^^^^^^^^

**Syntaxe :**

.. code-block:: bash

    tee <options> <fichier>
   

Permet de rediriger la sortie d'une commande vers le terminal et un ou plusieurs fichiers. 

*Exemple :* 

.. code-block:: bash

    lsblk -f | tee ~/Documents/lsblk.txt
    ping yum.home.arpa | tee -i ping-gateway.txt

.. note:: *options connues :*

    - L'option `-i` permet d'ignorer les interruptions.
    - L'option `-a` permet de de ne pas écraser le ou les fichiers cibles mais d'écrire à la suite de ceux-ci.

.. note::

    Généralement, est en amont ou en aval d'autres commandes. 


**1.18 echo** 
^^^^^^^^^^^^^

**Syntaxe :**

.. code-block:: bash

    echo <options> <string>
   

Permet d'afficher ce qu'on lui demande d'afficher. Commande absolument essentielle en scripting bash.

*Exemple :* 

.. code-block:: bash

    echo "Bonjour"
    echo $((a=5+5 , b=10+5 , c=21+21))
    # var1="Bonjour"
    echo ${var1}
    echo $?

.. note:: 

    - `$?` permet d'afficher le code de retour de la commande précédente. 
    - `echo$(())` permet de faire du calcul.
    - `echo $[[]]` permet de faire des tests de variables. 


