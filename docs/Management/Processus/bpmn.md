---
tags:
  - Management
  - Processus
  - BPMN
  - Diagramme
---

# BPMN (Business Process Model and Notation)

Le standard mondial pour modéliser visuellement les processus métier.

## 1. Définition
Le **BPMN** est une norme internationale de modélisation graphique de processus d'affaires. Il fournit une notation standardisée, compréhensible à la fois par les analystes métier (qui conçoivent et optimisent les processus de l'entreprise), par les développeurs (qui les implémentent dans des logiciels), et par les managers (qui les lisent et les valident).

## 2. Description / Fonctionnement
Un diagramme BPMN se construit comme un logigramme très avancé, composé de 5 familles d'éléments principaux :
1. **Les Corridors (Swimlanes)** : Ils délimitent "Qui fait quoi". Le diagramme est découpé en grandes piscines (*Pools*) représentant l'entreprise ou un partenaire, et en lignes d'eau (*Lanes*) représentant les rôles précis (ex: Service Client, Comptabilité, Logiciel Informatique).
2. **Les Événements (Events - Cercles)** : Ce qui se passe dans le temps.
   * **Début (Cercle Vert / Fin)** : Le déclencheur unique du processus (ex: "Réception d'un e-mail d'un client").
   * **Intermédiaire (Cercle à double trait)** : Une temporisation ("Attendre 2 jours") ou un message reçu en plein milieu du processus.
   * **Fin (Cercle Rouge ou à trait très épais)** : L'état final et terminal du processus.
3. **Les Tâches (Activities - Rectangles)** : Les actions concrètes effectuées par une personne ou un système (ex: "Vérifier l'état du stock de l'article").
4. **Les Passerelles (Gateways - Losanges)** : Les choix et les séparations de chemin (ex: Branchement OU, Branchement ET).
5. **Les Objets de Données (Data Objects)** : Ils représentent l'enregistrement physique ou numérique d'informations (un document papier, un e-mail reçu, une écriture dans une base de données) générés ou requis par une tâche pour fonctionner.

## 3. Utilisation / Cas Pratique
Lorsqu'une entreprise souhaite automatiser ou auditer son processus de "Validation des notes de frais", un Business Analyst dessine un BPMN. 
Il y trace le chemin complet de l'information : l'employé remplit la note dans sa ligne d'eau (Tâche), la note est stockée (Data Object), le logiciel envoie un mail au manager (Événement), le manager valide ou refuse (Gateway), et la comptabilité procède au virement final. Ce diagramme servira de "cahier des charges" exact et sans ambiguïté aux développeurs logiciels.

## 4. Modifications possibles / Alternatives
Une alternative plus simple au BPMN (souvent trop complexe pour le grand public) est le simple diagramme de flux classique (*Flowchart*) ou un diagramme UML d'Activité pour les développeurs.
L'avantage magique du BPMN moderne, c'est qu'il peut être couplé à des moteurs d'exécution métier automatisés (Des BPMS comme *Camunda* ou *Bonita*) : dans ces logiciels, le dessin BPMN n'est plus juste une image statique, c'est le code lui-même qui s'exécute techniquement !

## 5. Exemples visuels et Liens utiles

### Les symboles clés du BPMN à retenir
| Élément BPMN | Symbole typique | Explication |
| :--- | :--- | :--- |
| **Événement de Début** | 🟢 Cercle simple | L'événement précis qui déclenche l'existence du processus. |
| **Événement de Fin** | 🔴 Cercle au trait épais | La conclusion du chemin. |
| **Tâche (Activité)** | 🟦 Rectangle à bords arrondis | L'action humaine, manuelle ou automatisée. |
| **Gateway Exclusive (XOR)**| 🔶 Losange avec une croix "X" | Choix "OUI ou NON" (Un seul et unique chemin possible). |
| **Gateway Parallèle (AND)**| 🔶 Losange avec un "+" | Les deux chemins se divisent et s'exécutent en même temps. |
| **Objet de Données** | 📄 Icône de feuille cornée | L'enregistrement d'une information ou d'un document. |
| **Swimlane (Couloir)** | ➖ Ligne horizontale (Couloir) | Attribue une série de tâches à un rôle/département précis. |

`Voir aussi : [Diagramme des flux](diagramme_des_flux.md)`
