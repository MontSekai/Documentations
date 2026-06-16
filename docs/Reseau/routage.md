---
tags:
  - Reseau
  - Routage
  - VLAN
---

# Routeur, Routage et Routage Inter-VLAN

Le mécanisme intelligent de transfert des paquets IP entre les réseaux.

## 1. Définition
Le **routage** est le processus réseau fondamental qui permet d'acheminer des paquets IP (Couche 3) d'un réseau source vers un autre réseau de destination. Un **routeur** (ou un pare-feu/Switch L3) est l'équipement dédié à cette tâche. Sans mécanisme de routage, une machine est incapable de communiquer avec une autre machine située en dehors de son propre sous-réseau local.

## 2. Description / Fonctionnement
Pour fonctionner, chaque routeur maintient en mémoire vive une "carte GPS" appelée **Table de routage**. Lorsqu'il reçoit un paquet IP entrant sur l'une de ses pattes, il lit l'adresse IP de destination, consulte sa table, et transmet le paquet vers l'interface ou le routeur voisin approprié (le *Next-Hop*).

Les tables de routage sont alimentées par deux grandes méthodes :
* **Routage Statique** : Les chemins sont renseignés à la main par l'administrateur (ex: "Pour aller vers le réseau 10.0.0.0/8, passe par le routeur 192.168.1.254"). Inadapté aux grands réseaux car statique en cas de panne de lien.
* **Routage Dynamique** : Les routeurs utilisent des protocoles mathématiques complexes (OSPF, BGP) pour s'échanger en direct la liste des réseaux qu'ils connaissent. Le routeur calcule automatiquement le chemin le plus court et réagit instantanément si une fibre est coupée.

## 3. Utilisation / Cas Pratique
Le routage est indispensable sur Internet pour lier les fournisseurs d'accès, mais il est aussi la clé des réseaux LAN d'entreprise avec le principe du **Routage Inter-[VLAN](vlan.md)**.
Exemple : Par sécurité matérielle (Couche 2), un poste situé dans le VLAN 10 (Comptabilité) ne peut pas communiquer directement avec un serveur situé dans le VLAN 20 (Production). Il faut donc placer un routeur ou un Pare-feu au milieu pour faire "passer la frontière" aux paquets IP de la couche 3, tout en y appliquant éventuellement des règles de sécurité (ACL).

## 4. Modifications possibles / Alternatives
Il existe deux manières standards de concevoir du routage inter-VLAN en LAN :
* **Router-on-a-Stick** (Ancienne méthode) : On utilise un Routeur externe relié au Switch central par un seul lien physique "Trunk" (qui porte tous les VLANs). Le routeur crée des "sous-interfaces virtuelles" (ex: interface gig0/0.10 et gig0/0.20) qui serviront de passerelles pour les différents VLANs. C'est simple, mais le câble unique devient un goulot d'étranglement sévère.
* **Switch Multicouche de Couche 3** (SVI - Méthode moderne) : On se passe de routeur physique local. Le Switch (modèle plus haut de gamme) embarque le processeur de routage et gère directement cela en interne à des vitesses faramineuses grâce à des interfaces virtuelles internes (SVI).

## 5. Exemples visuels et Liens utiles

### Architecture Router-on-a-Stick
```mermaid
graph LR
    V10["💻 PC VLAN 10\nIP 192.168.10.x"]
    V20["💻 PC VLAN 20\nIP 192.168.20.x"]
    SW["🔀 Switch L2"]
    R["🌐 Routeur Pare-Feu"]

    V10 -- "Access" --> SW
    V20 -- "Access" --> SW
    SW -- "Câble Trunk Unique" --> R
    
    note over R: Interfaces virtuelles\nEth0.10 et Eth0.20
```

### Table de routage typique (Exemple console Cisco)
| Code initial | Réseau de Destination | Passerelle (Next Hop) | Origine (Comment a-t-il été appris ?) |
| :---: | :--- | :--- | :--- |
| **C** | `192.168.1.0/24` | *Directly connected* | Le réseau est branché sur mon port local. |
| **S** | `10.0.0.0/8` | `via 192.168.1.254` | **Route statique** ajoutée à la main. |
| **O** | `172.16.0.0/16` | `via 192.168.2.1` | **OSPF** (Protocole dynamique intra-entreprise). |
| **S*** | `0.0.0.0/0` | `via 192.168.1.254` | **Route par défaut** (Le chemin vers Internet). |
