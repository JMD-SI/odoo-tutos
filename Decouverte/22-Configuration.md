# 📋 Configuration de Odoo 

Pour mes tests, j’ai choisi d’auto-héberger **Odoo 19 Community** sur une VM Linux Ubuntu via mon petit serveur local.

## 🧩 Créer le fichier de configuration

Fichier de configuration Odoo :
* **Création de odoo.conf**
```bash
sudo nano /etc/odoo.conf
```
* **Contenu du fichier :**
```bash
[options]
admin_passwd = mdp4Master
db_host = localhost 
db_port = 5432 
db_user = odoo 
db_password = mdp2OdooPgSql
addons_path = /opt/odoo/addons,/opt/odoo/custom-addons
xmlrpc_port = 8069 
logfile = /var/log/odoo/odoo.log
```

* le mot de passe **admin_passwd**  est le mot de passe général de Odoo qui sera demandé pour chaque action sur les bases de données
* le mot de passe **db_password** est celui crée au moment de l’install de Postgre (cf. un peu plus haut)

Sauvegarder et quitter nano (Ctrl+O, Entrée, Ctrl+X)


## ⚙️ Créer le service odoo 


* Créer le fichier service **odoo.service** avec :
```bash
sudo nano /etc/systemd/system/odoo.service
```

* **Contenu du fichier :**

```bash
[Unit]
Description= Odoo 19 Community
After=network.target postgresql.service

[Service]
Type=simple
SyslogIdentifier=odoo
PermissionsStartOnly=true
User=odoo
Group=odoo
ExecStart=/opt/odoo/venv/bin/python3 /opt/odoo/odoo-bin -c /etc/odoo.conf
WorkingDirectory=/opt/odoo
StandardOutput=journal
StandardError=journal
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

* Relancer les services :
```bash
sudo systemctl daemon-reload 
sudo systemctl enable odoo 
sudo systemctl start odoo 
``` 

> [!TIP] 
> A partir de là, Odoo doit fonctionner sur le port 8069.</BR>
>  http://[Votre IP]:8069



## 🔒 Basculer en HTTPS avec Nginx  


* On commence par installer Nginx et certbot  
```bash
sudo apt install nginx certbot python3-certbot-nginx
``` 

* On génère un certificat pour l’ip du serveur :
```bash
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/nginx-selfsigned.key -out /etc/ssl/certs/nginx-selfsigned.crt -subj "/CN=[Votre IP]"
``` 
 

* créer le vhost du site :
```bash
sudo rm /etc/nginx/sites-enabled/default
sudo nano /etc/nginx/sites-available/odoo 
``` 

* Avec la configuration : 
```bash
server {
    listen 80;
    server_name 192.168.1.15;
    return 301 https://192.168.1.15$request_uri;
}

server {
    listen 443 ssl;
    server_name 192.168.1.15;

    ssl_certificate /etc/ssl/certs/nginx-selfsigned.crt;
    ssl_certificate_key /etc/ssl/private/nginx-selfsigned.key;

    location / {
        proxy_pass http://127.0.0.1:8069;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }

    location /longpolling/ {
        proxy_pass http://127.0.0.1:8072;
    }
}
``` 

* Puis l’activer !
```bash
sudo ln -s /etc/nginx/sites-available/odoo /etc/nginx/sites-enabled/ 
sudo nginx -t # Test config 
sudo systemctl restart nginx
``` 


> [!TIP] 
> Maintenant, on peut accéder au site avec http://[Votre IP] 





<div align="center">

[![Précédent](https://img.shields.io/badge/⬅️%20Précédent-blue)](./21-Installation.md)
[![Sommaire](https://img.shields.io/badge/🏠%20%20%20Sommaire-gray)](../README.md#sommaire)
[![Suivant](https://img.shields.io/badge/Suivant%20%20%20%20➡️-blue)](./23-Install_Module.md)

</div>

 


JMD @2026






