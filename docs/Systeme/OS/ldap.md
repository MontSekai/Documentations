---
tags:
  - Systeme
  - Active_Directory
  - Protocoles
  - IAM
---

# LDAP et LDAPS

Le protocole standard pour interroger les annuaires d'entreprise.

## 1. Définition
* **LDAP (Lightweight Directory Access Protocol)** : Le protocole réseau standard mondial (ouvert et interopérable) pour interroger, chercher et modifier des annuaires de données centralisés (Il est massivement utilisé en entreprise pour interroger les listes d'utilisateurs et de mots de passe).
* **LDAPS (LDAP over SSL/TLS)** : La version sécurisée et chiffrée de LDAP.

## 2. Description / Fonctionnement
Un annuaire LDAP (comme le célèbre [Active Directory de Microsoft](ad_forets_domaines.md) ou *OpenLDAP* sous Linux) stocke l'information sous forme d'une immense arborescence (un Arbre) strictement hiérarchisée.
Pour trouver un utilisateur spécifique, le client ou l'application LDAP doit fournir une requête de recherche textuelle très formatée appelée le *Distinguished Name (DN)*.
Exemple de chemin : `CN=Raphael Hirsch, OU=Informatique, DC=mondomaine, DC=com` (*Common Name* = Raphael, *Organizational Unit* = Département Informatique, *Domain Component* = mondomaine).

**La Faille mortelle du LDAP (Port 389 TCP/UDP)** : À l'image du vieux HTTP, le protocole LDAP classique envoie les requêtes et surtout les mots de passe de tous les employés en texte clair sur le câble réseau.
**La Solution LDAPS (Port 636 TCP)** : Totalement obligatoire de nos jours, LDAPS utilise un certificat TLS pour chiffrer la communication de bout-en-bout entre l'application et le contrôleur de domaine (Le Serveur AD).

## 3. Utilisation / Cas Pratique
L'entreprise possède un grand serveur Active Directory et vient d'acheter un nouveau logiciel web de gestion de congés (ex: *Lucca* ou *Eurécia*) hébergé sur un serveur interne.
Plutôt que de forcer l'informatique à créer manuellement 500 nouveaux comptes, et forcer les 500 employés à retenir un énième mot de passe différent pour ce site web, l'administrateur système configure le site des congés pour qu'il "pointe" directement vers l'Active Directory interne via le protocole **LDAPS**. 

Quand Raphaël tape son mail et son mot de passe Windows habituel sur la page web des congés, le site web ne vérifie rien lui-même : il envoie secrètement une requête LDAPS chiffrée au serveur AD. Le serveur AD vérifie dans sa propre base de sécurité et répond au site : "Oui, le mot de passe est le bon, tu as mon autorisation pour lui ouvrir sa session !". C'est l'ancêtre du [SSO (Single Sign-On)](entra_id.md).

`Voir aussi : [Entra ID et SSO Cloud](entra_id.md) | [Forêts et Domaines AD](ad_forets_domaines.md)`
