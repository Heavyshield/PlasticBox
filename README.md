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
* Création d'un entrepot de données et d'un ETL liant dashboard et la couchDB

##Organisation:   

**Repartition des tâches:**  
![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/utilisateur.png)
Ce projet d'études a été réalisé par un groupe de 4 élèves de l'EXIA CESI TOULOUSE. Les compétences et les envies de chacun ont permis la répartition des tâches et des responsabilités suivantes:  
**Matrice RACI:**  
Pour déterminer l'ordre de priorité des tâches ainsi qu'avoir un planning et un suivi constant, nous avons mis en place un Trello (liste des tâches en ligne et suivi) mis régulièrement à jour, ainsi que le Gantt suivant:
**Gantt:**  


### Conception:
**Architecture Réseau:**  
L'entreprise avait déja mis en place un système de base de données et de réseaux:  
![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/archi.PNG)
**Merise:** 
Nous avons réalisés les 4 bases de données suivantes:  
>images des 4 base + commentaires
**UML:**  
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

Ce projet a été réalisé à l'aide de plusieurs VM de Windows 7 Pro avec l'aide de virtual box: [(https://www.virtualbox.org/)]
Les bases de données ont été créées avec MySQLServeur: [(https://dev.mysql.com/downloads/mysql/)]
Le langage de développement est le C#
CouchDB
Talente pour l'ETL
QlickView pour le dahsboard

###Code:      
Le code de notre application est récupérable [Ici](https://github.com/Heavyshield/PlasticBox)

###Bilan de groupe:  

Le scope du projet a été affiné en cours de projet 
Temps assez rapide
Choix libre des techno et outils utilisé donc c'etait sympa quand mm
projet avec plein de domaines d'informatique demande + gestion + analyse
