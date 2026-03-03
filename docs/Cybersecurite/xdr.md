---
tags:
  - Cybersecurite
  - XDR
  - Endpoint
  - Reseau
---

# XDR (Extended Detection and Response)

Le **XDR** est l'évolution naturelle de l'[EDR](edr.md). Là où l'EDR se limite aux endpoints, le XDR **corrèle les alertes et les données en provenance de sources multiples** : endpoints, réseau, cloud, email, identité... dans une console unifiée.

## Pourquoi l'EDR seul ne suffit plus

Dans une cyberattaque moderne (ex: un ransomware), les étapes se déroulent sur **plusieurs couches** de l'infrastructure simultanément :

```mermaid
graph LR
    A["📧 Email de Phishing"] --> B["💻 Endpoint infecté (EDR)"]
    B --> C["🌐 Mouvement latéral réseau (NDR)"]
    C --> D["☁️ Exfiltration Cloud (CASB/Cloud)"]
    D --> E["🔑 Compromission identité AD (SIEM)"]
```

Si chaque outil (EDR, NDR, SIEM...) génère ses alertes dans des consoles séparées, les analystes perdent du temps à corréler manuellement les informations. Le XDR résout ce problème.

## Ce que fait un XDR

* **Ingestion de données multi-sources** : Collecte et normalise les événements depuis les endpoints, le réseau, les emails, les serveurs cloud et les identités.
* **Corrélation automatisée** : Croise les événements de sources différentes pour construire un **récit d'attaque complet** (kill chain), réduisant le nombre d'alertes isolées en incidents qualifiés.
* **Console unifiée** : Un seul outil pour voir, investiguer et répondre à un incident, quelle que soit la couche impactée.
* **Réponse orchestrée** : Peut déclencher des actions de remédiation sur toutes les couches simultanément (isoler l'endpoint + bloquer l'IP sur le firewall + désactiver le compte AD).

## XDR Natif vs XDR Ouvert (Open XDR)

| Type | Description | Avantages | Inconvénients |
| :--- | :--- | :--- | :--- |
| **XDR Natif** | Le fournisseur intègre ses propres produits (EDR + Email + Cloud d'un même éditeur) | Corrélation profonde, intégration parfaite | Dépendance à un seul éditeur (*vendor lock-in*) |
| **XDR Ouvert** | La plateforme XDR agrège des données de produits tiers via des connecteurs | Flexibilité, conserve l'existant | La corrélation est moins précise, intégration plus complexe |

## Exemples de XDR du marché

* **Microsoft Defender XDR** : Endpoint (MDE) + Email (MDO) + Identité (MDI) + Cloud Apps (MDCA).
* **CrowdStrike Falcon XDR** : Extension de l'EDR Falcon avec intégrations tierces.
* **Palo Alto Cortex XDR** : XDR ouvert avec nombreuses intégrations.
* **Trend Micro Vision One** : XDR avec télémétrie native endpoint, réseau et email.

## XDR vs SIEM

| Critère | XDR | SIEM |
| :--- | :--- | :--- |
| Objectif principal | Détection et réponse aux incidents actifs | Centralisation des logs + conformité |
| Données ingérées | Limitées, mais très enrichies (contexte sécurité) | Tout type de logs (volume très élevé) |
| Corrélation | Automatisée par l'IA du fournisseur | Basée sur des règles manuelles (SIGMA, YARA...) |
| Temps de déploiement | Rapide | Long (tuning des règles) |
| Audience | Équipes SOC N1/N2 | SOC N2/N3, analystes, équipes conformité |
