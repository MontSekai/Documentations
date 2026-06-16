---
tags:
  - Systeme
  - OS
  - Architecture
---

# Noyau (Kernel)

Le cœur du réacteur des systèmes d'exploitation.

## 1. Définition
Le **Noyau** (ou *Kernel*) est la partie fondamentale et centrale d'un système d'exploitation (Le noyau *Linux*, le noyau *Windows NT*, ou le noyau *XNU* d'Apple). C'est le chef d'orchestre absolu, le pont logiciel direct et exclusif entre les composants électroniques physiques de l'ordinateur (Le Matériel / *Hardware*) et les différents logiciels (Les Applications / *Software*).

## 2. Description / Fonctionnement
Le processeur de l'ordinateur (CPU) possède deux modes de privilèges de sécurité extrêmement stricts :
* **Le Mode Utilisateur (User Space)** : Là où s'exécutent les logiciels normaux (Navigateur web, Jeux, Base de données, Scripts). Ces logiciels n'ont absolument AUCUN droit d'accès direct au matériel.
* **Le Mode Noyau (Kernel Space)** : La forteresse réservée au noyau. Lui seul a l'autorisation de parler à la puce de RAM, d'envoyer des impulsions à la carte réseau ou de lire les secteurs du disque dur.

Quand un jeu vidéo veut afficher un pixel 3D complexe sur la carte graphique, il ne peut pas le faire lui-même. Il doit exécuter un **Appel Système (System Call)** vers le noyau. Le noyau vérifie d'abord que le jeu a le droit de faire ça (Sécurité), puis c'est le noyau lui-même qui envoie l'ordre au pilote (*Driver*) de la carte graphique.

## 3. Utilisation / Cas Pratique
Le **Noyau Linux** (créé de toutes pièces par Linus Torvalds en 1991) est aujourd'hui de très loin le noyau le plus utilisé au monde. Il est le moteur libre et open-source de tous les smartphones Android, de la majorité écrasante des serveurs web mondiaux, des routeurs internet, des télévisions connectées, et de l'IoT.
Si le noyau détecte une erreur mathématique fatale, un pilote corrompu ou une corruption grave dans la mémoire RAM, il arrête instantanément l'intégralité du système par sécurité stricte pour éviter de détruire les disques durs : C'est le fameux **Kernel Panic** sous Linux, ou l'**Écran Bleu de la Mort (BSOD)** sous Windows.

`Voir aussi : [Les commandes Linux](../OS/commande_linux.md)`
