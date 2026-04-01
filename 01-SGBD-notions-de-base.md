# Introduction aux Systèmes de Gestion de Bases de Données (SGBD)

## Qu'est-ce qu'un SGBD ?

Un Système de Gestion de Bases de Données (SGBD) est un logiciel permettant de créer, gérer et manipuler des bases de données. Il agit comme une interface entre les utilisateurs et les données, garantissant leur organisation, leur sécurité et leur accessibilité.

## Objectifs d'un SGBD

- **Stockage structuré des données** : Permet de gérer de grandes quantités d'informations.
- **Accès efficace** : Facilite la récupération rapide des données.
- **Sécurité** : Protège les données contre les accès non autorisés.
- **Intégrité** : Garantit la cohérence des données.
- **Multi-utilisateurs** : Permet à plusieurs utilisateurs d'accéder simultanément aux données.

## Composants d'un SGBD

1. **Base de données** : Ensemble structuré de données.
2. **Langage de requête** : Langage utilisé pour interagir avec les données (ex. SQL).
3. **Moteur de stockage** : Gère la lecture et l'écriture des données.
4. **Système de contrôle d'accès** : Gère les permissions des utilisateurs.

## Types de SGBD

1. **Relationnel (RDBMS (en) ou SGBD)** : Organise les données sous forme de tables (ex. MySQL, PostgreSQL).
2. **NoSQL** : Conçu pour des données non structurées ou semi-structurées (ex. MongoDB, Cassandra).
3. **Hiérarchique** : Structure les données sous forme d'arborescence.
4. **Orienté objet** : Intègre les concepts de programmation orientée objet.

## Avantages des SGBD

- Réduction de la redondance des données.
- Amélioration de la cohérence des données.
- Sauvegarde et récupération en cas de panne.
- Gestion centralisée des données.

## Exemple simple en SQL

```sql
-- Création d'une table
CREATE TABLE Etudiants (
    id INT PRIMARY KEY,
    nom VARCHAR(50),
    age INT
);

-- Insertion de données
INSERT INTO Etudiants (id, nom, age) VALUES (1, 'Alice', 22);

-- Requête pour récupérer les données
SELECT * FROM Etudiants;
```

## Conclusion

Les SGBD sont essentiels pour gérer efficacement les données dans les systèmes modernes. Leur compréhension est cruciale pour les développeurs et les administrateurs de bases de données.

<!-- POUR ACCESS ! -->

## ACCESS est-il un SGBD ?

Oui, Microsoft Access est un Système de Gestion de Bases de Données (SGBD). Il permet de créer, gérer et manipuler des bases de données relationnelles. Access combine un moteur de base de données avec une interface utilisateur graphique, ce qui le rend accessible aux utilisateurs non techniques. Il est souvent utilisé pour des projets de petite à moyenne envergure.

### Caractéristiques principales de Microsoft Access :

- **Interface conviviale** : Permet de créer des bases de données sans nécessiter de compétences avancées en programmation.
- **Support SQL** : Inclut un langage SQL pour interagir avec les données.
- **Intégration avec d'autres outils Microsoft** : Fonctionne bien avec Excel, Word, et d'autres produits Office.
- **Multi-utilisateurs** : Permet un accès simultané à plusieurs utilisateurs, bien que limité pour des bases de données complexes.

Cependant, pour des systèmes plus grands ou nécessitant des performances élevées, des SGBD comme SQL Server ou MySQL sont souvent préférés.

<!-- base de données relationnelle -->

## C'est quoi une base de données relationnelle ?

Une base de données relationnelle est un type de base de données qui organise les données sous forme de tables. Chaque table, appelée relation, contient des lignes (enregistrements) et des colonnes (attributs). Les bases de données relationnelles utilisent des clés primaires et étrangères pour établir des relations entre les tables.

### Caractéristiques principales :

- **Structure tabulaire** (tableaux): Les données sont organisées en lignes et colonnes.
- **Relations entre les tables** : Les tables peuvent être liées entre elles grâce à des clés.
- **Langage SQL** : Utilise SQL (Structured Query Language) pour manipuler et interroger les données.
- **Intégrité des données** : Garantit la cohérence et la validité des données grâce à des contraintes.

### Exemple :

Imaginons deux tables : `Etudiants` et `Cours`.

**Table Etudiants** :
| id | nom | age |
|----|--------|-----|
| 1 | Alice | 22 |
| 2 | Bob | 24 |

**Table Cours** :
| id_cours | nom_cours | id_etudiant |
|----------|-----------------|-------------|
| 101 | Mathématiques | 1 |
| 102 | Informatique | 2 |

Dans cet exemple, la colonne `id_etudiant` dans la table `Cours` est une clé étrangère qui fait référence à la colonne `id` dans la table `Etudiants`. Cela permet de relier les étudiants aux cours qu'ils suivent.

Les bases de données relationnelles sont largement utilisées dans les systèmes modernes en raison de leur flexibilité, de leur fiabilité et de leur capacité à gérer des relations complexes entre les données.

## Comment créer un tableau de références pour construire une base de données ?

Un tableau de références est une étape essentielle dans la conception d'une base de données relationnelle. Il permet de définir les relations entre les différentes tables et de structurer les données de manière cohérente.

### Étapes pour créer un tableau de références :

1. **Identifier les entités principales** :

   - Déterminez les objets ou concepts principaux que vous souhaitez modéliser (ex. Étudiants, Cours, Professeurs).

