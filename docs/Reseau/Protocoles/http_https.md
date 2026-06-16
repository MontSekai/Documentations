---
tags:
  - Reseau
  - Protocoles
  - Web
---

# HTTP et HTTPS

Le cœur de la navigation Web mondiale.

## 1. Définition
* **HTTP (HyperText Transfer Protocol)** : Le protocole historique de la couche applicative (couche 7) qui permet d'échanger des pages Web structurées entre un client (navigateur) et un serveur.
* **HTTPS (HTTP Secure)** : La version sécurisée de HTTP, encapsulée dans un tunnel chiffré TLS/SSL.

## 2. Description / Fonctionnement
Le protocole fonctionne sur le principe de **Requête/Réponse** avec des verbes d'action stricts :
* `GET` : Demander la lecture d'une page au serveur.
* `POST` : Envoyer des données au serveur (ex: valider un formulaire de connexion ou un panier).
* `PUT / DELETE` : Modifier ou supprimer des données.

**Le problème mortel du HTTP (Port 80)** : Absolument tout le texte (y compris les mots de passe) transite en clair sur le câble. Un pirate sur le même réseau Wi-Fi public peut lire toutes les requêtes avec Wireshark.
**La solution HTTPS (Port 443)** : Le serveur possède un Certificat de sécurité cryptographique (fourni par une autorité comme *Let's Encrypt*). Lors de la connexion, le client et le serveur font un "Handshake" pour convenir d'une clé de chiffrement asymétrique. Tout le trafic devient illisible de l'extérieur.

## 3. Utilisation / Cas Pratique
Aujourd'hui, **100% des sites web professionnels imposent le HTTPS** par défaut. Les navigateurs modernes (Chrome, Firefox) affichent d'ailleurs une alerte rouge effrayante bloquant la page si un site est encore en HTTP.
Dans une architecture d'entreprise, le passage difficile du HTTP au HTTPS est souvent géré par un équipement frontal appelé [Reverse Proxy](../Securite/proxy_firewall.md) (comme Nginx) qui s'occupe de chiffrer/déchiffrer le trafic lourd (*Terminaison SSL*) pour soulager les petits serveurs web situés derrière lui.

`Voir aussi : [Reverse Proxy et WAF](../Securite/proxy_firewall.md) | [Chiffrement et PKI](../../Cybersecurite/pki_crypto.md)`
