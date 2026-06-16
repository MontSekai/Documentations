---
tags:
  - Management
  - Gestion_de_projet
  - GANTT
  - PERT
  - RACI
  - QCD
---

# Outils de la Gestion de Projet

La gestion de projet s'appuie sur plusieurs méthodologies et outils fondamentaux. Voici les quatre principaux outils utilisés pour planifier, répartir les rôles et équilibrer les contraintes.

---

## 1. Triangle QCD (Qualité, Coût, Délai)

### 1.1. Définition
Le triptyque QCD représente les trois contraintes majeures et indissociables de tout projet (le "triangle de fer"). 

### 1.2. Description / Fonctionnement
Toute modification sur l'un de ces sommets aura un impact direct sur les autres :
* **Qualité + Coût (Bien & Pas cher)** = **Projet lent** (Délai non respecté).
* **Qualité + Délai (Bien & Rapide)** = **Projet cher** (Nécessite beaucoup de ressources).
* **Coût + Délai (Pas cher & Rapide)** = **Faible qualité** (Travail bâclé ou dette technique).

### 1.3. Utilisation / Cas Pratique
Le modèle QCD est un outil d'aide à la décision très puissant pour comparer des offres de prestataires, ou pour évaluer le succès d'un projet *post-mortem* (Le budget a-t-il été tenu ? Les délais ? Le taux de bugs est-il acceptable ?).

### 1.4. Modifications possibles / Alternatives
On peut y ajouter d'autres indicateurs selon le domaine (ex: la Sécurité pour l'IT).

### 1.5. Exemples visuels et Liens utiles
<div align="center">
  <img src="../../images/qcd.webp" alt="Triangle QCD" width="200">
</div>

---

## 2. Matrice RACI (Répartition des rôles)

### 2.1. Définition
La matrice RACI est un tableau à double entrée qui définit "Qui fait quoi" de manière non ambiguë au sein d'un projet ou d'un processus.

### 2.2. Description / Fonctionnement
| Lettre | Rôle | Description | Règle d'or |
| :--- | :--- | :--- | :--- |
| **R** | **Responsible** (Réalisateur) | La personne ou l'équipe qui exécute concrètement la tâche (le "faiseur"). | Au moins un "R" par tâche. |
| **A** | **Accountable** (Approbateur) | Le responsable final. C'est lui qui assume si la tâche échoue. | **UN SEUL "A" par tâche.** |
| **C** | **Consulted** (Consulté) | L'expert(e) à qui l'on demande conseil ou avis *avant* d'agir. | Communication bidirectionnelle. |
| **I** | **Informed** (Informé) | Les personnes tenues au courant *après* l'action. | Communication unidirectionnelle. |

### 2.3. Utilisation / Cas Pratique
Créée lors du lancement du projet pour éviter que les collaborateurs se marchent sur les pieds ou que certaines tâches critiques soient oubliées.

### 2.4. Modifications possibles / Alternatives
Il existe la variante RASCI (ajout du rôle "S" pour Support), ou encore le DACI (Driver, Approver, Contributor, Informed) utilisé par Atlassian.

### 2.5. Exemples visuels et Liens utiles
*(Ajouter un exemple de matrice avec noms de personnes en colonnes et tâches en lignes).*

---

## 3. Diagramme de GANTT

### 3.1. Définition
Le GANTT est le tableau de bord visuel de l'avancement temporel d'un projet.

### 3.2. Description / Fonctionnement
* **En ordonnée (à gauche)** : La liste exhaustive des tâches.
* **En abscisse (en haut)** : Le temps (Jours, Semaines).
Il met en évidence les dates de début/fin, les jalons (milestones), et les **dépendances** (On ne peut pas commencer la tâche B tant que la tâche A n'est pas terminée).

### 3.3. Utilisation / Cas Pratique
Outil central du chef de projet pour piloter les délais, généralement géré via des logiciels (MS Project, Jira, Asana, Monday).

### 3.4. Modifications possibles / Alternatives
Moins utilisé "strictement" dans les approches Agiles (qui préfèrent les boards Kanban), bien qu'on puisse avoir un macro-GANTT des Sprints.

### 3.5. Exemples visuels et Liens utiles
Pour approfondir, voir les articles et modèles sur le [Blog de la Gestion de Projet (BDGP)](https://blog-gestion-de-projet.com/).

---

## 4. Diagramme PERT

### 4.1. Définition
Contrairement au GANTT qui est lié au calendrier, le diagramme PERT (*Program Evaluation and Review Technique*) est axé sur la logique d'enchaînement en réseau.

### 4.2. Description / Fonctionnement
Il sert avant tout à visualiser et calculer le **Chemin Critique** (la suite de tâches incompressibles qui dicte la durée totale du projet. Si une tâche du chemin critique prend du retard, tout le projet prend du retard).

### 4.3. Utilisation / Cas Pratique
Extrêmement utile en début de phase de planification pour estimer le temps minimal nécessaire avant même de fixer des dates précises dans le calendrier.

### 4.4. Modifications possibles / Alternatives
Souvent utilisé de pair avec la méthode CPM (Critical Path Method). Le PERT et le GANTT sont très complémentaires.

### 4.5. Exemples visuels et Liens utiles
*(Ajouter le dessin typique d'un réseau PERT avec ses cercles et ses flèches).*
