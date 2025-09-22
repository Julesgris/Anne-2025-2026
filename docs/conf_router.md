# CONFIGURATION ROUTEUR 
**Dans cette page on va écrire les étapes, qu'on a fait pour la configuration** |
**de nos routers CISCO 1900 Séries**

## Nom du switch et nom de domain

Entrer en mode configuration pour faire les étape suivante :

Pour confgurer le nom du switch
```
hostname [nom souhaité]
```
Pour le nom de domain :
```
ip domain-name [nom de domain]
```
On a créé
## Interface et adresse IP
Sur un routeur pour faire un routage intervlan il faut configurer des interface virtuelle. Pour cela suivez les étapes ci-dessous:

En mode configuration 
```
interface GigabitEthernet0/1.[numéro pour identifer l'interfce virtuelle]
```
Ensuite associer une adresse ip et l'encapsulation dot1Q
```
ip address [adresse ip] [masque de sous réseau]
ecapsulation dot1Q [numero de vlan]
```

Sur une interface physique configurer un lien vers internet. Ne pas oublier d'autorise les routes de retour.
```
interface GigabitEthernet0/2
ip address [adresse public vers internet] [masque de sous réseau]
nat outside
```
## Compte SSH 

On a créé nos comptes utilisateurs pour la connection en ssh 

```
Username [nom d'utilisateur] privilege 15 secret [mot de passe]
```
Avoir mis secret au lieu de password permet de crypté le mot de passe.

## SSH
Dans le mode configuration tapez les commandes suivantes :

```
crypto key generate rsa
```
puis mettre une clé en 1024 ou 2048 pour le ssh 2.0 

puis il faut activer le ssh 

```
ip ssh version 2
```
autoriser les utilisateurs a se connecter en ssh

```
line vty 0 4
login local
transport input ssh
exit
```

## NAT
sur interface WAN 
```
ip nat outside
```
sur interface lan
```
ip nat inside
```
on a créé une ACL qui autorise notre réseau à être naté

```
access-list 1 permit [adresse réseau ] [Masque inversé]
```
puis on autorise notre réseau via l'interfacde GiggEthernet 0/1
```
ip nat inside source list 1 interface gigaethernet 0/1 overload
```
## ROUTE
puis on fait notre route par défault + notre route de retours 

route par défault
```
ip route 0.0.0.0 0.0.0.0 [le prochain routeur]
```
notre route de retours 
```
ip route [Réseau] [masque] [prochain routeur]
```
## HSRP
ça nous permet d'avoir 2 routeur mais un prorisé par rapport à l'autre
le deuxieme est la pour de la redondance en cas de panne

on fait les commande sur notre interface lan 
``` 
standby 1 ip 172.28.x.254 (interface virtuel)
standby 1 priority 100 (priorité)
standby 1 preempt (prendre le relay)
```

