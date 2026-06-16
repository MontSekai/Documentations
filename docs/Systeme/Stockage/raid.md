---
tags:
  - Systeme
  - Stockage
  - RAID
---

# RAID (Redundant Array of Independent Disks)

La technologie de mutualisation des disques durs pour gagner en vitesse et survivre aux pannes matérielles.

## 1. Définition
Le **RAID** est un concept matériel (carte contrôleur RAID) ou logiciel permettant de combiner plusieurs petits disques durs physiques indépendants en une seule grosse grappe logique (un "Volume") aux yeux du système d'exploitation. L'objectif est d'augmenter la vitesse de lecture/écriture, ou d'assurer la tolérance aux pannes, ou les deux.

## 2. Description / Fonctionnement (Les niveaux de RAID)
* **RAID 0 (Stripping / La Vitesse)** : Les données sont coupées en morceaux et réparties sur au moins 2 disques qui écrivent en même temps. Vitesse doublée. **Danger :** Si 1 seul disque lâche, l'intégralité des données est définitivement perdue.
* **RAID 1 (Mirroring / La Sécurité)** : Les données sont clonées à l'identique (en miroir) sur 2 disques. Vitesse normale. **Avantage :** Si 1 disque meurt, le système continue de fonctionner instantanément sur l'autre, aucune perte.
* **RAID 5 (Parité / L'équilibre)** : Nécessite au moins 3 disques. Les données sont réparties (comme le RAID 0) avec en plus un calcul mathématique de "parité" distribué sur tous les disques. Si 1 disque meurt, le contrôleur recalcule à la volée les données manquantes grâce à la parité des 2 autres. On perd toujours la capacité totale de stockage équivalente à 1 disque.
* **RAID 10 (Le compromis Ultime)** : Une grappe RAID 0 de sous-grappes RAID 1 (minimum 4 disques nécessaires). Très rapide en lecture/écriture et extrêmement sécurisé (on peut perdre jusqu'à 2 disques selon leur emplacement). Très coûteux.

## 3. Utilisation / Cas Pratique
Dans un serveur d'entreprise rackable (ex: *Dell PowerEdge*, *HPE ProLiant*), l'entreprise achète 8 disques durs physiques de 2 To. 
La carte matérielle RAID interne va les configurer en RAID 5 ou 6 (autorisant la mort de 2 disques).
Si une alerte rouge s'allume sur la baie signalant un disque mort, l'administrateur peut extraire le disque défectueux "à chaud" sans éteindre le serveur (*Hot-Swap*), en insérer un neuf, et la carte RAID va lancer la *Reconstruction* automatique des données dessus pendant la nuit sans jamais interrompre la production du serveur.

> [!CAUTION]
> **Le RAID N'EST PAS UNE SAUVEGARDE !** Le RAID protège de la panne matérielle. Mais si un virus ransomware chiffre les fichiers ou si un utilisateur supprime un dossier par erreur, la modification est écrite en miroir sur tous les disques du RAID instantanément. Seule [une vraie sauvegarde à froid hors-ligne (Veeam)](../Services/sauvegarde.md) permet de restaurer la donnée dans ces cas-là.
