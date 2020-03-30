Pi Swarm Cluster
=========

Ce projet met à disposition un ensemble de scripts permettant de déployer un cluster Docker Swarm sur un ensemble de Raspberry Pi.

Les groupes
-----------

* Leader  : Leader au sens Swarm du terme
* Manager : Manager au sens Swarm du terme
* Worker  : Worker au sens Swarm du terme
* Data    : Ensemble des hôtes pouvant lire et écrire dans volume-shared (Volume Gluster)
		  ( => tous les workers )
		  
Minetest : Hôte accueillant l'instance unique de minetest (volume-shared trop lent pour que minetest puisse être volatile. L'espace de travail est donc défini dans volume-local)

Rôle "system" (group: all)
-------------

* Mise à jour des packages 
* Mise à jour du nom d'hôte
* Mémoire GPU fixée à 16M
* Désactivation de la sortie hdmi au démarrage

Rôle "docker" (group: all)
-------------

* Installation des dépendances
* Installation de Docker

Rôle "swarm-leader" (group: leader)
-------------------

* Initialisation du cluster Swarm sur l'host défini en leader
* Déploiement du service 'Docker Swarm Visualizer' sur le leader

Rôle "swarm-manager" (group: manager)
--------------------

Rôle "swarm-worker" (group: worker)
-------------------

* Attachement du node au leader
* Création du volumne "volume-local" non partagé

Rôle "gluster" (group: data)
--------------

* Installation des dépendances
* Installation de Gluster
* Création du volume "volume-shared" partagé par les participants au groupe data
