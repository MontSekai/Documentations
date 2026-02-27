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

*(Note sur le **bit de parité** : En télécommunication bas niveau - couche 1 et 2 OSI - un "bit de parité" peut être ajouté à une trame binaire pour détecter des erreurs de transmission de données matérielles. Cependant, à la couche IP - couche 3 - dans l'adresse IP elle-même, chaque bit sert uniquement au routage (il n'y a pas de bit de parité intégré à l'adresse). La vérification d'erreur se fait par un "Checksum / Somme de contrôle" dans l'en-tête du paquet IP.)*

### 2. Le Masque de sous-réseau et le CIDR
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

Pourquoi retirer 2 ? Dans chaque sous-réseau, **deux adresses sont toujours réservées** et ne peuvent techniquement pas être assignées à un ordinateur ou une carte réseau :

1. **L'Adresse Réseau (_Network Address_)** :
   * C'est la toute première adresse du bloc (tous les bits de la partie hôte sont à `0`).
   * Elle sert d'identifiant unique pour router le trafic vers le réseau global lui-même (ex: la rue).
   * Dans un sous-réseau "standard" `/24`, elle se termine par `.0`.
   
2. **L'Adresse de Diffusion (_Broadcast Address_)** :
   * C'est la toute dernière adresse du bloc (tous les bits de la partie hôte sont à `1`).
   * Elle sert à envoyer un paquet à **toutes les machines** du sous-réseau simultanément (ex: une annonce générale dans la rue).
   * Dans un sous-réseau "standard" `/24`, elle se termine par `.255`.

### Exemple de décodage d'une IP (Tableau)

Prenons une adresse classique : `192.168.1.130/24`. 
Qu'est ce que l'ordinateur comprend de ça ? 

| Élément | Valeur / Exemple | Explication |
| :--- | :--- | :--- |
| **L'IP de la machine** | `192.168.1.130` | L'adresse unique configurée sur mon poste. |
| **Le Masque** *(Mask)* | `255.255.255.0` | Déduit du `/24`. Il indique que les 3 premiers octets (192.168.1) fixent le réseau ! |
| **L'Adresse Réseau** *(Network Address)* | `192.168.1.0` | La première adresse. Utilisée dans les tables de routage pour désigner tout le bloc. |
| **La plage utilisable** *(Host Range)* | `.1` jusqu'à `.254` | Les 254 adresses que je peux distribuer manuellement ou via DHCP à mes appareils. |
| **L'Adresse de diffusion** *(Broadcast)* | `192.168.1.255` | La dernière adresse. Si on ping cette IP, tout le réseau `192.168.1.x` répondra. |

*(Note: Le mythe du ".0=Réseau" et ".255=Broadcast" n'est vrai **que dans le cadre d'un /24 ou d'un /16**. Sur un réseau plus petit comme un /28, l'adresse réseau pourrait très bien être `.16` et le broadcast `.31` !)*

**Exemple rapide - Calcul pour un sous-réseau `/28` :**
* L'adresse fait toujours 32 bits au total.
* Bits réservés par le masque (partie Réseau) : 28 bits (notation CIDR).
* Bits restants pour les machines ($n$) : $32 - 28 = \mathbf{4}$ bits.
* Nombre total d'IPs dans le bloc : $2^4 = \mathbf{16}$ IPs (ex: de `.0` à `.15`).
* Nombre d'**hôtes configurables** : $16 - 2 = \mathbf{14}$ machines possibles.
## Fonctionnement

...
