# 📦 Installation de modules

Lors de l'installation, on a crée et configuré un répertoire dédié aux addons : /opt/odoo/custom-addons 
On va donc déposer là tous les modules et apps que nous allons rajouter.

## ⚠️ Avant de bidouiller / Customiser ...

Pour une raison de stabilité, il est (plus que) préferable d'installer d'abord les modules officiels et touchant la "structure" (Ventes, Facturation ...) avant les modules tiers.  
De plus, la règle d'or est, bien entendu, de NE JAMAIS TESTER, un nouveau module sur la base de données de production. Toujours utiliser une base de test (Duplicate) !     
Faites aussi des sauvegardes avant de bidouiller …   
Ce sont des évidences mais ça ne fait pas de mal de le rappeler car le résultat pourrait être désastreux.



## 🔍 Trouver et télécharger des modules tiers

Pour enrichir Odoo, la source officielle est l'[Odoo Apps Store](https://apps.odoo.com/apps), qui regroupe des milliers de modules gratuits et payants. 
Pour une approche plus "Open Source" et communautaire, il est possible de puiser dans les dépôts de l'[OCA (Odoo Community Association)](https://github.com/OCA), qui impose des règles strictes de qualité et de pérennité. 
Enfin, si vous savez ce que vous faites, certains sont parfois téléchargeables directement depuis Github.

Pour les tests, il est frequent qu'un module payant sur l'App Store dont le créateur appartient à l'OCA, soit disponible en "open source" sur leur GitHub 

Il est, enfin, TRES important de vérifier que la version du module correspond exactement à la version d'Odoo car un module conçu pour une version antérieure peut provoquer des erreurs critiques de base de données.


## 📥 Installer un module téléchargé 

Pour installer un module téléchargé sur l'App Store Odoo ou Github dans une archive zip, il faut la decompresser et la transferer dans /opt/odoo/custom-addons  

Vous pouvez par exemple telecharger le zip, le decompresser puis l'envoyer via sftp sur votre serveur (avec filezilla par exemple).  
Il est aussi possiblke de tout faire depuis le seveur (en ssh avec Putty) :  on le télécharge et verifie puis on le décompresse avant d'effacer l'archive et de propoager les droits odoo sur les nouveaux fichiers.

```bash
cd /opt/odoo/custom-addons/
wget -O module.zip "url_du_module"
unzip -l module.zip
sudo unzip -o module.zip
rm module.zip
sudo chown -R odoo:odoo /opt/odoo/custom-addons/
```
 
Dans le cadre de modules Github (module de l'OCA par exemple), il est possible de le cloner directement avec git :

```bash
cd /opt/odoo/custom-addons
sudo git clone https://github.com/OCA/...le_Module... -b 19.0 --depth 1
```
Note : Ici, la branche est la 19.0 mais il est important de l'adapter en fonction de la version
 
Il faut alors redémarrer Odoo pour que la nouvelle configuration soit prise en compte :

```bash
sudo systemctl restart odoo
```


## 🚀 Activer le module dans Odoo

Même copié sur le serveur, le module ne s'active pas tout seul et il est necessaire de demander à Odoo de le prendre en compte. 

Pour ceci, il faut : 
* Se Connecter à ton Odoo avec un compte Administrateur.
* Aller ddans Paramètres (Settings) et activer le Mode Développeur (en bas de la page).
* Puis aller dans le menu Applications.
* "Mettre à jour la liste des applications" (Update Apps List) dans la barre de menu du haut.
* chercher son modules (via les catégories à gauche ou en supprimant le filtre par defaut)
* cliquer sur Activer.


> [!TIP] 
> Certains modules ont besoin de bibliothèques Python supplémentaires.  
> En cas d'echec d'activation, ceci est alors indiqué dans le message d'erreur (ou dans les logs) 

 

<div align="center">

[![Précédent](https://img.shields.io/badge/⬅️%20Précédent-blue)](./22-Configuration.md)
[![Sommaire](https://img.shields.io/badge/🏠%20%20%20Sommaire-gray)](../README.md#sommaire)
[![Suivant](https://img.shields.io/badge/Suivant%20%20%20%20➡️-blue)](../README.md#sommaire)

</div>



