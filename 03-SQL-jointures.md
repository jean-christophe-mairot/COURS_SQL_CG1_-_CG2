# Les Jointures en SQL : Exemple avec Clients et Factures

Les jointures en SQL permettent de combiner des données provenant de plusieurs tables en fonction d'une condition commune. Voici un cours simple utilisant des tables `Clients` et `Factures`.

## Tables Exemple

### Table `Clients`

| ClientID | Nom    | Ville     |
| -------- | ------ | --------- |
| 1        | Dupont | Paris     |
| 2        | Martin | Lyon      |
| 3        | Durand | Marseille |

### Table `Factures`

| FactureID | ClientID | Montant |
| --------- | -------- | ------- |
| 101       | 1        | 500     |
| 102       | 2        | 300     |
| 103       | 1        | 200     |

## Comprendre les Tables à Gauche et à Droite dans une Jointure

Dans une jointure SQL, il est important de comprendre les notions de "table à gauche" et "table à droite". Ces termes sont définis par la position des tables dans la requête SQL.

### Définition

- **Table à gauche** : C'est la table mentionnée en premier dans la clause `FROM`.
- **Table à droite** : C'est la table mentionnée après la clause `JOIN`.

### Exemple

Prenons l'exemple suivant :

```sql
SELECT Clients.Nom, Factures.Montant
FROM Clients
LEFT JOIN Factures ON Clients.ClientID = Factures.ClientID;
```

- Ici, `Clients` est la table à gauche car elle est mentionnée dans la clause `FROM`.
- `Factures` est la table à droite car elle est mentionnée après `LEFT JOIN`.

### Cas des Jointures Externes

Pour les jointures externes (`LEFT JOIN` ou `RIGHT JOIN`), la table "gauche" ou "droite" détermine quelles lignes seront incluses dans le résultat, même si aucune correspondance n'est trouvée :

- Dans un `LEFT JOIN`, toutes les lignes de la table à gauche sont incluses, même si aucune correspondance n'existe dans la table à droite.
- Dans un `RIGHT JOIN`, toutes les lignes de la table à droite sont incluses, même si aucune correspondance n'existe dans la table à gauche.

### Visualisation

Voici un schéma simplifié pour illustrer :

```
LEFT JOIN : Toutes les lignes de la table à gauche + correspondances
RIGHT JOIN : Toutes les lignes de la table à droite + correspondances
```

Comprendre cette distinction est essentiel pour écrire des requêtes SQL précises et adaptées à vos besoins.

## Types de Jointures

### 1. Jointure Interne (INNER JOIN)

Récupère les lignes correspondantes dans les deux tables.

### Explication de INNER JOIN

Une jointure interne (`INNER JOIN`) permet de récupérer uniquement les lignes qui ont des correspondances dans les deux tables. Si une ligne dans l'une des tables n'a pas de correspondance dans l'autre table, elle sera exclue du résultat.

#### Syntaxe Générale

```sql
SELECT colonnes
FROM table1
INNER JOIN table2 ON condition;
```

- `table1` : La première table.
- `table2` : La deuxième table.
- `condition` : La condition qui relie les deux tables (souvent une clé étrangère).

#### Exemple avec les Tables `Clients` et `Factures`

```sql
SELECT Clients.Nom, Factures.Montant
FROM Clients
INNER JOIN Factures ON Clients.ClientID = Factures.ClientID;
```

Dans cet exemple :

- La condition `Clients.ClientID = Factures.ClientID` relie les deux tables.
- Seules les lignes où un `ClientID` existe dans les deux tables seront incluses dans le résultat.

#### Résultat

| Nom    | Montant |
| ------ | ------- |
| Dupont | 500     |
| Dupont | 200     |
| Martin | 300     |

#### Utilisation

L'`INNER JOIN` est utile lorsque vous souhaitez travailler uniquement avec les données qui ont des correspondances dans les deux tables.

```sql
SELECT Clients.Nom, Factures.Montant
FROM Clients
INNER JOIN Factures ON Clients.ClientID = Factures.ClientID;
```

