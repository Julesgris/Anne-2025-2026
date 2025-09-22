# Configuration du switch core

Voici les étapes pour la configuration de notre coeur de réseau 

## VLAN
en mode configuration
``` 
vlan [numero]
```
dans la configuration du vlan 
```
name [nom du VLAN]
```
## nom du switch
Il faut se mettre en mode configuration
```
conf t
```
Ensuite hanger le nom avec hostname

```
Hostname [nom du switch]
```
## IP vlan
Pour configurer une adresse IP a un vlan il faut :

Se mettre sur l'interface du vlan
```
interface vlan [numero du vlan]
```
Ensuite avec renseigner l'adresse ip suivie du masque de sous-réseau
```
ip address X.X.X.X X.X.X.X
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

## LACP
```
conf t
interface range Gi1/0/1 - 2
channel-group 1 mode active
exit
 
interface Port-channel1
switchport mode trunk
switchport access allowed vlan [numero de vlan]
```
## ROUTE
Pour activer le routage 
```
ip routing
```
puis on fait notre route par défault + notre route de retours 

route par défault
```
ip route 0.0.0.0 0.0.0.0 [le prochain routeur]
```
notre route de retours 
```
ip route 
ip route [Réseau] [masque] [prochain routeur]