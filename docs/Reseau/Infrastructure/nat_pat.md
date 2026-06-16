---
tags:
  - Reseau
  - Routage
  - NAT
  - PAT
---

# NAT, PAT et Bridge

Les techniques de traduction d'adresses réseau pour palier au manque d'IPv4 et relier les mondes isolés.

## 1. Définition
* **NAT (Network Address Translation)** : Mécanisme permettant à un routeur de traduire une adresse IP privée (interne) en une adresse IP publique (Internet), et inversement.
* **PAT (Port Address Translation / NAT Overload)** : Une variante du NAT qui traduit plusieurs IPs privées vers une seule IP publique en utilisant des numéros de ports différents pour les différencier.
* **Bridge (Pont)** : Équipement ou configuration logicielle (couche 2 OSI) qui relie deux réseaux physiques distincts pour qu'ils agissent comme un seul grand réseau local.

## 2. Description / Fonctionnement
Le problème majeur d'Internet est qu'il n'y a plus d'IPv4 publiques disponibles. 
Le routeur (ou la Box internet) de l'entreprise possède la seule IP publique valide (ex: `82.50.X.X`). Les 200 ordinateurs du LAN ont des IPs privées invisibles sur Internet (ex: `192.168.1.10`).
Grâce au **PAT**, quand le PC `192.168.1.10` veut aller sur Google, le routeur intercepte le paquet, remplace l'adresse source par sa propre IP publique `82.50.X.X` et lui attribue un port source aléatoire (ex: `45000`). Il garde cette correspondance dans sa table NAT. Quand Google répond, le routeur lit le port `45000` et sait instantanément qu'il doit renvoyer la réponse au petit PC `192.168.1.10` en interne.

## 3. Utilisation / Cas Pratique
* **Le NAT statique (1 pour 1)** : Utilisé pour héberger un serveur web en interne. On lie définitivement une IP publique fixe à l'IP privée du serveur. 
* **Le PAT (1 pour plusieurs)** : Utilisé dans 100% des entreprises et foyers du monde pour permettre à tous les utilisateurs de surfer sur le web avec une seule IP publique commune.
* **Le Mode Bridge** : Souvent utilisé en virtualisation (VMware/VirtualBox) ou pour lier deux switchs distants. La machine virtuelle configurée en mode "Bridge" obtient une IP directement sur le même réseau local physique que l'ordinateur hôte, contournant le routeur interne du logiciel.

`Voir aussi : [IPv4](../Protocoles/ipv4.md) | [Routage](routage.md)`
