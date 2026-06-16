---
tags:
  - Cybersecurite
  - RGPD
  - ISO
  - HDS
  - Conformite
---

# Normes et Réglementations

La conformité réglementaire est un pilier de la gouvernance IT. Voici les principales normes que tout professionnel IT doit connaître.

---

## 1. RGPD (Règlement Général sur la Protection des Données)

### 1.1. Définition
Le RGPD est le règlement européen en vigueur depuis mai 2018 qui encadre et protège le traitement des données personnelles des citoyens européens.

### 1.2. Description / Fonctionnement
Il impose le respect de principes forts aux organisations : Licéité du traitement, Minimisation (ne collecter que le strict nécessaire), Finalité précise, et Droits des personnes (droit d'accès, de rectification, droit à l'oubli).

### 1.3. Utilisation / Cas Pratique
Lors du développement d'une nouvelle application, le RGPD impose le principe de *Privacy by Design* (la confidentialité dès la conception du code). En cas de fuite de données, l'entreprise doit obligatoirement le notifier à la [CNIL](cnil.md) sous 72 heures.

### 1.4. Modifications possibles / Alternatives
À l'international, d'autres réglementations s'inspirent fortement du RGPD, comme le CCPA en Californie.

### 1.5. Exemples visuels et Liens utiles
Les sanctions sont colossales : Jusqu'à 4% du chiffre d'affaires mondial ou 20 millions d'euros.
[Visiter le site de la CNIL pour les guides pratiques.](cnil.md)

---

## 2. ISO 27001 (Système de Management de la Sécurité de l'Information)

### 2.1. Définition
ISO 27001 est la norme internationale de référence pour la sécurité de l'information. Elle définit un cadre strict pour créer et maintenir un SMSI (Système de Management de la Sécurité de l'Information).

### 2.2. Description / Fonctionnement
Elle impose un cadre d'amélioration continue (la roue de Deming : Plan-Do-Check-Act) pour identifier, évaluer et traiter les risques liés à l'information. Elle s'appuie très fortement sur l'analyse de risques (voir [EBIOS](ebios.md)).

### 2.3. Utilisation / Cas Pratique
L'ISO 27001 est une norme *certifiable*. Une entreprise peut faire auditer son SMSI par un tiers indépendant (comme l'AFNOR). Obtenir cette certification permet de prouver contractuellement à ses clients et partenaires que la sécurité est gérée de manière mature.

### 2.4. Modifications possibles / Alternatives
Elle est systématiquement couplée à la norme **ISO 27002** qui fournit le catalogue pratique des contrôles de sécurité à implémenter. Pour gérer spécifiquement la continuité d'activité, on se tourne vers l'**ISO 22301**.

### 2.5. Exemples visuels et Liens utiles
*(Ajouter une illustration du cycle de Deming Plan-Do-Check-Act propre aux normes ISO).*

---

## 3. Réglementations Nationales Spécifiques (HDS, LPM, NIS 2)

### 3.1. Définition
Au-delà du RGPD, des lois spécifiques extrêmement contraignantes s'appliquent selon le secteur d'activité ou la criticité de l'entreprise (Santé, Industrie, Opérateurs vitaux).

### 3.2. Description / Fonctionnement
* **HDS (Hébergeur de Données de Santé)** : Certification obligatoire en France pour toute entreprise hébergeant des données de santé personnelles.
* **LPM (Loi de Programmation Militaire)** : Impose aux Opérateurs d'Importance Vitale (OIV) des règles de sécurité ultra-strictes dictées par l'[ANSSI](anssi.md).
* **NIS 2** : Directive européenne imposant un niveau de cybersécurité élevé, incluant la sécurisation de la Supply Chain, aux dizaines de milliers d'entités "essentielles" et "importantes" de l'économie.

### 3.3. Utilisation / Cas Pratique
Un grand prestataire Cloud (ex: OVH ou Azure) ne peut légalement stocker les données d'un hôpital français que s'il a passé l'audit rigoureux HDS. S'il n'est pas certifié, le contrat est nul.

### 3.4. Modifications possibles / Alternatives
Pour le cloud ultra-sécurisé de l'État français, l'ANSSI a créé son propre référentiel souverain nommé **SecNumCloud**.

### 3.5. Exemples visuels et Liens utiles
Pour la Santé, ces règles techniques sont déclinées via la [PGSSI-S](pgssi_s.md).
