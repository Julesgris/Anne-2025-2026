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
## Interface et adresse IP
Sur un routeur pour faire un routage intervlan il faut configurer des interface virtuelle. Pour cela suivez les étapes ci-dessous:

En mode configuration 
```
interface GigabitEthernet0/1.[numéro pour identifer l'interfce virtuelle]
```
Ensuite associer une adresse ip et l'encapsulation dot1Q
```
ip adresse [adresse ip] [masque de sous réseau]
ecapsulation dot1Q [numero de vlan]
```
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