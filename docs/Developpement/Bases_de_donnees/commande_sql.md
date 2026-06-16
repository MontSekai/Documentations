---
tags:
  - Developpement
  - SQL
  - Commandes
  - Mémento
---

# Mémento : Requêtes SQL (MariaDB / MySQL)

Ce mémento regroupe les commandes essentielles pour manipuler une base de données SQL. Les requêtes s'exécutent via l'outil en ligne de commande `mysql -u root -p`, via des interfaces web (ex: *phpMyAdmin*) ou des logiciels lourds (ex: *DBeaver*).

## 1. Création et Structure (DDL - Data Definition Language)

| Commande | Action | Exemple concret |
| :--- | :--- | :--- |
| `CREATE DATABASE` | Créer une nouvelle base de données | `CREATE DATABASE boutique;` |
| `USE` | Se placer dans une base pour y travailler | `USE boutique;` |
| `CREATE TABLE` | Créer une nouvelle table avec ses colonnes | `CREATE TABLE users (id INT AUTO_INCREMENT PRIMARY KEY, nom VARCHAR(50));` |
| `DROP TABLE` | Supprimer définitivement une table et son contenu | `DROP TABLE users;` |

## 2. Lecture de données (DQL - Le "R" du CRUD)

| Commande | Action | Exemple concret |
| :--- | :--- | :--- |
| `SELECT *` | Lire absolument toutes les colonnes d'une table | `SELECT * FROM users;` |
| `WHERE` | Filtrer les résultats (Condition essentielle) | `SELECT nom FROM users WHERE id = 144;` |
| `ORDER BY` | Trier les résultats par ordre | `SELECT * FROM users ORDER BY nom ASC;` |
| `LIMIT` | Restreindre le nombre de résultats (Pagination) | `SELECT * FROM users LIMIT 10;` |

## 3. Les Jointures (Croiser des tables - Inclusions/Exclusions)

Les jointures (`JOIN`) permettent de relier la Table A et la Table B dans une seule requête.

| Type de Jointure | Action (Venn Diagram) | Syntaxe SQL (Exemple) |
| :--- | :--- | :--- |
| **INNER JOIN** | L'intersection stricte. Ne renvoie QUE les éléments communs à A et B. | `SELECT * FROM A INNER JOIN B ON A.key = B.key` |
| **LEFT JOIN** | Tout le cercle A, plus l'intersection avec B. | `SELECT * FROM A LEFT JOIN B ON A.key = B.key` |
| **LEFT JOIN (Exclusif)** | Tout le cercle A, **SANS** l'intersection avec B (Ce qui est unique à A). | `SELECT * FROM A LEFT JOIN B ON A.key = B.key WHERE B.key IS NULL` |
| **RIGHT JOIN** | Tout le cercle B, plus l'intersection avec A. | `SELECT * FROM A RIGHT JOIN B ON A.key = B.key` |
| **RIGHT JOIN (Exclusif)**| Tout le cercle B, **SANS** l'intersection avec A (Ce qui est unique à B). | `SELECT * FROM A RIGHT JOIN B ON A.key = B.key WHERE A.key IS NULL` |
| **FULL JOIN** | L'union totale. Renvoie absolument tout (A, B, et l'intersection). | `SELECT * FROM A FULL JOIN B ON A.key = B.key` |
| **FULL JOIN (Exclusif)** | L'exclusion mutuelle. Renvoie tout, **SAUF** l'intersection. | `SELECT * FROM A FULL JOIN B ON A.key = B.key WHERE A.key IS NULL OR B.key IS NULL` |

## 4. Écriture, Modification et Suppression (DML)

| Commande | Action | Exemple concret |
| :--- | :--- | :--- |
| `INSERT INTO` | Ajouter une nouvelle ligne (Création) | `INSERT INTO users (nom, email) VALUES ('Dupont', 'dupont@mail.fr');` |
| `UPDATE` | Modifier une donnée existante. | `UPDATE users SET email = 'nouveau@mail.fr' WHERE id = 144;` |
| `DELETE` | Supprimer une ou plusieurs lignes. | `DELETE FROM users WHERE id = 144;` |

> [!WARNING]
> **DANGER ABSOLU :** Toujours utiliser une clause `WHERE` avec `UPDATE` et `DELETE` ! 
> Si vous tapez `UPDATE users SET email = 'test@mail.fr';` sans la clause `WHERE`, la commande écrasera TOUTES les adresses e-mail de TOUS les utilisateurs de votre base de données d'un seul coup.
