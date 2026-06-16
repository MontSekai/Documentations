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

---

## 3. Checklist obligatoire à la création d'une page

**À NE JAMAIS OUBLIER :** La simple création d'une nouvelle page Markdown avec du texte ne suffit pas. Pour qu'elle soit correctement intégrée au wiki, vous devez systématiquement vérifier ces 3 points :

1. **L'en-tête YAML (Tags)** : Toute page doit commencer par un bloc définissant ses catégories pour le moteur de recherche.
   ```yaml
   ---
   tags:
     - CategoriePrincipale
     - MotClef
   ---
   ```
2. **Le Maillage Interne (Liens)** : Créez des ponts ! Ajoutez systématiquement dans le corps du texte ou dans la section 5 des liens vers d'autres concepts du wiki (ex: `Voir aussi : [Modèle OSI](../Protocoles/modele_osi.md)`).
3. **Mise à jour de la Navigation** : Pour que la page soit visible par l'utilisateur, vous devez ajouter son chemin d'accès à deux endroits précis :
   - Le fichier racine **`mkdocs.yml`** (pour l'intégrer au menu latéral gauche).
   - Le fichier **`docs/index.md`** (pour l'intégrer aux blocs de la page d'accueil).
