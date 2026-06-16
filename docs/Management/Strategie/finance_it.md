---
tags:
  - Management
  - Strategie
  - Finance
---

# Finance et Gestion IT

La gestion financière est un pilier de la stratégie et de la gestion de projet. Les décisions techniques se justifient toujours par des indicateurs économiques.

---

## 1. ROI (Return on Investment)

### 1.1. Définition
Le ROI (Retour sur Investissement) est un indicateur financier permettant de mesurer la rentabilité d'un investissement par rapport à son coût initial.

### 1.2. Description / Fonctionnement
La formule de base est : `((Gain de l'investissement - Coût de l'investissement) / Coût de l'investissement) x 100`.
Un ROI positif signifie que le projet rapporte plus d'argent (ou fait réaliser plus d'économies) qu'il n'en a coûté.

### 1.3. Utilisation / Cas Pratique
Avant de valider l'achat d'un nouveau logiciel d'automatisation à 50 000 €, on calcule le ROI : si le logiciel fait gagner 100 000 € de temps humain sur l'année, le ROI est de 100%, l'investissement est validé.

### 1.4. Modifications possibles / Alternatives
Le ROI se concentre sur l'argent. On utilise parfois le **VOI (Value on Investment)** pour intégrer des gains immatériels (satisfaction client, bien-être des employés, réduction de la pénibilité).

### 1.5. Exemples visuels et Liens utiles
*(Calculateur de rentabilité).*

---

## 2. CAPEX vs OPEX

### 2.1. Définition
CAPEX (*Capital Expenditure*) et OPEX (*Operational Expenditure*) sont les deux grandes catégories de dépenses d'une entreprise.

### 2.2. Description / Fonctionnement
* **CAPEX (Dépenses d'investissement)** : Achat d'actifs physiques ou durables (ex: achat de serveurs physiques, achat de licences logicielles à vie, construction d'un datacenter). Cela s'amortit comptablement sur plusieurs années.
* **OPEX (Dépenses opérationnelles)** : Frais récurrents pour faire fonctionner l'entreprise au quotidien (ex: abonnement Cloud AWS/Azure, licences SaaS mensuelles, salaires, électricité).

### 2.3. Utilisation / Cas Pratique
La tendance IT actuelle est de **passer du CAPEX à l'OPEX** (modèle Cloud/SaaS). Au lieu d'acheter des serveurs coûteux tous les 5 ans (CAPEX), l'entreprise loue de la puissance de calcul au mois chez AWS (OPEX), ce qui offre plus de flexibilité.

### 2.4. Modifications possibles / Alternatives
Le FinOps est une nouvelle discipline qui vise précisément à optimiser ces coûts OPEX dans les environnements Cloud (ne payer que ce que l'on consomme).

### 2.5. Exemples visuels et Liens utiles
Rechercher des articles explicatifs sur l'économie du Cloud (FinOps).

---

## 3. TJM et Coût Humain

### 3.1. Définition
Le TJM (Taux Journalier Moyen) représente le coût moyen d'un prestataire ou d'un salarié pour une journée de travail. Le "Coût Humain" représente l'ensemble des dépenses liées au personnel sur un projet.

### 3.2. Description / Fonctionnement
Le Coût Humain n'est pas juste le salaire net de l'employé. Il inclut les charges patronales, les frais de structure (locaux, matériel), etc. Pour un prestataire externe, le TJM est directement facturé à l'entreprise (ex: 600€/jour pour un développeur senior).

### 3.3. Utilisation / Cas Pratique
Dans le budget d'un projet IT (le "C" du triangle QCD), le coût humain est très souvent le poste de dépense n°1, bien devant le matériel ou les licences. Multiplier le nombre de jours de travail estimés par le TJM des intervenants donne le budget principal du projet.

### 3.4. Modifications possibles / Alternatives
Pour les projets internes, on parle de coûts "cachés" si on ne facture pas les heures, mais il est de bonne pratique de calculer virtuellement ce coût humain pour évaluer la rentabilité réelle (ROI) d'un projet interne.

### 3.5. Exemples visuels et Liens utiles
*(Tableaux de simulation de coûts de personnel).*
