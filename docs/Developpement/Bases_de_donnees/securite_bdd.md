---
tags:
  - Developpement
  - Bases_de_donnees
  - Cybersécurité
  - SQL Injection
---

# Sécurisation des Bases de Données

Les bonnes pratiques vitales pour protéger le cœur de l'information de l'entreprise (MariaDB, MySQL, PostgreSQL).

## 1. Définition
La sécurisation d'une base de données est l'ensemble des pratiques techniques, réseaux et logicielles visant à empêcher le vol d'informations, l'altération ou la destruction des données par des pirates informatiques, ou même par de simples erreurs humaines en interne. Les bases de données étant la cible et le "trésor" numéro 1 des hackers, leur sécurisation est une priorité absolue de la politique de sécurité (PSSI).

## 2. Description / Fonctionnement
La sécurité d'un serveur SGBDR s'opère obligatoirement sur trois couches distinctes :
1. **La Couche Réseau** : Isoler la base de données de l'Internet public.
2. **La Couche d'Authentification (Moindre Privilège)** : Les comptes informatiques qui accèdent à la base ne doivent avoir que les droits strictement nécessaires (le droit de supprimer ne doit pas être donné par défaut).
3. **La Couche Applicative (Le Code web)** : Le code des développeurs doit filtrer impitoyablement les requêtes envoyées par les utilisateurs pour éviter les injections.

## 3. Utilisation / Cas Pratique (Les 3 Règles d'Or)

### Règle n°1 : Isoler la base (Niveau Réseau)
Un serveur MariaDB ou MySQL tourne et écoute par défaut sur le port réseau **3306**. Ce port ne doit **absolument JAMAIS** être ouvert sur Internet (vers l'IP publique). Seul le serveur Web (Apache/Nginx) situé dans l'entreprise ou hébergeant le site a le droit de communiquer avec le port 3306 de la base de données. Dans MariaDB, l'administrateur force l'écoute sur l'interface locale en configurant : `bind-address = 127.0.0.1`.

### Règle n°2 : Le Principe du Moindre Privilège (Niveau Droits SQL)
L'application web PHP ou Python ne doit JAMAIS se connecter à MariaDB en utilisant le compte maître `root`. Ce compte a le pouvoir absolu de supprimer toutes les bases de données du serveur.
L'administrateur système doit créer un compte SQL dédié par application (ex: un utilisateur "Wordpress"), avec un mot de passe très complexe, et ne lui donner (via la commande SQL `GRANT`) que le droit strict de lire et d'écrire (`SELECT, INSERT, UPDATE, DELETE`) et ce, **uniquement** sur sa propre petite base de données.

### Règle n°3 : Parer l'Injection SQL (Niveau Code)
L'injection SQL est la vulnérabilité la plus destructrice et la plus courante. Un pirate tape un bout de code SQL malveillant directement dans le champ de recherche du site web (ex: `' OR 1=1; DROP TABLE users;`). Si le développeur concatène bêtement ce texte directement dans la requête SQL sans le nettoyer, le moteur MariaDB va exécuter la fin de la phrase et détruire la table `users`.
**La Solution infaillible :** Le développeur doit obligatoirement utiliser des **Requêtes Préparées (Prepared Statements)** avec des bibliothèques modernes (ex: *PDO* en PHP, *Prisma* en Node.js) qui séparent hermétiquement l'ordre SQL d'un côté, et la donnée envoyée par l'utilisateur de l'autre.

## 4. Modifications possibles / Alternatives
Outre ces trois protections actives fondamentales, la sécurité passe inévitablement par une politique de **sauvegarde hors-ligne robuste** ([La règle du 3-2-1](../../Systeme/Services/sauvegarde.md)).
Dans les environnements très sensibles (santé, finance), on ajoute le **Chiffrement au repos**. Les disques durs contenant les fichiers physiques de la base MariaDB sont chiffrés (BitLocker, LUKS) afin que le vol physique du serveur dans le DataCenter ne permette pas de lire les tables de données.

## 5. Exemples visuels et Liens utiles

### Les commandes SQL de sécurité (Moindre privilège)
Une fois la base de données créée, voici le flux parfait pour sécuriser l'accès de l'application web :

```sql
-- 1. Création d'un utilisateur spécifique pour le site (avec mot de passe très fort)
CREATE USER 'site_web_user'@'localhost' IDENTIFIED BY 'UnMotDePasseTresLongEtComplexe!!';

-- 2. On lui donne uniquement le droit de lire et écrire, EXCLUSIVEMENT sur la base nommée 'boutique'
GRANT SELECT, INSERT, UPDATE, DELETE ON boutique.* TO 'site_web_user'@'localhost';

-- 3. On applique les droits immédiatement dans la mémoire de MariaDB
FLUSH PRIVILEGES;
```

`Voir aussi : [Mémento SQL](commande_sql.md) | [Moindre privilège et IAM](../../Cybersecurite/identite_acces.md)`
