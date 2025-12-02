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

## probleme usurpation d'identité

    l'ips du stormshield refusait les retours de ping, on arrivait pas à communiquer avec internet après l'application de la regle de filtrage qui permet a notre réseau lan de sortir sur internet. on a du autorisé l'usurpation d'identité entrant.