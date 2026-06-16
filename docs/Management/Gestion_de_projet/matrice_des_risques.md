---
tags:
  - Management
  - Gestion_de_projet
  - Risques
---

# Matrice des risques

Outil d'analyse permettant d'évaluer et de hiérarchiser les risques identifiés sur un projet.

## 1. Définition
La matrice des risques est un outil visuel d'analyse permettant d'évaluer et de hiérarchiser les risques identifiés sur un projet ou une architecture, en croisant leur probabilité d'occurrence avec la gravité de leur impact.

## 2. Description / Fonctionnement
On définit d'abord une échelle de **Probabilité** (ex: 1=Rare à 4=Très probable) et une échelle d'**Impact** (ex: 1=Mineur à 4=Catastrophique). 
Le produit de ces deux valeurs (Probabilité x Impact) donne un **Score de Criticité**. Ce score est généralement coloré :
* **Vert** : Risque acceptable.
* **Jaune/Orange** : Risque modéré nécessitant une surveillance.
* **Rouge** : Risque inacceptable, nécessitant un plan d'action immédiat.

## 3. Utilisation / Cas Pratique
Elle est indispensable lors du lancement d'un grand projet informatique ou lors d'un audit de sécurité (ex: norme ISO 27005). Elle permet au comité de direction de comprendre instantanément quels sont les 3 ou 4 risques majeurs qui pourraient détruire le projet.

## 4. Modifications possibles / Alternatives
Face à un risque, l'entreprise doit choisir une **stratégie de remédiation** parmi quatre choix possibles :
1. **Accepter** : Le risque est faible, le corriger coûterait plus cher que le subir.
2. **Atténuer / Réduire** : Mettre en place des actions pour baisser la probabilité ou l'impact (ex: Installer un anti-virus, prévoir un serveur de rechange).
3. **Transférer** : Faire porter le risque financier à un tiers (ex: Prendre une assurance, sous-traiter au Cloud).
4. **Éviter** : Annuler carrément l'activité qui porte le risque.

## 5. Exemples visuels et Liens utiles

### Matrice des Risques (Technique & Projet)

Voici une représentation classique 4x4 croisant la probabilité et l'impact :

| Probabilité \ Impact | 1 - Mineur | 2 - Modéré | 3 - Majeur | 4 - Catastrophique |
| :--- | :---: | :---: | :---: | :---: |
| **4 - Très probable** | 🟡 Moyen (4) | 🟠 Élevé (8) | 🔴 Critique (12) | 🔴 Critique (16) |
| **3 - Probable**     | 🟢 Faible (3) | 🟡 Moyen (6) | 🟠 Élevé (9) | 🔴 Critique (12) |
| **2 - Peu probable** | 🟢 Faible (2) | 🟡 Moyen (4) | 🟡 Moyen (6) | 🟠 Élevé (8) |
| **1 - Rare**         | 🟢 Faible (1) | 🟢 Faible (2) | 🟢 Faible (3) | 🟡 Moyen (4) |

### Tableau de Remédiation / Solution

Une fois les risques classés dans la matrice, ils doivent être consignés dans un registre avec un plan de remédiation :

| ID | Description du Risque | Criticité (Score) | Stratégie choisie | Plan de Remédiation (Solution) | Responsable |
| :---: | :--- | :---: | :--- | :--- | :--- |
| R01 | Retard de livraison du serveur physique | 🔴 12 | Atténuer | Louer temporairement un serveur Cloud en attendant la livraison. | Chef de projet |
| R02 | Fuite de données due à un mot de passe faible | 🔴 16 | Éviter | Imposer l'authentification MFA et des mots de passe robustes (GPO). | RSSI |
| R03 | Absence pour maladie d'un développeur clé | 🟡 6 | Accepter / Atténuer | Prévoir un binôme sur le code critique (Pair Programming). | Lead Tech |
| R04 | Incendie détruisant le datacenter principal | 🟠 8 | Transférer | Souscrire une assurance et mettre en place un [PRA](../../Cybersecurite/pca_pra.md) sur un site distant. | DSI |

Pour des exemples approfondis et des templates excel, consultez le [Blog de la Gestion de Projet (BDGP)](https://blog-gestion-de-projet.com/).
