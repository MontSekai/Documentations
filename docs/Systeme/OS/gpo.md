---
tags:
  - System
  - Windows
  - Active Directory
  - GPO
---

# GPO (Group Policy Object)

Le cœur de l'administration centralisée dans un environnement Microsoft Active Directory.

## 1. Définition
Les **Stratégies de Groupe (GPO)** sont des règles configurées sur un contrôleur de domaine Active Directory, permettant d'imposer à distance et massivement des paramètres de configuration aux ordinateurs et aux utilisateurs du réseau.

## 2. Description / Fonctionnement
Une GPO est divisée en deux sections :
1. **Configuration Ordinateur** : Modifie la base de registre `HKEY_LOCAL_MACHINE`. S'applique à l'ordinateur, peu importe qui se connecte. S'exécute au démarrage de la machine.
2. **Configuration Utilisateur** : Modifie la base de registre `HKEY_CURRENT_USER`. S'applique au profil utilisateur, peu importe le PC. S'exécute à l'ouverture de session de l'utilisateur.

L'ordre d'application suit le modèle **LSDOU** (Local, Site, Domaine, Unité Organisationnelle). En cas de conflit, c'est la dernière appliquée (l'OU la plus proche) qui gagne et écrase la précédente.

## 3. Utilisation / Cas Pratique
Les GPO servent à standardiser l'environnement de travail :
* Déployer automatiquement une imprimante réseau.
* Déployer silencieusement un logiciel (fichier d'installation MSI).
* Imposer un fond d'écran d'entreprise.
* Bloquer l'accès au Panneau de configuration ou fixer la politique de complexité des mots de passe.

## 4. Modifications possibles / Alternatives

### Modèles d'administration (ADMX / ADML)
Les fichiers ADMX/ADML permettent d'étendre les capacités natives des GPO pour contrôler des applications tierces (ex: Google Chrome, Mozilla Firefox). Placés dans le "Magasin Central" du contrôleur de domaine (`SYSVOL\policies\PolicyDefinitions`), ils ajoutent des menus spécifiques dans l'éditeur GPO.

### Cas Pratique : Gestion des extensions navigateur
En utilisant les ADMX de Google Chrome, on peut créer une GPO qui force de manière transparente l'installation d'un bloqueur de publicité (ex: uBlock Origin) sur tous les postes, et qui interdit l'installation d'extensions non validées (Whitelisting) pour prévenir la fuite de données (DLP).

## 5. Exemples visuels et Liens utiles

**Outils et Commandes indispensables :**
* `gpmc.msc` : La console graphique pour créer et lier les GPO.
* `gpupdate /force` : Commande à lancer sur un PC pour le forcer à télécharger immédiatement les dernières GPO.
* `gpresult /r` : Affiche quelles GPO sont appliquées (ou refusées) sur le PC cible.
