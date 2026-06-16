---
tags:
  - Documentation
  - Charte
---

# Charte Éditoriale de la Documentation

Pour maintenir une base de connaissances claire, lisible et uniforme, toutes les pages de ce wiki doivent respecter l'une des deux structures définies ci-dessous.

## 1. Modèle pour les "Concepts" (Théorie, Méthodes, Outils, Normes)

La grande majorité des pages de la documentation concerne des concepts théoriques. Elles doivent suivre cette structure à 5 sections :

```markdown
---
tags:
  - [Tag 1]
  - [Tag 2]
---

# [Titre Principal H1]

[Courte phrase d'introduction résumant de quoi parle la page]

## 1. Définition
Ce que c'est de manière simple et directe (le "Quoi").

## 2. Description / Fonctionnement
Comment ça marche techniquement ou conceptuellement (le "Comment").

## 3. Utilisation / Cas Pratique
Dans quel contexte l'utiliser concrètement en entreprise (le "Pourquoi").

## 4. Modifications possibles / Alternatives
Les limites, les outils concurrents, ou comment adapter le concept à son environnement spécifique.

## 5. Exemples visuels et Liens utiles
Obligatoire pour les concepts visuels (ex: GANTT, RACI, WBS). 
Insérer une image, un diagramme Mermaid, ou des liens externes vers des sites de référence reconnus (ex: BDGP).
**IMPORTANT :** C'est également ici (ou dans le corps du texte via des liens Markdown standard) qu'il faut ajouter des liens de redirection internes vers d'autres concepts liés du wiki (ex: `Voir aussi : [Nom du concept](../dossier/fichier.md)`). Cela permet de créer un maillage logique entre les pages.
```

## 2. Modèle pour les "Mémentos Techniques" (Commandes)

Les pages regroupant des commandes CLI (Linux, Windows) ou des bouts de code doivent consolider l'information en utilisant des tableaux classés par catégories (Titres H2). 
Il est **recommandé** de garder les commandes d'un même écosystème sur une seule et même page (ex: `commande_linux.md`) pour faciliter la recherche `Ctrl+F`.

```markdown
---
tags:
  - [Tag 1]
---

# Mémento : [Sujet]

[Courte phrase d'introduction expliquant le but du mémento]

## 1. [Catégorie 1, ex: Gestion des Utilisateurs]

| Commande | Action | Exemple concret |
| :--- | :--- | :--- |
| `ls -la` | Lister tout le contenu en détail | `ls -la /var/log/` |

> [!NOTE] 
> Une explication spécifique ou complexe concernant l'une des commandes du tableau (Optionnel).

## 2. [Catégorie 2, ex: Réseau]

| Commande | Action | Exemple concret |
| :--- | :--- | :--- |
| `ping` | Tester la connectivité IP | `ping 8.8.8.8` |
```