**Résultat :**
| Nom | Montant |
|--------|---------|
| Dupont | 500 |
| Dupont | 200 |
| Martin | 300 |

### 2. Jointure Gauche (LEFT JOIN)

Récupère toutes les lignes de la table de gauche et les correspondances de la table de droite.

```sql
SELECT Clients.Nom, Factures.Montant
FROM Clients
LEFT JOIN Factures ON Clients.ClientID = Factures.ClientID;
```

**Résultat :**
| Nom | Montant |
|---------|---------|
| Dupont | 500 |
| Dupont | 200 |
| Martin | 300 |
| Durand | NULL |

### 3. Jointure Droite (RIGHT JOIN)

Récupère toutes les lignes de la table de droite et les correspondances de la table de gauche.

```sql
SELECT Clients.Nom, Factures.Montant
FROM Clients
RIGHT JOIN Factures ON Clients.ClientID = Factures.ClientID;
```

**Résultat :**
| Nom | Montant |
|--------|---------|
| Dupont | 500 |
| Dupont | 200 |
| Martin | 300 |

### 4. Jointure Complète (FULL OUTER JOIN)

Récupère toutes les lignes des deux tables, avec des `NULL` pour les non-correspondances.

### La Notion de NULL en SQL

En SQL, `NULL` représente une valeur manquante ou inconnue. Ce n'est pas équivalent à zéro ou à une chaîne vide, mais plutôt à l'absence de valeur.

#### Points Clés sur `NULL`

- `NULL` signifie "inconnu" ou "non applicable".
- Les opérations arithmétiques ou comparaisons avec `NULL` renvoient également `NULL`.
- Pour tester la présence de `NULL`, utilisez les opérateurs `IS NULL` ou `IS NOT NULL`.

#### Exemple

Considérons la table `Clients` suivante :

| ClientID | Nom    | Ville |
| -------- | ------ | ----- |
| 1        | Dupont | Paris |
| 2        | Martin | Lyon  |
| 3        | Durand | NULL  |

Si nous exécutons la requête suivante :

```sql
SELECT Nom, Ville
FROM Clients
WHERE Ville IS NULL;
```

**Résultat :**

| Nom    | Ville |
| ------ | ----- |
| Durand | NULL  |

#### Importance de `NULL` dans les Jointures

Dans les jointures, `NULL` apparaît souvent lorsque :

- Une ligne dans une table n'a pas de correspondance dans l'autre table.
- Une jointure externe (`LEFT JOIN`, `RIGHT JOIN`, ou `FULL OUTER JOIN`) est utilisée.

Exemple avec un `LEFT JOIN` :

```sql
SELECT Clients.Nom, Factures.Montant
FROM Clients
LEFT JOIN Factures ON Clients.ClientID = Factures.ClientID;
```

**Résultat :**

| Nom    | Montant |
| ------ | ------- |
| Dupont | 500     |
| Dupont | 200     |
| Martin | 300     |
| Durand | NULL    |

Dans cet exemple, `NULL` dans la colonne `Montant` indique qu'aucune facture n'existe pour le client `Durand`.

#### Bonnes Pratiques (OPTION)

- Utilisez `COALESCE` pour remplacer `NULL` par une valeur par défaut :

```sql
SELECT Nom, COALESCE(Ville, 'Non spécifiée') AS Ville
FROM Clients;
```

**Résultat :**

| Nom    | Ville         |
| ------ | ------------- |
| Dupont | Paris         |
| Martin | Lyon          |
| Durand | Non spécifiée |

Comprendre et gérer les `NULL` est crucial pour éviter des erreurs dans vos requêtes SQL.

```sql
SELECT Clients.Nom, Factures.Montant
FROM Clients
FULL OUTER JOIN Factures ON Clients.ClientID = Factures.ClientID;
```

**Résultat :**
| Nom | Montant |
|---------|---------|
| Dupont | 500 |
| Dupont | 200 |
| Martin | 300 |
| Durand | NULL |

## Conclusion

Les jointures sont essentielles pour manipuler des bases de données relationnelles. Choisissez le type de jointure en fonction de vos besoins pour combiner les données efficacement.
