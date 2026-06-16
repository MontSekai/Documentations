---
tags:
  - Reseau
  - Architecture
---

# Peer-to-Peer (P2P)

L'architecture réseau décentralisée où tout le monde est client et serveur.

## 1. Définition
Le **Peer-to-Peer (Pair-à-Pair / P2P)** est un modèle d'architecture réseau où chaque nœud (chaque ordinateur connecté au réseau) joue en même temps le rôle de client (celui qui demande et télécharge de la donnée) et le rôle de serveur (celui qui fournit et téléverse de la donnée vers les autres).

## 2. Description / Fonctionnement
Dans le modèle classique ultra-centralisé (Client-Serveur), des millions de clients se connectent à un seul et unique gros serveur central (ex: YouTube ou Netflix). Si ce serveur tombe en panne, le réseau entier s'arrête. Si tout le monde télécharge le même gros fichier au même moment, la bande passante du serveur central sature et tout devient lent.

Dans le modèle très résilient du **P2P**, il n'y a pas de serveur central exclusif.
Si Alice télécharge un gros fichier de 10 Go (ex: une mise à jour logicielle), son client P2P va télécharger simultanément des milliers de petits morceaux cryptés de ce fichier provenant de 500 ordinateurs différents (les "Pairs") répartis dans le monde, qui possèdent déjà ce fichier. 
La magie du système réside dans le partage : pendant qu'elle télécharge, le propre ordinateur d'Alice upload et envoie automatiquement les petits morceaux qu'elle a déjà reçus à d'autres personnes qui les demandent en ce moment même.

## 3. Utilisation / Cas Pratique
Bien qu'historiquement très célèbre pour le téléchargement illégal via le protocole *BitTorrent* (eMule, uTorrent, Napster), le P2P est une architecture fondamentale de l'informatique moderne, massivement utilisée de façon légale et cruciale :
* **Windows Update (Delivery Optimization)** : Dans un grand réseau LAN d'entreprise, si 100 PC doivent faire une grosse mise à jour Windows le mardi matin, un seul PC va la télécharger depuis les serveurs Microsoft sur Internet. Ensuite, ce PC va envoyer la mise à jour en P2P aux 99 autres PC de l'étage pour soulager la petite box Internet de l'entreprise (une économie drastique de bande passante).
* **La Blockchain (Bitcoin / Crypto-monnaies)** : L'entièreté de la colossale base de données des transactions financières (le Grand Registre) est synchronisée, chiffrée et validée en P2P par Consensus sur des dizaines de milliers d'ordinateurs simultanément dans le monde. C'est ce qui la rend incensurable, infalsifiable et impossible à éteindre.

`Voir aussi : [Architecture Haute Disponibilité](../haute_disponibilite.md)`
