---
tags:
  - [Thème principal]
  - [Sujet]
  - [Sous-sujet]
---

# Titre du fichier (ex: Docker)

Ce fichier est le **modèle de base** (Template) pour chaque ajout de nouvelle documentation.

## Règles d'arborescence

Toute nouvelle documentation doit respecter l'arborescence stricte suivante dans le dossier `docs/` :
`Thème principal` > `Sujet` > `Fichier unique par sous-sujet`

### Exemple concret :
`Systeme` > `Conteneurs` > `docker.md` (ou `kubernetes.md`)

* **Thème principal** (`Systeme`) : Correspond au point d'entrée global dans la navigation MkDocs. Au clic, l'index principal présente tous les sujets de ce thème (OS, Virtualisation, Conteneurs, etc.).
* **Sujet** (`Conteneurs`) : Correspond au dossier qui regroupera tous les outils ou notions de même nature. Au clic (ou dans la section), vous y trouvez les outils spécifiques (Docker, Kubernetes).
* **Sous-sujet** (`docker.md`) : Fichier Markdown unique détaillant l'outil ou le sous-sujet en question.

---

## Modèle de contenu

*Le contenu de votre fichier `.md` devrait suivre cette base :*

```markdown
---
tags:
  - [Thème principal]
  - [Sujet]
  - [Nom du Sous-sujet]
---

# Nom du Sous-sujet

Introduction breve sur le sous-sujet.

## Section 1 (Ex: Installation / Principes)

... description ...

## Section 2 (Ex: Commandes principales ou Configuration)

... description ou blocs de code ...
```
