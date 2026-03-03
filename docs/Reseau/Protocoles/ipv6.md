---
tags:
  - Reseau
  - Protocoles
  - IPv6
  - IP
---

# L'Adressage IPv6

L'**IPv6** (Internet Protocol version 6) a été développé pour faire face à la pénurie d'adresses [IPv4](ipv4.md). Contrairement à IPv4 qui n'offre "que" 4,3 milliards d'adresses, IPv6 en propose une quantité astronomique (340 sextillions), permettant de donner une IP publique unique à chaque appareil sur Terre (ordinateurs, téléphones, IoT, voitures...).

## 1. Structure et Notation

Une adresse IPv6 fait **128 bits** (contre 32 bits pour IPv4). Elle est représentée par 8 groupes de 4 caractères hexadécimaux, séparés par des deux-points (`:`).

* **Exemple complet** : `2001:0db8:85a3:0000:0000:8a2e:0370:7334`

### Règles d'abréviation
Pour rendre les adresses plus courtes et lisibles, deux règles s'appliquent :
1. **Omission des zéros de tête** dans un groupe : `0db8` devient `db8`, et `0000` devient `0`.
2. **Compression des suites de zéros** : Une suite consécutive de groupes composés de zéros peut être remplacée par un double deux-points `::`. (Attention : Cette règle de compression ne peut être utilisée qu'**une seule fois** par adresse, sinon on ne saurait pas combien de zéros remplacer).

* L'adresse d'exemple devient : `2001:db8:85a3::8a2e:370:7334`

### Masque (Préfixe)
Comme en IPv4, la notation **CIDR (Préfixe)** est utilisée pour distinguer la partie "Réseau" de la partie "Machine" (Interface ID).
* Exemple : `2001:db8:abcd:0012::/64` indique que les 64 premiers bits identifient le réseau, et les 64 derniers bits identifient précisément l'appareil. Le préfixe `/64` est le "masque de sous-réseau" standard absolu pour les réseaux Ethernet IPv6.

## 2. Types d'Adresses IPv6

Il n'y a plus de notion de "Broadcast" en IPv6 (il a été remplacé par du Multicast intelligent).

| Type d'adresse | Équivalent IPv4 | Reconnaissable par | Explication |
| :--- | :--- | :--- | :--- |
| **Global Unicast (GUA)** | IP Publique | `2000::/3` (ex: `2001:xxx...`) | Adresse unique, routable sur tout Internet. Vous êtes identifié directement mondialement. |
| **Unique Local (ULA)** | IP Privée | `fc00::/7` ou `fd00::/8` | Utilisée en réseau local uniquement (intranet), non routable sur Internet. |
| **Link-Local Address (LLA)** | APIPA / 169.254 | `fe80::/10` | Auto-configurée par la carte réseau. Valable UNIQUEMENT sur le lien physique actuel. |
| **Multicast** | Broadcast / 224.0 | `ff00::/8` | Adresse un message à un groupe cible d'appareils, au lieu d'inonder le réseau. |
| **Loopback** | 127.0.0.1 | `::1` | La machine se désigne elle-même. |
| **Route par défaut** | 0.0.0.0 | `::/0` | Identifie "Toutes les adresses globales". |

## 3. Auto-configuration (SLAAC)
Contrairement à IPv4 qui nécessitait presque toujours un serveur [DHCP](../../Systeme/Services/dhcp.md), IPv6 est *"Plug-n-Play"*. Lorsqu'un ordinateur est branché au réseau, le routeur (ou la Box opérateur) lui envoie le Prefix Réseau (les 64 premiers bits). L'ordinateur "invente" lui-même les 64 derniers bits pour s'auto-attribuer son IP (Souvent en se basant aléatoirement ou à partir de son Adresse MAC - procédé EUI-64). C'est le mécanisme SLAAC (*Stateless Address Autoconfiguration*). Le DHCPv6 existe toujours pour gérer l'attribution de serveurs DNS de façon plus fine, mais n'est techniquement plus obligatoire pour le routage.
