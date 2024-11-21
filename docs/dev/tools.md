# Stations de travail & outils

## Ce dont on a généralement besoin

* Connectivité à Google Cloud Platform
* Authentification au Gitlab DIOD par clé SSH
* Une capacité à installer des outils avec droits d'aministration sur nos postes
* Un IDE - Integrated Development Environment
* De la fléxibilité dans la gestion des proxies: DEVACCESS

En fonction de ce que vous possédez (comme poste de travail ou comme accès) il ne sera pas forcément
nécessaire d'installer tous les outils ni d'appliquer toutes les configurations présentées ci-dessous.

C'est de qui rend l'exercice complexe.

Il faudra dans tous les cas un client ssh et un client Git pour travailler à plusieurs sur un même dépot.

### SSH client

* natif sous Linux et MacOS (pas besoin de putty, winSCP, …)
* .ssh/config peut être customizable

A la première utilisation, il faudra générer un couple de clés (privée et publique) et enregistrer sa clé publique dans Gitlab.

```bash
ssh-keygen -t ed25519
```

Appuyez sur ENTREE plusieurs fois, les clés seront générées dans votre HOME directory dans un sous répertoire .ssh.

Il ne reste plus qu'à copier la clé publique sous [Gitlab](https://gitlab.tech.orange/-/user_settings/ssh_keys)

## Usage 1 : E-Buro - Git - SQL

Pour un usage basique de Git, un simple programme de ligne de commande peut suffire.

Dans ce cas, se référer à la documentation suivante:
<!-- markdown-link-check-disable -->
[Environnement-de-développement-web](https://recommendations.innov.intraorange/environnement-de-developpement-web/#procdure-dinstallation)
<!-- markdown-link-check-enable -->

Ne suivre que les chapitres:

* Cmder
* Git (avec CNTLM si vous ne possédez pas de DevAccess)

Sinon, il vous faudra suivre:

* Cmder
* Cntlm
* Git

## Usage 2 : E-Buro - Git - SQL - Python

Pour un usage plus avancé, il faudra vous munir d'un IDE (Environnement de développement).

### IDE
<!-- markdown-link-check-disable -->
* [VisualStudio](https://code.visualstudio.com/)
* [PyCharm](https://www.jetbrains.com/fr-fr/pycharm/)
<!-- markdown-link-check-enable -->

## Usage 3 : E-Buro - Git - SQL - Python - Docker

Il sera nécessaire d'installer [WSL](https://plazza.orange.com/docs/DOC-2051952)
pour travailler sur ce type de PC E-Buro.

Il est souvent nécessaire d'accéder à une ressource distante par ssh, de récupérer des librairies ou
des packages afin d'éxécuter des programmes sur son poste de travail.

!!! warning
    Cette documentation concerne une configuration Windows WSL2. Elle peut être
    utilisée pour tout autre système **GNU Linux** ou **MacOS**.
    Dans ce cas, ne réinstallez pas le composant wsl-vpnkit.

Composants à installer :

| Composant          |   Commentaire                            |
|:-------------------|:-----------------------------------------|
| wsl-vpnkit | Pour l'accès réseau depuis WSL2 vers le réseau Windows |
| docker CE  | Un docker engine et un client CLI client (optionnel)   |

### VPN Kit (windows/WSL)

Doc d'installation: [on plazza](https://plazza.orange.com/docs/DOC-2051952#jive_content_id_Installation_de_VPNKit)

Pour lancer le service:

```bash
sudo service wsl-vpnkit start
```

### Docker CE

Si vous souhaitez localement : construire des images docker, récupérer des
images de conteneurs, tagguer des images...

Doc d'installation: [on plazza](https://plazza.orange.com/docs/DOC-2051952#jive_content_id_Installation_de_Docker_CE)
