---
tags:
  - Reseau
  - VPN
  - OpenVPN
---

# OpenVPN

OpenVPN est une solution logicielle libre permettant de créer un réseau privé virtuel (VPN).

## Installation

Sous Debian/Ubuntu, l'installation se fait simplement via les dépôts officiels :

```bash
sudo apt update
sudo apt install openvpn easy-rsa
```
*(L'outil `easy-rsa` est souvent installé en complément pour gérer votre propre infrastructure à clés publiques - PKI - et générer vos certificats)*.

## Configuration

Un fichier de configuration OpenVPN standard porte l'extension `.conf` coté serveur, et souvent `.ovpn` coté client.

Il définit des paramètres critiques tels que :
1. **L'IP et le Port** : (Ex: Port 1194, souvent en UDP pour de meilleures performances).
2. **Le mode de routage** : `dev tun` (Tunnel IP classique, le plus utilisé) ou `dev tap` (Tunnel Ethernet de niveau 2).
3. **Les certificats** : Chemins vers le CA, le certificat serveur et la clé privée.
4. **La plage d'IP** attribuée aux clients (Ex: `server 10.8.0.0 255.255.255.0`).
