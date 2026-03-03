---
tags:
  - Systeme
  - OS
  - Windows
  - Active Directory
---

# Windows Server

Windows Server est la gamme de systèmes d'exploitation de Microsoft destinée aux serveurs d'entreprise. Il constitue la fondation de la majorité des infrastructures IT en environnement professionnel, principalement autour de l'**Active Directory (AD)**.

## Les principaux rôles et services

Un rôle Windows Server est un ensemble de fonctionnalités installables répondant à un besoin précis. Voici les plus courants en entreprise :

### Active Directory Domain Services (AD DS)

C'est **le** service central de toute infrastructure Windows. Il gère l'**annuaire d'entreprise** : l'ensemble des objets (utilisateurs, ordinateurs, groupes, imprimantes) et leurs droits d'accès aux ressources du réseau.
* **Authentification** : Valide l'identité de chaque utilisateur grâce au protocole Kerberos (ou NTLM).
* **Stratégies de Groupe (GPO)** : Permet de déployer massivement des configurations (paramètres de sécurité, logiciels, fond d'écran...) sur des milliers de postes en quelques secondes.
* **Voir aussi** : [Forêts et Domaines](ad_forets_domaines.md) · [Rôles FSMO](ad_fsmo.md) · [Types de contrôleurs AD](ad_types_dc.md)

### DNS (Domain Name System)

Sur un réseau Windows en domaine, le serveur DNS Microsoft est étroitement couplé à l'AD DS. Il enregistre automatiquement les noms et adresses des machines du domaine (enregistrements dynamiques, zone `_msdcs`). **Sans DNS fonctionnel, l'AD tombe en panne.**

### DHCP (Dynamic Host Configuration Protocol)

Distribue les adresses IP de façon automatique aux postes du réseau. Sous Windows Server, le service DHCP doit être **autorisé dans l'Active Directory** pour pouvoir démarrer, ce qui évite les serveurs DHCP pirates.

### File Server (Serveur de fichiers)

Centralise le stockage des fichiers de l'entreprise et gère les partages réseau via le protocole **SMB** (Server Message Block). Les fonctionnalités clés associées sont :
* **DFS** (Distributed File System) : Espace de noms unifié pour agréger plusieurs serveurs de fichiers.
* **FSLogix / Quotas** : Limitation de l'espace disque par utilisateur.

### Hyper-V (Hyperviseur)

Le rôle d'**hyperviseur de type 1** de Microsoft. Il permet de créer et gérer des **machines virtuelles (VMs)** directement sur le matériel physique, sans OS hôte intermédiaire. Alternative à VMware ESXi.

### RDS (Remote Desktop Services)

Permet aux utilisateurs d'accéder à distance soit à un **bureau Windows complet** (Desktop Session Host), soit à des **applications publiées** (RemoteApp) qui s'exécutent sur le serveur mais s'affichent sur le poste client.

### WSUS (Windows Server Update Services)

Centralise la gestion des mises à jour Windows pour le parc de machines. Les postes récupèrent leurs patchs depuis le serveur WSUS interne plutôt qu'auprès de Microsoft directement, permettant ainsi de valider et planifier les mises à jour avant leur déploiement.

### IIS (Internet Information Services)

Le serveur web de Microsoft. Héberge des sites web et des applications web ASP.NET sur le réseau interne (Intranet) ou exposé sur Internet. Alternative à Apache / Nginx.

### NPS (Network Policy Server)

Serveur RADIUS de Microsoft. Centralise l'authentification des accès réseau (VPN, Wi-Fi WPA2-Enterprise, connexions commutées) en s'appuyant sur l'AD.

## Résumé des rôles

| Rôle | Protocole / Standard | Utilité principale |
| :--- | :---: | :--- |
| **AD DS** | Kerberos, LDAP | Annuaire central, authentification, GPO |
| **DNS** | DNS | Résolution de noms (indispensable à l'AD) |
| **DHCP** | DHCP | Attribution automatique des IPs |
| **File Server** | SMB | Partage de fichiers centralisé |
| **Hyper-V** | — | Virtualisation |
| **RDS** | RDP | Accès bureau/applicatif distant |
| **WSUS** | HTTP/HTTPS | Gestion des mises à jour |
| **IIS** | HTTP/HTTPS | Hébergement web |
| **NPS** | RADIUS | Auth. réseau centralisée (VPN, Wi-Fi) |
