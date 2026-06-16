---
tags:
  - Reseau
  - Protocoles
  - Administration
---

# Sessions Distantes (SSH et RDP)

Les protocoles indispensables pour prendre le contrôle à distance des serveurs et équipements de l'entreprise.

## 1. Définition
* **SSH (Secure Shell)** : Le standard mondial pour prendre le contrôle distant en ligne de commande des serveurs Linux et des équipements réseau (Switchs, Routeurs).
* **RDP (Remote Desktop Protocol)** : Le protocole propriétaire de Microsoft permettant de prendre le contrôle distant de l'interface graphique (Le Bureau) d'une machine Windows.

## 2. Description / Fonctionnement
* **SSH (Port 22 - TCP)** : Remplace l'ancêtre *Telnet* (qui transmettait les mots de passe en texte clair). SSH chiffre puissamment tout le trafic. L'authentification se fait soit par un mot de passe classique, soit (et c'est la norme en sécurité d'entreprise) par une **Paire de clés cryptographiques** (Clé privée sur le PC du développeur, Clé publique déposée sur le serveur distant).
* **RDP (Port 3389 - TCP)** : Transmet l'affichage visuel des pixels de l'écran Windows à distance et renvoie en direct les clics de souris et frappes clavier vers le serveur. Très gourmand en bande passante par rapport au SSH, mais l'expérience est visuellement identique à la présence physique devant l'écran du Datacenter.

## 3. Utilisation / Cas Pratique
Un administrateur système gère un parc de 500 serveurs répartis dans 3 Datacenters différents à travers l'Europe.
Il utilise l'outil **PuTTY** ou son terminal natif (Session SSH) pour mettre à jour un serveur Linux Debian distant : `ssh root@10.0.5.50`.
Il utilise l'outil **Connexion Bureau à Distance Windows (mstsc)** pour configurer l'Active Directory sur un serveur graphique Windows Server : `Connexion RDP sur 10.0.5.100`.

> [!WARNING]
> Ces ports (22 et 3389) ne doivent **JAMAIS** être exposés sur Internet publiquement dans une box ou un pare-feu, sous peine d'attaque force brute (Bruteforce) réussie dans les heures qui suivent. L'administrateur doit obligatoirement se connecter au [VPN IPsec ou OpenVPN](../VPN/open_vpn.md) de l'entreprise avant de pouvoir initier une connexion SSH ou RDP sécurisée.
