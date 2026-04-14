# SQL - Clauses et Notions Avancées

## 1. WHERE
Filtre les lignes avant la sélection.

```sql
SELECT * FROM clients WHERE age > 18;
SELECT * FROM produits WHERE prix < 100 AND categorie = 'Électronique';
```

**Opérateurs disponibles :**
- `=`, `!=`, `<>` (égal, différent)
- `<`, `>`, `<=`, `>=`
- `BETWEEN` : `WHERE age BETWEEN 18 AND 65`
- `IN` : `WHERE ville IN ('Paris', 'Lyon', 'Marseille')`
- `LIKE` : `WHERE nom LIKE 'A%'` (commence par A)
- `AND`, `OR`, `NOT`

---

## 2. GROUP BY
Regroupe les lignes par colonnes spécifiées et agrège les données.


```sql
SELECT categorie, COUNT(*) as nombre_produits 
FROM produits 
GROUP BY categorie;

SELECT client_id, SUM(montant) as total_achats 
FROM commandes 
GROUP BY client_id;
```

**Fonctions d'agrégation :**
- `COUNT()` : compte les lignes
- `SUM()` : somme
- `AVG()` : moyenne
- `MIN()` : minimum
- `MAX()` : maximum

---

## 3. HAVING
Filtre les groupes après le `GROUP BY` (comme `WHERE` mais pour les agrégats).

```sql
SELECT categorie, COUNT(*) as nombre 
FROM produits 
GROUP BY categorie 
HAVING COUNT(*) > 5;

SELECT client_id, SUM(montant) as total 
FROM commandes 
GROUP BY client_id 
HAVING SUM(montant) > 1000;
```

**Différence :** 
- `WHERE` filtre avant le regroupement
- `HAVING` filtre après le regroupement

---

## 4. ORDER BY
Trie les résultats selon une ou plusieurs colonnes.

```sql
SELECT * FROM clients ORDER BY nom ASC;
SELECT * FROM commandes ORDER BY date DESC;
SELECT * FROM produits ORDER BY categorie ASC, prix DESC;
```

**Paramètres :**
- `ASC` : ascendant (par défaut)
- `DESC` : descendant

---

## 5. LIMIT
Limite le nombre de lignes retournées.

```sql
SELECT * FROM produits LIMIT 10;
SELECT * FROM clients ORDER BY date_creation DESC LIMIT 5;
```

---

## 6. OFFSET
Saute les N premières lignes (pagination).

```sql
SELECT * FROM produits LIMIT 10 OFFSET 0;   -- Lignes 1-10
SELECT * FROM produits LIMIT 10 OFFSET 10;  -- Lignes 11-20
SELECT * FROM produits LIMIT 10 OFFSET 20;  -- Lignes 21-30
```

**Syntaxe alternative :**
```sql
SELECT * FROM produits LIMIT 10, 10;  -- Skip 10, prendre 10
```

---

## 7. DISTINCT
Élimine les doublons dans les résultats.

```sql
SELECT DISTINCT ville FROM clients;
SELECT DISTINCT categorie FROM produits;
SELECT DISTINCT client_id, date FROM commandes;
```

**Utilisation avec COUNT :**
```sql
SELECT COUNT(DISTINCT ville) as nombre_villes 
FROM clients;
```

---

## 8. NULL
Représente l'absence de valeur.

```sql
SELECT * FROM clients WHERE email IS NULL;
SELECT * FROM commandes WHERE discount IS NOT NULL;
SELECT COALESCE(telephone, 'Non fourni') FROM clients;
```

**Opérateurs NULL :**
- `IS NULL` : teste si vide
- `IS NOT NULL` : teste si non vide
- `COALESCE(col1, col2, ...)` : retourne la première valeur non NULL
- `IFNULL()` ou `ISNULL()` : selon la BD

**Important :** NULL != NULL (toujours faux), utiliser `IS NULL`

---

## Exemple complet

```sql
SELECT 
    categorie,
    COUNT(*) as nombre_produits,
    AVG(prix) as prix_moyen,
    MAX(prix) as prix_max
FROM produits
WHERE prix > 50
GROUP BY categorie
HAVING COUNT(*) > 3
ORDER BY prix_moyen DESC
LIMIT 10;
```

**Ordre d'exécution :**
1. FROM / WHERE → sélectionne les lignes
2. GROUP BY → regroupe
3. HAVING → filtre les groupes
4. SELECT → sélectionne les colonnes
5. ORDER BY → trie
6. LIMIT / OFFSET → limite les résultats

---

## Schémas des Tables

