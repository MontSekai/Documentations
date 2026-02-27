---
tags:
  - Reseau
  - Protocoles
  - TCP
  - IP
---

# TCP/IP

La suite des protocoles TCP/IP (Transmission Control Protocol / Internet Protocol) est l'ensemble des protocoles utilisés pour le transfert de données sur Internet.

## Couches du modèle OSI / TCP/IP
## Adressage IPv4 : Fonctionnement détaillé

Une adresse IP (IPv4) est l'identifiant logique d'une interface connectée à un réseau IP. 

### 1. Bits et Octets
Une adresse IPv4 est composée de **32 bits** (des 0 et des 1).
Pour la rendre lisible par les humains, elle est divisée en **4 octets** de 8 bits chacun, séparés par des points (notation décimale pointée).
* **Exemple** : `192.168.1.10`
* **Valeur en binaire** : `11000000.10101000.00000001.00001010`

Pour convertir un octet (8 bits) en nombre décimal, on utilise le tableau des puissances de 2 suivant :

| Binaire | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Valeur**| **128** | **64** | **32** | **16** | **8** | **4** | **2** | **1** |

*(Note sur le **bit de parité** : En télécommunication bas niveau - couche 1 et 2 [OSI](modele_osi.md) - un "bit de parité" peut être ajouté à une [trame binaire](ethernet_trames.md) pour détecter des erreurs de transmission de données matérielles. Cependant, à la couche IP - couche 3 - dans l'adresse IP elle-même, chaque bit sert uniquement au routage (il n'y a pas de bit de parité intégré à l'adresse). La vérification d'erreur se fait par un "Checksum / Somme de contrôle" dans l'en-tête du paquet IP.)*

### 2. Classes d'adresses IP et IPs remarquables

Historiquement, les adresses IPv4 ont été divisées en classes pour faciliter leur distribution :

| Classe | Plage d'adresses réseau | Masque par défaut | Cas d'usage typique |
| :--- | :--- | :--- | :--- |
| **A** | `1.0.0.0` à `126.0.0.0` | `/8` (255.0.0.0) | Réseaux géants (gouvernements, grands opérateurs). |
| **B** | `128.0.0.0` à `191.255.0.0` | `/16` (255.255.0.0) | Moyennes et grandes entreprises. |
| **C** | `192.0.0.0` à `223.255.255.0` | `/24` (255.255.255.0) | Petits réseaux (domestique, TPE). |

Certaines adresses et plages ont des rôles très spécifiques :

| IP / Plage | Nom | Rôle |
| :--- | :--- | :--- |
| `127.0.0.1` | **Loopback** (Boucle locale) | Permet à une machine de communiquer avec elle-même pour tester sa propre carte réseau. |
| `169.254.x.x` | **APIPA** | Adresse auto-assignée par l'OS si le serveur [DHCP](../../Systeme/Services/dhcp.md) (qui distribue les IP) est injoignable. |
| `0.0.0.0` | **Route par défaut** / Any | Désigne "n'importe quelle adresse" ou la route de sortie globale vers Internet. |
| `255.255.255.255` | **Broadcast global** | Envoie un message à absolument toutes les machines du réseau physique local. |

### 3. Le Masque de sous-réseau et le CIDR
Pour savoir quelle partie de l'adresse identifie le **Réseau** et quelle partie identifie l'**Hôte** (la machine), on utilise un masque de sous-réseau.
Le masque est aussi composé de 32 bits, mais c'est toujours une suite ininterrompue de `1` suivie d'une suite de `0`.
* **Exemple de masque** : `255.255.255.0`
* **Valeur en binaire** : `11111111.11111111.11111111.00000000`

**La notation CIDR** (Classless Inter-Domain Routing) est un raccourci pour écrire ce masque. Elle compte simplement le nombre de bits à `1` présents dans le masque.
* `255.255.255.0` possède 24 bits positionnés à `1`, on l'écrit donc **`/24`**.
* Le réseau complet s'écrit alors : `192.168.1.0/24`.

### 3. Calcul du nombre d'IP disponibles (Puissances de 2)
Le calcul des hôtes possibles se fait grâce aux puissances de 2 (symbolisé `2^n`), où `n` correspond aux **bits restants à 0** dans le masque de sous-réseau (la partie hôte).

**Formule magique : $2^n - 2$**

Pourquoi retirer 2 ? Peu importe la taille de votre sous-réseau, **la première et la dernière adresse sont toujours réservées** et ne peuvent jamais être attribuées à une machine informatique :

1. **La Première Adresse = Adresse Réseau (_Network Address_)** :
   * Elle désigne l'ensemble du réseau. C'est l'adresse lue par les routeurs pour diriger le trafic global vers la bonne direction.
   
2. **La Dernière Adresse = Adresse de Diffusion (_Broadcast Address_)** :
   * Elle sert à envoyer un message simultanément à toutes les machines présentes dans la totalité de ce sous-réseau précis.

*(Remarque : Il est courant de penser qu'une adresse réseau finit forcément par `.0` et qu'une adresse de diffusion finit forcément par `.255`. C'est vrai pour les réseaux standards `/24`, mais ce n'est plus le cas dès que l'on découpe des sous-réseaux plus petits, où le réseau pourrait très bien être `.16` et la diffusion `.31`.)*

### Exemple de décodage d'une IP (Tableau)

Prenons une adresse classique : `192.168.1.130/24`. 
Qu'est ce que l'ordinateur comprend de ça ? 

| Élément | Valeur / Exemple | Explication |
| :--- | :--- | :--- |
| **L'IP de la machine** | `192.168.1.130` | L'adresse unique configurée sur mon poste. |
| **Le Masque** *(Mask)* | `255.255.255.0` | Déduit du `/24`. Il indique que les 3 premiers octets (192.168.1) fixent le réseau ! |
| **L'Adresse Réseau** *(Network Address)* | `192.168.1.0` | La **première** adresse. Utilisée dans les tables de routage. |
| **La plage utilisable** *(Host Range)* | `.1` jusqu'à `.254` | Les 254 adresses que je peux distribuer (de la 2ème à l'avant-dernière). |
| **L'Adresse de diffusion** *(Broadcast)* | `192.168.1.255` | La **dernière** adresse du bloc. Pinguer cette IP interroge tout le réseau local. |

**Exemple de découpage plus complexe : Calcul pour un sous-réseau `/28`**
* L'adresse fait toujours 32 bits au total, sur lesquels le réseau en bloque 28 (notation CIDR).
* Bits restants pour les machines ($n$) : $32 - 28 = \mathbf{4}$ bits.
* Nombre total d'IPs dans le bloc : $2^4 = \mathbf{16}$ IPs.
* Par exemple, si la première IP est `192.168.1.0` (Adresse Réseau), les IP utilisables vont de `.1` à `.14`, et la dernière est `192.168.1.15` (Adresse de Diffusion).
* Nombre d'**hôtes configurables** : $16 - 2 = \mathbf{14}$ machines possibles.
Le fonctionnement détaillé du modèle TCP/IP se retrouve dans la comparaison globale sur la page du [Modèle OSI](modele_osi.md).
