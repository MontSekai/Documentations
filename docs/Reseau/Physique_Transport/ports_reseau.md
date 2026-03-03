---
tags:
  - Reseau
  - Ports
  - Protocoles
---

# Ports Réseau Courants

Un **port réseau** est un numéro logique (de 0 à 65535) associé à un protocole ou service réseau. Il complète l'adresse IP pour identifier précisément quel service est visé sur un équipement.

## Plages de ports

| Plage | Nom | Description |
| :---: | :--- | :--- |
| **0 – 1023** | Well-Known Ports | Ports standards réservés aux services connus (IANA) |
| **1024 – 49151** | Registered Ports | Ports enregistrés pour des applications tierces |
| **49152 – 65535** | Dynamic / Private | Ports éphémères attribués automatiquement aux connexions clients |

## Ports courants à connaître

### Administration et accès distant

| Port | Protocole | Description |
| :---: | :---: | :--- |
| **22** | SSH | Accès distant sécurisé (remplace Telnet) |
| **23** | Telnet | Accès distant NON chiffré — ❌ **Ne plus utiliser** |
| **3389** | RDP | Remote Desktop Protocol (bureau à distance Windows) |
| **5900** | VNC | Virtual Network Computing (bureau à distance multi-OS) |

### Web

| Port | Protocole | Description |
| :---: | :---: | :--- |
| **80** | HTTP | Web non chiffré |
| **443** | HTTPS | Web chiffré (TLS) |
| **8080** | HTTP-alt | Port alternatif HTTP (proxy, dev) |
| **8443** | HTTPS-alt | Port alternatif HTTPS |

### Messagerie

| Port | Protocole | Description |
| :---: | :---: | :--- |
| **25** | SMTP | Envoi d'email entre serveurs |
| **465** | SMTPS | SMTP sur SSL (obsolète mais encore utilisé) |
| **587** | SMTP/STARTTLS | Envoi d'email depuis un client de messagerie (recommandé) |
| **110** | POP3 | Récupération d'email (non chiffré) |
| **995** | POP3S | POP3 sur SSL |
| **143** | IMAP | Synchronisation d'emails |
| **993** | IMAPS | IMAP sur SSL |

### Infrastructure réseau

| Port | Protocole | Description |
| :---: | :---: | :--- |
| **53** | DNS | Résolution de noms (UDP et TCP) |
| **67/68** | DHCP | Attribution d'adresses IP (server/client) |
| **161/162** | SNMP | Supervision réseau (161=poll, 162=trap) |
| **123** | NTP | Synchronisation de l'heure |
| **514** | Syslog | Envoi de journaux vers un serveur centralisé |

### Transfert de fichiers

| Port | Protocole | Description |
| :---: | :---: | :--- |
| **21** | FTP (control) | Transfert de fichiers (non chiffré) — ❌ Éviter |
| **22** | SFTP | FTP via SSH (chiffré) — ✅ Recommandé |
| **989/990** | FTPS | FTP sur TLS |
| **445** | SMB | Partage de fichiers Windows (Active Directory) |
| **2049** | NFS | Partage de fichiers Unix/Linux |

### Bases de données

| Port | Protocole | Description |
| :---: | :---: | :--- |
| **1433** | MSSQL | Microsoft SQL Server |
| **3306** | MySQL / MariaDB | Base de données MySQL |
| **5432** | PostgreSQL | Base de données PostgreSQL |
| **1521** | Oracle | Oracle Database |
| **27017** | MongoDB | Base de données MongoDB |
| **6379** | Redis | Cache Redis |

### Autres services courants

| Port | Protocole | Description |
| :---: | :---: | :--- |
| **389** | LDAP | Annuaire LDAP (Active Directory) |
| **636** | LDAPS | LDAP sur SSL |
| **88** | Kerberos | Authentification Active Directory |
| **443** | HTTPS / RPC | Aussi utilisé par WinRM (HTTPS) et Office 365 |
| **500/4500** | IKE / IPSec NAT-T | Établissement de tunnels VPN IPSec |
| **1194** | OpenVPN | VPN OpenVPN (UDP/TCP) |
| **4443** | HTTPS-alt | Utilisé par certains proxy et appliances |

## Protocoles de transport : TCP vs UDP

| Protocole | Orienté connexion | Fiabilité | Usage typique |
| :--- | :---: | :---: | :--- |
| **TCP** | Oui (3-way handshake) | ✅ Oui (accusés de réception) | HTTP, SSH, FTP, SMTP |
| **UDP** | Non | ❌ Non (best-effort) | DNS, DHCP, SNMP, streaming, jeux |
