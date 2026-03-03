---
tags:
  - Reseau
  - VPN
  - IPSec
  - Securite
---

# IPSec (IP Security)

Contrairement à OpenVPN qui opère sur les couches applicatives avec SSL/TLS, **IPSec** est une suite de protocoles de sécurité qui fonctionne nativement au niveau de la **couche 3 (Réseau)** du modèle OSI.

IPSec est le **standard mondial pour sécuriser le trafic IP**. Il est utilisé massivement pour monter des **Tunnels VPN Site-to-Site** (relier deux routeurs ou pare-feux pour connecter deux sites distants) ou Client-to-Site.

## Les deux protocoles principaux d'IPSec

IPSec repose sur deux protocoles fondamentaux pour manipuler et sécuriser les paquets IP :

| Protocole | Numéro IP | Fonctionnalité | Description |
| :--- | :---: | :--- | :--- |
| **AH (Authentication Header)** | 51 | **Intégrité et Authentification** | Protège l'intégrité du paquet pour garantir qu'il n'a pas été modifié. **Il ne chiffre pas les données**. Rarement utilisé seul aujourd'hui. |
| **ESP (Encapsulating Security Payload)** | 50 | **Confidentialité, Intégrité, Auth** | **Chiffre la payload** (données utiles) du paquet IP + protège l'intégrité. C'est le protocole massivement utilisé. |

## Mode Transport vs Mode Tunnel

IPSec peut appliquer ESP ou AH selon deux modes distincts :

### Mode Transport
Seules les données (la charge utile, TCP/UDP) du paquet IP sont chiffrées par ESP. L'en-tête IP original reste intact et visible.
* **Usage moyen** : Connexion host-to-host ou sécurisation d'un trafic encapsulé via d'autres tunnels (ex: GRE over IPSec ou L2TP over IPSec).

### Mode Tunnel
C'est le mode le plus répandu pour les VPNs. Le paquet IP **entier** (en-tête original + données) est chiffré par ESP. IPSec ajoute ensuite un **nouvel en-tête IP** pour permettre au paquet de naviguer sur Internet entre les deux pare-feux.
* L'Internet public ne voit "que" les adresses IP publiques des pare-feux extérieurs, pas les adresses privées originelles, qui sont encapsulées et protégées.

```text
! IPSEC MODE TUNNEL ESP
+-----------+---------+-----------+---------------+----------+
| New IP    | ESP     | Orig. IP  | Orig. Data    | ESP      |
| Header    | Header  | Header    | (TCP/RDP/...) | Trailer  |
+-----------+---------+-----------+---------------+----------+
                      \___ CHIFFRÉ PAR ESP (Confidentialité)_/
```

## Le protocole d'établissement : IKE (Internet Key Exchange)

Avant de pouvoir envoyer du trafic TCP/IP chiffré, les deux périphériques distants doivent négocier *comment* ils vont communiquer de façon sécurisée (quels algorithmes cryptographiques utiliser, échange de clés secrètes, etc.).

C'est le rôle du protocole **IKE** (qui utilise les **ports UDP 500 et UDP 4500 (NAT-T)**). IKE se déroule en **deux phases**.

### IKE Phase 1 (Négociation des SA IKE)

Le but de la Phase 1 est de créer un **premier tunnel unique, bidirectionnel, chiffré et sécurisé**, non pas pour faire passer les données des utilisateurs, mais juste pour protéger l'échange de gestion entre les deux routeurs.

Pour monter cette Phase 1, les routeurs négocient selon le cadre **ISAKMP** :
* Hachage (SHA-1, SHA-256)
* Échange de clé (Diffie-Hellman - Group 2, 14, etc.)
* Authentification du pair (PSK - Pre-Shared Key, ou Certificats RSA)
* Chiffrement (AES-128, AES-256, 3DES)
* Durée de vie (Lifetime, ex: 86400s)

> [!TIP]
> En cas d'échec de Phase 1 (*Main Mode* ou *Aggressive Mode*), le tunnel de gestion est mort. En général, c'est dû à une **Pre-Shared Key (PSK)** erronée, une IP publique qui a changé, ou à une asymétrie entre les paramètres IKE (ex: AES côté A mais 3DES côté B).

### IKE Phase 2 (Négociation des SA IPSec)

Une fois la Phase 1 sécurisée, les routeurs l'utilisent pour négocier la **Phase 2**, qui montera les **véritables tunnels IPSec ciblés pour transporter les paquets utilisateurs**.

La phase 2 donne lieu à l'établissement de **SA (Security Associations)**. Une SA est **unidirectionnelle**. Pour relier un Site A et un Site B, il y aura au minimum une SA pour envoyer de A vers B, et une SA pour envoyer de B vers A (donc **2 SA** créées en Phase 2 par tunnel monté).

En Phase 2, outre le chiffrement (ESP, AES, etc.), on définit le **Proxy ID** (ou Traffic Selector). Ce sont les IPs privées cibles autorisées à emprunter le VPN (ex: "Le réseau 192.168.1.0/24 du Site A a le droit d'atteindre le réseau 10.0.0.0/8 du Site B via ce tunnel").

> [!WARNING]
> En cas de tunnel IPSec *"UP avec Phase 1 OK"* mais **où aucun ping ne passe**, l'erreur se situe presque dans 100% des cas dans la définition des adresses proxy-id / traffic selectors et les règles de Firewall / ACL !
