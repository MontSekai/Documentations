---
tags:
  - Reseau
  - Protocoles
  - Trame
---

# Ethernet et les Trames

Une trame (ou *frame* en anglais) est l'unité de données de la couche 2 (Liaison de données) du modèle OSI. 

## Fonctionnement

Contrairement aux paquets IP qui gèrent le routage à grande échelle (couche 3), les trames circulent sur le réseau local physique en utilisant les adresses MAC pour identifier la source et la destination matérielle.

## Composition d'une Trame Ethernet (Standard 802.3)

À la différence d'un paquet IP, la trame possède un **En-tête** (Header) et un **En-queue** (Trailer/Footer) pour encadrer la donnée. Elle a généralement une taille maximale de 1518 octets (MTU standard).

Voici la représentation simplifiée de sa structure :

```mermaid
block-beta
  columns 6
  Préambule["Préambule / SFD<br/>(8 octets)"]
  Dest["MAC Destination<br/>(6 octets)"]
  Src["MAC Source<br/>(6 octets)"]
  Type["Type / Longueur<br/>(2 octets)"]
  Data["Données / Paquet IP<br/>(46 à 1500 octets)"]
  FCS["FCS / CRC<br/>(4 octets)"]
  
  style Préambule fill:#d9e1e8,stroke:#333
  style Dest fill:#f9f871,stroke:#333
  style Src fill:#f9f871,stroke:#333
  style Type fill:#f18f01,stroke:#333
  style Data fill:#9bde7e,stroke:#333
  style FCS fill:#e06666,stroke:#333
```

### Explication par contenu

1. **Préambule et SFD (Start of Frame Delimiter)** : 
   * C'est une suite alternée de 0 et de 1 qui sert à "réveiller" l'interface réseau réceptrice et synchroniser les horloges (les cartes réseaux se mettent au même rythme de lecture). Le dernier bit (le SFD) avertit que le contenu utile commence juste après.
   
2. **L'Adresse MAC de Destination** : 
   * L'adresse matérielle (couche 2) de l'appareil censé recevoir le message sur ce réseau local. S'il s'agit d'un message global, cette zone contient des "F" (`FF:FF:FF:FF:FF:FF`, une trame Broadcast).
   
3. **L'Adresse MAC Source** : 
   * L'adresse matérielle de l'appareil qui a créé et émis cette trame.

4. **L'EtherType (Type / Longueur)** : 
   * Permet d'indiquer quel type de protocole se cache dans la section "Données" juste après (ex: `0x0800` signifie que la donnée contient un Paquet IPv4, `0x86DD` pour de l'IPv6).
   
5. **Les Données (Payload)** :
   * C'est le colis lui-même (généralement le Paquet IP issu de la Couche 3 du modèle OSI). Cette section doit faire entre 46 octets (minimum) et 1500 octets (MTU habituel). S'il y a moins de 46 octets de données, on ajoute du bourrage (padding) artificiellement.
   
6. **Le Trailer : FCS (Frame Check Sequence)** :
   * C'est la **vérification d'erreur**. L'ordinateur expéditeur passe toute sa trame à travers un algorithme mathématique (le CRC) et y range ce résultat.
   * L'ordinateur récepteur refait lui-même le calcul quand il reçoit la trame. **Si le résultat est différent du FCS**, cela signifie que la trame a été corrompue pendant le voyage (interférences sur le câble, bout cassé) : la carte réseau du receveur **détruit silencieusement** la trame défectueuse.