**Clients**
```
┌─────────────┬──────────────┬─────────┬──────────────────┐
│ client_id   │ nom          │ age     │ ville            │
├─────────────┼──────────────┼─────────┼──────────────────┤
│ 1           │ Alice        │ 28      │ Paris            │
│ 2           │ Bob          │ 22      │ Lyon             │
│ 3           │ Claire       │ 35      │ Paris            │
│ 4           │ David        │ 18      │ Marseille        │
│ 5           │ Eva          │ 42      │ Bordeaux         │
└─────────────┴──────────────┴─────────┴──────────────────┘
```

**Produits**
```
┌────────────┬──────────────┬─────────┬──────────────────┐
│ id         │ nom          │ prix    │ categorie        │
├────────────┼──────────────┼─────────┼──────────────────┤
│ 101        │ Laptop       │ 1200    │ Électronique     │
│ 102        │ Souris       │ 25      │ Électronique     │
│ 103        │ Livre SQL    │ 35      │ Livres           │
│ 104        │ Clavier      │ 150     │ Électronique     │
│ 105        │ Moniteur     │ 450     │ Électronique     │
│ 106        │ Chaise       │ 250     │ Meubles          │
│ 107        │ Bureau       │ 800     │ Meubles          │
│ 108        │ Lampe        │ 45      │ Meubles          │
│ 109        │ Cache        │ 15      │ Accessoires      │
│ 110        │ Câble        │ 20      │ Accessoires      │
│ 111        │ Tapis        │ 120     │ Meubles          │
│ 112        │ Curseur      │ 85      │ Électronique     │
└────────────┴──────────────┴─────────┴──────────────────┘
```

**Commandes**
```
┌─────────────┬────────────┬─────────┬──────────────────┐
│ id          │ client_id  │ montant │ date             │
├─────────────┼────────────┼─────────┼──────────────────┤
│ 1001        │ 1          │ 1200    │ 2025-01-15       │
│ 1002        │ 1          │ 75      │ 2025-01-20       │
│ 1003        │ 2          │ 450     │ 2025-02-01       │
│ 1004        │ 3          │ 1050    │ 2025-02-10       │
│ 1005        │ 3          │ 150     │ 2025-02-15       │
│ 1006        │ 2          │ 200     │ 2025-02-20       │
│ 1007        │ 4          │ 85      │ 2025-02-22       │
│ 1008        │ 5          │ 2000    │ 2025-03-01       │
└─────────────┴────────────┴─────────┴──────────────────┘
```

---

## Exercices d'Application

### Exercice 1 : WHERE - Filtrage simple
Afficher tous les clients âgés de plus de 25 ans.
```sql
SELECT * FROM clients WHERE age > 25;
```

**Réponse :**
```
┌───────────┬─────────┬─────┬───────────┐
│ client_id │ nom     │ age │ ville     │
├───────────┼─────────┼─────┼───────────┤
│ 1         │ Alice   │ 28  │ Paris     │
│ 3         │ Claire  │ 35  │ Paris     │
│ 5         │ Eva     │ 42  │ Bordeaux  │
└───────────┴─────────┴─────┴───────────┘
```

### Exercice 2 : WHERE avec conditions multiples
Afficher les produits de la catégorie 'Électronique' avec un prix entre 100 et 500.
```sql
SELECT * FROM produits 
WHERE categorie = 'Électronique' AND prix BETWEEN 100 AND 500;
```

**Réponse :**
```
┌────┬──────────┬───────┬──────────────┐
│ id │ nom      │ prix  │ categorie    │
├────┼──────────┼───────┼──────────────┤
│ 104│ Clavier  │ 150   │ Électronique │
│ 105│ Moniteur │ 450   │ Électronique │
│ 112│ Curseur  │ 85    │ Électronique │
└────┴──────────┴───────┴──────────────┘
```

### Exercice 3 : GROUP BY et COUNT
Compter le nombre de commandes par client.
```sql
SELECT client_id, COUNT(*) as nombre_commandes 
FROM commandes 
GROUP BY client_id;
```

**Réponse :**
```
┌───────────┬───────────────────────┐
│ client_id │ nombre_commandes      │
├───────────┼───────────────────────┤
│ 1         │ 2                     │
│ 2         │ 2                     │
│ 3         │ 2                     │
│ 4         │ 1                     │
│ 5         │ 1                     │
└───────────┴───────────────────────┘
```

### Exercice 4 : GROUP BY avec agrégation
Calculer le montant total et le montant moyen des commandes par client.
```sql
SELECT client_id, SUM(montant) as total, AVG(montant) as moyenne 
FROM commandes 
GROUP BY client_id;
```

