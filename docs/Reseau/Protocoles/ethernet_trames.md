---
tags:
  - Reseau
  - Protocoles
  - Trame
---

# Ethernet et les Trames (802.3)

Le standard de communication des réseaux locaux physiques.

## 1. Définition
Une **Trame** (ou *Frame* en anglais) est l'unité fondamentale de données qui circule sur la couche 2 (Liaison de données) du [modèle OSI](modele_osi.md). C'est l'emballage physique standardisé par la norme planétaire **IEEE 802.3 (Ethernet)** pour transporter de la donnée sur un câble réseau RJ45 en cuivre ou une Fibre Optique.

## 2. Description / Fonctionnement
Contrairement aux paquets IP (Couche 3) qui gèrent la navigation mondiale de routeur en routeur, les trames Ethernet sont aveugles sur les longues distances : elles ne savent circuler **que sur le réseau local immédiat**, en passant d'un switch à une carte réseau (Saut par Saut).
Pour s'identifier au niveau matériel, elles n'utilisent absolument pas les adresses IP, mais les adresses physiques inaltérables gravées sur les cartes réseau à l'usine : les **Adresses MAC**.

Une trame complète encapsule le paquet IP dans un En-tête (Header) et un En-queue (Trailer / FCS). La taille utile classique d'une trame est de 1500 octets (le célèbre MTU - *Maximum Transmission Unit*).

## 3. Utilisation / Cas Pratique
Lorsqu'un PC d'employé veut parler à un serveur de fichiers local, la carte réseau du PC crée une Trame Ethernet. Elle y inscrit sa propre adresse MAC dans le champ "Source", et l'adresse MAC du serveur dans le champ "Destination". S'il ne connaît pas l'adresse MAC du serveur, il utilise au préalable le protocole **ARP** (qui est une trame spéciale envoyée à tout le monde simultanément - adresse de Broadcast `FF:FF:FF:FF:FF:FF` - pour demander *"Qui possède cette IP ?"*).
Le Switch réseau lit ensuite cet en-tête MAC et redirige physiquement la trame vers le bon câble réseau.

## 4. Modifications possibles / Alternatives
Par défaut, une trame Ethernet standard est dite "plate" et très simple. Cependant, pour répondre aux besoins de flexibilité de l'entreprise moderne (VLANs, Voix sur IP, priorisation), on utilise très souvent des [trames taguées (Norme 802.1Q)](802.1Q_802.1X.md). Le switch ouvre temporairement la trame Ethernet, y insère 4 octets de "Tag", et la referme avant de l'expédier.

**La gestion des erreurs - Le FCS (Frame Check Sequence)** : 
L'ordinateur expéditeur passe toute sa trame à travers un algorithme mathématique lourd et range le résultat final dans le Trailer (à la fin de la trame). L'ordinateur récepteur refait lui-même le calcul : si la trame a été abîmée, pliée ou parasitée électriquement sur le câble, les résultats ne correspondent pas. La carte réseau réceptrice **détruit alors silencieusement** la trame défectueuse. Le réseau Ethernet de couche 2 n'a aucun système d'accusé de réception (c'est le rôle supérieur du [protocole TCP](tcp_ip.md) de constater la perte de la trame Ethernet et de demander le renvoi du paquet).

## 5. Exemples visuels et Liens utiles

### Architecture d'une Trame Ethernet (Norme 802.3)
```mermaid
block-beta
  columns 6
  Préambule["Préambule / SFD<br/>(8 octets)"]
  Dest["MAC Destination<br/>(6 octets)"]
  Src["MAC Source<br/>(6 octets)"]
  Type["EtherType<br/>(2 octets)"]
  Data["Données / Paquet IP Applicatif<br/>(46 à 1500 octets max)"]
  FCS["FCS (Vérification d'erreur)<br/>(4 octets)"]
  
  style Préambule fill:#d9e1e8,stroke:#333
  style Dest fill:#f9f871,stroke:#333
  style Src fill:#f9f871,stroke:#333
  style Type fill:#f18f01,stroke:#333
  style Data fill:#9bde7e,stroke:#333
  style FCS fill:#e06666,stroke:#333
```

**Explication des champs majeurs :**
* **Préambule** : Alternance électrique de 0 et 1 pour synchroniser les horloges et "réveiller" les cartes réseau qui "écoutent" le câble.
* **MAC Dest/Source** : Les identifiants matériels locaux de l'expéditeur et du destinataire.
* **EtherType** : Indique au système d'exploitation ce qui est transporté dans la "boîte" de données (Ex: Code `0x0800` signifie que la boîte contient un Paquet IPv4, Code `0x86DD` pour de l'IPv6).
* **Données** : La charge utile elle-même.
* **FCS** : Algorithme de vérification d'intégrité du signal électrique/optique (Détruit la trame en cas d'erreur).
