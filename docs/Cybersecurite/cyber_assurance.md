---
tags:
  - Cybersecurite
  - Assurance
  - Gouvernance
---

# Cyber Assurance

La **cyber assurance** (ou assurance cyber) est un contrat qui permet à une organisation de **transférer une partie du risque financier** lié à une cyberattaque ou à un incident de sécurité vers un assureur. Elle ne remplace pas les mesures de sécurité mais constitue un filet de sécurité financier en cas de sinistre.

> [!NOTE]
> L'assurance cyber est un **transfert de risque**, pas une élimination du risque. Les assureurs exigent de plus en plus des preuves de maturité cybersécurité avant d'accorder une couverture.

## Ce que couvre une police cyber

### Couverture de première partie (dommages propres)
| Garantie | Exemples concrets |
| :--- | :--- |
| **Frais de réponse à l'incident** | Experts forensiques, RSSI externe, gestion de crise |
| **Interruption d'activité** | Perte de chiffre d'affaires pendant la panne |
| **Restauration des données** | Coûts de récupération et de reconstruction des données |
| **Rançon et extorsion** | Prise en charge (partielle) des rançongiciels (controversé) |
| **Notification des victimes** | Obligation RGPD de notifier les personnes concernées |
| **Frais de communication de crise** | Gestion de la réputation, relations presse |

### Couverture de tierce partie (responsabilité civile)
| Garantie | Exemples concrets |
| :--- | :--- |
| **Responsabilité en cas de fuite de données** | Amendes CNIL, recours des clients |
| **Atteinte à la vie privée** | Violation de données personnelles (RGPD) |
| **Responsabilité vis-à-vis de tiers** | L'attaque a servi de rebond vers des clients |

## Conditions des assureurs (exigences de sécurité)

Les assureurs cyber évaluent la **maturité cybersécurité** de l'organisme avant d'accorder une couverture. Les exigences minimales courantes en 2024 :

| Exigence | Niveau requis |
| :--- | :--- |
| **Authentification multi-facteurs (MFA)** | Obligatoire sur les accès distants et les comptes admin |
| **Sauvegardes testées et isolées** | Règle 3-2-1, sauvegardes hors-line ou immuables |
| **Plan de réponse à incident documenté** | PCA/PRA à jour et testé |
| **Gestion des correctifs (Patch)** | Politique de mise à jour définie |
| **Formation et sensibilisation** | Preuve de sensibilisation des utilisateurs |
| **[EDR](edr.md)** | Sur tous les endpoints |
| **Tests d'intrusion** | Pentests réguliers appréciés |

> [!WARNING]
> Un sinistre peut être **refusé** par l'assureur si les mesures de sécurité déclarées au moment de la souscription n'étaient pas réellement en place. La déclaration du niveau de sécurité engage la responsabilité de l'organisme.

## Facteurs influençant le coût

* **Chiffre d'affaires** : Principal critère de tarification
* **Secteur d'activité** : Santé, finance et collectivités sont considérés à risque élevé
* **Historique de sinistres** : Un incident passé augmente la prime
* **Niveau de maturité cyber** : Plus l'organisme est mature, plus la prime est basse
* **Montant de la franchise** : Plus la franchise est haute, plus la prime est basse

## Liens utiles

* [PSSI — Politique de Sécurité](pssi.md)
* [PCA / PRA — Continuité d'activité](pca_pra.md)
* [ANSSI — Agence nationale de cybersécurité](anssi.md)
