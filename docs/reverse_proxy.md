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
Puis dans le fichiers on configure http:
```
server {
    listen 80 #port http
    server_name www.ville.sportludique.fr;

    location / {
        proxy_pass http://adresse_ip_du_site: port;
        proxy_set_header Host $host;
        proxy_set_header X-real-ip $remote_add;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}
```

