---
tags:
  - Management
  - Gestion_de_projet
  - QCD
---

# Triangle QCD (Qualité, Coût, Délai)

Le triptyque QCD représente les trois contraintes majeures et indissociables de tout projet. On l'appelle souvent le "triangle de fer" de la gestion de projet.

## Le principe d'équilibre

Toute modification structurelle sur l'un de ces sommets aura un impact direct sur au moins un autre :
- Un livrable plus rapide (Délai) demandera souvent plus de ressources (Coût) ou une baisse d'exigence (Qualité).
- Une réduction de budget (Coût) allongera les délais ou sacrifiera des fonctionnalités (Qualité).

## Les compromis du triangle QCD

<div align="center">
  <img src="../../images/qcd.webp" alt="Triangle QCD" width="400">
</div>

En associant deux des trois sommets du triangle, on sacrifie inévitablement le troisième. Voici les trois combinaisons classiques :

* **Qualité + Coût (Bien & Pas cher) = Projet lent** : La livraison prendra beaucoup de temps (Délai non respecté).
* **Qualité + Délai (Bien & Rapide) = Projet cher** : Nécessite énormément de ressources financières ou humaines (Coût élevé).
* **Coût + Délai (Pas cher & Rapide) = Faible qualité** : Le travail est bâclé ou incomplet pour tenir le budget et les temps serrés (Qualité sacrifiée).

## Évaluation et comparatif de solutions

Le modèle QCD est un outil d'aide à la décision extrêmement puissant lorsqu'il s'agit de **comparer plusieurs choix** (Ex: prestataires, logiciels, méthodes de déploiement) ou d'**évaluer le succès d'un projet**.

### Comparer des solutions

Lors du recueil des offres, attribuez une note objective à chaque solution sur ces 3 critères :

* **Solution A (Le haut de gamme)** : Excellente Qualité métier, Délais garantis, mais Coût d'acquisition prohibitif.
* **Solution B (L'Open Source interne)** : Coût de licence nul, Qualité sur-mesure, mais Délai de mise en place très long dû au manque de ressources d'ingénierie interne.
* **Solution C (L'externalisation Low-Cost)** : Délai rapide, Coût imbattable, mais fort risque de Qualité technique médiocre (dette technique).

Le choix final dépendra toujours du curseur stratégique défini par la direction en amont du projet. Qu'étions-nous prêts à sacrifier ?

### Adaptabilité du Modèle (Indicateurs Supplémentaires)

Un outil de management n'est pas figé : il doit s'adapter à votre besoin pour exprimer au mieux votre attente. Bien que le modèle originel se limite à Triptyque Q-C-D, rien ne vous empêche d'y greffer de nouveaux critères indispensables liés à votre domaine d'étude.

* **Cybersécurité** : Ajouter le critère de *Sécurité* (confidentialité/chiffrement).
* **Support IT** : Ajouter le critère de *Temps de réponse* (SLA).
* **Technologie pure** : Ajouter les critères de *Prise en main* (courbe d'apprentissage), de *Maintenance* ou encore de *Ressources numériques nécessaires* au fonctionnement (poids en RAM/CPU).

**Graduation :**
Pour réaliser un comparatif solide, il est conseillé de graduer chacun de ces indicateurs (ex: de 1 à 5). Vous obtiendrez ainsi un modèle radar (ou *"spider chart"*) qui mettra visuellement en exergue les points forts et faibles de chaque offre.

### Évaluer un projet post-mortem

C'est LE métrique de réussite classique d'un Chef de Projet.

* Le budget a-t-il été dépassé ? (Coût)
* La date de *Go-Live* a-t-elle été respectée ou repoussée ? (Délai)
* Le taux de bugs/retours utilisateurs ou les fonctionnalités annulées sont-ils acceptables ? (Qualité)
