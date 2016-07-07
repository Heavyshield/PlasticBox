##**_BI Project Exia CESI_**
![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/exia.png)  
#Plastic Box

###Contexte du projet:
  
La société PlasticBox™ aussi appelée PBX, créée des boites en plastiques depuis des décennies.
Avec la mondialisation et la concurrence croissante, une refonte de ses méthodes de travail est nécessaire aujourd’hui : il faut améliorer son système de production, de conditionnement et d’expédition. Avant de faire cela de façon effective, elle voudrait essayer et tester une nouvelle architecture pour son volume de données très important .

###Reccueil des besoins:  
* Création d'un générateur de données
* Réalisation d'un analyseur de données métier
* Elaboration d'un Tableau de bord (Dashboard) avec plusieurs indicateurs (modification d'architecture)
* Reprendre les 4 serveurs avec leurs 4 bases de données


![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/CALENDAR2.png)**Organisation:**    
_Repartition des tâches:_  
![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/utilisateur.png)
Ce projet d'études a été réalisé par un groupe de 4 élèves de l'EXIA CESI TOULOUSE. Les compétences et les envies de chacun ont permis la répartition des tâches et des responsabilités suivantes:  
**Matrice RACI:**  
Pour déterminer l'ordre de priorité des tâches ainsi qu'avoir un planning et un suivi constant, nous avons mis en place un Trello (liste des tâches en ligne et suivi) mis régulièrement à jour, ainsi que le Gantt suivant:
**Gantt:**  


![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/reflexion.png)**Conception:**  
**Architecture Réseau:**  
L'entreprise avait déja mis en place un système de base de données et de réseaux:  
![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/archi.PNG)
**Merise:**  
**UML:**  
**Moke-Up de l'application:**      
![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/Mokeup.PNG)  
Pour faire varier les données simulées par le générateur, nous allons modifier:
* La variance d'un mois à l'autre entre - 15 et 15 % (choisi grâce au slider)
* La quantité initiale de commandes (entrée par l'utilisateur)
* La taille des lots commandés (choix entre 10, 15 et 20 dans une liste déroulante)
* La date de début de la simulation (choix avec le calendrier. La simulation commande 1 mois avant la date choisi et se fini 2 mois plus tard).  

![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/outils.png)**Choix des outils:**  

Ce projet a été réalisé à l'aide de plusieurs VM de Windows 7 Pro avec l'aide de virtual box: [(https://www.virtualbox.org/)]
Les bases de données ont été créées avec MySQLServeur: [(https://dev.mysql.com/downloads/mysql/)] pour un lien plus facile avec le C# et Visual Studio.

![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/terminal.png)**Code:**  

