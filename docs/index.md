# Welcome to MkDocs

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## Commands

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.
        Bonjour ceci est un test
# Adressage IP 
    - Chartres : 172.28.32-63.0 /19 
    - Tours : 172.28.64-95.0 /19 
    - Orléans : 172.28.96-127.0 /19 
    - Bourges : 172.28.128-159.0 /19
    - Blois : 172.28.160.0 /19
    - Nutomix : 172.16.90.200 : 9440

## Tableau d'adresse
    | Equipement        | réseaux           | adresse ip    |
    |-------------------------------------------------------|
    | TRS-Switch-core    192.168.130.0 /27   192.18.130.30  |

## Nutomix
    - login@lan.sio.lyceefulbert.fr

# Les problèmes rencontrer
## SSH
    Lors de l'installation de ssh sur le switch nous avons rencontrer un probleme de drivers qui bloqué la connexion depuis un terminal d'un autre equipement.
    En effet depuis windows et linux mint la difference de génératoin entre le switch et l'ordinateur fait que les drivers ne sont pas identiques donc par sécurité ssh n'accepte pas la liaison. Il faut donc utiliser putty ou un autre émulatuer car ils prenne en compte la difference de drivers.
## LACP ( agregation de lien)
    Lors de la mise en place de la liaison entre notre switch core et le switch de la baie nous avons voulus mettre en place une agregation de liens avec le protocole LACP.
    Lors de la mise en fonction nous avons rencontrer une erreur concernant le fait que la liaison physique fonctionne mais le switch met l'etat de la liaison en suspendu.
    Le problème peut venir de plusieurs facteurs:
    - Les deux swittch n'utilise pas le même protocole.
    - Les interfaces n'ont pas de configuration identique.
    - les deux switch n'ont pas le même état sur le protocole.

![mon logo](../Anne-2025-2026/image/tours-logo-73-12005.png)