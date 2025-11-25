# Installation HMAIL

## Installation
Sur une machine virtuelle windows installer HMAIL :
```
Installer le serveur depuis
www.hmailserver.com
```
Installation du framework avec :
```
Microsoft .NET Framework 2.0 Service Pack 1 (x64)
```
ou avec Powershell :
```
Install-WindowsFeature Net-Framework-Core -Source D:\sources\sxs
```
Puis finaliser l'installation avec vpotre administrateur et mot de passe.

## Configuration
Lors du début de la configuration dans l'onglet Domains ajouter votre domaine
```
ville.sportludique.fr
```

Ensuite dans Settings puis protocole:

![](image/capture_smtp.png)

Enfin dans l'onglet advanced du menu :

![](image/conf_hmail.png)

Ajouter une route permanante vers le LAN
```
route add -p <réseaux> mask <masque> <passerelle>
```

### Dans le DNS
#### Externe
Créer un nouvelle enregistrement dans le fichier /etc/bind/db.tours.sportludique.fr.externe :
```
smtp    IN      A       183.44.37.1

        IN      MX      10      smtp.tours.sportludique.fr
```
Cet enregistrement permet d'associer smtp.tours.sportludique.fr avec l'adresse ip 183.44.37.1 et le MX c'est pour Mail eXchange.

#### Interne
Créer un nouvelle enregistrement dans le fichier /etc/bind/db.tours.sportludique.fr.interne :
```
mail	IN	A	192.168.37.6

	IN	MX	10	smtp.tours.sportludique.fr

smtp	IN	CNAME	mail
imap	IN	CNAME	mail
```
Cet enregistrement associe mail.tours.sportludique.fr à l'adresse 192.168.37.6 et il permet également à smtp et imap de pointer vers mail.