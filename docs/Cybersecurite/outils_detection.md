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

La surveillance et la détection d'incidents de sécurité s'appuient sur plusieurs familles d'outils, souvent gérés par le SOC (Security Operations Center). Chacun a une zone de visibilité précise.

---

## 1. EDR (Endpoint Detection and Response)

### 1.1. Définition
L'EDR est une solution de sécurité installée sur les terminaux (endpoints : PC, Serveurs) qui remplace l'antivirus traditionnel pour détecter les menaces avancées.

### 1.2. Description / Fonctionnement
Là où l'antivirus fonctionne par signature stricte (connu vs inconnu), l'EDR fait de l'analyse comportementale en surveillant l'activité du système (processus, registre, réseau local). Il permet de bloquer automatiquement les comportements suspects et de tracer l'origine exacte de l'attaque.

### 1.3. Utilisation / Cas Pratique
L'EDR est indispensable pour détecter des attaques modernes comme les ransomwares *fileless* (en mémoire RAM) ou les attaques "Living off the Land" (utilisation d'outils système légitimes comme PowerShell à des fins malveillantes).
En cas d'alerte, l'analyste SOC peut utiliser l'EDR pour isoler la machine du réseau instantanément.

### 1.4. Modifications possibles / Alternatives
L'évolution directe de l'EDR est le XDR (voir section 4), qui ajoute d'autres sources de télémétrie réseau et cloud.

### 1.5. Exemples visuels et Liens utiles
Exemples du marché : CrowdStrike Falcon, Microsoft Defender for Endpoint (MDE), SentinelOne.

---

## 2. NDR (Network Detection and Response)

### 2.1. Définition
Le NDR est un outil de surveillance qui analyse le trafic réseau brut en temps réel pour détecter les comportements anormaux.

### 2.2. Description / Fonctionnement
Il s'appuie sur des sondes réseaux (Port SPAN / TAP), du Machine Learning et du DPI (Deep Packet Inspection) pour établir une ligne de base du réseau ("baselining") et alerter en cas de déviations suspectes.

### 2.3. Utilisation / Cas Pratique
Le NDR est l'outil privilégié pour détecter les mouvements latéraux d'un attaquant entre deux machines internes, l'exfiltration massive de données, ou la communication vers un serveur pirate (C2 - Command & Control). Point crucial : il voit tout ce qui passe sur le réseau, même ce qui provient de matériels où l'on ne peut pas installer d'EDR (caméras IP, imprimantes, systèmes industriels SCADA).

### 2.4. Modifications possibles / Alternatives
L'IDS (Intrusion Detection System) classique est l'ancêtre du NDR, mais il fonctionne principalement par signatures connues et est devenu insuffisant.

### 2.5. Exemples visuels et Liens utiles
Exemples du marché : Darktrace, ExtraHop Reveal(x), Cisco Secure Network Analytics.

---

## 3. SIEM (Security Information and Event Management)

### 3.1. Définition
Le SIEM est la "tour de contrôle" d'un SOC. C'est un outil centralisant les journaux d'événements (logs) de toute l'infrastructure IT (réseaux, serveurs, cloud, applications).

### 3.2. Description / Fonctionnement
Il remplit deux rôles principaux :
1. **Archivage (SIM)** : Stocker les logs à long terme pour la conformité légale et les enquêtes (forensics).
2. **Corrélation (SEM)** : Analyser les logs en direct via des règles de corrélation (Ex: "Si un compte Admin se connecte de Paris puis de Tokyo 5 min après => Alerte").

### 3.3. Utilisation / Cas Pratique
Si un pare-feu bloque une adresse IP suspecte, et qu'au même moment l'Active Directory signale 50 erreurs de mot de passe pour un compte précis, le SIEM va corréler ces deux logs indépendants (et invisibles séparément) pour générer une alerte globale d'"Attaque Brute Force".

### 3.4. Modifications possibles / Alternatives
Le SIEM est de plus en plus souvent couplé à un **SOAR** (Security Orchestration, Automation, and Response) pour réagir automatiquement aux alertes générées par le SIEM via des scripts ("Playbooks").

### 3.5. Exemples visuels et Liens utiles
Exemples du marché : Splunk, IBM QRadar, Microsoft Sentinel, Elastic SIEM.

---

## 4. XDR (Extended Detection and Response)

### 4.1. Définition
Le XDR est une plateforme de sécurité unifiée qui collecte et corrèle automatiquement les données provenant de multiples couches de l'entreprise (endpoints, réseau, serveurs, cloud, e-mails).

### 4.2. Description / Fonctionnement
C'est l'évolution du concept d'EDR étendu à toute l'infrastructure. Face à la multiplication des consoles de sécurité dispersées, le XDR se propose de tout corréler au sein d'une seule et même interface native pour casser les silos.

### 4.3. Utilisation / Cas Pratique
Lorsqu'une attaque commence par un email (Phishing), infecte un poste (vu par l'EDR), se propage sur le réseau (vu par le NDR) pour exfiltrer la donnée vers un cloud (vu par le CASB), le XDR relie nativement tous ces événements pour former une "Attack Story" chronologique claire pour l'analyste.

### 4.4. Modifications possibles / Alternatives
Il existe deux approches XDR : 
* **Natif** (l'éditeur fournit tous les outils de la chaîne : EDR, Pare-feu, Email, ex: Microsoft Defender XDR).
* **Ouvert** (la plateforme XDR s'interface par API avec les outils de sécurité de différents éditeurs déjà existants chez le client, ex: Palo Alto Cortex XDR).

### 4.5. Exemples visuels et Liens utiles
| Outil | Zone de surveillance | Point fort | Point aveugle |
| :--- | :--- | :--- | :--- |
| **EDR** | Endpoints (PC, Serveurs) | Bloque au plus près du système. | Ne voit pas le trafic réseau ou les IoT. |
| **NDR** | Réseau (Flux, Trames) | Détecte les mouvements latéraux. | Ne voit pas l'intérieur de la RAM des PC. |
| **SIEM** | Toute l'infrastructure (Logs) | Centralise et prouve la conformité. | Dépend des logs envoyés, beaucoup de bruit. |
| **XDR** | L'ensemble unifié | "Attack Story" claire, unifiée. | Dépend de l'intégration des outils de la chaîne. |
