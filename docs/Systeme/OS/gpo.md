---
tags:
  - System
  - Windows
  - Active Directory
  - GPO
---

# GPO (Group Policy Object)

Les **Stratégies de Groupe** (Group Policy) sont le cœur de l'administration centralisée dans un environnement Microsoft [Active Directory](ad_forets_domaines.md). Elles permettent de configurer, à distance et massivement, les paramètres des ordinateurs et des utilisateurs du domaine.

## 1. À quoi sert une GPO ?
Une GPO est un "paquet de règles" appliquées automatiquement au démarrage du PC (Machine) ou à l'ouverture de session (Utilisateur).
* **Exemples courants** :
    * Déployer automatiquement une imprimante ou monter un lecteur réseau `Z:`.
    * Imposer un fond d'écran d'entreprise.
    * Bloquer l'accès au Panneau de configuration (pour éviter que l'utilisateur modifie ses IP).
    * Déployer un logiciel MSI en arrière-plan.
    * Configurer les règles du pare-feu Windows, créer des raccourcis sur le bureau, paramétrer la politique de mot de passe du domaine (longueur, complexité).

## 2. Les deux cibles d'une GPO
Une GPO est divisée en deux grandes sections :
1. **Configuration Ordinateur** (Computer Configuration) :
    * Modifie la base de registre `HKEY_LOCAL_MACHINE`.
    * S'applique à l'ordinateur, *peu importe l'utilisateur qui s'y connecte*.
    * S'exécute au (re)démarrage de la machine Windows.
2. **Configuration Utilisateur** (User Configuration) :
    * Modifie la base de registre `HKEY_CURRENT_USER`.
    * S'applique au profil de l'utilisateur concerné, *peu importe sur quel ordinateur du domaine il se loggue*.
    * S'exécute à l'ouverture de sa session Windows.

## 3. L'héritage et l'ordre d'application (LSDOU)
Les GPO s'appliquent sur les **OU (Unités Organisationnelles)**. C'est l'un des rôles majeurs du découpage d'Active Directory. L'ordre d'application des stratégies suit le modèle **LSDOU** :

1. **L**ocal (La stratégie locale de l'ordinateur de base)
2. **S**ite (Les stratégies liées au Site Active Directory — rare)
3. **D**omaine (Les stratégies liées à la racine du domaine, ex: `Default Domain Policy`)
4. **OU** (Les stratégies liées aux Unités Organisationnelles : l'OU parente, puis l'OU enfant)

> [!IMPORTANT]
> **Règle de conflit : La dernière appliquée gagne.** Une règle fixée sur une "OU Ventes" écrasera la même règle si elle était paramétrée différemment au niveau du "Domaine".

## 4. Outils et Commandes Utiles

* **GPMC (`gpmc.msc`)** : La console *Group Policy Management*, outil principal de l'administrateur pour créer, lier, sauvegarder et lister les GPO.
* `gpupdate /force` : Commande à lancer sur un PC cible pour le "forcer" à re-télécharger la dernière version des règles du serveur immédiatement (au lieu d'attendre l'intervalle régulier de 90 minutes).
* `gpresult /r` (ou `/h report.html`) : Commande indispensable de diagnostic sur un PC cible pour voir en clair la liste exacte des règles GPO qui sont appliquées (ou refusées) sur ce poste ou cet utilisateur.
* **WMI Filtering** : Permet d'appliquer une GPO selon un critère particulier plutôt qu'une OU entière (Exemple: "Appliquer cette GPO uniquement s'il s'agit d'une machine Windows 10").
