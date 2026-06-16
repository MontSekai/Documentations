---
tags:
  - Systeme
  - Stockage
  - SAN
  - Protocoles
---

# iSCSI (Internet Small Computer Systems Interface)

Le stockage en réseau (SAN) à très haute performance.

## 1. Définition
L'**iSCSI** est un protocole de stockage réseau (SAN - *Storage Area Network*) qui permet de transporter des requêtes et commandes de disque dur (commandes SCSI natives) à travers un réseau IP standard local (via des câbles Ethernet classiques RJ45 ou Fibre).

## 2. Description / Fonctionnement
Contrairement au [stockage NAS (NFS / SMB / CIFS)](netapp.md) où l'on partage un simple "dossier réseau" géré par un autre ordinateur, l'iSCSI partage un bloc physique pur et brut appelé le LUN (*Logical Unit Number*).
* **La Baie de stockage (La Cible / iSCSI Target)** : Une grosse baie matérielle (comme NetApp) découpe un bout de son pool de disques durs physiques et le met à disposition sur le port Ethernet.
* **Le Serveur (L'Initiateur / iSCSI Initiator)** : Le serveur Windows ou l'Hyperviseur (VMware/Proxmox) se connecte à ce disque via un simple câble réseau Ethernet.

**La Magie technologique de l'iSCSI** : Le serveur Windows a l'illusion totale que le disque dur iSCSI est vissé et branché physiquement à l'intérieur de sa propre carte mère. Il le voit dans le "Gestionnaire de disques" comme le lecteur local `D:\`, il peut le formater en NTFS, alors que le disque matériel est en réalité situé à 200 mètres dans une autre armoire du Datacenter !

## 3. Utilisation / Cas Pratique
L'iSCSI est la technologie fondatrice de la [Virtualisation moderne](../virtualisation.md) (et des Clouds).
Si 3 serveurs physiques VMware (les Hyperviseurs) exécutent les machines virtuelles (VM) de l'entreprise mais stockent les disques virtuels (.vmdk) de ces VM sur une baie de stockage **iSCSI partagée**, alors on obtient de la [Haute Disponibilité absolue](../../Reseau/haute_disponibilite.md).
Si le Serveur VMware n°1 prend feu et explose, le Serveur VMware n°2 peut immédiatement rallumer la VM à sa place, car il a lui aussi accès simultanément au même disque dur iSCSI sur le réseau. L'arrêt de service ne dure que le temps de redémarrage de la VM.
