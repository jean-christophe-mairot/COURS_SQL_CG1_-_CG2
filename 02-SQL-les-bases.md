# Introduction à SQL : La commande SELECT

SQL (Structured Query Language) est un langage utilisé pour interagir avec les bases de données relationnelles. La commande `SELECT` est l'une des plus fondamentales et permet de récupérer des données depuis une ou plusieurs tables.

---

## Syntaxe de base

```sql
SELECT colonne1, colonne2, ...
FROM table;
```

- **`colonne1, colonne2, ...`** : Les colonnes que vous souhaitez afficher.
- **`table`** : Le nom de la table contenant les données.

---

## Exemple 1 : Sélectionner toutes les colonnes

Pour afficher toutes les colonnes d'une table, utilisez `*` :

```sql
SELECT * 
FROM Employes;
```

Cela retourne toutes les colonnes et lignes de la table `Employes`.

---

## Exemple 2 : Sélectionner des colonnes spécifiques

Si vous ne voulez afficher que certaines colonnes :

```sql
SELECT Nom, Prenom 
FROM Employes;
```

Cela retourne uniquement les colonnes `Nom` et `Prenom` de la table `Employes`.

---

## Exemple 3 : Ajouter une condition avec WHERE

Vous pouvez filtrer les résultats avec une clause `WHERE` :

```sql
SELECT Nom, Prenom 
FROM Employes
WHERE Departement = 'Informatique';
```

Cela retourne les employés du département "Informatique".

---

## Exemple 4 : Trier les résultats avec ORDER BY

Pour trier les résultats, utilisez `ORDER BY` :

```sql
SELECT Nom, Prenom, Salaire 
FROM Employes
ORDER BY Salaire DESC;
```

Cela retourne les employés triés par salaire décroissant.

---

## Exemple 5 : Limiter le nombre de résultats avec LIMIT

Pour afficher un nombre limité de lignes :

```sql
SELECT Nom, Prenom 
FROM Employes
LIMIT 5;
```

Cela retourne les 5 premiers employés.

---

## Exemple 6 : Combiner des conditions avec AND et OR

Vous pouvez combiner plusieurs conditions :

```sql
SELECT Nom, Prenom 
FROM Employes
WHERE Departement = 'Informatique' AND Salaire > 3000;
```

Cela retourne les employés du département "Informatique" ayant un salaire supérieur à 3000.

---

## Conclusion

La commande `SELECT` est essentielle pour interroger une base de données. En combinant des clauses comme `WHERE`, `ORDER BY` et `LIMIT`, vous pouvez affiner vos requêtes pour extraire exactement les données dont vous avez besoin.

<!-- ********************************************************************************* -->
<!-- ************************************* EXERCICE ********************************** -->
<!-- ********************************************************************************* -->
## Exercice : Pratique avec des requêtes SELECT

Voici un ensemble de tables représentant une base de données pour une entreprise fictive. Utilisez ces tables pour répondre aux questions suivantes en écrivant les requêtes SQL appropriées.

### Table : Employes
| ID_Employe | Nom       | Prenom    | Departement    | Salaire | Date_Embauche |
|------------|-----------|-----------|----------------|---------|---------------|
| 1          | Dupont    | Jean      | Informatique   | 3500    | 2018-05-10    |
| 2          | Martin    | Claire    | RH             | 2800    | 2020-03-15    |
| 3          | Bernard   | Sophie    | Informatique   | 4000    | 2017-11-23    |
| 4          | Durand    | Paul      | Marketing      | 3200    | 2019-07-01    |
| 5          | Leroy     | Anne      | Informatique   | 3700    | 2021-01-12    |

### Table : Projets
| ID_Projet | Nom_Projet         | Budget  | Departement    |
|-----------|--------------------|---------|----------------|
| 101       | Migration Serveurs | 15000   | Informatique   |
| 102       | Recrutement 2023   | 5000    | RH             |
| 103       | Campagne Pub       | 12000   | Marketing      |
| 104       | Sécurité Réseau    | 20000   | Informatique   |

### Table : Participation
| ID_Employe | ID_Projet | Role          |
|------------|-----------|---------------|
| 1          | 101       | Chef de Projet|
| 3          | 101       | Développeur   |
| 5          | 104       | Analyste      |
| 4          | 103       | Responsable   |

---

### Questions

### Requêtes SQL

1. **Afficher tous les employés du département "Informatique" :**
    ```sql
    SELECT * 
    FROM Employes
    WHERE Departement = 'Informatique';
    ```

2. **Lister les projets ayant un budget supérieur à 10 000 :**
    ```sql
    SELECT * 
    FROM Projets
    WHERE Budget > 10000;
    ```

3. **Afficher les employés embauchés après le 1er janvier 2020 :**
    ```sql
    SELECT * 
    FROM Employes
    WHERE Date_Embauche > '2020-01-01';
    ```

4. **Lister les projets du département "Marketing" :**
    ```sql
    SELECT * 
    FROM Projets
    WHERE Departement = 'Marketing';
    ```

5. **Afficher les employés ayant un salaire supérieur ou égal à 3500 :**
    ```sql
    SELECT * 
    FROM Employes
    WHERE Salaire >= 3500;
    ```

6. **Lister les projets avec un budget compris entre 5 000 et 15 000 :**
    ```sql
    SELECT * 
    FROM Projets
    WHERE Budget BETWEEN 5000 AND 15000;
    ```

7. **Afficher les employés dont le prénom commence par "S" :**
    ```sql
    SELECT * 
    FROM Employes
    WHERE Prenom LIKE 'S%';
    ```

8. **Lister les projets dont le nom contient le mot "Réseau" :**
    ```sql
    SELECT * 
    FROM Projets
    WHERE Nom_Projet LIKE '%Réseau%';
    ```

9. **Afficher les employés qui ne sont pas dans le département "RH" :**
    ```sql
    SELECT * 
    FROM Employes
    WHERE Departement != 'RH';
    ```

10. **Lister les projets ayant un budget inférieur à 20 000 :**
     ```sql
     SELECT * 
     FROM Projets
     WHERE Budget < 20000;
     ```
