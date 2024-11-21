# Documentation en code

Dans ce projet, nous faisons la promotion des méthodologies autour de Git.
En conséquence, la documentation, est considérée comme du code et est donc gérée
en tant que tel.

La documentation est realisée en [Markdown](https://www.markdownguide.org/)
et nous tirons parti du [Framework MkDocs](https://www.mkdocs.org/)
pour mettre en ligne une documentation dans laquelle on puisse naviguer
simplement.

La documentation est générée automatiquement grâce aux Github actions.
Le site web statique est mis en ligne avec `github pages`, l'accès à la
documentation est public tout comme le projet.

L'URL est fournie dans la description du projet, elle est construite comme
ci-dessous:

<!-- markdownlint-disable -->
|   Champ           |                            Valeur                             |
|:-----------------:|:-------------------------------------------------------------:|
| Github project    |    https://gitlab.tech.orange/<group\>/<project_subpath\>     |
| Documentation URL | https://<group\>.github.io/<project_subpath\>  |
<!-- markdownlint-enable -->

## Construire la documentation et naviguer locallement dedans

Afin d'éviter les multiples allers-retours sur la doc en ligne, il est
préférable de l'éditer locallement sur son poste de travail.
Pour cela, vous devez construire votre environnement de documentation.

MkDocs est un framework python, il est fortement recommandé de créer un
environnement virtuel pour l'installer.

```bash
cd <my-folder>
poetry config virtualenvs.in-project true
# virtualenv is located in <my-folder> .venv subdirectory 
poetry shell
poetry install --no-root
$(mkdocs) mkdocs serve
```

<!-- markdown-link-check-disable -->
Une fois créé, vous pouvez visualiser votre documentation localement à l'url
[http://127.0.0.1:8000/](http://127.0.0.1:8000/).
<!-- markdown-link-check-enable -->

## Suggérer une modification

La documentation est comme le code et le dépot Git représente la **source de vérité**.

N'importe quel changement commence par une Issue Github décrivant le changement.
Cette Issue est utilisée pour créer une Pull Request.

Vous soumettez ensuite votre proposition dans cette Pull Request.
En travaillant le local sur votre poste de travail, il est possible de
bénéficier de linter dans VS Code pour vérifier le bon format de ce que vous
rédigez.

Des extensions comme:

* markdownlint: id = DavidAnson.vscode-markdownlint
* rewrap: id = stkb.rewrap

Permettent de voir assez tôt les erreurs de formatage.

Une fois que vous êtes satisfait, vous devez

* Mettre la Pull Request à l'état `Ready`
* Communiquer avec le reste de l'équipe afin qu'elle soit revue
* Une fois que toutes les remarques de revue sont répondues, vous pouvez merger.

!!! note
    Le Reviewer ne merge pas après avoir revu et approuvé la Pull Request, il informe
    l'auteur de la Pull Request qui s'en chargera.

## MkDocs

### Table des matières

La table des matières se trouve dans le fichier `mkdocs.yaml` dans la section
`nav`.

Un fichier `index.md` est attendu dans chaque répertoire car nous utilisons la
fonctionalité `navigation.indexes`.

### Plugins

Le dépot de documentation peut contenir un certain nombre de pluggins. A date, ils n'ont pas été
installés.

* `search`: moteur de recherche
* `awesome-pages`: améliorations cosmétiques
* `gitsnippet`: pour inclure des pages markdown externes provenant d'autres
  projets de docs.
* [Mermaid](https://mermaid.js.org/intro/):permet d'éditer des workflows, graphique et diagrammes.
* [Gantt](https://github.com/Neoteroi/mkdocs-plugins)
* [Plantuml](https://github.com/quantorconsulting/mkdocs_build_plantuml)

Il est possible d'en ajouter d'autres (à declarer dans le `mkdocs.yaml` et dans
le `requirements.txt`).

Voir [MkDocs plugin list](https://github.com/mkdocs/mkdocs/wiki/MkDocs-Plugins).

## Diagrammes

Les diagrammes doivent être faits avec `drawio.io` puis ajoutés au projet de
documentation gitlab dans le répertoire `draw` et exportés commes images `png`
dans le répertoire `docs/assets` pour être intégrés à la documentation. Il est
aussi possible de les inclure directement comme fichiers `draw.io`dans la doc.

<!-- markdown-link-check-disable -->
!!! note
    DIOD fourni une version en ligne de `draw.io`[https://draw.tech.orange/](https://draw.tech.orange/)
<!-- markdown-link-check-enable -->

## Ajouter une table

Declaration avec des colonnes centrées:

```markdown
|  Variable | Value  |
|:---------:|:------:|
|   FIRST   |  first |
```

Resultat:

|  Variable | Value  |
|:---------:|:------:|
|   FIRST   |  first |

### Caractères d'échapement

utilisez `\>` pour échapper un caractère `>`

### Afficher des flèches

| description | Symbol |  Value   |
|:-----------:|:------:|:--------:|
| Haut        | &uarr; | `&uarr;` |
| Bas         | &darr; | `&darr;` |
| Gauche      | &larr; | `&larr;` |
| Droite      | &rarr; | `&rarr;` |

### Liste à deux niveaux

Declaration:

```markdown
Ceci est une liste:

* Level 1
    * Level 2
    * Level 2
* Level 1
    * Level 2
```

Resultat &rarr; Ceci est une liste:

* Level 1
    * Level 2
    * Level 2
* Level 1
    * Level 2

!!! note
    4 espaces sont nécessaires pour passer au second niveau.
    `"MD007": { "indent": 4 }` configuré dans le fichier `.markdownlint.json`
