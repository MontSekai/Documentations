---
tags:
  - Systeme
  - Active Directory
  - Windows
  - FSMO
---

# Rôles FSMO (Flexible Single Master Operations)

Dans un environnement **Active Directory multi-contrôleurs**, toutes les modifications ne peuvent pas être réalisées sur n'importe quel DC (Domain Controller / Contrôleur de Domaine) en même temps, sous peine de conflit. C'est pourquoi Microsoft a défini 5 rôles spéciaux, appelés **rôles FSMO** (prononcer "Fismo"), dont chacun est attribué à **un seul DC à la fois** dans sa portée.

## Les 5 rôles FSMO

### Au niveau de la Forêt (1 seul dans toute la forêt)

Ces deux rôles sont **uniques dans toute la forêt AD**, et résident par défaut sur le premier DC installé dans la forêt.

#### 1. Schema Master (Maître du Schéma)

> **Le seul DC autorisé à modifier la structure de l'annuaire.**

Le schéma AD est le "dictionnaire" qui définit tous les types d'objets et leurs attributs (ex : ajouter un attribut "NuméroEmployé" sur un objet Utilisateur). Ce rôle n'est sollicité que lors de modifications du schéma, par exemple lors de l'installation d'Exchange Server ou de l'élévation du niveau fonctionnel.

#### 2. Domain Naming Master (Maître d'Attribution des Noms de Domaine)

> **Le seul DC autorisé à ajouter ou supprimer des domaines dans la forêt.**

Il garantit l'unicité des noms de domaines au sein de la forêt et doit être accessible lors des opérations d'ajout/suppression de domaine.

---

### Au niveau du Domaine (1 par domaine)

Ces trois rôles sont **présents dans chaque domaine** de la forêt.

#### 3. PDC Emulator (Émulateur PDC)

> **Le DC le plus important du domaine au quotidien.**

C'est le couteau suisse des rôles FSMO. Ses responsabilités :
* **Source de temps (NTP)** : Référence de temps pour tous les membres du domaine. Kerberos exige une horloge synchronisée (tolérance de 5 min max).
* **Changements de mots de passe** : Receveur prioritaire des changements de mots de passe et arbitre des verrouillages de comptes en temps réel.
* **Compatibilité rétrograde** : Émule le comportement d'un vieux contrôleur primaire NT4 pour les systèmes anciens.
* **Mise à jour des GPO** : Point d'édition central des stratégies de groupe.

#### 4. RID Master (Maître des RID - Relative Identifiers)

> **Le DC qui alloue les pools d'identifiants uniques.**

Chaque objet AD (utilisateur, groupe, ordinateur…) possède un identifiant unique appelé **SID** (*Security IDentifier*). La partie variable du SID est le **RID**. Le RID Master attribue des "blocs" de RID disponibles (ex : 1000 RID à la fois) à chaque DC qui en fait la demande, afin d'éviter les doublons lors de la création d'objets.

#### 5. Infrastructure Master (Maître d'Infrastructure)

> **Le DC qui maintient les références croisées inter-domaines.**

Dans une forêt multi-domaines, il gère la cohérence des références entre les objets de différents domaines (ex : un utilisateur du domaine A membre d'un groupe du domaine B).

> [!IMPORTANT]
> Dans un domaine **à DC unique**, ou si **tous les DC sont des Catalogues Globaux**, le rôle Infrastructure Master n'a pas d'importance car l'information est déjà universellement disponible.

## Résumé et criticité

| Rôle FSMO | Portée | Criticité si absent | Impact immédiat si HS |
| :--- | :---: | :---: | :--- |
| **Schema Master** | Forêt | Faible | Impossible de modifier le schéma |
| **Domain Naming Master** | Forêt | Faible | Impossible d'ajouter/supprimer des domaines |
| **PDC Emulator** | Domaine | **Très Haute** | Problèmes d'auth, GPO, blocages de comptes |
| **RID Master** | Domaine | Moyenne | Stock de RID épuisé → création d'objets impossible |
| **Infrastructure Master** | Domaine | Faible (cas simples) | Références inter-domaines obsolètes |

## Commandes utiles

```powershell
# Afficher les 5 rôles FSMO du domaine actuel
netdom query fsmo

# Transférer un rôle FSMO via PowerShell (ici le PDC Emulator vers DC02)
Move-ADDirectoryServerOperationMasterRole -Identity "DC02" -OperationMasterRole PDCEmulator

# Lister tous les rôles (via AD Module)
Get-ADDomain | Select-Object PDCEmulator, RIDMaster, InfrastructureMaster
Get-ADForest | Select-Object SchemaMaster, DomainNamingMaster
```
