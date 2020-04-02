Pi Swarm Cluster
=========

Ce projet met à disposition un ensemble de scripts permettant de déployer un cluster Docker Swarm sur un ensemble de Raspberry Pi.

Les groupes
-----------

* Leader  : Leader au sens Swarm du terme
* Manager : Manager au sens Swarm du terme
* Worker  : Worker au sens Swarm du terme
* Minetest : Hôte accueillant l'instance unique de minetest

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
* Création du volume "volume-local" non partagé
* Création du volume "volume-share" partagé entre les workers :
  * Installation des dépendances
  * Installation de Gluster
