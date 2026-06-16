---
tags:
  - Reseau
  - Protocoles
  - IPv6
  - IP
---

# L'Adressage IPv6

Le futur obligatoire de l'adressage Internet face à la pénurie globale d'adresses IPv4.

## 1. Définition
L'**IPv6** (Internet Protocol version 6) a été développé pour remplacer progressivement et définitivement [l'IPv4](ipv4.md). Contrairement à l'IPv4 qui n'offre "que" 4,3 milliards d'adresses (un chiffre aujourd'hui épuisé), l'IPv6 en propose une quantité astronomique de 340 sextillions, permettant d'attribuer une adresse IP publique et unique à chaque appareil présent sur Terre (ordinateurs, IoT, montres, serveurs, voitures connectées).

## 2. Description / Fonctionnement
Une adresse IPv6 fait **128 bits** de long (contre seulement 32 bits pour IPv4). Elle s'écrit obligatoirement en format hexadécimal, séparée par des deux-points (`:`).
* **Exemple complet** : `2001:0db8:85a3:0000:0000:8a2e:0370:7334`
* **Compression (Raccourci visuel)** : Pour la rendre humainement lisible, on enlève les zéros superflus. Les suites entières de zéros peuvent être remplacées par un double deux-points `::` (cette règle ne s'applique qu'une seule fois par IP). L'exemple devient alors : `2001:db8:85a3::8a2e:370:7334`.

Le concept de Broadcast (diffusion massive polluante) disparaît complètement en IPv6, remplacé par du Multicast beaucoup plus intelligent et ciblé.

## 3. Utilisation / Cas Pratique
Lors du déploiement d'un réseau IPv6 d'entreprise ou chez un particulier, on n'utilise presque plus de [serveur DHCP](../../Systeme/Services/dhcp.md) pour distribuer les adresses IP.
L'IPv6 est intrinsèquement *"Plug-n-Play"*. C'est le mécanisme d'auto-configuration **SLAAC**. Le routeur ou la box Internet diffuse simplement sur le réseau le "Préfixe" réseau (les 64 premiers bits). Ensuite, le PC ou le smartphone écoute ce préfixe et calcule de manière autonome ses 64 derniers bits (Interface ID) pour se forger une IP globale totalement unique et fonctionnelle en une fraction de seconde.

## 4. Modifications possibles / Alternatives
Il n'existe plus d'adresses "publiques" ou "privées" au sens IPv4. En IPv6, il existe plusieurs types d'adresses selon leur portée (*Scope*) :
* **Global Unicast (GUA)** (`2000::/3`) : C'est l'équivalent de l'IP publique. L'adresse est globale et routable librement sur tout Internet de bout en bout.
* **Unique Local (ULA)** (`fd00::/8`) : C'est l'équivalent de l'IP privée. Utilisée strictement en interne (LAN), elle est non routable sur Internet.
* **Link-Local (LLA)** (`fe80::/10`) : Auto-générée nativement par la carte réseau. Elle n'est valable et utilisable **que** sur le câble ou le réseau physique immédiat, elle ne passe jamais le premier routeur.

## 5. Exemples visuels et Liens utiles

### Tableau comparatif majeur IPv4 / IPv6
| Caractéristique | IPv4 (Standard historique) | IPv6 (Nouveau standard) |
| :--- | :--- | :--- |
| **Taille mathématique** | 32 bits | 128 bits |
| **Format d'écriture** | Décimal pointé (`192.168.1.1`) | Hexadécimal (`2001:db8::1`) |
| **Diffusion (Message à tous)** | Broadcast massif | Multicast ciblé |
| **Configuration automatique** | Serveur DHCP requis | SLAAC natif autonome |
| **IP Privée de réseau local** | `192.168.x.x` etc. | `fd00::` (ULA) |
| **Accès Internet** | NAT obligatoire (Box/Routeur) | Adressage GUA de bout en bout |
