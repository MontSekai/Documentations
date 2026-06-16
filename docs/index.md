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
            - [GPO (Stratégies de groupe)](Systeme/OS/gpo.md)
    ??? note "Automatisation"
        - [Ansible](Systeme/Automatisation/ansible.md)
    ??? note "Virtualisation et Conteneurs"
        - [Virtualisation (VM, LXC)](Systeme/virtualisation.md)
        - [Docker](Systeme/Conteneurs/docker.md)
        - [Kubernetes](Systeme/Conteneurs/kubernetes.md)
    ??? note "Infrastructure as Code"
        - [Terraform](Systeme/Infrastructure_as_Code/terraform.md)
    ??? note "Services"
        - [DHCP](Systeme/Services/dhcp.md)
        - [DNS](Systeme/Services/dns.md)
        - [Sauvegarde](Systeme/Services/sauvegarde.md)
        - [Supervision](Systeme/Services/supervision.md)
    ??? note "Stockage"
        - [Baies NetApp (Concept)](Systeme/Stockage/netapp.md)
        - [Commandes NetApp (CLI)](Systeme/Stockage/commande_netapp.md)

??? note "Réseau"
    - [Général (Page Accueil)](Reseau/reseau.md)
    ??? note "Protocoles"
        - [Ethernet et Trames](Reseau/Protocoles/ethernet_trames.md)
        - [Trames taguées : 802.1Q/802.1X](Reseau/Protocoles/802.1Q_802.1X.md)
        - [Modèle OSI](Reseau/Protocoles/modele_osi.md)
        - [TCP/IP](Reseau/Protocoles/tcp_ip.md)
        - [IPv4](Reseau/Protocoles/ipv4.md)
        - [IPv6](Reseau/Protocoles/ipv6.md)
        - [Protocoles de routage](Reseau/protocoles_routage.md)
    ??? note "Physique et Transport"
        - [Câblage et Fibre](Reseau/Physique_Transport/cablage.md)
        - [Ports réseau courants](Reseau/Physique_Transport/ports_reseau.md)
    ??? note "Sans Fil"
        - [Wi-Fi et Sécurité (802.11)](Reseau/wifi.md)
    ??? note "VPN"
        - [OpenVPN](Reseau/VPN/open_vpn.md)
        - [IPSec](Reseau/VPN/ipsec.md)
    ??? note "Sécurité réseau"
        - [Proxy, Reverse Proxy, WAF, Pare-feu](Reseau/Securite/proxy_firewall.md)
        - [ACL](Reseau/Securite/acl.md)
    ??? note "Infrastructure"
        - [VLAN et Segmentation réseau](Reseau/vlan.md)
        - [Routage et Routage inter-VLAN](Reseau/routage.md)
        - [Spanning Tree (STP)](Reseau/spanning_tree.md)
        - [Haute Disponibilité (Cluster)](Reseau/haute_disponibilite.md)

??? note "Cybersécurité"
    - [Général (Page Accueil)](Cybersecurite/cybersecurite.md)
    ??? note "Méthodologies"
        - [EBIOS Risk Manager](Cybersecurite/ebios.md)
    ??? note "Chiffrement et Certificats"
        - [Cryptographie et PKI](Cybersecurite/pki_crypto.md)
    ??? note "Outils de détection"
        - [EDR, NDR, SIEM, XDR (Synthèse)](Cybersecurite/outils_detection.md)
    ??? note "Normes et Réglementation"
        - [RGPD, HDS, ISO 27001, NIS2...](Cybersecurite/normes_reglementation.md)
    ??? note "Gouvernance"
        - [Identité et Accès (IAM/MFA)](Cybersecurite/identite_acces.md)
        - [PSSI](Cybersecurite/pssi.md)
        - [PGSSI-S](Cybersecurite/pgssi_s.md)
        - [PCA / PRA](Cybersecurite/pca_pra.md)
        - [Cyber Assurance](Cybersecurite/cyber_assurance.md)
        - [ANSSI](Cybersecurite/anssi.md)
        - [CNIL](Cybersecurite/cnil.md)

??? note "Management"
    - [Général (Page Accueil)](Management/management.md)
    ??? note "Gestion de projet"
        - [Outils fondamentaux (GANTT, PERT, RACI)](Management/Gestion_de_projet/outils_gestion_projet.md)
        - [Méthodologies de Projet (Cycle en V, Prince2)](Management/Gestion_de_projet/methodologies_projet.md)
        - [Agilité et Scrum](Management/Gestion_de_projet/agile_scrum.md)
        - [PMO et PPM](Management/Gestion_de_projet/pmo_ppm.md)
        - [Matrice des risques](Management/Gestion_de_projet/matrice_des_risques.md)
    ??? note "Processus"
        - [Diagramme des flux](Management/Processus/diagramme_des_flux.md)
        - [BPMN](Management/Processus/bpmn.md)
        - [Référentiel ITIL V4](Management/Processus/itil.md)
    ??? note "Stratégie"
        - [Buts et Objectifs](Management/Strategie/but_objectif.md)
        - [KPI](Management/Strategie/kpi.md)
        - [Matrice SWOT](Management/Strategie/swot.md)
        - [Finance IT (ROI, CAPEX/OPEX)](Management/Strategie/finance_it.md)
        - [Transformation Numérique](Management/Strategie/transformation_numerique.md)
        - [Industrie 4.0](Management/Strategie/industrie_40.md)

??? note "Développement"
    - [Général (Page Accueil)](Developpement/developpement.md)
    ??? note "Bases de données"
        - [SQL](Developpement/Bases_de_donnees/sql.md)

??? note "Autres et Projets"
    - [Général (Page Accueil)](Autres/autres.md)
    - [Charte Éditoriale du Wiki](Autres/charte_editoriale.md)
    ??? note "Projets"
        - [RPG Tower Crawler](Autres/rpg-tower-crawler.md)

---

*L'intégration d'un Chatbot IA type "RAG" (Mendable, Dify...) est prévue pour pouvoir poser des questions en langage naturel à cette documentation.*
