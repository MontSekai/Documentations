---
tags:
  - Systeme
  - Services
  - DHCP
---

# DHCP (Dynamic Host Configuration Protocol)

Le DHCP est un protocole réseau dont le rôle est d'assurer la configuration automatique des paramètres IP d'une machine.

## Fonctionnement

Lorsqu'un appareil se connecte au réseau, il envoie une requête de diffusion (*DHCP Discover*) pour trouver un serveur DHCP, qui va lui attribuer dynamiquement :
- Une adresse IP
- Un masque de sous-réseau
- Une passerelle par défaut
- Un ou plusieurs serveurs [DNS](dns.md)

## Le Relais DHCP (DHCP Relay / IP Helper)

Par défaut, les requêtes DHCP sont des requêtes de **diffusion réseau (Broadcast)**. Or, par définition, **un routeur bloque les broadcasts**. 

Si votre serveur DHCP (ex: un Windows Server) ne se trouve pas physiquement sur le même sous-réseau que le PC client (par exemple, le serveur est dans le VLAN Serveurs et le PC dans le VLAN Utilisateurs), la requête du PC n'atteindra jamais le serveur.

Pour résoudre ce problème, on configure un **Relais DHCP** (souvent appelé *IP Helper-Address* chez Cisco) sur l'interface du routeur côté client. 
1. Le client envoie sa requête Broadcast `255.255.255.255`.
2. Le routeur intercepte ce Broadcast.
3. Le routeur transforme la requête en message **Unicast** (un message direct point-à-point) et l'envoie à l'adresse IP exacte du serveur DHCP.
4. Le serveur DHCP répond au routeur, qui retransmet l'IP au client.
