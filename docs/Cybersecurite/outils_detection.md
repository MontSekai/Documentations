---
tags:
  - Cybersecurite
  - Detection
  - SOC
  - EDR
  - XDR
  - SIEM
  - NDR
---

# Outils de Détection (EDR, NDR, SIEM, XDR)

La surveillance et la détection d'incidents de sécurité s'appuient sur plusieurs familles d'outils, souvent gérés par le **SOC** (Security Operations Center). Chacun a une zone de visibilité précise.

## Synthèse des outils

| Outil | Acronyme | Zone de surveillance | Point fort | Point aveugle |
| :--- | :--- | :--- | :--- | :--- |
| **EDR** | Endpoint Detection & Response | Les machines (PC, Serveurs) | Bloque les malwares avancés au plus près du système. | Ne voit pas les équipements sans agent (IoT, switches) ni le trafic réseau. |
| **NDR** | Network Detection & Response | Le trafic réseau (Trames, Flux) | Détecte les mouvements latéraux, le beaconing C2, l'exfiltration. | Ne sait pas ce qui se passe dans la RAM d'une machine. |
| **SIEM** | Security Information & Event Management | Toute l'infrastructure (Logs) | Centralise les logs, prouve la conformité, corrèle tout. | Dépend de ce qu'on lui envoie. Souvent lent (beaucoup de bruit). |
| **XDR** | Extended Detection & Response | Endpoints + Réseau + Cloud + Email | Unifie la détection et la réponse dans une seule console. | Dépend des intégrations disponibles (natif vs ouvert). |

---

## EDR (Endpoint Detection and Response)

L'EDR s'installe sur les endpoints et remplace l'antivirus traditionnel. Là où l'antivirus fonctionne par **signature** (connu vs inconnu), l'EDR fait de l'**analyse comportementale**.

* **Fonctionnalités clés** : Collecte des événements système (processus, registre, réseau), détection comportementale, Threat Hunting (recherche d'IoC), et réponse à incident (isolation réseau de la machine, kill automatique).
* **Face aux attaques modernes** : L'EDR est indispensable contre les attaques *Living off the Land* (LoTL) qui détournent des outils légitimes (PowerShell, WMI) ou les ransomwares *fileless* (en mémoire).
* **Exemples du marché** : CrowdStrike Falcon, Microsoft Defender for Endpoint (MDE), SentinelOne.

---

## NDR (Network Detection and Response)

Le NDR analyse le **trafic réseau en temps réel** (Sondes, Port SPAN/TAP, NetFlow). Il est indispensable pour voir ce que les agents EDR ne peuvent pas voir.

* **Fonctionnalités clés** : Analyse DPI (Deep Packet Inspection), Machine Learning pour établir une ligne de base (*baselining*), analyse des flux, détection de trafic vers serveurs C2 (Command & Control), analyse des certificats SSL/TLS.
* **Point fort** : Il peut détecter une compromission sur une machine où l'attaquant a réussi à désactiver l'EDR, ou sur des équipements non administrables (caméras IP, imprimantes, SCADA/OT).
* **Exemples du marché** : Darktrace, ExtraHop Reveal(x), Cisco Secure Network Analytics.

---

## SIEM (Security Information and Event Management)

Le SIEM est la "tour de contrôle" d'un SOC. Il ingère des **journaux d'événements (logs)** de toutes les sources (Active Directory, pare-feux, serveurs, antivirus...).

* Il remplit deux rôles :
    1. **SIM (Information Management)** : Archiver les logs sur le long terme (ex: 1 an) pour répondre aux obligations légales de conformité (RGPD, LPM, ISO 27001).
    2. **SEM (Event Management)** : Analyser les logs en direct via des règles de corrélation (Ex: "Si un compte se connecte de Paris puis de Tokyo 5 min après => Alerte Incident").
* **SOAR** : Le SIEM est de plus en plus couplé au SOAR (Orchestration et Automatisation) pour réagir automatiquement aux alertes (Playbooks).
* **Exemples du marché** : Splunk, IBM QRadar, Microsoft Sentinel, Elastic SIEM.

---

## XDR (Extended Detection and Response)

Le XDR est l'évolution naturelle de l'EDR. Face à la multiplication des consoles de sécurité (EDR, Pare-feu, Filtre email, Broker Cloud), le XDR se propose de **tout corréler au sein d'une seule interface native**.

* **Pourquoi le XDR ?** Une attaque commence par un email (Phishing), infecte un poste (EDR), se propage sur le réseau (NDR) pour voler un mot de passe (AD/Identité) et exfiltrer la donnée vers un cloud (CASB/Cloud). Le XDR relie tous ces événements isolés pour former une "Attack Story" claire.
* **XDR Natif vs Ouvert** :
    * *Natif* : L'éditeur fournit l'EDR, la sécu email, la sécu réseau (ex: Microsoft Defender XDR). L'intégration est parfaite mais on est dépendant d'un seul partenaire.
    * *Ouvert* : La plateforme XDR se connecte aux outils divers du client via API (ex: Palo Alto Cortex XDR). Plus de flexibilité.
