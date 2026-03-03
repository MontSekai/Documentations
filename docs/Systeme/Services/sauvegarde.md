---
tags:
  - Systeme
  - Sauvegarde
  - ANSSI
  - Securite
---

# Sauvegarde et Plan de Reprise d'Activité

La sauvegarde est le socle de la **résilience numérique**. L'ANSSI et les bonnes pratiques du secteur convergent vers des règles simples mais souvent non respectées.

## La règle 3-2-1 (Recommandée par l'ANSSI)

C'est la règle minimale absolue pour toute politique de sauvegarde sérieuse :

| Chiffre | Signification |
| :---: | :--- |
| **3** | Au moins **3 copies** des données (1 originale + 2 sauvegardes) |
| **2** | Sur **2 supports différents** (ex : disque local ET NAS, ou NAS ET cloud) |
| **1** | Dont **1 copie hors-site** (externalisée géographiquement ou air-gappée) |

> [!IMPORTANT]
> L'ANSSI recommande d'aller plus loin avec la règle **3-2-1-1-0** dans les environnements critiques :
> - **1** copie **immuable** (non modifiable, protégée contre les ransomwares)
> - **0** erreur vérifiée lors des tests de restauration

## Types de sauvegardes

| Type | Description | Avantages | Inconvénients |
| :--- | :--- | :--- | :--- |
| **Complète** | Copie intégrale de toutes les données | Restauration simple | Longue, occupe beaucoup d'espace |
| **Incrémentale** | Copie uniquement les données modifiées depuis la **dernière sauvegarde** (complète *ou* incrémentale) | Rapide, peu d'espace | Restauration lente (enchaîner toutes les incrémentales) |
| **Différentielle** | Copie uniquement les données modifiées depuis la **dernière sauvegarde complète** | Restauration plus rapide qu'incrémentale | Grossit dans le temps |
| **Snapshot** | Image à un instant T du système (VM, stockage) | Instantané, très rapide | Ne remplace pas une vraie sauvegarde externe |

## Recommandations de l'ANSSI

L'ANSSI publie le guide **"Recommandations sur la sauvegarde des systèmes d'information"** dont les points clés sont :

* **Tester régulièrement les restaurations** : Une sauvegarde non testée est une sauvegarde inutile. Planifier des tests de restauration complets au minimum une fois par an, et partiels plus fréquemment.
* **Isoler les sauvegardes du réseau de production** : En cas de ransomware, si les sauvegardes sont accessibles depuis le réseau infecté, elles seront elles aussi chiffrées. Utiliser des sauvegardes **"air-gappées"** (déconnectées physiquement ou réseau).
* **Chiffrer les sauvegardes** : Surtout pour les copies externalisées ou cloud, pour protéger la confidentialité en cas de vol du support.
* **Journaliser et alerter** : Monitorer les jobs de sauvegarde et alerter en cas d'échec.
* **Définir les RTO et RPO** :

| Indicateur | Définition | Exemple |
| :--- | :--- | :--- |
| **RPO** (Recovery Point Objective) | Perte de données maximale acceptable. Jusqu'à quand peut-on remonter ? | RPO = 4h → sauvegarde toutes les 4h |
| **RTO** (Recovery Time Objective) | Durée maximale acceptable avant le retour à la normale | RTO = 8h → le système doit être restauré en 8h max |

## Plan de Reprise d'Activité (PRA) vs Plan de Continuité (PCA)

| Plan | Objectif |
| :--- | :--- |
| **PCA** (Plan de Continuité d'Activité) | Maintenir l'activité pendant la crise (redondance, basculement automatique) |
| **PRA** (Plan de Reprise d'Activité) | Rétablir l'activité *après* l'incident (restauration depuis sauvegardes) |

## Outils courants

* **Veeam Backup & Replication** : Standard de facto pour les environnements virtualisés (VMware, Hyper-V).
* **Acronis Cyber Protect** : Backup + protection contre les ransomwares intégrée.
* **Bacula / Amanda** : Solutions open-source pour les environnements Linux.
* **Windows Server Backup** : Intégré à Windows Server, basique mais natif.
* **Snapshots (NetApp, Pure Storage, VMware)** : Complément, pas un substitut à la sauvegarde externe.
