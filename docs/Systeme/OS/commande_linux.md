---
tags:
  - Systeme
  - OS
  - Debian
  - Linux
---

# Mémento : Commandes Linux (Debian)

Debian est un système d’exploitation libre pour votre ordinateur, considéré comme l'un des piliers des distributions GNU/Linux modernes. Voici un mémento des commandes d'administration essentielles.

## 1. Gestion des Utilisateurs

| Commande | Action | Exemple concret |
| :--- | :--- | :--- |
| `adduser` | Créer un nouvel utilisateur avec son dossier personnel | `sudo adduser jean` |
| `passwd` | Modifier le mot de passe d'un utilisateur | `sudo passwd jean` |
| `deluser` | Supprimer un utilisateur | `sudo deluser jean` |
| `usermod -aG` | Ajouter un utilisateur à un groupe (ex: sudo) | `sudo usermod -aG sudo jean` |

> [!NOTE] 
> Pour `deluser`, ajoutez l'option `--remove-home` pour effacer également les fichiers personnels de l'utilisateur.

## 2. Navigation et Listage de fichiers (`ls`)

| Commande | Action | Exemple concret |
| :--- | :--- | :--- |
| `ls` | Liste les fichiers et dossiers visibles | `ls /var/log/` |
| `ls -l` | Affiche une liste détaillée (droits, taille, date) | `ls -l` |
| `ls -a` | Affiche tous les fichiers, y compris les fichiers cachés (`.`) | `ls -a` |
| `ls -h` | Affiche la taille dans un format humain (Ko, Mo) | `ls -lh` |
| `ls -t` | Trie les résultats par date de modification (récents en 1er) | `ls -lt` |
| `ls -la` | Liste détaillée et intégrale incluant les fichiers cachés | `ls -la` |

## 3. Gestion des Fichiers et des Droits

| Commande | Action | Exemple concret |
| :--- | :--- | :--- |
| `chown` | Changer le propriétaire et/ou le groupe | `sudo chown jean:admin fichier.txt` |
| `chown -R` | Changer le propriétaire récursivement pour un dossier | `sudo chown -R jean:admin /dossier/` |
| `chmod` (lettres) | Modifier les droits `r` (lire), `w` (écrire), `x` (exécuter) | `sudo chmod u+x script.sh` |
| `chmod` (octal) | Modifier les droits via système numérique (ex: 755) | `sudo chmod 755 script.sh` |

> [!TIP]
> **Le système Octal pour `chmod` :**
> - **4** : Lecture (Read)
> - **2** : Écriture (Write)
> - **1** : Exécution (eXecute)
> On additionne ces valeurs pour le Propriétaire, le Groupe et les Autres. Exemple : `755` = Propriétaire (4+2+1=7 : Tout), Groupe (4+1=5 : Lire/Exécuter), Autres (4+1=5 : Lire/Exécuter).

## 4. Configuration Réseau et Nom d'hôte

| Commande | Action | Exemple concret |
| :--- | :--- | :--- |
| `hostnamectl` | Modifier le nom d'hôte de la machine | `sudo hostnamectl set-hostname SRV-WEB-01` |
| `ip a` | Voir l'adresse IP actuelle (équivalent ipconfig) | `ip a` |
| `systemctl restart` | Redémarrer un service (ex: service réseau) | `sudo systemctl restart networking` |
| `ping` | Vérifier la connectivité avec une autre machine | `ping 8.8.8.8` |
| `traceroute` | Identifier le chemin emprunté par les paquets | `traceroute google.com` |

## 5. Requêtes Web (`curl`)

| Commande | Action | Exemple concret |
| :--- | :--- | :--- |
| `curl` | Affiche le code source d'une page web | `curl https://site.com` |
| `curl -I` | Affiche uniquement les en-têtes HTTP (Headers) | `curl -I https://site.com` |
| `curl -O` | Télécharge le fichier et le sauvegarde localement | `curl -O https://site.com/fichier.zip` |
| `curl -k` | Ignore les erreurs de certification SSL | `curl -k https://site.com` |
| `curl -X POST` | Envoie une requête POST vers une API | `curl -X POST -d "cle=val" api.com` |

## 6. Maintenance au quotidien

| Commande | Action | Exemple concret |
| :--- | :--- | :--- |
| `apt update && apt upgrade` | Mettre à jour la liste des paquets et le système | `sudo apt update && sudo apt upgrade -y` |
| `df -h` | Voir l'utilisation de l'espace disque | `df -h` |
| `free -m` | Voir l'utilisation de la RAM | `free -m` |
| `grep -r` | Rechercher du texte dans les fichiers d'un dossier | `grep -r "Erreur" /var/log/` |
| `top` / `htop` | Voir les processus en cours | `top` |
