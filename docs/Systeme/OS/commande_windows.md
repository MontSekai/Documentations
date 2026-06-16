---
tags:
  - Systeme
  - OS
  - Windows
---

# Mémento : Commandes Réseau Windows

Dans le support et l’administration système, savoir diagnostiquer rapidement un problème réseau en ligne de commande fait gagner un temps énorme. Voici un mémento des commandes essentielles sous Windows.

## 1. Configuration & Dépannage Réseau

| Commande | Action | Exemple concret |
| :--- | :--- | :--- |
| `ipconfig` | Afficher la configuration réseau de base | `ipconfig` |
| `ipconfig /all` | Afficher des informations détaillées IP, DNS et DHCP | `ipconfig /all` |
| `ipconfig /release` | Libérer l’adresse IP actuelle | `ipconfig /release` |
| `ipconfig /renew` | Renouveler l’adresse IP depuis le serveur DHCP | `ipconfig /renew` |
| `ipconfig /flushdns` | Vider le cache DNS pour corriger des problèmes d’accès aux sites | `ipconfig /flushdns` |

## 2. Tests de Connectivité

| Commande | Action | Exemple concret |
| :--- | :--- | :--- |
| `ping` | Tester la connectivité vers une machine ou un serveur | `ping 8.8.8.8` |
| `ping -t` | Lancer un ping en continu (Ctrl+C pour arrêter) | `ping -t google.com` |
| `tracert` | Identifier où se situe un blocage sur le réseau | `tracert google.com` |
| `nslookup` | Vérifier la résolution DNS d’un nom de domaine | `nslookup exemple.com` |

## 3. Surveillance Réseau & Système

| Commande | Action | Exemple concret |
| :--- | :--- | :--- |
| `netstat -an` | Afficher les connexions réseau actives et les ports ouverts | `netstat -an` |
| `netstat -b` | Associer les connexions réseau aux applications (Admin requis) | `netstat -b` |
| `arp -a` | Afficher la table ARP (correspondance IP ←→ MAC) | `arp -a` |
| `getmac` | Afficher les adresses MAC des interfaces réseau | `getmac` |

## 4. Informations et Services Windows

| Commande | Action | Exemple concret |
| :--- | :--- | :--- |
| `hostname` | Afficher le nom de l’ordinateur | `hostname` |
| `net use` | Vérifier ou connecter des lecteurs réseau | `net use Z: \\serveur\partage` |
| `net share` | Lister les ressources partagées sur la machine | `net share` |
| `net start` | Afficher les services Windows en cours d’exécution | `net start` |
| `tasklist` | Lister les processus actifs sur le système | `tasklist` |

## 5. Diagnostic Avancé

| Commande | Action | Exemple concret |
| :--- | :--- | :--- |
| `route print` | Afficher la table de routage réseau | `route print` |
| `netsh advfirewall` | Vérifier les règles du pare-feu Windows | `netsh advfirewall firewall show rule name=all` |
