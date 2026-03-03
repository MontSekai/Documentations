---
tags:
  - Reseau
  - Protocoles
  - IPv4
  - TCP
  - IP
---

# L'Adressage IPv4

L'**adresse IPv4** est l'identifiant logique historique d'une interface connectée à un réseau IP. Pour la théorie globale d'encapsulation, voir le [Modèle OSI](modele_osi.md) et la structure TCP/IP. Face à la pénurie d'adresses, ce protocole est destiné à être remplacé à long terme par [IPv6](ipv6.md).

## 1. Bits, Octets et CIDR

Une adresse IPv4 est composée de **32 bits** (des 0 et des 1). Pour la rendre lisible, elle est divisée en **4 octets** (de 8 bits chacun), notés en décimal : `192.168.1.10`.

Le **Masque de sous-réseau** (Subnet Mask) permet à l'ordinateur de savoir, dans ces 32 bits, quelle partie désigne l'**Adresse du Réseau** (fixe) et quelle partie désigne l'**Hôte** (la machine). La notation **CIDR** compte le nombre de "1" consécutifs du masque.
* Exemple : Un masque `255.255.255.0` (3 octets bloqués = 24 bits à "1") s'écrit de manière abrégée **`/24`**. L'IP complète est notée `192.168.1.10/24`.

## 2. Classes d'adresses (Historique)

Historiquement, le routage Internet s'appuyait sur des classes rigides :

| Classe | Plage d'adresses | Masque naturel | Volume d'hôtes | Cas d'usage typique |
| :--- | :--- | :--- | :--- | :--- |
| **A** | `1.0.0.0` à `126.0.0.0` | `/8` (255.0.0.0) | 16 Millions | Gouvernements, Telcos |
| **B** | `128.0.0.0` à `191.255.0.0` | `/16` (255.255.0.0) | 65 534 | Moyennes/Grandes entreprises |
| **C** | `192.0.0.0` à `223.255.255.0` | `/24` (255.255.255.0) | 254 | LAN de PME/TPE |

## 3. IPs Remarquables (Publiques vs Privées)

### Plages Privées (RFC 1918)
Sur Internet (qui est un gigantesque réseau public), les adresses IP doivent être uniques au monde. Cependant, pour économiser ces adresses, des **plages privées** ont été définies. Ces IPs peuvent être réutilisées librement en entreprise ou à la maison, car elles ne sont **pas routables sur Internet**. C'est le routeur/Box qui traduit ces IP vers son unique IP publique avec le [NAT / PAT](routage.md).

* Classe A privée : `10.0.0.0` à `10.255.255.255`
* Classe B privée : `172.16.0.0` à `172.31.255.255`
* Classe C privée : `192.168.0.0` à `192.168.255.255`

### Adresses systémiques spéciales

| IP / Plage | Nom | Rôle |
| :--- | :--- | :--- |
| `127.0.0.1` | **Loopback** (Localhost) | Permet à une machine de se "désigner elle-même". |
| `169.254.x.x` | **APIPA** | IP de "secours" générée par l'OS Windows si le serveur DHCP est injoignable après timeout. |
| `0.0.0.0` | **Route par défaut** / All | Désigne "n'importe" quelle IP, ou la route globale dans une table de routage vers Internet. |
| `255.255.255.255` | **Broadcast universel** | Envoi à destination de toutes les machines d'un segment Layer 2. |

## 4. Subnetting : La règle des -2

Quel que soit le sous-réseau (du gigantesque `/8` au microscopique `/30`), il comprend toujours deux adresses qui ne peuvent **jamais** être assignées à un ordinateur :

1. **La Première IP = L'Adresse Réseau** : Identifie l'ensemble du sous-réseau (ex: `192.168.1.0`).
2. **La Dernière IP = L'Adresse de Broadcast (Diffusion)** : Utilisée pour adresser simultanément tout le monde (ex: `192.168.1.255`).

Le nombre d'ordinateurs (hôtes) que l'on peut brancher se calcule via `2^n - 2`, où `n` = la partie Hôte (Adresses totales 32 bits - Masque CIDR).
* *Exemple avec un `/24` : Il reste 8 bits pour les hôtes. $2^8 = 256$. Moins 2 (Réseau/Broadcast) = 254 IPs disponibles.*
