##**_BI Project Exia CESI_**
#Plastic Box

  
>image du pointeur    

###Contexte du projet:
  
La société PlasticBox™ aussi appelée PBX, créée des boites en plastiques depuis des décennies.
Avec la mondialisation et la concurrence croissante, une refonte de ses méthodes de travail est nécessaire aujourd’hui : il faut améliorer son système de production, de conditionnement et d’expédition. Avant de faire cela de façon effective, elle voudrait essayer et tester une nouvelle architecture pour son volume de données très important .

###Reccueil des besoins:  
* Création d'un générateur de données
* Réalisation d'un analyseur de données métier
* Elaboration d'un Tableau de bord (Dashboard) avec plusieurs indicateurs (modification d'architecture)
* Reprendre les 4 serveurs avec leurs 4 bases de données
>image calendrier ?  

###Organisation:  
**Repartition des tâches:** 
![](https://github.com/Heavyshield/PlasticBox/blob/master/annexe/utilisateur.png)
Ce projet d'études a été réalisé par un groupe de 4 élèves de l'EXIA CESI TOULOUSE. Les compétences et les envies de chacun ont permis la répartition des tâches et des responsabilités suivantes:  
**Matrice RACI:**  
Pour déterminer l'ordre de priorité des tâches ainsi qu'avoir un planning et un suivi constant, nous avons mis en place un Trello (liste des tâches en ligne et suivi) mis régulièrement à jour, ainsi que le Gantt suivant:
**Gantt:**  
>image reflexion  

###Conception:
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
>image outil  
###Choix des Outils:
Ce projet a été réalisé à l'aide de plusieurs VM 
>image console  
###Code:  

