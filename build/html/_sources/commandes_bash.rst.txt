**Commandes Bash**
====================

**1. Commandes de base**
------------------------

**1.1 python3**
^^^^^^^^^^^^^^^

**Syntaxe :**

.. code-block:: python

    python3

Permet de lancer des scripts Python.

*Exemple :* 

.. code-block:: python

    python3 mon_script.py
    python3 -m venv env

.. note::

    Pas besoin de le spécifier si le chemin d'accès est dans le PATH et qu'on place la ligne de commande suivante en tête de script :

    .. code-block:: python

        #!/usr/bin/env python
    
    -m pour spécifier qu'on souhaite utiliser un module de Python et non un fichier script.

**1.2 # et """commentaire"""**
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Syntaxe :**

.. code-block:: python

    # en début de ligne
    """mettre ici le texte qui peut tenir 
    sur plusieurs lignes et inclure fonctions et autres."""

Permet de commenter le code. **Capital** pour maintenir un code à jour, propre et simple d'utilisation notamment pour les autres utilisateurs.

*Exemple :* 

.. code-block:: python

    # ceci est un commentaire
    """ Ceci est une chaine de commentaires, 
    utilisée pour les fonctions par exemple, 
    et ça tient sur plusieurs lignes. """

.. note::

    # Utilisé pour commenter sur une ligne.

    """ Permet de commenter sur plusieurs lignes, on peut s'en servir pour générer des tooltips dans le cadre de fonctions et classes par exemple. 

**1.3 import / from**
^^^^^^^^^^^^^^^^^^^^^

**Syntaxe :**

.. code-block:: python
    
    import
    from

- Permet d'importer un module (fichier contenant du code Python). 
- Ce dernier peut contenir des fonctions, des classes, des variables etc. 
- Pratique pour organiser le code de manière logique et réutilisable.\
- **A placer en début de code.**

*Exemple :* 

.. code-block:: python

    import mon_module
    #resultat
    mon_module.ma_fonction()

    from mon_module import ma_fonction
    #resultat
    ma_fonction() # Directement exploitable sans spécifier le module.

.. note::

    - Il faut impérativement penser à spécifier le nom du module avant d'appeler la fonction, sauf si on utilise `from`. 
    - Pour importer plusieurs éléments spécifiques, il suffit de les séparer par des virgules. 
    - Il ne faut pas mettre l'extension de fichiers .py quand on appelle l'import.

.. tip::

    On peut utiliser `as` pour attacher un alias à l'import de manière à clarifier le code et le rendre moins lourd. Voici un exemple :
    
    .. code-block:: python
        
        import numpy as np

**1.4 pip**
^^^^^^^^^^^

**Syntaxe :**

.. code-block:: python
    
    pip install <nom_du_package>
    pip uninstall <nom_du_package>
    pip freeze
    pip show 
    pip list
    
Gestionnaire de paquets inclu dans Python pour gérer des packages.

*Exemple :* 

.. code-block:: python

    pip install numpy
    pip uninstall numpy
    pip freeze
    pip freeze > requirements.txt
    pip list
    pip show numpy requests pandas
    pip install -r requirements.txt

.. note::

    - A utiliser dans un shell et non dans Python directement. 
    - Doit être installé au préalable.
    - On peut installer des versions spécifiques des packages avec ==, ~=, > et >0.0.0<.
    - On peut installer plusieurs packages en les séparant par de espaces.
    - `-r` est utilisé pour spécifier un fichier "requirements.txt" contenant la liste des scripts à installer. Pratique pour élaborer des listes de packages "to use".
    - `uninstall` pour désinstaller un package.
    - `freeze` et `list` pour afficher la liste des packages installés. `freeze` est plus complet que `list` et permet d'incrémenter un fichier requirements.txt.
    - `show` permet de voir les informations des packages passés en argument. 

**1.5 print**
^^^^^^^^^^^^^

**Syntaxe :**

.. code-block:: python
    
    print("texte à afficher")
    print(f"texte à afficher contenant des {variables}.")
    
Equivalent d'`echo` ou de `printf`, permet d'afficher du texte, des charactères, variables et autre.

*Exemple :* 

.. code-block:: python

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

    