2. **Lister les attributs de chaque entité** :

   - Pour chaque entité, identifiez les informations importantes à stocker (ex. nom, âge, adresse).

3. **Définir les clés primaires** :

### C'est quoi une clé primaire ?

Une clé primaire est un attribut ou un ensemble d'attributs d'une table qui permet d'identifier de manière unique chaque enregistrement dans cette table. Elle garantit qu'aucune ligne de la table n'aura de valeur dupliquée ou nulle pour cet attribut.

### Caractéristiques principales :

- **Unicité** : Chaque valeur de la clé primaire doit être unique dans la table.
- **Non-nullité** : Une clé primaire ne peut pas contenir de valeur nulle.
- **Identifiant unique** : Elle sert d'identifiant pour chaque enregistrement.

### Exemple :

Dans une table `Etudiants` :
| id | nom | age |
|----|--------|-----|
| 1 | Alice | 22 |
| 2 | Bob | 24 |

Ici, la colonne `id` est une clé primaire car elle identifie de manière unique chaque étudiant.

### Pourquoi utiliser une clé primaire ?

- Pour garantir l'intégrité des données.
- Pour établir des relations entre les tables (via des clés étrangères).
- Pour faciliter les recherches et les opérations sur les données.

### Définir une clé primaire en SQL :

```sql
CREATE TABLE Etudiants (
    id INT PRIMARY KEY,
    nom VARCHAR(50),
    age INT
);
```

Dans cet exemple, la colonne `id` est définie comme clé primaire. - Chaque table doit avoir une clé primaire, un identifiant unique pour chaque enregistrement (ex. `id`).

4. **Identifier les relations entre les entités** :

   - Déterminez comment les entités sont liées entre elles (ex. un étudiant peut suivre plusieurs cours).

5. **Créer les clés étrangères** :

   - Ajoutez des colonnes dans les tables pour représenter les relations (ex. `id_etudiant` dans la table `Cours`).

6. **Dessiner un schéma relationnel** :
   - Représentez graphiquement les tables et leurs relations pour visualiser la structure.

### Exemple de tableau de références :

| Table       | Attributs                 | Clé primaire | Clés étrangères       |
| ----------- | ------------------------- | ------------ | --------------------- |
| Étudiants   | id, nom, age              | id           | -                     |
| Cours       | id_cours, nom_cours       | id_cours     | -                     |
| Inscription | id, id_etudiant, id_cours | id           | id_etudiant, id_cours |

### Schéma relationnel correspondant :

- **Étudiants** : `id` (clé primaire)
- **Cours** : `id_cours` (clé primaire)
- **Inscription** : `id` (clé primaire), `id_etudiant` (clé étrangère vers Étudiants), `id_cours` (clé étrangère vers Cours)

Ce tableau de références vous aide à structurer votre base de données et à garantir l'intégrité des relations entre les données.

<!-- ********************************************************************************* -->
<!-- ************************************* EXERCICE ********************************** -->
<!-- ********************************************************************************* -->

## Exercice : Création et manipulation d'une base de données relationnelle

### Objectif :

Mettre en pratique les notions abordées dans ce cours en créant une base de données relationnelle simple et en effectuant des opérations SQL.

### Énoncé :

Vous êtes chargé de créer une base de données pour gérer les informations d'une école. Cette base de données doit inclure les entités suivantes :

1. **Étudiants** : Contient les informations des étudiants.
2. **Cours** : Contient les informations des cours proposés.
3. **Inscriptions** : Permet de suivre quels étudiants sont inscrits à quels cours.

#### Étapes à suivre :

1. **Création des tables** :

   - Créez une table `Etudiants` avec les colonnes suivantes : `id` (clé primaire), `nom`, `age`.
   - Créez une table `Cours` avec les colonnes suivantes : `id_cours` (clé primaire), `nom_cours`.
   - Créez une table `Inscriptions` avec les colonnes suivantes : `id` (clé primaire), `id_etudiant` (clé étrangère vers `Etudiants`), `id_cours` (clé étrangère vers `Cours`).

2. **Insertion de données** :

   - Ajoutez au moins 3 étudiants dans la table `Etudiants`.
   - Ajoutez au moins 2 cours dans la table `Cours`.
   - Ajoutez des inscriptions pour associer les étudiants aux cours.

3. **Requêtes SQL** :
   - Récupérez tous les étudiants inscrits à un cours spécifique.
   - Affichez les cours auxquels un étudiant particulier est inscrit.
   - Comptez le nombre d'étudiants inscrits à chaque cours.

#### Exemple de données :

- Étudiants :
  - (1, 'Alice', 22)
  - (2, 'Bob', 24)
  - (3, 'Charlie', 21)
- Cours :
  - (101, 'Mathématiques')
  - (102, 'Informatique')
- Inscriptions :
  - (1, 1, 101)
  - (2, 2, 102)
  - (3, 3, 101)

### Livrables :

- Le script SQL complet pour créer les tables, insérer les données et exécuter les requêtes.
- Une capture d'écran ou un tableau montrant les résultats des requêtes.

### Bonus :

- Ajoutez une table `Professeurs` et modifiez la structure pour associer chaque cours à un professeur.
- Écrivez une requête pour afficher les cours avec le nom du professeur et les étudiants inscrits.

Bonne chance !
