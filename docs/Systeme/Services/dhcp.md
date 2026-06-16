---
tags:
  - Systeme
  - Services
  - DHCP
---

# DHCP (Dynamic Host Configuration Protocol)

Protocole réseau assurant la configuration automatique des paramètres IP d'une machine.

## 1. Définition
Le DHCP (Dynamic Host Configuration Protocol) est un protocole réseau dont le rôle est d'attribuer dynamiquement et automatiquement une adresse IP et des paramètres de configuration réseau aux appareils qui s'y connectent.

## 2. Description / Fonctionnement
Lorsqu'un appareil se connecte, l'échange se fait en 4 étapes (DORA) :
* **D**iscover : Le client envoie une requête de diffusion pour trouver un serveur.
* **O**ffer : Le serveur propose une IP disponible.
* **R**equest : Le client accepte et demande cette IP.
* **A**cknowledge : Le serveur confirme et valide le bail (Lease).

Les paramètres distribués incluent l'adresse IP, le masque de sous-réseau, la passerelle par défaut, et les serveurs [DNS](dns.md).

## 3. Utilisation / Cas Pratique
Le DHCP est utilisé sur la quasi-totalité des réseaux (de la box Internet grand public au réseau d'entreprise) pour éviter à l'administrateur de configurer manuellement l'adresse IP de chaque ordinateur ou smartphone. Cela représente un gain de temps massif et prévient les conflits d'adresses IP.

## 4. Modifications possibles / Alternatives
Pour les serveurs (Web, AD, Fichiers) ou les équipements fixes (imprimantes, caméras), on utilise une IP statique fixée manuellement, ou bien on configure une "réservation DHCP" sur le serveur (il donne toujours la même IP à la même adresse MAC physique).

**Le Relais DHCP (IP Helper)** : Si le serveur DHCP n'est pas sur le même réseau local (VLAN) que le client, on configure le routeur pour intercepter le *Discover* et le relayer directement en Unicast au serveur. C'est obligatoire car les routeurs bloquent nativement le trafic Broadcast.

## 5. Exemples visuels et Liens utiles
*(Ajouter un schéma réseau illustrant le processus DORA).*
