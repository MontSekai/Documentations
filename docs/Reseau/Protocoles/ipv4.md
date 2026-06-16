---
tags:
  - Reseau
  - Protocoles
  - IPv4
  - TCP
  - IP
---

# L'Adressage IPv4

Identifiant logique historique d'une interface réseau connectée.

## 1. Définition
Une **adresse IPv4** est l'identifiant logique (Couche 3 du [Modèle OSI](modele_osi.md)) unique attribué à une interface réseau connectée à un réseau utilisant la suite TCP/IP. Bien qu'elle soit vouée à être remplacée très progressivement par l'[IPv6](ipv6.md) à cause de la pénurie mondiale d'adresses, elle reste le standard technique dominant dans les réseaux locaux d'entreprise.

## 2. Description / Fonctionnement
Une adresse IPv4 est mathématiquement composée de **32 bits**, affichée sous la forme de 4 octets décimaux (ex: `192.168.1.10`).
Pour qu'un ordinateur puisse communiquer avec les autres, il a besoin d'un **Masque de sous-réseau** (Subnet Mask) qui vient "découper" cette IP en deux parties distinctes :
* **La partie Réseau** : Identifie l'ensemble du sous-réseau global (ex: le nom de la rue).
* **La partie Hôte** : Identifie la machine précise au sein de ce sous-réseau (ex: le numéro de maison).

La notation **CIDR** permet de raccourcir le masque en comptant le nombre de bits alloués à la partie réseau. Par exemple, un masque `255.255.255.0` (qui fige 24 bits sur 32) s'écrit de manière élégante `/24`. L'IP complète de la machine devient donc `192.168.1.10/24`.

## 3. Utilisation / Cas Pratique
Sur Internet, les IP doivent être publiques et payées. Ainsi, à l'intérieur des réseaux LAN d'entreprise ou à la maison, on utilise presque exclusivement les **Plages d'adresses privées** (RFC 1918) :
* Classe A : `10.x.x.x`
* Classe B : `172.16.x.x` à `172.31.x.x`
* Classe C : `192.168.x.x`

Ces adresses sont gratuites, réutilisables, mais **absolument non routables sur Internet**. C'est le routeur de l'entreprise (ou la box Internet) qui s'occupe de faire la traduction à la volée (le protocole **NAT**) vers l'unique IP publique achetée chez l'opérateur.

## 4. Modifications possibles / Alternatives
**Calcul de sous-réseaux (Subnetting)** :
Les administrateurs découpent souvent les grands blocs réseaux (ex: `/16`) pour en créer des plus petits (ex: `/24`), afin de les isoler dans des [VLANs](vlan.md) spécifiques.
Il existe une règle mathématique d'or : Dans tout réseau IPv4 (peu importe sa taille), on perd **toujours 2 adresses hôtes inutilisables pour les PC** :
1. La toute première IP du bloc = l'**Adresse Réseau** (identifie le réseau dans les tables de routage).
2. La toute dernière IP du bloc = l'**Adresse de Broadcast** (utilisée pour envoyer un message à tout le monde simultanément).
*Formule mathématique du nombre d'IPs utiles pour des machines = $2^n - 2$* (où $n$ est le nombre de bits restants pour l'hôte).

## 5. Exemples visuels et Liens utiles

### IPs remarquables à connaître
| IP / Plage spéciale | Nom technique | Rôle / Explication |
| :--- | :--- | :--- |
| `127.0.0.1` | **Loopback** (Localhost) | Permet à la machine de se "pinguer" elle-même en boucle fermée. |
| `169.254.x.x` | **APIPA** | Adresse de "secours" auto-assignée par Windows si le serveur [DHCP](../../Systeme/Services/dhcp.md) est injoignable. |
| `0.0.0.0` | **Route par défaut** | Désigne la route de sortie globale vers l'inconnu (souvent Internet). |
| `255.255.255.255` | **Broadcast universel** | Message envoyé à toutes les machines du réseau physique. |
