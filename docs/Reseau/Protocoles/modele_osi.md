---
tags:
  - Reseau
  - Protocoles
  - OSI
---

# Le modèle OSI

Le modèle OSI (Open Systems Interconnection) est un standard de communication en réseau qui décrit les protocoles en 7 couches empilées.

## Les 7 Couches en détail

| N° | Couche OSI | Matériel / Équipement | Vérification d'erreur possible | Rôle de la couche |
| :--- | :--- | :--- | :--- | :--- |
| **7** | **Application** | PC, Serveur, Pare-feu applicatif (WAF) | Gérée selon le protocole (ex: HTTPS gère ses erreurs, HTTP non). | Fournit les interfaces réseau aux logiciels (HTTP, DNS, FTP, SMTP). |
| **6** | **Présentation** | PC, Serveur | Non | Formatage (ASCII, JPEG) et chiffrement (TLS/SSL) des données. |
| **5** | **Session** | PC, Serveur | Non | Ouvre, gère et ferme la communication (session) entre les applications. |
| **4** | **Transport** | PC, Pare-feu (Firewall), Load Balancer | **Oui** (avec TCP). **Non** (avec UDP). | Transport de bout en bout, segmentation et gestion des ports (ex: Port 80, 443). |
| **3** | **Réseau** | Routeur, Switch de Niveau 3 | **Oui** (Checksum dans l'en-tête du paquet IP). | Adressage logique (Adresses IP) et Routage (chemin optimal). Unité : Le Paquet. |
| **2** | **Liaison de données** | Switch, Carte Réseau (NIC) | **Oui** (FCS - Frame Check Sequence à la fin de la trame). | Adressage physique (Adresses MAC) et contrôle d'accès au support (CSMA/CD). Unité : La [Trame](ethernet_trames.md). |
| **1** | **Physique** | Câble RJ45, Fibre optique, Hub, Répéteur | **Non** (ou matériellement très basique via le voltage). | Conversion des bits (0 et 1) en signaux électriques, lumineux ou ondes radio. |

---

### La fameuse "Couche 0" (ou Couche 8)

En informatique, on entend souvent parler en blaguant de la **Couche 0** (ou de la **Couche 8**).
* **La Couche 8 (L'Utilisateur)** : Fait référence à l'humain devant l'écran (*"Le problème se situe entre la chaise et le clavier"*).
* **La Couche 0 (L'Environnement Physique)** : Fait souvent référence à un problème encore plus basique que le câble lui-même. C'est l'absence d'électricité, le câble arraché par une pelleteuse, ou un équipement physiquement éteint ou non branché.

---

## Comparaison : Le modèle TCP/IP

Le modèle OSI est un modèle **théorique** conçu pour standardiser et expliquer le fonctionnement des réseaux mondiaux. Dans la **pratique réelle**, Internet utilise le modèle **TCP/IP** (modèle DoD - *Department of Defense*), qui est plus condensé (4 couches) :

| Modèle OSI (7 couches) | Modèle TCP/IP (4 couches) | Protocoles Associés |
| :--- | :--- | :--- |
| Application (7), Présentation (6), Session (5) | **Application** (4) | HTTP, FTP, DNS, SMTP |
| Transport (4) | **Transport** (3) | TCP, UDP |
| Réseau (3) | **Internet** (2) | IPv4, IPv6, ICMP, IPsec |
| Liaison de données (2), Physique (1) | **Accès Réseau** (1) *(ou Network Interface)* | Ethernet, Wi-Fi (802.11) |
