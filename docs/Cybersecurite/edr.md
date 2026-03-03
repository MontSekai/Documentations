---
tags:
  - Cybersecurite
  - EDR
  - Endpoint
---

# EDR (Endpoint Detection and Response)

Un **EDR** est une solution de sécurité installée directement sur les **postes de travail et serveurs** (les *endpoints*). Il va bien au-delà d'un antivirus classique en analysant en continu les comportements sur la machine pour détecter les menaces avancées.

## Limites de l'Antivirus traditionnel

Un antivirus classique fonctionne par **signature** : il compare les fichiers à une base de données de malwares connus. S'il ne connaît pas la signature, il ne détecte rien. Les attaquants modernes utilisent des techniques *"Living off the Land"* (LoTL) : ils détournent des outils légitimes Windows (`powershell.exe`, `wmic.exe`) pour mener leurs attaques, rendant les antivirus classiques inefficaces.

## Ce que fait un EDR

| Capacité | Description |
| :--- | :--- |
| **Collecte de données** | Journalise tous les événements de l'endpoint : créations de processus, connexions réseau, modifications du registre, accès fichiers. |
| **Détection comportementale** | Détecte les enchaînements suspects (ex : Word qui lance Powershell → Powershell qui contacte un serveur externe). |
| **Threat Hunting** | Permet aux analystes SOC de chercher proactivement des indicateurs de compromission (IoC) dans l'historique des données. |
| **Réponse à l'incident** | Capacités de remédiation : isolation réseau de la machine, kill d'un processus malveillant, collecte de preuves forensiques à distance. |
| **Timeline des attaques** | Reconstruit la chronologie complète d'une attaque (Patient Zero, propagation latérale...). |

## Exemples d'EDR du marché

* **CrowdStrike Falcon** : Leader du marché, 100% cloud, très léger sur l'endpoint.
* **Microsoft Defender for Endpoint (MDE)** : Intégré à Windows, excellent dans les environnements Microsoft 365.
* **SentinelOne** : Connu pour ses capacités de remédiation et rollback automatique.
* **Trend Micro Vision One** : EDR avec extension XDR native.
* **Cybereason** : Axé sur la corrélation et la visualisation des attaques.

## EDR vs Antivirus

| Critère | Antivirus | EDR |
| :--- | :---: | :---: |
| Détection par signature | ✅ Oui | ✅ Oui |
| Détection comportementale | ❌ Non | ✅ Oui |
| Threat Hunting | ❌ Non | ✅ Oui |
| Réponse à incident | ❌ Limitée | ✅ Complète |
| Visibilité forensique | ❌ Non | ✅ Oui |
| Impact performance | Faible | Faible à modéré |

> [!NOTE]
> Un EDR ne remplace pas toujours un antivirus : dans certaines solutions, l'EDR *intègre* les fonctionnalités antivirus. C'est le cas de **Microsoft Defender for Endpoint** ou de **SentinelOne**.
