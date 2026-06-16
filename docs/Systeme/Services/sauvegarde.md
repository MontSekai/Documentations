---
tags:
  - Systeme
  - Sauvegarde
  - ANSSI
  - Securite
---

# Sauvegarde

Le socle de la résilience numérique et de la continuité d'activité.

## 1. Définition
La sauvegarde informatique consiste à dupliquer et mettre en sécurité les données et systèmes d'une organisation pour pouvoir les restaurer en cas de perte (cyberattaque, ransomware, panne matérielle, erreur humaine, sinistre). 

## 2. Description / Fonctionnement
Il existe plusieurs méthodes de sauvegarde :
* **Complète** : Copie intégrale de toutes les données. Très longue à réaliser, mais restauration très simple et rapide.
* **Incrémentale** : Copie uniquement les modifications depuis la *dernière sauvegarde* (complète ou incrémentale). Très rapide à exécuter, mais restauration plus longue (il faut reconstruire toute la chaîne).
* **Différentielle** : Copie les modifications depuis la *dernière complète*. C'est un bon équilibre entre temps de sauvegarde et de restauration.
* **Snapshot** : Image instantanée de l'état d'une VM. Attention : ce n'est pas une vraie sauvegarde externe.

## 3. Utilisation / Cas Pratique
L'[ANSSI](../Cybersecurite/anssi.md) recommande fermement la **règle 3-2-1** :
* **3** copies des données.
* Sur **2** supports physiques différents (ex: Disque et Bande, ou NAS et Cloud).
* Dont **1** copie hors-site (externalisée géographiquement).

Pour les environnements critiques, on ajoute le "1-0" : **1** copie immuable (inaltérable par les ransomwares), et **0** erreur lors des tests réguliers de restauration.

## 4. Modifications possibles / Alternatives
La sauvegarde alimente le **[PRA (Plan de Reprise d'Activité)](../Cybersecurite/pca_pra.md)**. 
Il faut la différencier du **PCA (Plan de Continuité d'Activité)** qui, lui, s'appuie sur de la redondance en temps réel (cluster actif/actif) pour maintenir le service sans coupure.
La stratégie de sauvegarde est définie par les métiers grâce au **RPO** (Perte de données maximale acceptable en heures) et au **RTO** (Temps de restauration maximal acceptable).

## 5. Exemples visuels et Liens utiles
**Outils de référence sur le marché :**
* Veeam Backup & Replication (Le standard absolu pour la virtualisation VMware/Hyper-V).
* Acronis Cyber Protect.
* Proxmox Backup Server (PBS).

*Lien utile :* Le guide ANSSI "Recommandations sur la sauvegarde des systèmes d'information".
