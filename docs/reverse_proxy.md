# Reverse Proxy

On va installer nginx pour configurer le reverse proxy
Oour cela il faut :
```
sudo apt update
sudo apt install nginx
```
Ensuite il suffit de créer le fichier correspondant à votre site:

```
sudo nano /etc/nginx/sites-availables/nom_du_site
```
Puis dans le fichiers:
```
server {
    listen [le port]
    server_name www.ville.sportludique.fr;

    location / {
        proxy_pass http://adress_ip_du_site: port;
        proxy_set_header Host $host;
        proxy_set_header X-real-ip $remote_add;
    }
}
```