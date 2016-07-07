##**_BI Project Exia CESI_**
![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/exia.png)  
#Plastic Box

###Contexte du projet:
  
La société PlasticBox™ aussi appelée PBX, créée des boites en plastiques depuis des décennies.
Avec la mondialisation et la concurrence croissante, une refonte de ses méthodes de travail est nécessaire aujourd’hui : il faut améliorer son système de production, de conditionnement et d’expédition. Avant de faire cela de façon effective, elle voudrait essayer et tester une nouvelle architecture pour son volume de données très important .

Ce sujet fait clairemennt appel à la recherche opérationnelle, dont l'analyse peut être représentée par la mind map suivante:  
![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/mind%20map.png)  

####Reccueil des besoins:  
* Création d'un générateur de données
* Réalisation d'un analyseur de données métier
* Elaboration d'un Tableau de bord (Dashboard) avec plusieurs indicateurs (modification d'architecture)
* Reprendre les 4 serveurs avec leurs 4 bases de données
* Création d'un entrepot de données
* Fabrication d'un ETL liant dashboard et couchDB

##Organisation:   

**Repartition des tâches:**  
![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/utilisateur.png)
Ce projet d'études a été réalisé par un groupe de 4 élèves de l'EXIA CESI TOULOUSE. Les compétences et les envies de chacun ont permis la répartition des tâches et des responsabilités suivantes:  
**Matrice RACI:**  
  
  
Nom de la tâche | EA | CF | TL | DVA  
--- | --- | --- | --- | ---  
Générateur de données | RA | R | I | I
Générateur de dashboard	 | I | 	I | 	R | 	RA
UML | 	RA | 	C | 	I | 	I
MySQL Préparation | 	I | 	I	 | I	 | RA
MySQL Fabrication | 	C | 	I	 | I | 	RA
MySQL Administration | 	I	 | I | 	I | 	RA
MySQL Exportation | 	C	 | I | 	I	 | RA
CouchDB SGBD | 	I	 | I | 	R | 	RA
Merise | 	C | 	C | R	 | RA
Epuration des données | 	I | 	I | 	I | 	R
Trello | 	I | 	I | 	RA | 	I
Gantt | 	C | 	RA | 	C | 	C
Github | 	A | 	I	 | R | 	I
Coggle	 | C | 	RA | 	R | 	C
Répartition des tâches | 	R | 	R	 | RA	 | R
Drive | 	I	 | I | 	RA | 	I
Matrice RACI | 	C	 | RA | 	C | 	C
VM | 	I	 | I | 	RA | 	I
Schéma infrastructure	 | I | 	I | 	R | 	RA
Définitions des indicateurs	 | R | 	R	 | RA | 	R
Mise en place des étoiles | 	I | 	I | 	RA | 	I
Création des doc (JSON) depuis CouchDB	 | R	 | C | 	RA | 	I
Définitions des dashboard	 | C	 | C	 | RA | 	R
Rapport	 | C | 	RA | 	C	 | C
Power Point | 	C | 	RA | 	C | 	C
Liens ODBC | 	RA | 	R	 | R	 | C
MySql -> CouchDB | 	C	 | C | 	RA | 	C
CouchDB -> QlickView | 	C	 | C | 	R	 | RA

Pour déterminer l'ordre de priorité des tâches ainsi qu'avoir un planning et un suivi constant, nous avons mis en place un Trello (liste des tâches en ligne et suivi) mis régulièrement à jour, ainsi que le Gantt suivant:  
**Gantt:**  


### Conception:
**Architecture Réseau:**  
L'entreprise est composé de 4 services: Administration, Exportation, Importation, Production, chacun aillant son propre serveur. La composition de chaqe service nous étant inconnus, nous avons supposé que la perspective d'évolution maximum par service serait d'environ 200 postes, chaque servie etant indépendant et invisibles des autres.  
![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/archi.PNG)  
Nous avons donc dû reprendre cette architecture réseaux, et donc calculé les plages pour nos 4 réseaux de postes mais aussi convenu d'une convention de nommage.  
Tous les appareils sur le réseau hormis les postes clients répondent à la norme suivante:  
<Type_Equipement>_<Service>_<Numéro_appareil>  
  
_les VLAN(s):_  

Service|Nom VLAN  | Numéro VLAN  | Plage IP | Masque
--- | --- | --- | --- | ---
Production | vlan_production | 10 | 192.168.10.0 | 255.255.255.0
Administration | vlan_administration | 20 | 192.168.20.0 | 255.255.255.0
Conditionnement | vlan_conditionnement | 30 | 192.168.30.0 | 255.255.255.0
Exportation | vlan_exportation | 40 | 192.168.L40.0 | 255.255.255.0  

les 11 premières adresses de chaque plage réseau étant réservés par le service informatique, nous obtenons 244 adresses libres par VLAN.  

_Les Serveurs:_  
Chaque service disposant d'un serveur de données, nous avons respecté notre convention de nommage mais aussi la règle suivante: tout serveur stockant de la donnée propre aux activités de l'entreprise doit être compris entre une adresse IP "192.168.XX.5" et "192.168.XX.9".  
Dans le but d'éviter une redondance inutile, nous ne disposons que d'un serveur DNS et DHCP.  

Service | Nom du Serveur  | IP
--- | --- | ---
Production | BDD_Production_1 | 192.168.10.5
Administration | BDD_Administration_1 | 192.168.10.5
Administration | DHCP/DNS_Administration_1 | 12.168.10.10
Conditionnement | BDD_Conditionnement_1 | 192.168.10.5
Exportation | BDD_Exportation_1 | 192.168.10.5  

