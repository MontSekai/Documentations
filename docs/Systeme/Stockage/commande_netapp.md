---
tags:
  - Systeme
  - Stockage
  - NetApp
  - Commandes
  - CLI
---

# Mémento : Commandes NetApp (ONTAP)

Ce mémento regroupe les commandes en ligne (CLI) essentielles pour administrer une baie de stockage NetApp tournant sous le système d'exploitation ONTAP.
La CLI NetApp est hiérarchique. On utilise souvent le bouton `?` ou la touche `Tab` pour l'auto-complétion.

## 1. Gestion du Cluster et des Nœuds

| Commande | Action | Exemple concret |
| :--- | :--- | :--- |
| `cluster show` | Affiche l'état de santé général du cluster. | `cluster show` |
| `node show` | Affiche l'état des contrôleurs (nœuds) physiques. | `node show` |
| `system node hardware show`| Affiche les composants matériels d'un nœud. | `system node hardware show -node Node-01` |
| `version` | Affiche la version d'ONTAP installée. | `version` |

## 2. Gestion du Stockage Physique (Disques & Agrégats)

| Commande | Action | Exemple concret |
| :--- | :--- | :--- |
| `storage disk show` | Liste tous les disques physiques. | `storage disk show` |
| `storage disk show -broken`| Affiche uniquement les disques en panne. | `storage disk show -broken` |
| `storage aggregate show` | Liste les agrégats (groupes de disques RAID). | `storage aggregate show` |
| `storage aggregate show -space` | Affiche l'espace disponible et consommé d'un agrégat. | `storage aggregate show -aggregate aggr1_node1 -space` |

## 3. Gestion Logique (SVM & Volumes)

| Commande | Action | Exemple concret |
| :--- | :--- | :--- |
| `vserver show` | Liste les Storage Virtual Machines (SVM). | `vserver show` |
| `volume show` | Affiche la liste des volumes et leur état. | `volume show` |
| `volume show -vserver [svm]`| Filtre les volumes pour un SVM précis. | `volume show -vserver SVM_Prod` |
| `volume size` | Modifie la taille d'un volume. | `volume size -vserver SVM_Prod -volume vol_data -new-size 500GB` |
| `volume offline` / `online` | Désactive ou active un volume. | `volume offline -vserver SVM_Prod -volume vol_test` |

## 4. Gestion SAN (LUNs & iGroup)

| Commande | Action | Exemple concret |
| :--- | :--- | :--- |
| `lun show` | Liste tous les LUNs (disques virtuels SAN). | `lun show` |
| `lun mapping show` | Affiche à quels serveurs (iGroup) le LUN est présenté. | `lun mapping show` |
| `igroup show` | Affiche les groupes d'initiateurs (groupes de serveurs).| `igroup show` |

## 5. Gestion NAS (CIFS / SMB)

| Commande | Action | Exemple concret |
| :--- | :--- | :--- |
| `vserver cifs show` | Affiche l'état du service CIFS et l'intégration AD. | `vserver cifs show` |
| `vserver cifs share show` | Liste les partages réseaux Windows (SMB). | `vserver cifs share show` |
| `vserver cifs session show`| Affiche les utilisateurs actuellement connectés. | `vserver cifs session show` |

## 6. Protection des Données (Snapshots & SnapMirror)

| Commande | Action | Exemple concret |
| :--- | :--- | :--- |
| `volume snapshot show` | Liste les snapshots (photos instantanées) d'un volume.| `volume snapshot show -vserver SVM_Prod -volume vol_data` |
| `volume snapshot create` | Crée manuellement un nouveau snapshot. | `volume snapshot create -vserver SVM_Prod -volume vol_data -snapshot snap_manuel_1` |
| `snapmirror show` | Affiche l'état des réplications vers une autre baie. | `snapmirror show` |
| `snapmirror update` | Force une réplication manuelle immédiate. | `snapmirror update -destination-path SVM_Secours:vol_data_dest` |

> [!TIP]
> **Privilège avancé** : Certaines commandes de dépannage bas-niveau nécessitent de basculer en mode avancé. Tapez `set -privilege advanced` (tapez `y` pour confirmer). N'oubliez pas de revenir en mode normal via `set -privilege admin` après utilisation.
