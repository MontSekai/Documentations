---
tags:
  - Systeme
  - Conteneurs
  - Docker
  - Deploiement
---

# Docker (Aide-mémoire)

Ceci est une page d'exemple pour vous montrer comment un outil est rangé dans l'arborescence (ici : `Systeme/Conteneurs/docker.md`) mais qu'il peut posséder de multiples tags.

## Commandes principales

Lancer un conteneur :
```bash
docker run -d --name mon-serveur nginx:latest
```

Lister les conteneurs actifs :
```bash
docker ps
```

Nettoyer les images inutilisées : 
```bash
docker system prune -a
```

## Intégration

Docker s'intègre avec d'autres concepts de la documentation, comme le [Réseau](../Reseau) avec ses réseaux virtuels ou la [Cybersécurité](../Cybersecurite) avec le renforcement des conteneurs. Utilisez les tags en haut de page pour naviguer.