_Routage Inter-Vlan_  
Ne disposant que d’un service DHCP à l’intérieur de l’entreprise, il a fallu crée un routage inter-vlan.Nous sommes partis sur des routeurs disposant au minimum de 4 ports (10 dans notre POC ci dessous).Cette ensemble de routeur a permis de mettre en place un routeur logique grâce à la technologie de VRRP  
![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/PT.png)    

_le routeur Virtuel_  
Plusieurs technologies permettent de créer un routeur virtuel malheureusement aucune n’est disponible sur cette version de packet tracer (la version 6 ayant un bug sur le sujet).  
Dans l’onglet bleu du schéma réseaux, on remarque deux routeurs physiques.
La technologie  HSRP/VRRP/ permet d’avoir de la redondance de routeur et de pouvoir répondre à cette constante

que chaque gateway possède.  

**Merise:**  
Nous avons réalisés les 4 bases de données suivantes:  

**_Administration:_**    
![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/MLD_Administration.JPG)  
La base de données "Administration" regroupe l'ensemble des tables de commandes et de catalogue  

**_Conditionnement:_**      
![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/MLD_Conditionnement.JPG) 
La base de données "Conditionnement" regroupe l'ensemble des tables qui concernent le conditionnement et les commandes

**_Expedition:_**      
![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/MLD_Expedition.JPG)  
La basee de données "Expedition" regroupe l'ensemble des tables de commandes et des clients

**_Fabrication:_**       
![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/MLD_Fabrication.JPG)  
La base de données "Fabrication" regroupe l'ensemble des tables de fabrication, des pieces et de maintenance


**UML:**    

![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/Component_v1.0%20(2).PNG)

![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/UseCase_v1.1.PNG)

![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/Class_v1.0.PNG)


**Moke-Up de l'application:**      
![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/Mokeup.PNG)  
Pour faire varier les données simulées par le générateur, nous allons modifier:
* La variance d'un mois à l'autre entre - 15 et 15 % (choisi grâce au slider)
* La quantité initiale de commandes (entrée par l'utilisateur)
* La taille des lots commandés (choix entre 10, 15 et 20 dans une liste déroulante)
* La date de début de la simulation (choix avec le calendrier. La simulation commande 1 mois avant la date choisi et se fini 2 mois plus tard).    

**Les indicateurs:**  

Sachant que les indicateurs sont des outils d’aide à la prise de décision et de pilotage il est nécessaire de réduire leurs nombres et de sélectionner les plus pertinents. Nous partirons sur 10 indicateurs par Dashboard.
Dans une base de données CouchDB le format sera le Document en JSON afin de garder de la flexibilité sur la donnée.  

5 tableaux de bords donneront une vision de l’activité de l’entreprise. Qualité contiendra des indicateurs sur la satisfaction des clients en fonction par exemple de délai, de la qualité des produits, de leurs pays etc. … Production sera centré sur les matériaux, les conditionnements les produits et les pièces. Echéance sur les dates d’expédition, de commandes les temps de production. Vente sur les volumes de ventes au cours du temps, la rentabilité des produits. Maintenance sur les anomalies, temps de maintenant en fonction des produits ou du temps.  

* Qualité (satisfaction / client)
 * Évolution de la satisfaction
 * Satisfaction moyenne
 * Taux d’annulation
 * Rapport satisfaction / produit
 * Rapport satisfaction / pays
 * Rapport satisfaction / pièces
 * Rapport satisfaction / Ligne d’assemblage
 * Rapport satisfaction / taux de pannes
 * Rapport satisfaction / Date
 * Rapport prix / satisfaction
* Production
 * Évolutions des stocks
 * Stocks moyens produits
 * Répartition stock / produit
 * Répartition stock / pays
 * Répartition stock / pièces
 * Répartition stock / Commande
 * Nombre de produit fabriqué
 * Durée moyenne de production
* Échéance
 * Différence date commande date livraison 
 * Temps de production moyen
 * Temps de livraison moyen
 * Rapport satisfaction temps de livraison
 * Taux de rupture de prod
* Vente
 * Évolutions des ventes 
 * Répartition produits / CA
 * Répartition produits / clients
 * Répartition pays / CA
 * Répartition produits / Pays
 * Répartition pièce / CA
 * Répartition MP / CA
 * Répartition des produits vendus / jour
 * Répartition des pièces vendus / jour
 * Correspondance des produits
* Maintenance
 * Taux de panne
 * Créneau des pannes
 * Rapport satisfaction / pannes


**Choix des outils:**  

Ce projet a été réalisé en C# avec l'utilisation de Visual Studio 2015.  
Les différents serveurs ont été simulé grâce à des VM de Windows 7 Pro avec l'aide de [Virtual box](https://www.virtualbox.org/)  
Les bases de données ont été créées avec [MySQLServeur](https://dev.mysql.com/downloads/mysql/)  
Notre base de donnée a été stocké avec [CouchDB](http://couchdb.apache.org/)  
Notre ETL avec [Talend](https://fr.talend.com/products/big-data)  
Le Dashboard (ou tableau de bord) a été réalisé à l'aide de [QlickView](http://www.qlik.com/products/qlikview)  
Pour générer une partie de table de jeu de données nous avons utilisé [Generatedata](http://www.generatedata.com/#generator)  

###Code:      
Le code de notre application est récupérable [Ici](https://github.com/Heavyshield/PlasticBox)

###Bilan de groupe:  

Le scope du projet a été affiné en cours de projet 
Temps assez rapide
Choix libre des techno et outils utilisé donc c'etait sympa quand mm
projet avec plein de domaines d'informatique demande + gestion + analyse
