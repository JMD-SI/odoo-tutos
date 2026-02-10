# ✅ Version de Odoo


## 🦄 Un "petit" avec plein de potes devenu cador de la cour d'école  

En 2002, Fabien Pinckaers, un jeune belge de 23 ans, crée TinyERP. Ce "petit" logiciel 100% Open Source et modulaire souhaite offrir une alternative gratuite aux logiciels de gestion (ERP) ultra-chers de l'époque.     

Grâce à un développement continu, le logiciel gagne en robustesse et en popularité. En 2008, il est renommé OpenERP. Un réseau solide de partenaires intégrateurs se structure et le modèle économique s'affine : le logiciel reste gratuit, mais les services associés (installation, formation, support) deviennent payants.    

En 2014, la solution change de nom pour Odoo et devient une suite d'applications complète (Site web, Marketing, E-commerce, RH). C'est aussi le passage à une philosophie "Open Core" : une base gratuite et libre (Odoo Community) est enrichie par une version commerciale (Odoo Enterprise) disposant de fonctionnalités avancées.  

Autour du "coeur" Open Source de l'application, une immense communauté de développeurs a enrichi Odoo de milliers de modules supplémentaires. Pour pérenniser cette liberté, l'association OCA (Odoo Community Association) s'est constituée comme "garde-fou" face à Odoo SA : elle veille à ce que les fonctionnalités essentielles restent accessibles gratuitement et garantit un standard de qualité élevé pour les modules distribués par la communauté.  

Aujourd'hui, Odoo est une "licorne" valorisée à plusieurs milliards d'euros. L'entreprise emploie plus de 4 000 salariés pour accompagner plus de 12 millions d'utilisateurs à travers le monde. Chaque année, une nouvelle version majeure vient enrichir cet écosystème.  
 
## 🧬 Choisir une version de Odoo  
 
 Comme souvent en informatique, le choix de la version va s'axer autour de quelques sujets clés :
* La structure de l'entreprise : une ou plusieurs entités juridiques, type de comptabilité, résponsabilités legales ...
* Le niveau de spécificité de mon besoin : Spécificités et exigences metiers importantes avec process particuliers  
* Nombre d'utilisateurs : seuls les metiers clef ou tout le monde ... Les réalités économiques  
* La capacité à gerer et deployer un changement par les équipes : "utilisateurs" éparpillés / peu disponibles / peu disciplinés ou peu enclin à s'adapter ... 
* La necessité d'interactions entre Odoo et d'autres systemes numériques : interconnections avec applications/meteriels tiers, accès direct aux donénes ... 
* Besoin de souveraineté, confidentialité et de contôle 
* Niveau de maîtrise technique en interne 
* Le deploiement doit il etre rapide ? Peut il etre progressif ?
 
  
La réponse à ces quelques questions conditionne ainsi :
* l'édition de Odoo choisie : Community, Standard ou Custom
* le type d'accompagnement necessaire : architecte, fonctionnel, technique, developpeur, formateur ...
* L'hebergement et les interactions : interne/cloud/Saas et utilisation de l'API/Accés direct à la BD
* Les modules à installer : apps de base, apps officielles ou apps customs/exotiques
  
 
## 🔧 Stratégie de mise à jour & Maintenance
Odoo est très réactif et sort une nouvelle version majeure chaque année en octobre. Si c'est un vrai plus fonctionnellement, cela peut devenir un défi technique pour les administrateurs et les développeurs.  

Chaque nouvelle version fait évoluer le "coeur" du système, ce qui impacte la structure de la base de données (champs modifiés, supprimés ou déplacés) et potentiellement la compatibilité de vos modules.  

Pour les utilisateurs en ligne (SaaS) limités aux apps officielles, ces évolutions sont automatisées et transparentes.  

Par contre, dès que des modules tiers ou spécifiques sont installés, la prudence est de mise : 
* Ne pas se précipiter sur la version qui vient de sortir ! Il est préferable d'attendre quelques mois pour que les bogues de jeunesse soient corrigés et que les mainteneurs de modules (comme l'OCA) aient adapté leur code.
* Odoo supporte les 3 dernières versions stables. Upgrader une version sur deux est le rythme idéal pour bénéficier des nouveautés sans s'épuiser techniquement.
* Une migration de version est délicate et elle doit être considéré comme un projet à part entière.
* Utiliser un serveur de test en parallèle pour valider les processus avant la bascule réelle et surtout ne pas oublier le backup ET le test de restauration ... (Mais vous savez 😉).
* Biens sur, pas de changement de version en fin d'année fiscale ... (une histoire de comptables, de séquestration et de pneus de voiture ...)

Début 2026, moment ou j'ecris ceci, la meilleure version à installer est donc la version 18 (même si la v.19 est là !).
 


## 📋 Synthese

|                             |Community                    |Entreprise "Standard"      |  Entreprise "Custom" Saas |  Entreprise "Custom"      |    
|:----------------------------|:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:| 
|Multi/Societé				  |           ✅                |          🚫                 |          🚫                 |✅✅✅
|Besoins spécifiques		  |        ✅✅✅                   |          🚫               |            🚫             |		✅✅
|Customisation			  |                ✅✅✅           |              ✅         |                  ✅       |	✅✅
|Interconnections tierces	  |          ✅✅                 |          ✅                |          ✅                |		✅✅✅	
|Souveraineté				  |           ✅✅✅                |           🚫                |            🚫               | ✅✅
|Rapidité			    |            ⚠️               |             ✅✅✅         |                  ✅✅       |	✅
|Besoin de maitrise technique	  |       ⚠️⚠️⚠️                    |               🚫            |                🚫           |		⚠️⚠️	
|Besoin de maitrise fonctionelle	  |       ✅✅✅                    |               ✅            |                ✅✅           |		✅✅	
|Support technique officiel	  |           🚫                |              ✅✅✅             |         ✅✅✅                 |✅✅
|Gestion des evolutions     |⚠️⚠️⚠️|✅✅✅|✅✅|✅|
|Conformité RGPD |        ⚠️⚠️                   |              ✅✅✅            |        ✅✅✅                  |✅
|Coût licenses				  |        🚫                   |              💰💰             |         💰💰💰                  |💰💰💰
|Coût hébergement	  |            💰💰💰               |                 🚫          |                  🚫         |		entre 🚫 et 💰💰💰
|Difficulté du projet |⚠️⚠️⚠️ |✅✅|✅|⚠️|


**💡 Légende :**  
* ✅ : Adapté / Inclus
* ⚠️ : Demande une attention particulière ou des ressources externes
* 🚫 : Non disponible ou non inclus
* 💰 : Impact budgétaire (plus il y a de symboles, plus c'est coûteux)
 
 
## 💡 Conclusion

Pour des raisons de coûts évidents, la version Community 18 est la solution la plus adaptée, d'autant qu'un des trois pourra se charger de l'administration et de l'hébergement.
En effet, le cout annuel pour 3 utilisateurs serait bien plus élevé qu'un simple hébergement (150€ Vs 12*3*20€ = 720€). 


