---
tags:
  - Developpement
  - API
  - REST
---

# API (Application Programming Interface)

Le langage universel qui permet aux logiciels de se parler entre eux.

## 1. Définition
Une **API** (Interface de Programmation d'Application) est un "pont technique" et un contrat strict. C'est un ensemble de règles définies par le créateur d'un logiciel pour permettre à d'autres logiciels (développés par des sociétés tierces) de venir piocher ses données ou utiliser ses fonctionnalités, de manière très sécurisée, sans jamais avoir besoin de connaître ou d'accéder au code source secret interne.

## 2. Description / Fonctionnement
Aujourd'hui, le standard mondial du web est l'**API REST (RESTful API)**, qui est basée sur le classique [protocole Web HTTP](../../Reseau/Protocoles/http_https.md). 
Elle fonctionne avec des requêtes Web standards (`GET, POST, PUT, DELETE`) mais contrairement à un site web qui renvoie du code visuel complexe (HTML/CSS) fait pour un œil humain, l'API serveur renvoie des données brutes, propres et structurées dans un format texte léger fait pour les robots : le format **JSON**.

Exemple de requête vers une API Météo publique :
L'application smartphone envoie : `GET https://api.meteo.com/v1/ville/paris`
Le serveur API répond instantanément avec ce code JSON :
```json
{
  "ville": "Paris",
  "temperature_celsius": 22,
  "condition": "Soleil",
  "alerte_meteo": false
}
```

## 3. Utilisation / Cas Pratique
L'intégralité de l'économie numérique moderne repose sur les APIs (C'est le modèle d'*API Economy*) :
* Quand vous utilisez l'application Uber sur votre téléphone, Uber ne possède pas ses propres satellites ni sa propre base de données cartographique mondiale. L'application Uber appelle en temps réel **l'API de Google Maps** pour afficher la carte.
* Quand vous payez sur un petit site e-commerce, le site appelle secrètement l'API de **Stripe** ou de **PayPal** pour sécuriser et valider la fraude bancaire, de sorte que le site web ne touche jamais à votre vrai numéro de carte de crédit.
* En automatisation d'infrastructure système, un script de [Terraform](../../Systeme/Infrastructure_as_Code/terraform.md) interroge l'API du Cloud *AWS (Amazon)* pour lui ordonner la création automatique de 100 nouvelles machines virtuelles en 10 secondes, sans qu'aucun humain n'ouvre l'interface graphique.

`Voir aussi : [Bases de données SQL](../Bases_de_donnees/sql.md)`
