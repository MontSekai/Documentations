---
tags:
  - Management
  - Strategie
  - Processus
  - Pareto
---

# Loi de Pareto (Règle des 80/20)

Le principe empirique de priorisation et d'efficacité de l'effort.

## 1. Définition
La **Loi de Pareto** (couramment appelée la règle des 80/20) est un phénomène empirique universel qui observe qu'**environ 80 % des effets sont le produit de seulement 20 % des causes**. Découverte par l'économiste Vilfredo Pareto à l'origine sur la répartition des richesses, cette règle s'applique de manière frappante dans presque tous les domaines de la gestion, de l'informatique et de la production industrielle.

## 2. Description / Fonctionnement
Plutôt que d'essayer de résoudre 100% d'un problème (ce qui demande un temps et un budget quasi infinis), la règle de Pareto incite fortement le management à identifier et à se concentrer en priorité absolue sur la petite portion (les fameux 20%) de causes qui génèrent l'immense majorité (les 80%) des résultats ou des pannes.

## 3. Utilisation / Cas Pratique
Ce principe est massivement utilisé par les managers, les chefs de projet et les équipes informatiques pour prioriser leurs actions (afin d'être proactifs plutôt que réactifs) :
* **En Gestion de Projet Logiciel** : 20 % des fonctionnalités d'un logiciel répondent en réalité à 80 % des besoins quotidiens des utilisateurs. L'équipe doit donc développer ces 20% vitaux en premier pour fournir de la valeur rapidement ([Méthode Agile](../Gestion_de_projet/agile_scrum.md)).
* **En Support Informatique (ITIL)** : 80 % des tickets d'incidents informatiques (les appels au support) sont causés par seulement 20 % des bugs ou des vieux serveurs. L'équipe du *Problem Management* doit identifier ces 20% de causes racines pour faire chuter radicalement la charge du centre de services d'un seul coup.
* **En Cybersécurité** : 80 % des failles et piratages réussis proviennent de seulement 20 % de mauvaises pratiques humaines basiques (ex: mots de passe faibles, manque de MFA, absence de mises à jour Windows).

## 4. Modifications possibles / Alternatives
Bien qu'elle soit une règle d'or puissante, la répartition mathématique n'est presque jamais d'exactement 80/20 (elle peut être de 90/10, 70/30, ou même 80/10 car la somme ne doit pas obligatoirement faire 100). L'important est de comprendre le déséquilibre profond entre l'effort et le résultat. 
Une méthodologie qui prolonge l'esprit de Pareto pour traquer les causes majeures de problèmes dans l'industrie est la **Matrice d'Ishikawa** (Diagramme en arêtes de poisson) souvent couplée à la méthode qualité *Lean / Six Sigma*.

## 5. Exemples visuels et Liens utiles

### Tableau de distribution de Pareto (Concept Support IT)
Imaginons un centre de support qui analyse la cause de ses pannes du mois passé :

| Cause racine identifiée (Les 20%) | Nombre de tickets générés (Les 80%) |
| :--- | :---: |
| **Oubli de mot de passe** | 450 appels |
| **Imprimante de l'étage 2 bloquée** | 350 appels |
| *Réseau légèrement ralenti* (Détail) | 50 appels |
| *Clavier cassé* (Détail) | 10 appels |

*Conclusion managériale basée sur Pareto : Au lieu d'embaucher 3 techniciens pour gérer tous les appels, le DSI met en place un bouton de "Réinitialisation de mot de passe en libre-service par SMS" et change l'imprimante de l'étage 2. Il vient d'éradiquer instantanément près de 80% de la charge de travail de son équipe d'un seul coup (Action préventive).*

`Voir aussi : [KPI](kpi.md) | [ITIL V4](../Processus/itil.md)`
