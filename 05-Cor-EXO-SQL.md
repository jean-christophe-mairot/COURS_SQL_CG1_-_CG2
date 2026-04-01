
<!-- ********************************************************************************* -->
<!-- ************************************** REPONSES ********************************* -->
<!-- ********************************************************************************* -->

### Réponses aux exercices SQL

#### Niveau 1 : Requêtes simples

1. ```sql
   SELECT * FROM Produits;
   ```
2. ```sql
   SELECT nom, email FROM Clients;
   ```
3. ```sql
   SELECT * FROM Commandes WHERE date_commande > '2023-01-01';
   ```
4. ```sql
   SELECT * FROM Produits WHERE prix > 50;
   ```
5. ```sql
   SELECT * FROM Clients WHERE pays = 'France';
   ```

#### Niveau 2 : Utilisation de filtres et tris

6. ```sql
   SELECT * FROM Produits ORDER BY prix ASC;
   ```
7. ```sql
   SELECT * FROM Clients ORDER BY nom ASC;
   ```
8. ```sql
   SELECT * FROM Commandes WHERE montant_total BETWEEN 100 AND 500;
   ```
9. ```sql
   SELECT * FROM Produits WHERE stock = 0;
   ```
10. ```sql
     SELECT * FROM Produits ORDER BY prix DESC LIMIT 5;
    ```

#### Niveau 3 : Fonctions d'agrégation

11. ```sql
     SELECT COUNT(*) AS total_produits FROM Produits;
    ```
12. ```sql
     SELECT AVG(prix) AS prix_moyen FROM Produits;
    ```
13. ```sql
     SELECT COUNT(*) AS total_commandes FROM Commandes;
    ```
14. ```sql
     SELECT SUM(montant_total) AS total_2022 FROM Commandes WHERE YEAR(date_commande) = 2022;
    ```
15. ```sql
     SELECT pays, COUNT(*) AS nombre_clients FROM Clients GROUP BY pays;
    ```

#### Niveau 4 : Groupes et sous-totaux

16. ```sql
     SELECT categorie, COUNT(*) AS nombre_produits FROM Produits GROUP BY categorie;
    ```
17. ```sql
     SELECT id_client, SUM(montant_total) AS total_commandes FROM Commandes GROUP BY id_client;
    ```
18. ```sql
     SELECT categorie, SUM(stock) AS stock_total FROM Produits GROUP BY categorie;
    ```
19. ```sql
     SELECT MONTH(date_commande) AS mois, AVG(montant_total) AS moyenne_montant FROM Commandes GROUP BY mois;
    ```
20. ```sql
     SELECT ville, COUNT(*) AS nombre_clients FROM Clients GROUP BY ville;
    ```

#### Niveau 5 : Requêtes avec jointures

21. ```sql
     SELECT dc.id_commande, p.nom, dc.prix_unitaire
     FROM Details_Commandes dc
     JOIN Produits p ON dc.id_produit = p.id_produit;
    ```
22. ```sql
     SELECT c.id_commande, cl.nom, c.montant_total
     FROM Commandes c
     JOIN Clients cl ON c.id_client = cl.id_client;
    ```
23. ```sql
     SELECT cl.nom AS client, p.nom AS produit
     FROM Commandes c
     JOIN Details_Commandes dc ON c.id_commande = dc.id_commande
     JOIN Produits p ON dc.id_produit = p.id_produit
     JOIN Clients cl ON c.id_client = cl.id_client;
    ```
24. ```sql
     SELECT DISTINCT cl.nom
     FROM Commandes c
     JOIN Details_Commandes dc ON c.id_commande = dc.id_commande
     JOIN Produits p ON dc.id_produit = p.id_produit
     JOIN Clients cl ON c.id_client = cl.id_client
     WHERE p.categorie = 'Électronique';
    ```
25. ```sql
     SELECT c.id_commande, cl.nom, c.date_commande
     FROM Commandes c
     JOIN Clients cl ON c.id_client = cl.id_client;
    ```

#### Niveau 6 : Requêtes avancées

26. ```sql
     SELECT * FROM Clients
     WHERE id_client NOT IN (SELECT id_client FROM Commandes);
    ```
27. ```sql
     SELECT * FROM Produits
     WHERE id_produit NOT IN (SELECT id_produit FROM Details_Commandes);
    ```
28. ```sql
     SELECT id_client, COUNT(*) AS nombre_commandes
     FROM Commandes
     GROUP BY id_client
     HAVING nombre_commandes > 5;
    ```
29. ```sql
     SELECT id_produit, SUM(quantite) AS total_commande
     FROM Details_Commandes
     GROUP BY id_produit
     ORDER BY total_commande DESC;
    ```
30. ```sql
     SELECT id_client, SUM(montant_total) AS total_depense
     FROM Commandes
     GROUP BY id_client
     HAVING total_depense > 1000;
    ```

#### Niveau 7 : Sous-requêtes

31. ```sql
     SELECT * FROM Produits
     WHERE prix > (SELECT AVG(prix) FROM Produits);
    ```
32. ```sql
     SELECT id_client
     FROM Commandes
     WHERE montant_total > (SELECT AVG(montant_total) FROM Commandes);
    ```
33. ```sql
     SELECT id_produit
     FROM Details_Commandes
     GROUP BY id_produit
     HAVING COUNT(DISTINCT id_client) = 1;
    ```
34. ```sql
     SELECT id_commande
     FROM Details_Commandes
     GROUP BY id_commande
     HAVING COUNT(DISTINCT id_produit) > 3;
    ```
35. ```sql
     SELECT id_client
     FROM Details_Commandes dc
     JOIN Produits p ON dc.id_produit = p.id_produit
     GROUP BY id_client, p.categorie
     HAVING COUNT(DISTINCT p.id_produit) = (SELECT COUNT(*) FROM Produits WHERE categorie = p.categorie);
    ```

#### Niveau 8 : Requêtes complexes

36. ```sql
     SELECT id_client, SUM(montant_total) AS total_depense
     FROM Commandes
     GROUP BY id_client
     ORDER BY total_depense DESC
     LIMIT 3;
    ```
37. ```sql
     SELECT id_produit, SUM(quantite) AS total_commande
     FROM Details_Commandes
     GROUP BY id_produit
     ORDER BY total_commande ASC
     LIMIT 5;
    ```
38. ```sql
     SELECT c.id_commande, c.montant_total, COUNT(dc.id_produit) AS nombre_produits
     FROM Commandes c
     JOIN Details_Commandes dc ON c.id_commande = dc.id_commande
     GROUP BY c.id_commande;
    ```
39. ```sql
     SELECT id_client
     FROM Commandes
     GROUP BY id_client
     HAVING COUNT(DISTINCT MONTH(date_commande)) >= 3;
    ```
40. ```sql
     SELECT p.id_produit, p.stock, SUM(dc.quantite) AS total_commande
     FROM Produits p
     JOIN Details_Commandes dc ON p.id_produit = dc.id_produit
     GROUP BY p.id_produit
     HAVING p.stock < total_commande;
    ```
