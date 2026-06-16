---
tags:
  - Reseau
  - Protocoles
  - OSI
---

# Le modèle OSI

Standard théorique de communication réseau décrivant les protocoles en 7 couches.

## 1. Définition
Le modèle OSI (Open Systems Interconnection) est un standard de communication en réseau créé par l'ISO. Il décrit de manière théorique et structurée le parcours de la donnée, depuis l'application de l'utilisateur jusqu'au câble physique, en divisant le processus en 7 couches indépendantes empilées.

## 2. Description / Fonctionnement
Chaque couche a un rôle très précis, utilise sa propre unité de données (PDU), et ne communique qu'avec la couche directement supérieure ou inférieure :
1. **Physique** : Conversion des bits en signaux électriques, optiques ou radio.
2. **Liaison de données** : Adressage physique MAC (Switch) et détection d'erreurs locales.
3. **Réseau** : Adressage logique IP et Routage à travers les réseaux (Routeur).
4. **Transport** : Contrôle de bout en bout, fiabilité et gestion des ports (TCP / UDP).
5. **Session** : Ouvre, gère et ferme la communication entre les applications.
6. **Présentation** : Formatage des données (ex: JPEG, ASCII) et chiffrement (TLS/SSL).
7. **Application** : Fournit les interfaces réseau directes aux logiciels (HTTP, DNS, FTP).

## 3. Utilisation / Cas Pratique
Le modèle OSI est le référentiel mental absolu pour le "Troubleshooting" (résolution de pannes). Face à une panne réseau complexe, l'ingénieur réseau remonte systématiquement les couches de bas en haut :
* *Couche 1* : Le câble RJ45 est-il bien branché ?
* *Couche 2* : Le port du switch est-il bien "Up" et dans le bon VLAN ?
* *Couche 3* : Le PC arrive-t-il à "ping" la passerelle par défaut (IP) ?
* *Couche 4* : Le port TCP 443 est-il ouvert sur le pare-feu ?
* *Couche 7* : Le service web Nginx est-il démarré sur le serveur ?

## 4. Modifications possibles / Alternatives
Dans la réalité technique, Internet fonctionne avec le modèle **TCP/IP** (modèle du DoD) qui est une implémentation plus pragmatique et condensée (4 couches : Accès Réseau, Internet, Transport, Application). Le modèle OSI est rarement implémenté tel quel à la lettre, il sert avant tout de vocabulaire universel pour les constructeurs et informaticiens.

## 5. Exemples visuels et Liens utiles

### Tableau détaillé des 7 couches
| N° | Couche | Matériel cible | Rôle principal |
| :--- | :--- | :--- | :--- |
| **7** | **Application** | Pare-feu Applicatif (WAF) | Interface logicielle (HTTP, DNS) |
| **6** | **Présentation** | PC, Serveur | Formatage et chiffrement (SSL) |
| **5** | **Session** | PC, Serveur | Gère la session (Ouverture/Fermeture) |
| **4** | **Transport** | Pare-feu (L4) | Ports (TCP, UDP), Segmentation |
| **3** | **Réseau** | Routeur (L3) | Adressage IP, Routage (Paquet) |
| **2** | **Liaison** | Switch (L2) | Adressage MAC (Trame Ethernet) |
| **1** | **Physique** | Câble, Fibre, Hub | Conversion en signal (Bits) |
