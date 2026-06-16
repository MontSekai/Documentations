---
tags:
  - Reseau
  - Ports
  - Protocoles
---

# Ports Réseau Courants

Les portes d'entrée logiques des services et applications réseau.

## 1. Définition
Un **port réseau** est un numéro logique (allant de 0 à 65535) qui fonctionne sur la couche 4 du [modèle OSI](modele_osi.md) (Transport - TCP ou UDP). Il vient obligatoirement en complément de l'adresse IP. Si l'adresse IP représente l'adresse d'un immeuble (le serveur), le port réseau est le numéro de l'appartement qui héberge un service bien précis (site web, mails, base de données).

## 2. Description / Fonctionnement
Les ports sont officiellement divisés en trois grandes plages par l'organisme IANA :
* **0 – 1023 (Well-Known Ports)** : Réservés aux protocoles universels historiques (Navigation Web, Mails, Transfert de fichiers).
* **1024 – 49151 (Registered Ports)** : Enregistrés officiellement pour des applications tierces spécifiques (Ex: Bases de données, Jeux vidéo).
* **49152 – 65535 (Dynamic Ports)** : Ports dits "éphémères", attribués à la volée de manière aléatoire aux PC clients pour identifier leur session de retour.

## 3. Utilisation / Cas Pratique
L'administrateur système et réseau se sert au quotidien de la connaissance de ces ports pour configurer la sécurité des **Pare-feux (Firewalls)** ou des [VLANs](../vlan.md).
Par exemple, pour exposer un serveur Web sécurisé sur Internet, l'administrateur crée une règle de filtrage autorisant uniquement le trafic entrant sur le **Port TCP 443 (HTTPS)** et bloque absolument tous les autres numéros (principe du moindre privilège).

## 4. Modifications possibles / Alternatives
Rien n'oblige techniquement à respecter ces conventions. Par simple sécurité supplémentaire (Security by Obscurity), un administrateur peut volontairement modifier la configuration d'un service critique (ex: un serveur SSH) pour qu'il n'écoute plus sur son port par défaut (22), mais sur un port alternatif secret (ex: 2222) afin d'échapper aux robots de scan automatiques qui pullulent sur Internet.

## 5. Exemples visuels et Liens utiles

### Mémento des Ports Informatiques Indispensables
| Numéro Port | Protocole / Service | Description (TCP ou UDP) | Sécurité |
| :---: | :---: | :--- | :---: |
| **20 / 21** | FTP | Transfert de fichiers (TCP) | ❌ Clair |
| **22** | SSH / SFTP | Prise de main et ligne de commande à distance (TCP) | ✅ Chiffré |
| **25 / 587** | SMTP | Envoi d'E-mails entre serveurs et clients (TCP) | ⚠️ Variable |
| **53** | DNS | Résolution de noms de domaines (TCP et UDP) | ⚠️ Variable |
| **67 / 68** | DHCP | Attribution IP automatique (UDP) | ❌ Clair |
| **80** | HTTP | Navigation Web standard (TCP) | ❌ Clair |
| **443** | HTTPS | Navigation Web sécurisée (TCP) | ✅ Chiffré |
| **161** | SNMP | [Supervision / Monitoring réseau](../../Systeme/Services/supervision.md) (UDP) | ✅ Chiffré v3 |
| **389** | LDAP | Requêtes vers l'Annuaire Active Directory (TCP/UDP) | ❌ Clair |
| **3389** | RDP | Bureau à distance Windows graphique (TCP/UDP) | ✅ Chiffré |
