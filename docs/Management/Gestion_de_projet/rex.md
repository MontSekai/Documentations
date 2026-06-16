---
tags:
  - Management
  - Gestion_de_projet
  - Amelioration_Continue
  - Incident
---

# Le REX (Retour d'Expérience / Post-Mortem)

La réunion et le document essentiels pour transformer les erreurs du passé en succès futurs.

## 1. Définition
Le **REX (Retour d'Expérience)**, très souvent appelé **Post-Mortem** dans les environnements IT anglophones (ou *Rétrospective* dans le vocabulaire Agile), est une démarche d'analyse collective réalisée à la fin d'un projet complet, ou suite à un incident de production majeur. L'objectif est d'identifier de manière transparente ce qui a bien fonctionné, ce qui a échoué, et d'en tirer des leçons systémiques pour l'avenir.

## 2. Description / Fonctionnement
Un bon REX n'est pas une simple discussion plaintive autour de la machine à café, c'est un processus formel qui aboutit impérativement à un **document écrit**. Il s'articule généralement autour de 3 axes :
1. **Les succès (Keep)** : Qu'est-ce qui a super bien marché et qu'il faut absolument institutionnaliser pour les prochains projets (ex: *L'utilisation systématique du [Journal RAID](journal_raid.md) nous a permis d'éviter 3 crises majeures*).
2. **Les échecs (Drop / Improve)** : Qu'est-ce qui a causé des retards, des bugs, ou des tensions ? Qu'est-ce qu'on doit arrêter de faire ou corriger (ex: *Le prestataire externe a livré avec 3 semaines de retard sans prévenir*).
3. **Les plans d'action (Action Items)** : C'est le cœur du REX. Comment on corrige concrètement le problème pour la prochaine fois ? Il faut aboutir à des tâches précises assignées à des personnes.

> [!IMPORTANT]
> **La Règle d'Or du "Blame-Free" (Sans Reproche)** : Le REX ne sert **absolument jamais** à trouver un coupable ou à punir un collaborateur. Il part du principe que l'erreur humaine est en réalité causée par un processus défaillant. Si un technicien a formaté le mauvais serveur par erreur, le REX ne pointe pas le technicien du doigt, il cherche à comprendre pourquoi l'outil informatique et les procédures lui ont permis de le faire sans double sécurité.

## 3. Utilisation / Cas Pratique
**Suite à une panne majeure (Incident Post-Mortem) :**
Le site de l'entreprise a été hors ligne pendant 4 heures à cause d'une mise à jour réseau ratée. Le lendemain, le DSI organise un REX avec les administrateurs réseaux et l'équipe de développement.
Le document de REX va reconstruire la Timeline exacte de l'incident : 
- *14h00 : Déploiement.*
- *14h05 : Crash total du site.*
- *14h40 : L'alerte de supervision sonne enfin.* (Le vrai problème est identifié ici : l'alerte est beaucoup trop lente).
L'action d'amélioration décidée en fin de réunion sera technique : *"Ajuster le seuil d'alerte critique à 3 minutes au lieu de 30 minutes dans le logiciel de supervision"*.

## 4. Modifications possibles / Alternatives
* **Dans les Méthodes Classiques (PRINCE2 / [Cycle en V](methodologies_projet.md))** : Le REX est la phase ultime et obligatoire de la "Clôture du Projet". Le rapport de fin de projet est ensuite archivé précieusement par le [PMO](pmo_ppm.md) dans la base documentaire pour servir de leçon aux futurs chefs de projet de l'entreprise.
* **Dans l'approche [Agile (Scrum)](agile_scrum.md)** : Le REX ne se fait pas à la toute fin du projet de 2 ans (où il est souvent bien trop tard pour corriger le tir), mais toutes les 2 à 4 semaines, à la toute fin de chaque *Sprint*. C'est le fameux rituel de la **Rétrospective de Sprint**. L'équipe s'améliore ainsi en continu.

## 5. Exemples visuels et Liens utiles

### Déroulement d'un REX constructif
```mermaid
graph LR
    F[Faits\nTimeline exacte de l'événement] --> C[Causes\nPourquoi est-ce arrivé ?]
    C --> I[Impacts\nCoûts, retards, pannes]
    I --> A[Actions\nQue change-t-on demain ?]
```

`Voir aussi : [Agilité et Scrum (La Rétrospective)](agile_scrum.md) | [Plan de Management de Projet](plan_management_projet.md)`
