---
tags:
  - Cybersecurite
  - RGPD
  - ISO
  - HDS
  - Conformite
---

# Normes et Réglementations

La conformité réglementaire est un pilier de la gouvernance IT. Voici les principales normes et réglementations que tout professionnel IT doit connaître.

## Réglementations légales (Obligatoires)

### RGPD — Règlement Général sur la Protection des Données
Le **RGPD** (ou GDPR en anglais) est le règlement européen en vigueur depuis **mai 2018** qui encadre le traitement des **données personnelles** des citoyens européens.

**Principes clés :**
* **Licéité** : Le traitement doit reposer sur une base légale (consentement, contrat, obligation légale...).
* **Minimisation** : Ne collecter que les données strictement nécessaires.
* **Finalité** : Les données ne peuvent être utilisées qu'à la fin pour laquelle elles ont été collectées.
* **Droits des personnes** : Droit d'accès, de rectification, d'effacement (*droit à l'oubli*), de portabilité.
* **Notification des violations** : Toute violation de données doit être notifiée à la **CNIL** dans les **72 heures**.
* **DPO** : Un Délégué à la Protection des Données est obligatoire dans certains organismes.

**Sanctions :** Jusqu'à **4% du chiffre d'affaires mondial** ou 20 millions d'euros (le plus élevé des deux).

### HDS — Hébergeur de Données de Santé
La certification **HDS** est obligatoire en France pour tout organisme qui héberge des données de santé à caractère personnel pour le compte d'un professionnel ou établissement de santé.

* Elle impose des exigences sur la sécurité des infrastructures, la gestion des accès, la traçabilité et la continuité de service.
* Les prestataires cloud (AWS Health, Microsoft Azure, OVH HDS...) doivent obtenir cette certification pour héberger des données de santé françaises.
* Lien fort avec la norme **ISO 27001** et les exigences **ANSSI**.

### LPM — Loi de Programmation Militaire (France)
La LPM impose aux **Opérateurs d'Importance Vitale (OIV)** (énergie, eau, transport, finance...) des obligations de sécurité renforcées sous contrôle de l'ANSSI, notamment en matière de détection des incidents et de remontée d'alertes.

### NIS 2 — Network and Information Security Directive (EU)
La directive NIS 2 (2024) étend les obligations de cybersécurité à un plus grand nombre d'entités "essentielles" et "importantes" au sein de l'UE : gestion des risques, signalement d'incidents, chaîne d'approvisionnement.

---

## Normes ISO (Cadres de bonnes pratiques)

### ISO 27001 — Système de Management de la Sécurité de l'Information (SMSI)

C'est **LA** norme de référence mondiale pour la sécurité de l'information. Elle définit un cadre pour **identifier, évaluer et traiter les risques** liés à la sécurité de l'information de façon systématique et continue.

* Elle est certifiable : une entreprise peut faire auditer son SMSI par un organisme tiers pour obtenir la certification.
* Elle est complétée par **ISO 27002** (catalogue de mesures de sécurité à implémenter) et d'autres normes de la famille 27000.

| Norme | Contenu |
| :--- | :--- |
| **ISO 27001** | Exigences du SMSI (certifiable) |
| **ISO 27002** | Guide de bonnes pratiques et contrôles de sécurité |
| **ISO 27005** | Gestion des risques liés à la sécurité de l'information |
| **ISO 27017** | Sécurité dans le cloud |
| **ISO 27701** | Extension 27001 pour la protection des données (lien RGPD) |

### ISO 22301 — Continuité d'activité (BCM)
Norme internationale pour le **Système de Management de la Continuité d'Activité (SMCA)**. Permet de s'assurer qu'une organisation peut continuer à fonctionner lors de perturbations majeures. Étroitement lié au PCA/PRA.

---

## Autres référentiels

| Référentiel | Origine | Domaine |
| :--- | :--- | :--- |
| **PCI DSS** | PCI Security Standards Council | Sécurité des paiements par carte bancaire |
| **SOC 2** | AICPA (USA) | Contrôle des fournisseurs de services cloud (Trust Services Criteria) |
| **ITIL** | Axelos | [Bonnes pratiques de management des services IT](../Management/Processus/itil.md) |
| **COBIT** | ISACA | Gouvernance et management des SI |
| **NIST CSF** | NIST (USA) | Cybersecurity Framework (Identifier, Protéger, Détecter, Répondre, Récupérer) |
| **SecNumCloud** | ANSSI | Qualification cloud souverain pour données sensibles de l'État français |
