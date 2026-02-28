---
tags:
  - Systeme
  - OS
  - Debian
  - Linux
---

# Commande Linux

Debian est un système d’exploitation libre pour votre ordinateur, considéré comme l'un des piliers des distributions GNU/Linux modernes. 
Voici un mémento des commandes d'administration essentielles.

## 1. Gestion des Utilisateurs

* **Créer un nouvel utilisateur** (avec son dossier personnel interactif) :
  ```bash
  sudo adduser nom_utilisateur
  ```
  *(La commande `useradd` existe aussi mais est beaucoup plus basique et ne crée pas de dossier personnel par défaut, préférez `adduser`).*

* **Modifier le mot de passe d'un utilisateur** :
  ```bash
  sudo passwd nom_utilisateur
  ```

* **Supprimer un utilisateur** :
  ```bash
  sudo deluser nom_utilisateur
  ```
  *(Ajoutez l'option `--remove-home` pour effacer également ses fichiers personnels).*

* **Ajouter un utilisateur au groupe `sudo` (droits administrateur)** :
  ```bash
  sudo usermod -aG sudo nom_utilisateur
  ```

## 2. Navigation et Listage de fichiers (`ls`)

La commande `ls` (List) permet d'afficher le contenu d'un répertoire. Elle prend tout son sens lorsqu'elle est combinée à ses options.

| Commande / Option | Résultat | Explication |
| :--- | :--- | :--- |
| **`ls`** | Affichage simple | Liste les fichiers et dossiers visibles du répertoire courant dans l'ordre alphabétique. |
| **`ls -l`** | Liste détaillée | Affiche les fichiers sous forme de longue liste détaillée (propriétaire, groupe, droits, taille, date de modification). |
| **`ls -a`** | Fichiers cachés | Affiche **tous** les fichiers, y compris les fichiers cachés (ceux commençant par un point `.`). |
| **`ls -h`** | Tailles lisibles | Affiche la taille des fichiers dans un format humainement lisible (Ko, Mo, Go) au lieu des octets purs. |
| **`ls -t`** | Tri par date | Trie les résultats par date de dernière modification (les plus récents en premier). |
| **`ls -la`** *(combinaison)* | Le grand classique | Combine `-l` et `-a` pour avoir une liste détaillée et intégrale incluant les fichiers de configuration cachés. |


## 3. Gestion des Fichiers et des Droits (Chown / Chmod)

Sous Linux, chaque fichier possède 3 niveaux administratifs : le **Propriétaire** (U - *User*), le **Groupe** (G - *Group*) et les **Autres** (O - *Others*). Les droits se lisent avec `ls -l`.

### Les permissions alphanumériques (r, w, x)

| Symbole | Signification | Explication |
| :---: | :--- | :--- |
| **`r`** | **R**ead (Lecture) | Permet de lire le contenu du fichier (ou lister le contenu du dossier). |
| **`w`** | **W**rite (Écriture) | Permet de modifier le fichier (ou créer/supprimer dans le dossier). |
| **`x`** | e**X**ecute (Exécution) | Permet d'exécuter le script/programme (ou d'entrer à l'intérieur du dossier). |
| **`-`** | Droit refusé | L'utilisateur n'a pas cette permission. |
| **`d`** | Directory | (Apparaît en tout premier) Indique que cet élément est un dossier, pas un fichier. |

*Exemple de lecture d'un `ls -l` :* `drwxr-xr--`
-> C'est un **d**ossier. Le **rwx** définit que le propriétaire fait tout. Le **r-x** définit que le groupe peut lire et y entrer mais pas écrire. Le **r--** définit que tous les autres peuvent seulement lister mais pas y entrer ni écrire.

### `chown` (Change Owner)

Changer le propriétaire et/ou le groupe propriétaire d'un fichier/dossier.
```bash
sudo chown utilisateur:groupe fichier.txt  # Assigne l'utilisateur et le groupe
sudo chown -R utilisateur:groupe /dossier/ # L'option -R l'applique récursivement (au dossier ET tout son contenu)
```

### `chmod` (Change Mode - Système Octal)

Plutôt que d'utiliser les lettres, on utilise souvent le système numérique, où chaque droit a une valeur. On additionne ces valeurs pour chaque niveau (Propriétaire, Groupe, Autres).

| Valeur | Permission correspondante |
| :---: | :--- |
| **4** | Lecture (Read) |
| **2** | Écriture (Write) |
| **1** | Exécution (eXecute) |

* **Exemples courants :**
```bash
sudo chmod 755 script.sh   # Propriétaire (4+2+1=7 : Tout), Groupe et Autres (4+1=5 : Lire/Exécuter)
sudo chmod 644 fichier.txt # Propriétaire (4+2=6 : Lire/Écrire), Groupe et Autres (4=4 : Lire)
sudo chmod 777 dossier/    # Tout le monde fait tout (Dangereux !)
```

## 4. Configuration Réseau et Nom d'hôte

* **Modifier le nom d'hôte (hostname)** de la machine :
  Utilisez `hostnamectl` ou modifiez directement les fichiers natifs :
  ```bash
  sudo hostnamectl set-hostname NOUVEAU_NOM
  ```
  *(Il est également conseillé de modifier `/etc/hosts` manuellement pour remplacer l'ancien nom par le nouveau sur la ligne `127.0.1.1`)*.

* **Configuration IP et Interfaces réseaux (NetworkManager / netplan / interfaces)** :
  * Pour voir l'adresse IP actuelle (équivalent de `ipconfig` sur Windows) :
    ```bash
    ip a
    ```
  * Sur un vieux système ou sur serveur pur, le réseau se configure traditionnellement dans :
    ```bash
    sudo nano /etc/network/interfaces
    ```
  * Pour redémarrer le service réseau :
    ```bash
    sudo systemctl restart networking
    ```

* **Tests de connectivité et diagnostic réseau** :
  * Pour vérifier la connectivité avec une autre machine :
    ```bash
    ping [IP ou nom]
    ```
  * Pour identifier le chemin (les routeurs) emprunté par les paquets jusqu'à la destination :
    ```bash
    traceroute [IP ou nom]
    ```

## 5. Autres commandes utiles au quotidien

* **Mettre à jour la liste des paquets et le système** :
  ```bash
  sudo apt update && sudo apt upgrade -y
  ```
* **Voir l'utilisation de l'espace disque** (en format lisible humaine "h") :
  ```bash
  df -h
  ```
* **Voir l'utilisation de la RAM** :
  ```bash
  free -m
  ```
* **Rechercher du texte dans les fichiers (`grep`)** :
  ```bash
  grep -r "Texte à trouver" /var/log/
  ```
* **Voir les processus en cours (équivalent gestionnaire des tâches)** :
  ```bash
  top
  # ou encore mieux, utilisez 'htop' s'il est installé (sudo apt install htop)
  ```
