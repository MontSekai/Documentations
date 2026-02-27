---
tags:
  - Systeme
  - Automatisation
  - Ansible
---

# Ansible

Ansible est une plateforme logicielle libre pour la configuration et la gestion des ordinateurs.

## Inventaire

L'inventaire est un fichier (généralement appelé `hosts` ou `inventory.ini`) qui liste l'ensemble des serveurs que vous souhaitez administrer avec Ansible.
Il permet de regrouper les machines cibles par catégories :

```ini
[webservers]
192.168.1.10
192.168.1.11

[databases]
192.168.1.20
```

## Playbooks

Un *Playbook* est un fichier au format YAML dans lequel on décrit l'état final désiré (les tâches à accomplir) sur les machines cibles. Ansible est *idempotent* : si l'état est déjà atteint, il ne fera rien de plus.

**Exemple de Playbook simple (`install_nginx.yml`) :**
```yaml
---
- name: Installer et démarrer Nginx
  hosts: webservers
  become: yes  # Exécuter en tant que root (sudo)

  tasks:
    - name: Installation du paquet nginx
      apt:
        name: nginx
        state: present

    - name: S'assurer que le service est démarré
      service:
        name: nginx
        state: started
```

**Pour lancer ce Playbook :**
```bash
ansible-playbook -i inventory.ini install_nginx.yml
```
