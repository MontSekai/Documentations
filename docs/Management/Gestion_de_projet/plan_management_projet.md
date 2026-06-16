---
tags:
  - Management
  - Gestion_de_projet
  - Documentation
---

# Le Plan de Management de Projet (PMP)

Le document contractuel de référence (la bible) de l'exécution d'un projet classique.

## 1. Définition
*(Note : À ne pas confondre avec la [Certification PMP du PMI](pmi_pmp.md)).*
En francophonie, le **PMP (Plan de Management de Projet)**, parfois appelé *Plan Directeur de Projet* ou *PAQ (Plan d'Assurance Qualité)* en ingénierie, est le document officiel et formel qui définit comment le projet va être exécuté, surveillé et clôturé. 

## 2. Description / Fonctionnement
Contrairement au simple Cahier des Charges qui décrit *ce qu'il faut fabriquer* (le besoin technique du client), le PMP décrit très exactement **comment l'équipe va s'organiser pour le fabriquer**.
C'est un "super-document" maître qui regroupe (ou pointe vers) tous les plans de gestion annexes :
* **La Gouvernance** : Qui a le pouvoir de dire "oui" ou "non" (Sponsor, Chef de projet, Experts).
* **Le Plan de gestion du Périmètre** : Comment on gère les demandes de changements du client en cours de route (pour éviter que le projet ne grossisse à l'infini et n'explose le budget).
* **Le Plan de gestion des Délais** : Le planning de référence et les jalons.
* **Le Plan de gestion des Risques** : Comment on identifie et traite les dangers.
* **Le Plan de gestion des Communications** : Qui doit envoyer quel rapport à qui, comment, et tous les combien de temps.

## 3. Utilisation / Cas Pratique
Lors de la phase de "Démarrage" du projet, le chef de projet rédige ce PMP et **le fait signer** par le commanditaire (le Sponsor) et les parties prenantes. 
Si 6 mois plus tard, le client s'énerve en réunion et dit *"Je n'ai pas été prévenu de ce retard !"*, le Chef de projet ouvre le PMP à la page "Communication" et lui montre : *"Nous avons signé dans le PMP que les alertes de retard vous seraient envoyées par mail le vendredi soir au format PDF, ce que j'ai fait."* 
Le PMP est le bouclier juridique et organisationnel absolu du chef de projet.

## 4. Modifications possibles / Alternatives
* **Dans les [Méthodes Prédictives (Cycle en V / PRINCE2)](methodologies_projet.md)** : Le PMP est un document très lourd (souvent un PDF de dizaines de pages) figé. Toute modification du PMP en cours de projet doit faire l'objet d'un processus strict d'avenant.
* **En [Agile (Scrum)](agile_scrum.md)** : Le concept de gros document PMP figé disparaît totalement. La gestion du projet (comment l'équipe s'organise et communique) est directement intégrée de manière tacite dans le fonctionnement empirique des *Sprints*, du *Backlog* et des *Daily Meetings*. La lourdeur documentaire est remplacée par la collaboration humaine quotidienne.

## 5. Exemples visuels et Liens utiles

### Architecture typique d'un document PMP
| Chapitre du PMP | Que contient-il ? | Outil souvent utilisé |
| :--- | :--- | :--- |
| **1. Gouvernance** | Qui est le boss, qui valide quoi. | Organigramme, Matrice [RACI](outils_gestion_projet.md) |
| **2. Délais & Budget** | Quand est-ce qu'on livre et pour quel prix. | Planning [GANTT](outils_gestion_projet.md) |
| **3. Risques** | Ce qui peut mal se passer et comment on réagit. | [Journal RAID](journal_raid.md), Matrice des risques |
| **4. Communication** | Fréquence des réunions (Comité de Pilotage). | Plan de comm (Tableau croisé) |

`Voir aussi : [Méthodologies (Cycle en V / PRINCE2)](methodologies_projet.md) | [Journal RAID](journal_raid.md)`
