---
tags:
  - Management
  - Processus
  - ITIL
  - SLA
---

# ITIL V4 (Information Technology Infrastructure Library)

Le référentiel mondial des bonnes pratiques pour la gestion des services informatiques (ITSM).

## 1. Définition
**ITIL** est un cadre de travail (framework) recensant les meilleures pratiques mondiales pour la gestion des services IT. Son but principal est d'aligner l'informatique sur les besoins réels de l'entreprise : l'IT n'est plus vue comme un simple "centre de coûts" technique, mais comme un véritable partenaire stratégique **co-créateur de valeur** avec les métiers.

## 2. Description / Fonctionnement
ITIL 4 s'appuie sur le "Système de Valeur des Services" (SVS) et délaisse l'ancien cycle de vie en V très rigide (ITIL V3) pour une approche agile, moderne et intégrée aux méthodes DevOps. 

**Les Engagements de Service (SLA)**
Un des piliers fondateurs du fonctionnement ITIL est l'engagement de résultat contractuel :
* **SLA (Service Level Agreement)** : Le contrat de service formel signé entre le fournisseur IT et les clients/métiers (ex: "Le réseau Wi-Fi sera disponible 99.9% du temps").
* **OLA (Operational Level Agreement)** : L'accord interne à l'IT entre les différentes équipes techniques pour supporter le SLA (ex: L'équipe Réseau s'engage à répondre à l'équipe Serveur en moins de 2 heures).
* **UC (Underpinning Contract)** : Le contrat juridique avec les prestataires externes (ex: L'opérateur Fibre Optique).

## 3. Utilisation / Cas Pratique
Les entreprises utilisent les 34 "Pratiques" d'ITIL pour s'organiser au quotidien. Voici comment le Centre de Services (Service Desk) gère les problèmes avec différents types d'actions :

* **Incident Management (Action Réactive / Curative)** : Une imprimante est physiquement en panne ou un utilisateur n'arrive plus à se connecter. L'objectif est de rétablir le service dégradé le plus vite possible (Mode Pompier, solution de contournement autorisée). C'est du **réactif**.
* **Problem Management (Action Préventive / Proactive)** : Le support remarque que la même imprimante tombe en panne tous les lundis matin. L'équipe ouvre une enquête de fond pour trouver la cause racine du problème et remplacer la pièce défectueuse avant qu'une nouvelle panne ne survienne et ne crée de nouveaux tickets d'incident. C'est du **préventif**.
* **Change Enablement (Action Évolutive)** : L'entreprise veut changer de serveur de messagerie. Avant de toucher à quoi que ce soit, on analyse les risques et on prépare un plan de retour arrière (*Rollback*) pour minimiser les impacts métiers en cas de catastrophe lors du changement.

## 4. Modifications possibles / Alternatives
ITIL n'est pas une loi stricte à appliquer à la lettre. Le principe fondateur est "*Adopt and Adapt*" : il est fortement recommandé de piocher uniquement les pratiques utiles et de les adapter à la taille et à la culture de son organisation. 
Une alternative ou un complément technique pour le monde moderne du développement est l'approche **DevOps**, qui automatise, fluidifie et accélère tout ce qu'ITIL essaie de sécuriser de manière procédurale.

## 5. Exemples visuels et Liens utiles

### Les 4 Dimensions du Service Management (ITIL 4)
Pour réussir à délivrer un service correctement, ITIL impose de ne jamais oublier l'équilibre de ces 4 piliers fondamentaux (ne pas penser "que" à la technologie) :
1. **Organisation et Personnes** (La culture d'entreprise, les compétences, le management)
2. **Information et Technologie** (Les logiciels, les bases de données, les serveurs)
3. **Partenaires et Fournisseurs** (Les contrats externes, les sous-traitants vitaux)
4. **Flux de valeur et Processus** (Comment le travail s'enchaîne de manière logique)

`Voir aussi : [Diagramme des flux](diagramme_des_flux.md) | [KPI](../Strategie/kpi.md)`
