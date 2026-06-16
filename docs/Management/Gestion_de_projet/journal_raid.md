---
tags:
  - Management
  - Gestion_de_projet
  - Risques
  - RAID
---

# Le Journal RAID (Risks, Assumptions, Issues, Dependencies)

L'outil de pilotage essentiel du Chef de Projet pour sécuriser l'environnement de son projet.

## 1. Définition
Attention à ne pas confondre avec le [RAID matériel des disques durs (Informatique)](../../Systeme/Stockage/raid.md). 
En management de projet, le **Journal RAID (RAID Log)** est un registre (souvent un simple tableau Excel ou un Kanban partagé) utilisé par le Chef de Projet ou le PMO pour tracer, analyser et maîtriser en temps réel les 4 facteurs externes majeurs qui pourraient faire dérailler son projet : les Risques, les Hypothèses, les Problèmes et les Dépendances.

## 2. Description / Fonctionnement (L'acronyme RAID)
* **R - Risks (Risques)** : Ce qui *pourrait* arriver de mal. Événements futurs et incertains. Le chef de projet utilise une [Matrice des risques](matrice_des_risques.md) pour préparer un plan de remédiation préventif.
* **A - Assumptions (Hypothèses)** : Ce que l'on *croit* être vrai, mais qui n'est pas encore prouvé. Ce sont les éléments que l'on tient pour acquis pour construire le planning (ex: "Je pars de l'hypothèse absolue que le fournisseur livrera les serveurs avant le 15 août"). Si l'hypothèse s'avère fausse, elle se transforme instantanément en un Risque grave ou un Problème.
* **I - Issues (Problèmes / Incidents)** : Ce qui est *déjà* en train d'arriver. Ce n'est plus un risque éventuel, c'est un feu déclaré (ex: "Un développeur clé a démissionné hier, la production est à l'arrêt"). Il faut gérer la crise immédiate.
* **D - Dependencies (Dépendances)** : Ce dont le projet a absolument besoin venant de l'extérieur pour avancer, ou inversement. (ex: "L'équipe technique ne peut pas commencer la configuration réseau (Action B) tant que l'équipe Bâtiment n'a pas tiré les câbles électriques (Action A)"). Le [Diagramme de PERT ou de GANTT](outils_gestion_projet.md) sert à cartographier visuellement ces dépendances.

## 3. Utilisation / Cas Pratique
Pendant la réunion de pilotage hebdomadaire (Le Comité de Pilotage / Copil), le Chef de Projet ou le *Scrum Master* ne passe pas son temps à lire la liste des tâches (ToDo) qui se passent bien. 
Il projette sur grand écran le **Journal RAID**. Le but unique de la réunion de management est de trouver ensemble des décisions pour éteindre les *Problèmes (Issues)*, vérifier si les *Hypothèses (Assumptions)* sont toujours tenables, et s'assurer que les *Dépendances (Dependencies)* externes n'ont pas pris de retard.

`Voir aussi : [Matrice des risques](matrice_des_risques.md) | [Outils de base (GANTT, PERT, RACI)](outils_gestion_projet.md)`
