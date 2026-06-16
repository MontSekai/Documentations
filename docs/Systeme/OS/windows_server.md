---
tags:
  - Systeme
  - OS
  - Windows
  - Active Directory
---

# Windows Server

Système d'exploitation serveur de Microsoft et fondation des rôles de l'infrastructure d'entreprise.

## 1. Définition
Windows Server est la gamme de systèmes d'exploitation (OS) de Microsoft spécifiquement destinée aux environnements serveurs d'entreprise. Il constitue la colonne vertébrale applicative de l'écrasante majorité des infrastructures IT mondiales pour la gestion des utilisateurs.

## 2. Description / Fonctionnement
Contrairement à Windows 10/11 pour les postes de travail, Windows Server est conçu pour s'exécuter en continu et fournir de nombreux services réseau natifs appelés "Rôles".
Les rôles les plus cruciaux sont :
* **AD DS (Active Directory)** : Gestion centralisée des identités, droits et accès.
* **DNS** : Résolution de noms en adresses IP (absolument indispensable à la survie de l'AD).
* **DHCP** : Distribution automatisée des IPs sur le réseau local.
* **File Server (SMB)** : Stockage, gestion des quotas et partage sécurisé de données.
* **Hyper-V** : Hyperviseur pour la création de Machines Virtuelles.

## 3. Utilisation / Cas Pratique
Lors du montage d'un nouveau réseau d'entreprise, l'administrateur installe une machine sous Windows Server. Le premier serveur est "promu" en tant que **Contrôleur de Domaine (AD DS + DNS)**. Ensuite, d'autres serveurs rejoignent ce domaine et reçoivent les rôles de Serveur de fichiers ou **RDS** (accès à un bureau à distance pour le télétravail des employés). Le rôle **WSUS** est aussi très souvent déployé pour centraliser, tester et maîtriser la distribution des correctifs de sécurité (Patchs) sur le parc de PC.

## 4. Modifications possibles / Alternatives
L'alternative historique et écrasante à Windows Server est le monde **Linux**, qui domine le marché de l'hébergement web public (Apache, Nginx) et des conteneurs Cloud. 
Cependant, pour la gestion stricte d'un parc de PC bureautiques locaux, Active Directory sous Windows Server reste le standard incontesté. Ce modèle "On-Premise" (sur site) est toutefois progressivement concurrencé par les solutions 100% Cloud de Microsoft comme *Entra ID* (anciennement Azure AD) couplé à *Intune* (MDM).

## 5. Exemples visuels et Liens utiles

| Rôle Server | Protocole ou Standard | Utilité principale |
| :--- | :---: | :--- |
| **AD DS** | LDAP, Kerberos | Annuaire, Authentification, [GPO](gpo.md) |
| **DNS** | DNS | Résolution de noms |
| **DHCP** | DHCP | Attribution IP automatique |
| **File Server** | SMB / CIFS | Serveur de partage de fichiers |
| **Hyper-V** | Virtualisation Type 1 | Création de VMs |
| **RDS** | RDP | Bureaux à distance et Virtualisation d'applis |
| **WSUS** | HTTP/HTTPS | Mises à jour Windows centralisées |
| **IIS** | HTTP/HTTPS | Hébergement Web Microsoft |
| **NPS** | RADIUS | Authentification réseau (Wi-Fi d'entreprise) |
