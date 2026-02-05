# 🐧📦 Installation de Odoo 19 Community sur Ubuntu 24.04

Pour mes tests, j’ai choisi d’auto-héberger **Odoo 19 Community** sur une VM Linux Ubuntu via mon petit serveur local.

## 🖥️ Machine Virtuelle
Les caractéristiques de la VM sont : 
* **vCPU :** 4
* **RAM :** 8 Go
* **Disque :** 120 Go
* **OS :** Ubuntu 24.04.3 LTS (`ubuntu-24.04.3-live-server-amd64.iso`)

## 🛠️ Installation de l’OS et des outils
Après avoir installé Ubuntu de façon classique, j’installe quelques outils utiles :

```bash
sudo apt update && sudo apt install -y git curl wget unzip nginx wkhtmltopdf htop software-properties-common

```

* **Git** : pour récupérer les sources de Odoo depuis le dépôt GitHub.
* **Curl** : utile pour les scripts d'installation, les dépendances Python via pip, ou les configs Nginx.
* **Wget** : pour télécharger les fichiers de manière non interactive.
* **Unzip** : pour décompresser les archives `.zip`.
* **Nginx** : serveur web / reverse proxy ultra-léger et performant pour gérer la redirection de ports et le HTTPS.
* **Wkhtmltopdf** : indispensable pour générer les rapports PDF (factures, devis, bons de commande).
* **Htop** : moniteur système interactif pour surveiller CPU/RAM/PostgreSQL.
* **software-properties-common** : outils pour gérer les dépôts APT (sources.list), ajouter des PPAs, importer des clés GPG.

## 🗄️ Installation de PostgreSQL

J’installe PostgreSQL de façon classique :

```bash
sudo apt install -y postgresql postgresql-contrib

```

* **postgresql** : serveur de base de données PostgreSQL principal (le cœur du SGBD).
* **postgresql-contrib** : extensions et modules supplémentaires (recherche plein texte, UUID, statistiques avancées, etc.).

Puis je crée un utilisateur « **odoo** » (bien noter le mot de passe 😉) :

```bash
sudo -u postgres createuser --createdb --username postgres --no-createrole --no-superuser --pwprompt odoo

```

## 🐍 Installation de Python

Odoo utilise Python. Il faut donc l’installer et préparer tout le nécessaire :

```bash
sudo apt install -y python3 python3-pip python3-venv python3-dev

```

* **python3** : interpréteur Python 3 principal.
* **python3-pip** : gestionnaire de paquets Python (PyPI).
* **python3-venv** : module pour créer des environnements virtuels Python isolés.
* **python3-dev** : headers et libs de développement Python.

## 📦 Installation des dépendances Odoo

Odoo nécessite de nombreuses bibliothèques système pour compiler ses dépendances :

```bash
sudo apt install -y libpq-dev libxml2-dev libxslt1-dev libxmlsec1-dev libjpeg-dev libpng-dev libfreetype6-dev liblcms2-dev libldap2-dev libsasl2-dev libssl-dev libblas-dev libatlas-base-dev node-less

```

* **libpq-dev** : connecteur PostgreSQL.
* **libxml2-dev + libxslt1-dev** : compilation de lxml (parsing XML/HTML).
* **libxmlsec1-dev** : support des signatures XML (factures électroniques).
* **Bibliothèques d'images (libjpeg, etc.)** : pour compiler `Pillow` (logos, images produits).
* **libldap2-dev + libsasl2-dev** : authentification LDAP.
* **libssl-dev** : SSL/TLS pour les emails et APIs sécurisées.
* **libblas-dev + libatlas-base-dev** : calculs matriciels (modules analytiques).
* **node-less** : compilation des thèmes Odoo.

## 🚀 Installation de Odoo

Clonage des sources de Odoo 19 (branche 19.0) :

```bash
sudo git clone [https://github.com/odoo/odoo](https://github.com/odoo/odoo) --depth 1 --branch 19.0 --single-branch /opt/odoo

```

Création d’un utilisateur système dédié et configuration des droits :

```bash
sudo useradd -m -d /opt/odoo -s /bin/bash -U odoo 
sudo mkdir -p /opt/odoo/custom-addons /var/log/odoo /etc/odoo 
sudo chown -R odoo:odoo /opt/odoo /var/log/odoo /etc/odoo

```

## 🧪 Création de l'environnement virtuel (venv)

C’est la partie la plus délicate, elle permet d'isoler les paquets Python d'Odoo.

```bash
cd /opt/odoo 
sudo python3 -m venv odoo-venv 
sudo chown -R odoo:odoo /opt/odoo/odoo-venv/
sudo chmod -R u+rwX,g+rwX /opt/odoo/odoo-venv/

```

Activation du venv et installation des requirements :

```bash
# Activation
source odoo-venv/bin/activate

# Mise à jour des outils de paquets
pip install --upgrade pip
pip install -r requirements.txt

```


JMD @2026
