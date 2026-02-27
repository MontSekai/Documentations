---
tags:
  - Cybersecurite
  - Risques
  - EBIOS
---

# EBIOS RM (Expression des Besoins et Identification des Objectifs de Sécurité)

EBIOS Risk Manager est la méthode d'analyse et d’évaluation des risques cybernétiques créée par l'**ANSSI** (Agence Nationale de la Sécurité des Systèmes d'Information) en France.

## Objectif

Contrairement à une simple analyse de vulnérabilités techniques, EBIOS RM adopte une approche ciblée sur le **risque métier**. Elle vise à déterminer les mesures de sécurité concrètes à implémenter pour protéger ce qui compte vraiment pour l'organisation.

## La méthode en 5 étapes

La méthode complète (souvent animée sous forme d'ateliers avec les différentes parties prenantes) se déroule en 5 ateliers séquentiels :

### Atelier 1 : Cadrage et socle de sécurité
Définir le périmètre de l'étude (Le projet X, l'application Y) et s'assurer que les pré-requis de sécurité basiques (hygiène informatique) sont déjà en place. Identifier les *Valeurs Métier* (ce qu'on cherche à protéger).

### Atelier 2 : Sources de risques (SR)
Identifier "qui" pourrait nous attaquer. (ex: Un cybercriminel appâté par le gain, un concurrent, un hacktiviste, un employé malveillant ou négligent).

### Atelier 3 : Scénarios stratégiques
Évaluer les chemins d'attaque macroscopiques. Comment la SR pourrait-elle atteindre l'objectif qu'elle vise ? On se concentre sur l'écosystème (ex: attaquer un sous-traitant vulnérable pour rebondir vers notre entreprise).

### Atelier 4 : Scénarios opérationnels
Décliner les scénarios stratégiques en attaques techniques réelles (ex: Phishing ciblé sur la comptabilité -> Déploiement d'un Ranswomware -> Chiffrement des serveurs -> Arrêt de l'activité). C'est là que l'on calcule la **vraisemblance**.

### Atelier 5 : Traitement du risque
Prendre les décisions face aux risques identifiés (les risques résiduels inacceptables). 
Pour chaque risque, on décide si on le :
- **Réduit** (En ajoutant des mesures de sécurité : EDR, MFA...).
- **Refuse** (En arrêtant l'activité trop dangereuse).
- **Transfère** (En prenant une cyber-assurance ou en sous-traitant à un Cloud certifié).
- **Accepte** (En connaissance de cause, validé par la Direction).
