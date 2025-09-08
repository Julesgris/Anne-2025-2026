# Configuration du switch core
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


