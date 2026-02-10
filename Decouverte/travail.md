# Trouver, télecharger puis installer un module de l'OCA

L'[Odoo Community Association (OCA)](https://odoo-community.org/) est une association à but non lucratif basé en Suisse, indépendant de Odoo SA (qui pour l'anecdote est, de son coté, Belge), qui fédère la communauté open source Odoo pour développer, maintenir et partager des modules gratuits de qualité professionnelle. 


## Organisation du Github de l'OCA

L'OCA classe ses modules dans des dépots thematiques. Il existe plus de 250 dépôts différents. 
Pour s'y retrouver, heureusement, l'OCA propose un [App Store](https://odoo-community.org/shop) quir este, malgré tout, parfois un poil obscur :)



Chaque dépôt porte un nom qui indique sa thématique.

 :

ne fait pas un dépôt par module, mais un dépôt par thématique. Le module web_responsive se trouve dans le dépôt nommé "web".

Lien direct vers le dépôt :

Lien direct vers le dossier du module (en version 17.0) :




2. Comment le télécharger proprement ?
Il y a deux façons de faire, selon l'aisance de Mattéo :

Option A : La méthode "Ligne de commande" (Recommandée pour un VPS)
C'est la plus rapide. Mattéo tape ceci dans son terminal :

Une fois cette commande terminée, Mattéo aura un dossier nommé web. À l'intérieur, il y aura plein de modules, dont celui qui nous intéresse : web_responsive.

Option B : La méthode "Interface Web" (Téléchargement manuel)
Si Mattéo préfère passer par son navigateur :

Rends-toi sur .

Choisis la version : Clique sur le bouton qui dit "master" ou "16.0" en haut à gauche et sélectionne "17.0" (ou la version de son Odoo).

Clique sur le bouton vert "<> Code" puis sur "Download ZIP".

Une fois sur son PC, il décompresse le fichier.

Il doit ensuite envoyer le dossier web_responsive (qui se trouve à l'intérieur du ZIP) sur son VPS via un logiciel comme FileZilla ou WinSCP.

3. Pourquoi il y a plein de dossiers ?
Dans le dossier web que Mattéo va télécharger, il y a environ 50 modules. C'est normal. * Odoo est intelligent : même si Mattéo met tout le dossier web dans son addons_path, Odoo n'installera rien du tout tant que Mattéo ne clique pas manuellement sur "Installer" sur le module précis web_responsive depuis l'interface.

Cela permet à Mattéo d'avoir sous la main d'autres outils de l'OCA au cas où il en aurait besoin plus tard (comme des améliorations de barres de recherche).

4. Rappel pour le chemin (Addons Path)
Dans le fichier odoo.conf, Mattéo doit bien pointer vers le dossier parent. Si son dossier cloné est /opt/odoo/custom-addons/web, la ligne doit être : addons_path = /opt/odoo/odoo/addons, /opt/odoo/custom-addons/web

💡 Le petit truc en plus
Si Mattéo veut vérifier qu'il a le bon dossier avant de redémarrer Odoo, il peut taper ls /opt/odoo/custom-addons/web/web_responsive. S'il voit un fichier nommé __manifest__.py, c'est gagné !