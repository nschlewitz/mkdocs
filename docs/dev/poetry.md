# Premiers pas sous Poetry

Poetry est un système de gestion de dépendances et de packages python. Il permet de déclarer les
librairies dont dépendent votre projet et de les gérer (installation / mise à jour).
Poetry stocke l'ensemble des informations de votre projet dans le fichier `pyptoject.toml`.
Poetry utilise un lockfile `poetry.lock` pour s'assurer que les installations soient les mêmes à chaque fois.

## Installation

Se référer à la [page suivante](https://python-poetry.org/docs/#installing-with-the-official-installer).

Poetry fonctionne avec une version de python >= 3.8

## Créer un environnement poetry

La gestion des environnements est décrite sur [cette page](https://python-poetry.org/docs/managing-environments/).

### Construire une structure python en créant un répertoire et un package

```bash
poetry new my-folder --name my-package
```

### Ou initialiser un fichier pyproject.toml dans un répertoire existant

```bash
cd <my-folder>
poetry init
```

### Récupérer les informations sur l'environment virtuel d'éxécution

```bash
cd <my-folder>
poetry env info
```

### Installer votre projet poetry (décrit dans le pyproject.toml) avec l'executable python par défaut

```bash
cd <my-folder>
poetry config virtualenvs.in-project true
# virtualenv is located in <my-folder> .venv subdirectory 
poetry install
```

### Ou utiliser un éxécutable différent de python pour votre environnement virtuel

```bash
# on MacOS
cd <my-folder>
poetry config virtualenvs.in-project true
# virtualenv is located in <my-folder> .venv subdirectory 
poetry env use /opt/homebrew/Cellar/python@3.9/3.9.19/bin/python3.9

# on another system
cd <my-folder>
poetry config virtualenvs.in-project true
# virtualenv is located in <my-folder> .venv subdirectory 
poetry env use <path_to_your_python_version>
```

### Se connecter à l'environnement virtuel de votre projet poetry

```bash
# activate the virtualenv
poetry shell

# exit the virtualenv
exit

# deactivate the virtualenv
deactivate

# list
poetry env list

# remove
rm -r .venv
```

## Utiliser Poetry

On retrouve l'ensemble des commandes poetry sur [cette page](https://python-poetry.org/docs/cli/).

### Ajouter un package

```bash
# specific version
poetry add requests@2.12.1
# will install requests 2.12.1

# latest major version (up to requests version 3)
poetry add requests^2.12.1
# will install requests 2.31.0, same as
poetry add requests

# latest minor version (up to requests version 2.13)
poetry add requests~2.12.1
# will install requests 2.12.5
```

### Lister les packages

```bash
poetry show
```

### Desinstaller un package

```bash
poetry remove requests
```
