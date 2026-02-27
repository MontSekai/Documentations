---
tags:
  - Systeme
  - Conteneurs
  - Kubernetes
---

# Kubernetes

Kubernetes est un système open source d'orchestration de conteneurs.

## Architecture

Kubernetes fonctionne sur une architecture de cluster composée de deux types de nœuds :
- **Control Plane (Master Node)** : Gère le cluster (API Server, etcd, Scheduler, Controller Manager).
- **Worker Nodes** : Hébergent les applications via des Pods (Kubelet, Kube-proxy, Container Runtime).

## Commandes principales

Voici quelques commandes incontournables avec l'outil `kubectl` :

| Commande | Explication |
| :--- | :--- |
| **`kubectl get pods`** | Liste les Pods en cours d'exécution dans le namespace actuel. |
| **`kubectl describe pod <nom>`** | Affiche des détails complets sur un Pod spécifique. |
| **`kubectl get nodes`** | Affiche l'état des nœuds du cluster. |
| **`kubectl apply -f fichier.yaml`** | Déploie ou met à jour une ressource à partir d'un fichier manifeste. |

## Certifications Officielles (CNCF)

La CNCF (Cloud Native Computing Foundation) propose 3 certifications pratiques très reconnues pour valider ses compétences sur Kubernetes :

* **CKAD** (Certified Kubernetes Application Developer) : Destinée aux développeurs pour concevoir, construire et déployer des applications cloud natives dans K8s.
* **CKA** (Certified Kubernetes Administrator) : Destinée aux administrateurs pour installer, configurer et gérer des clusters K8s.
* **CKS** (Certified Kubernetes Security Specialist) : Certification avancée (nécessite le CKA préalable) axée sur la sécurisation d'un cluster complet.

## Ressources Utiles

Voici une vidéo de présentation pour aller plus loin :

[![Comprendre Kubernetes](https://img.youtube.com/vi/de0Mm9xT_2U/0.jpg)](https://www.youtube.com/watch?v=de0Mm9xT_2U&t=716s)
*(Cliquez sur l'image pour lancer la vidéo sur YouTube)*
