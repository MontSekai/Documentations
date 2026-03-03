---
tags:
  - Reseau
  - ACL
  - Securite
---

# ACL (Access Control List)

Une **ACL** est une liste de règles de contrôle d'accès appliquée sur une interface d'un routeur ou d'un switch de couche 3. Elle filtre le trafic en **autorisant ou refusant** des paquets selon des critères définis.

## Types d'ACL (logique Cisco)

| Type | Numérotation | Critère de filtrage |
| :--- | :---: | :--- |
| **Standard** | 1–99 / 1300–1999 | **Adresse IP Source** uniquement |
| **Étendue** | 100–199 / 2000–2699 | IP Source, IP Destination, Protocole (TCP/UDP/ICMP), Port |
| **Nommée** | Nom alphanumériqu | Standard ou étendue, identifiée par un nom lisible |

> [!TIP]
> **Règle de placement :**
> - ACL **Standard** → Placer le plus **près possible de la destination** (car ne filtre que la source, bloquer trop tôt couperait d'autres trafics).
> - ACL **Étendue** → Placer le plus **près possible de la source** (filtre plus précisément, évite le trafic inutile sur le réseau).

## Fonctionnement

Comme les règles de pare-feu, une ACL est traitée **de haut en bas**. La première règle correspondante est appliquée. Une règle **"deny any"** implicite termine toujours une ACL Cisco.

```
! ACL Étendue (exemple Cisco)
ip access-list extended FILTRAGE_WEB
  permit tcp 192.168.1.0 0.0.0.255 any eq 80    ! Autorise HTTP depuis le réseau 192.168.1.0/24
  permit tcp 192.168.1.0 0.0.0.255 any eq 443   ! Autorise HTTPS
  deny   ip 192.168.1.50 0.0.0.0 any            ! Bloque spécifiquement le poste .50
  permit ip any any                              ! Autorise tout le reste
```

## Wildcard Mask (Masque inversé)

Sur les équipements Cisco, les ACL utilisent un **wildcard mask** (masque de bits inversé, opposé du masque de sous-réseau).

| Réseau CIDR | Masque normal | Wildcard mask |
| :--- | :---: | :---: |
| `192.168.1.0/24` | `255.255.255.0` | `0.0.0.255` |
| `10.0.0.0/8` | `255.0.0.0` | `0.255.255.255` |
| `172.16.0.0/12` | `255.240.0.0` | `0.15.255.255` |
| Un hôte unique (host) | — | `0.0.0.0` |
| N'importe qui (any) | — | `255.255.255.255` |

## Application sur une interface

Une ACL n'est active que lorsqu'elle est **appliquée sur une interface** dans un sens (entrant `in` ou sortant `out`).

```bash
interface GigabitEthernet0/1
 ip access-group FILTRAGE_WEB in   ! Applique l'ACL sur le trafic entrant
```

## ACL et [VLAN](vlan.md) / [Routage inter-VLAN](routage.md)

Les ACL sont souvent utilisées en complément des VLANs pour **contrôler les flux entre VLANs** au niveau du routeur ou du switch de couche 3. On parle alors de **micro-segmentation** : même si deux VLANs peuvent techniquement se router, l'ACL détermine précisément ce qui est autorisé à passer.

## Vérification (Cisco)

```bash
show access-lists                    ! Affiche toutes les ACL et le nombre de correspondances
show ip interface GigabitEthernet0/1 ! Affiche les ACL appliquées sur une interface
