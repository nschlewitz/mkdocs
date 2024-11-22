# Documentation Car Accidents

Cette documentation est à destination unique des membres de l'équipe projet.
Chacun des membres peut contribuer à alimenter les pages de documentation.

## Contribuer à cette documentation

TLDR;

Installez les extensions suivantes dans VS Code:

* markdownlint: id = DavidAnson.vscode-markdownlint
* rewrap: id = stkb.rewrap

Faites tourner Mkdocs en local

```bash
poetry config virtualenvs.in-project true
poetry shell
poetry install --no-root
poetry run mkdocs serve &
```

<!-- markdown-link-check-disable -->
Une fois créé, vous pouvez visualiser votre documentation localement à l'url
[http://127.0.0.1:8000/](http://127.0.0.1:8000/).
<!-- markdown-link-check-enable -->
