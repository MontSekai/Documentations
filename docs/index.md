# Raphaël Hirsch - Base de Connaissances

Bienvenue sur la documentation technique centrale.

Cette documentation est construite sur un modèle de **dossiers plats** pour les grandes catégories et d'un **système de Tags** pour croiser les sujets complexes (ex: le Management dans la Cybersécurité, ou Docker dans le Système).

## Navigation Rapide

??? note "Système"
    - [Général (Page Accueil)](Systeme/systeme.md)
    ??? note "OS"
        - [Commandes Linux (Debian)](Systeme/OS/commande_linux.md)
        - [Commandes Windows](Systeme/OS/commande_windows.md)
        - [Windows Server](Systeme/OS/windows_server.md)
        ??? note "Active Directory"
            - [Forêts et Domaines](Systeme/OS/ad_forets_domaines.md)
            - [Rôles FSMO](Systeme/OS/ad_fsmo.md)
            - [Types de contrôleurs de domaine](Systeme/OS/ad_types_dc.md)
    ??? note "Automatisation"
        - [Ansible](Systeme/Automatisation/ansible.md)
    ??? note "Conteneurs"
        - [Docker](Systeme/Conteneurs/docker.md)
        - [Kubernetes](Systeme/Conteneurs/kubernetes.md)
    ??? note "Infrastructure as Code"
        - [Terraform](Systeme/Infrastructure_as_Code/terraform.md)
    ??? note "Services"
        - [DHCP](Systeme/Services/dhcp.md)
        - [DNS](Systeme/Services/dns.md)
        - [Sauvegarde et PRA](Systeme/Services/sauvegarde.md)
        - [Supervision / SNMP](Systeme/Services/supervision.md)

??? note "Réseau"
    - [Général (Page Accueil)](Reseau/reseau.md)
    ??? note "Protocoles"
        - [Ethernet et Trames](Reseau/Protocoles/ethernet_trames.md)
        - [Modèle OSI](Reseau/Protocoles/modele_osi.md)
        - [TCP/IP](Reseau/Protocoles/tcp_ip.md)
    ??? note "VPN"
        - [OpenVPN](Reseau/VPN/open_vpn.md)
    ??? note "Sécurité réseau"
        - [Proxy, Reverse Proxy, WAF, Pare-feu](Reseau/Securite/proxy_firewall.md)
        - [ACL](Reseau/Securite/acl.md)
    ??? note "Infrastructure"
        - [VLAN et Segmentation réseau](Reseau/vlan.md)
        - [Routage et Routage inter-VLAN](Reseau/routage.md)

??? note "Management"
    - [Général (Page Accueil)](Management/management.md)
    ??? note "Gestion de projet"
        - [Diagramme de GANTT](Management/Gestion_de_projet/gantt.md)
        - [Diagramme PERT](Management/Gestion_de_projet/pert.md)
        - [Matrice des risques](Management/Gestion_de_projet/matrice_des_risques.md)
        - [Matrice RACI](Management/Gestion_de_projet/raci.md)
        - [Triangle QCD](Management/Gestion_de_projet/qcd.md)
    ??? note "Processus"
        - [Diagramme des flux](Management/Processus/diagramme_des_flux.md)
        - [Référentiel ITIL](Management/Processus/itil.md)
    ??? note "Stratégie"
        - [Buts et Objectifs](Management/Strategie/but_objectif.md)
        - [KPI](Management/Strategie/kpi.md)
        - [Matrice SWOT](Management/Strategie/swot.md)

??? note "Cybersécurité"
    - [Général (Page Accueil)](Cybersecurite/cybersecurite.md)
    ??? note "Méthodologies"
        - [EBIOS Risk Manager](Cybersecurite/ebios.md)
    ??? note "Outils de détection"
        - [EDR](Cybersecurite/edr.md)
        - [XDR](Cybersecurite/xdr.md)
        - [SIEM](Cybersecurite/siem.md)
        - [NDR](Cybersecurite/ndr.md)
    ??? note "Normes et Réglementation"
        - [RGPD, HDS, ISO 27001, NIS2...](Cybersecurite/normes_reglementation.md)
    ??? note "Gouvernance"
        - [PSSI](Cybersecurite/pssi.md)
        - [PGSSI-S](Cybersecurite/pgssi_s.md)
        - [PCA / PRA](Cybersecurite/pca_pra.md)
        - [Cyber Assurance](Cybersecurite/cyber_assurance.md)
        - [ANSSI](Cybersecurite/anssi.md)
        - [CNIL](Cybersecurite/cnil.md)

??? note "Développement"
    - [Général (Page Accueil)](Developpement/developpement.md)
    ??? note "Bases de données"
        - [SQL](Developpement/Bases_de_donnees/sql.md)

??? note "Autres et Projets"
    - [Général (Page Accueil)](Autres/autres.md)
    ??? note "Projets"
        - [RPG Tower Crawler](Autres/rpg-tower-crawler.md)

---

*L'intégration d'un Chatbot IA type "RAG" (Mendable, Dify...) est prévue pour pouvoir poser des questions en langage naturel à cette documentation.*
