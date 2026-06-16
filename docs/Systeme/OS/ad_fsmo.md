---
tags:
  - Systeme
  - Active Directory
  - Windows
  - FSMO
---

# Rôles FSMO (Flexible Single Master Operations)

Les 5 rôles uniques garantissant la cohérence de l'Active Directory.

## 1. Définition
Dans un environnement Active Directory composé de multiples contrôleurs de domaine, certaines opérations critiques ne peuvent pas être effectuées simultanément par plusieurs serveurs sous peine de créer de graves conflits de base de données. Microsoft a défini 5 rôles spéciaux, appelés **FSMO**, qui sont obligatoirement détenus par un seul et unique contrôleur de domaine (DC) à la fois.

## 2. Description / Fonctionnement

**Niveau Forêt (1 seul par forêt dans tout le réseau) :**
1. **Schema Master** : Le seul autorisé à modifier la structure de la base de données de l'AD (le schéma).
2. **Domain Naming Master** : Le seul autorisé à ajouter ou supprimer des domaines dans la forêt.

**Niveau Domaine (1 présent dans chaque domaine) :**
3. **PDC Emulator** : Le "couteau-suisse". Gère la synchronisation de l'heure (NTP), reçoit en urgence les changements de mots de passe pour éviter les refus de connexion, et gère les verrouillages de comptes.
4. **RID Master** : Distribue des blocs d'identifiants uniques (SID/RID) aux autres serveurs pour qu'ils puissent créer de nouveaux objets (utilisateurs, PC) sans faire de doublons.
5. **Infrastructure Master** : Maintient les références croisées des objets entre plusieurs domaines (ex: un utilisateur du domaine A membre d'un groupe du domaine B).

## 3. Utilisation / Cas Pratique
L'administrateur interagit et dépend énormément du **PDC Emulator** au quotidien : si ce serveur tombe en panne, des désynchronisations d'horloge apparaissent sur le réseau (ce qui rend l'authentification Kerberos impossible) et les verrouillages/déverrouillages de mots de passe deviennent aléatoires.

## 4. Modifications possibles / Alternatives
En cas de panne matérielle définitive du contrôleur hébergeant un rôle FSMO, l'administrateur doit effectuer un **"Seize" (Saisie forcée)** du rôle pour l'attribuer à un DC survivant. Si l'ancien serveur réapparaît par la suite, il devra être détruit et formaté sans jamais être reconnecté au réseau.
En temps normal, on peut faire un **"Transfer"** (Transfert propre) des rôles avant d'éteindre un vieux serveur prévu pour le recyclage.

## 5. Exemples visuels et Liens utiles

| Rôle FSMO | Portée | Criticité de la panne | Impact immédiat |
| :--- | :---: | :---: | :--- |
| **Schema Master** | Forêt | Faible | Impossible d'étendre le schéma (ex: installation d'Exchange) |
| **Domain Naming** | Forêt | Faible | Impossible d'ajouter/supprimer un domaine |
| **PDC Emulator** | Domaine | **Très Forte** | Problèmes GPO, heure, mots de passe |
| **RID Master** | Domaine | Moyenne | Création d'objets impossible une fois le pool local épuisé |
| **Infrastructure** | Domaine | Faible | Références inter-domaines obsolètes |

**Commandes utiles :**
```powershell
# Afficher la liste des serveurs hébergeant les 5 rôles FSMO
netdom query fsmo

# Transférer proprement le rôle PDC vers le serveur DC02
Move-ADDirectoryServerOperationMasterRole -Identity "DC02" -OperationMasterRole PDCEmulator
```
