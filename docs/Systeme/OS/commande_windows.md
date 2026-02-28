---
tags:
  - Systeme
  - OS
  - Windows
---

# Commandes Réseau Windows

Dans le support et l’administration système, **savoir diagnostiquer rapidement un problème réseau en ligne de commande** fait gagner un temps énorme.
Voici 20 commandes essentielles, utilisées au quotidien par les techniciens informatiques pour le dépannage, la maintenance et l’exploitation réseau :

## Configuration & dépannage réseau

1. **`ipconfig`** – Afficher la configuration réseau de base
2. **`ipconfig /all`** – Afficher des informations détaillées IP, DNS et DHCP
3. **`ipconfig /release`** – Libérer l’adresse IP actuelle
4. **`ipconfig /renew`** – Renouveler l’adresse IP depuis le serveur DHCP
5. **`ipconfig /flushdns`** – Vider le cache DNS pour corriger des problèmes d’accès aux sites

## Tests de connectivité

6. **`ping [IP ou nom]`** – Tester la connectivité vers une machine ou un serveur
   * **`ping -t [IP ou nom]`** – Lancer un ping en continu (Ctrl+C pour arrêter)
7. **`tracert [IP ou nom]`** – Identifier où se situe un blocage sur le réseau
8. **`nslookup [domaine]`** – Vérifier la résolution DNS d’un nom de domaine

## Surveillance réseau & système

9. **`netstat -an`** – Afficher les connexions réseau actives et les ports ouverts
10. **`netstat -b`** – Associer les connexions réseau aux applications (Admin requis)

## Informations machine

11. **`arp -a`** – Afficher la table ARP (correspondance IP ←→ MAC)
12. **`hostname`** – Afficher le nom de l’ordinateur
13. **`getmac`** – Afficher les adresses MAC des interfaces réseau

## Partages & services Windows

14. **`net use`** – Vérifier ou connecter des lecteurs réseau
15. **`net share`** – Lister les ressources partagées sur la machine
16. **`net start`** – Afficher les services Windows en cours d’exécution

## Diagnostic avancé

18. **`tasklist`** – Lister les processus actifs sur le système
19. **`route print`** – Afficher la table de routage réseau
20. **`netsh advfirewall firewall show rule name=all`** – Vérifier les règles du pare-feu Windows
