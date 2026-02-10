# 🛠️ Modules Odoo necessaires / conseillés

Afin de gérer les points clés de leur projet : 
* Leur stock de produits et leur mise en valeur
* Les achats 
* Les ventes directes, en ligne et la fidélisation
* Le pilotage

Plusieurs modules officiels seront indispensables à l'implementation de Odoo Community.
Certains modules OCA seront aussi le bienvenus.    

## 💼 Socle de base : Produits, Stock et Achats

Le coeur du système, indispensable aux bases du business de Juliette, Dylan et Mattéo

![stock](img/stock.png)
* **Inventaire** (stock)  
    * Gérer les CD comme articles uniques avec gestion des caractéristiques (état, édition, ... )
    * Emplacement physique du stock (Étagère A, B, C du garage).

![purchase](img/purchase.png)
* **Achats** (purchase)  
    * Formaliser l’acquisition des lots (vide-greniers, Leboncoin, particuliers ...)
    * Suivre le coût d’acquisition réel pour calculer la marge
    

## 🧑‍🤝‍🧑 Clients : Contacts, fidélisation et réclamations 

![contacts](img/contacts.png)
* **Contacts** (contacts)  
    * Centraliser l'annuaire de tous les acteurs du business (acheteurs, vendeurs de lots, fournisseurs de fournitures).

![mass_mailing](img/mass_mailing.png)
* **E-Mail Marketing** (mass_mailing)  
    * Concevoir et envoyer des emails graphiques à votre base de contacts pour les informer ou proposer des promotions

![project](img/project.png)
* **Projet** (project)  
    * Suivre sous forme de tâches les emails et questions des clients

## 🛒 Canaux de Vente : Terrain et Web

![point_of_sale](img/point_of_sale.png)
* **Point de Vente** (point_of_sale)  
    * Interface de vente ("Caisse enregistreuse"), accessible sur tablette/telephone, pour les marchés et vide-greniers.

![website](img/website.png) ![website_sale](img/website_sale.png)
* **Vente en ligne** (website + website_sale)  
    * Boutique en ligne proposant le catalogue des CD et de leurs caracteristiques, mis à jour en temps réel
    * Gestion des clients et des achats 

![payment](img/payment.png) ![website_payment](img/website_payment.png)
* **Paiements en ligne** (payment + website_payment)  
    * Lien avec les passerelles de paiements en ligne (Stripe, PayPal, virement ...)

![sale_management](img/sale_management.png)
* **Ventes** (sale_management)  
    * Gestion du cycle de vente et des frais de ports
    * Indispensable pour la vente en ligne (panier validé devient commande à livrer)  
  
* **Connecteur Multi-canal** (connector + sale-channel)  
    * Module externe (OCA) pour lier Odoo à Vinted, eBay ou Discogs et centraliser les commandes provenant de plateformes, sans saisie manuelle

## 📊 Pilotage et administration : Facturation,  Tableaux de Bord

Partie cruciale pour la transparance dans l'équipe et la légalité fiscale.

![l10n_fr](img/l10n_fr.png)
* **Comptabilité simplifiée française** (l10n_fr)  
    * Configuration de la TVA à 0% (les micro-entreprises ne collectent généralement pas la TVA au début)

![account](img/account.png)
* **Facturation** (account)  
    * Génération des factures web et des rapports de vente
    * Automatise la création du "Livre des recettes" (obligation légale en micro-entreprise) et simplifie le calcul du CA brut pour les déclarations URSSAF
 
![aboardt](img/board.png)
* **Tableaux de Bord** (board) 
    * Visualisation des performances.
    * Création de graphiques sur mesure pour suivre la rentabilité réelle et la répartition des bénéfices

## 🎨 Ergonomie & Design

* **"Web Responsive"** (OCA) 
    * Module externe (OCA) qui remplace le menu classique par une icône "App Drawer" de la version entreprise
 


<div align="center">

[![Précédent](https://img.shields.io/badge/⬅️%20Précédent-blue)](./15-VersionOdoo.md)
[![Sommaire](https://img.shields.io/badge/🏠%20%20%20Sommaire-gray)](../README.md#sommaire)
[![Suivant](https://img.shields.io/badge/Suivant%20%20%20%20➡️-blue)](../README.md#sommaire)

</div>

