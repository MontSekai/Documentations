---
tags:
  - Systeme
  - Infrastructure_as_Code
  - Terraform
---

# Terraform

Terraform est un outil open source d'infrastructure en tant que code.

## Providers

Un "Provider" (fournisseur) est un plugin qui permet à Terraform d'interagir avec des API externes (comme AWS, Azure, Google Cloud, ou même Proxmox et VMware). 
C'est la première chose que l'on déclare dans un fichier `main.tf` :

```hcl
provider "aws" {
  region = "eu-west-3"
}
```

## Commandes principales

Voici le cycle de vie classique d'un déploiement avec Terraform :

| Commande | Explication |
| :--- | :--- |
| `terraform init` | Initialise le projet, télécharge les modules et les providers requis. |
| `terraform plan` | Analyse le code et montre ce qui va être créé/modifié/supprimé **sans rien appliquer**. |
| `terraform apply` | Applique les changements (après demande de confirmation). |
| `terraform destroy` | Détruit toute l'infrastructure définie dans le code. |
