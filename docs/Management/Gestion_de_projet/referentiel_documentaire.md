---
tags:
  - Management
  - Gestion_de_projet
  - Documentation
---

# Référentiel Documentaire (Livrables IT)

L'ossature documentaire standardisée, vitale pour la pérennité d'un projet informatique et le passage en production.

## 1. Définition
Le **Référentiel Documentaire** (ou Base documentaire du projet) est l'ensemble organisé, structuré, versionné et centralisé des documents (les *Livrables*) produits tout au long du cycle de vie d'un projet. 
Il garantit que la connaissance et les décisions architecturales ne disparaissent pas lorsque le chef de projet ou les ingénieurs quittent l'entreprise.

## 2. Description / Fonctionnement (Les grands Livrables IT)
Dans un projet technique classique (notamment en [méthode prédictive / Cycle en V](methodologies_projet.md)), la livraison d'un serveur ou d'un logiciel s'accompagne obligatoirement de la rédaction de documents standards :
* **Le CDC (Cahier des Charges)** : Ce que veut le client (Le Besoin fonctionnel).
* **Les SFD (Spécifications Fonctionnelles Détaillées)** : Comment le besoin va se traduire concrètement (Règles de calcul, maquettes, droits d'accès).
* **Le DAT (Document d'Architecture Technique)** : Le "Plan de la maison" à destination des ingénieurs. Il contient les schémas réseau, le dimensionnement RAM/CPU, les protocoles de sécurité, les flux pare-feu, etc.
* **Le DIT (Dossier d'Installation Technique)** : Le "Tutoriel" étape par étape (souvent avec les vraies lignes de commandes Linux/Windows) pour pouvoir reconstruire l'infrastructure de zéro en cas de sinistre total.
* **Le DEX (Document / Dossier d'Exploitation)** : Le manuel de vol quotidien pour les équipes de Support. Il explique comment démarrer/arrêter le service, où sont situés les fichiers de logs d'erreurs, quelles alertes de supervision surveiller, et comment effectuer les sauvegardes.

## 3. Utilisation / Cas Pratique
Le référentiel documentaire prend tout son sens lors du passage du projet (La phase de création / **Le BUILD**) vers les équipes de maintenance quotidienne (La phase de maintien en condition / **Le RUN**). 
C'est ce qu'on appelle la réunion de **Passation** (ou *Transition to Run*).
L'équipe d'exploitation (Le Support de Niveau 2) refusera catégoriquement de prendre la responsabilité de ce nouveau serveur flambant neuf si le **DAT** et le **DEX** ne sont pas rédigés, testés et signés. Sans le DEX, si le serveur plante à 3h du matin un dimanche, le technicien d'astreinte ne saura pas quoi faire.

## 4. Modifications possibles / Alternatives
* **Outils et Stockage** : Ces documents ne doivent **jamais** être de simples fichiers Word non tracés envoyés par mail. Ils doivent être stockés sur un outil centralisé (SharePoint, Confluence, ou un **Wiki MkDocs** comme le vôtre !) et disposer d'un historique de révision strict (Gestion des versions 1.0, 1.1).
* **L'approche [Agile](agile_scrum.md)** : Le Manifeste Agile stipule *"Un logiciel fonctionnel plutôt qu'une documentation exhaustive"*. Les documents lourds (CDC, SFD) y sont souvent remplacés par un *Backlog* vivant de *User Stories*. Néanmoins, en ingénierie système et réseau, la documentation d'infrastructure (Le **DAT** et le **DEX**) reste une obligation non-négociable, même en Agile.

## 5. Exemples visuels et Liens utiles

### Cycle de vie classique d'un Référentiel Documentaire
```mermaid
graph LR
    CDC[Cahier des Charges\n(Le Client/Métier)] --> SFD[Spécifications\n(Le Chef de Projet)]
    SFD --> DAT[Architecture Technique\n(Les Ingénieurs/Architectes)]
    DAT --> DIT[Dossier d'Installation\n(Les Techniciens)]
    DIT --> DEX[Dossier d'Exploitation\n(Les Équipes Support / RUN)]
```

`Voir aussi : [Plan de Management de Projet (PMP)](plan_management_projet.md) | [Méthodologies de Projet](methodologies_projet.md)`