**Réponse :**
```
┌───────────┬───────┬──────────┐
│ client_id │ total │ moyenne  │
├───────────┼───────┼──────────┤
│ 1         │ 1275  │ 637.50   │
│ 2         │ 650   │ 325.00   │
│ 3         │ 1200  │ 600.00   │
│ 4         │ 85    │ 85.00    │
│ 5         │ 2000  │ 2000.00  │
└───────────┴───────┴──────────┘
```

### Exercice 5 : HAVING - Filtrer les groupes
Afficher les clients ayant dépensé plus de 500 € en total.
```sql
SELECT client_id, SUM(montant) as total_depense 
FROM commandes 
GROUP BY client_id 
HAVING SUM(montant) > 500;
```

**Réponse :**
```
┌───────────┬────────────────┐
│ client_id │ total_depense  │
├───────────┼────────────────┤
│ 1         │ 1275           │
│ 2         │ 650            │
│ 3         │ 1200           │
│ 5         │ 2000           │
└───────────┴────────────────┘
```

### Exercice 6 : ORDER BY
Afficher les 5 clients ayant le plus dépensé, triés par montant décroissant.
```sql
SELECT client_id, SUM(montant) as total_depense 
FROM commandes 
GROUP BY client_id 
ORDER BY total_depense DESC 
LIMIT 5;
```

**Réponse :**
```
┌───────────┬────────────────┐
│ client_id │ total_depense  │
├───────────┼────────────────┤
│ 5         │ 2000           │
│ 1         │ 1275           │
│ 3         │ 1200           │
│ 2         │ 650            │
│ 4         │ 85             │
└───────────┴────────────────┘
```

### Exercice 7 : LIMIT et OFFSET - Pagination
Afficher les produits de la page 2 (5 produits par page).
```sql
SELECT * FROM produits 
ORDER BY id 
LIMIT 5 OFFSET 5;
```

**Réponse :**
```
┌────┬─────────────┬───────┬──────────────┐
│ id │ nom         │ prix  │ categorie    │
├────┼─────────────┼───────┼──────────────┤
│ 6  │ Chaise      │ 45    │ Meuble       │
│ 7  │ Table       │ 120   │ Meuble       │
│ 8  │ Lampe       │ 30    │ Décoration   │
│ 9  │ Miroir      │ 55    │ Décoration   │
│ 10 │ Étagère     │ 80    │ Meuble       │
└────┴─────────────┴───────┴──────────────┘
```

### Exercice 8 : DISTINCT
Lister toutes les villes distinctes où les clients sont situés, compter leur nombre.
```sql
SELECT DISTINCT ville FROM clients;
SELECT COUNT(DISTINCT ville) as nombre_villes FROM clients;
```

**Réponse (Villes distinctes) :**
```
┌──────────────┐
│ ville        │
├──────────────┤
│ Paris        │
│ Lyon         │
│ Marseille    │
│ Bordeaux     │
└──────────────┘
```

**Réponse (Nombre de villes) :**
```
┌────────────────┐
│ nombre_villes  │
├────────────────┤
│ 4              │
└────────────────┘
```

### Exercice 9 : NULL - Gestion des valeurs manquantes
Afficher tous les clients avec leur email, en remplaçant les valeurs NULL par 'Email manquant'.
```sql
SELECT client_id, nom, COALESCE(email, 'Email manquant') as email 
FROM clients;
```

**Réponse :**
```
┌────────────┬──────────┬──────────────────────┐
│ client_id  │ nom      │ email                │
├────────────┼──────────┼──────────────────────┤
│ 1          │ Jean     │ jean@mail.com        │
│ 2          │ Marie    │ Email manquant       │
│ 3          │ Pierre   │ pierre@mail.com      │
│ 4          │ Sophie   │ Email manquant       │
└────────────┴──────────┴──────────────────────┘
```

### Exercice 10 : Requête complète
Afficher le chiffre d'affaires total par catégorie, trié par chiffre d'affaires décroissant, en filtrant les catégories ayant un prix moyen supérieur à 50.
```sql
SELECT categorie, COUNT(*) as nombre_produits, AVG(prix) as prix_moyen, SUM(prix * quantite) as chiffre_affaires
FROM produits 
GROUP BY categorie 
HAVING AVG(prix) > 50
ORDER BY chiffre_affaires DESC;
```

**Réponse :**
```
┌────────────────┬──────────────────┬────────────┬──────────────────┐
│ categorie      │ nombre_produits  │ prix_moyen │ chiffre_affaires │
├────────────────┼──────────────────┼────────────┼──────────────────┤
│ Électronique   │ 5                │ 545.00     │ 2725.00          │
│ Vêtements      │ 4                │ 65.00      │ 260.00           │
└────────────────┴──────────────────┴────────────┴──────────────────┘
```
