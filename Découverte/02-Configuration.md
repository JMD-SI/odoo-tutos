# 📋 Configuration de Odoo 

Pour mes tests, j’ai choisi d’auto-héberger **Odoo 19 Community** sur une VM Linux Ubuntu via mon petit serveur local.

## Créer le fichier de configuration

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


## Créer le service odoo 


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
> A partir de là, Odoo doit fonctionner sur le port 8069.
>  http://[Votre IP]:8069


