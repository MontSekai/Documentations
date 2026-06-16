---
tags:
  - Cybersecurite
  - Authentification
  - Acces
---

# Gestion des Identités et des Accès (IAM)

## Coffre-fort de mots de passe

**Définition** : Un coffre-fort de mots de passe (ou gestionnaire de mots de passe) est un outil logiciel conçu pour stocker, gérer et sécuriser de manière centralisée les identifiants et mots de passe des utilisateurs.
**Description** : Il chiffre localement ou dans le cloud la base de données contenant les mots de passe (souvent avec AES-256). L'accès à ce coffre nécessite un "mot de passe maître" unique et très robuste, souvent couplé à une authentification multifacteur (MFA).
**Utilisation** : Il est utilisé pour générer des mots de passe forts et uniques pour chaque service, soulageant l'utilisateur de l'effort de mémorisation. En entreprise, il permet le partage sécurisé d'identifiants entre collaborateurs (ex: KeePass, Bitwarden, 1Password, Dashlane).
**Modifications possibles** : Les coffres peuvent être auto-hébergés (on-premise) pour un contrôle total des données, ou en mode SaaS. Les stratégies d'entreprise (GPO ou console d'administration SaaS) peuvent forcer des règles de complexité, auditer l'usage ou imposer l'utilisation d'une clé physique de sécurité (ex: YubiKey).

## Principe du moindre privilège

**Définition** : Le principe du moindre privilège (PoLP - *Principle of Least Privilege*) stipule que tout utilisateur, programme ou processus ne doit posséder que les droits d'accès strictement nécessaires pour accomplir ses tâches.
**Description** : C'est une règle fondamentale de la sécurité informatique. Par exemple, un employé des RH n'a pas besoin de droits administrateur sur son poste, ni d'accès aux serveurs de production.
**Utilisation** : Il est appliqué via les listes de contrôle d'accès (ACL), la gestion des rôles (RBAC - *Role-Based Access Control*), ou via des GPO. Il permet de limiter drastiquement la surface d'attaque en cas de compromission d'un compte utilisateur.
**Modifications possibles** : Le concept peut évoluer vers une approche "Just-in-Time" (JIT) où les privilèges élevés sont accordés temporairement et révoqués automatiquement à la fin d'une tâche. On peut également adopter une approche "Zero Trust" où même les accès légitimes sont vérifiés en permanence.
