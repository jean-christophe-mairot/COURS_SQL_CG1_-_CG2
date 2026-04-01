# Exercices SQL - Utilisation de SELECT

## Contexte : Gestion d'un site e-commerce

Ces exercices sont à réaliser sur papier ou sous format word puis vous mettrez en place ce même exercice sur access en créant les différentes requêtes avec son sytème de selection et manuellement.

Vous travaillez pour une entreprise de commerce en ligne. La base de données contient plusieurs tables, notamment :

- **Produits** : Informations sur les produits vendus.
  - `id_produit`, `nom`, `categorie`, `prix`, `stock`
- **Clients** : Informations sur les clients.
  - `id_client`, `nom`, `email`, `ville`, `pays`
- **Commandes** : Informations sur les commandes passées.
  - `id_commande`, `id_client`, `date_commande`, `montant_total`
- **Details_Commandes** : Détails des produits dans chaque commande.
  - `id_commande`, `id_produit`, `quantite`, `prix_unitaire`

### Exercices

#### Niveau 1 : Requêtes simples

1. Affichez tous les produits disponibles dans la table `Produits`.
2. Listez les noms et emails des clients.
3. Affichez les commandes passées après le 1er janvier 2023.
4. Listez les produits dont le prix est supérieur à 50.
5. Affichez les clients résidant en France.

#### Niveau 2 : Utilisation de filtres et tris

6. Affichez les produits triés par prix croissant.
7. Listez les clients triés par leur nom par ordre alphabétique.
8. Affichez les commandes dont le montant total est compris entre 100 et 500.
9. Listez les produits en rupture de stock (stock = 0).
10. Affichez les 5 produits les plus chers.

#### Niveau 3 : Fonctions d'agrégation

11. Comptez le nombre total de produits dans la table `Produits`.
12. Calculez le prix moyen des produits.
13. Affichez le nombre total de commandes passées.
14. Trouvez le montant total des commandes pour l'année 2022.
15. Affichez le nombre de clients par pays.

#### Niveau 4 : Groupes et sous-totaux

16. Listez le nombre de produits par catégorie.
17. Affichez le montant total des commandes pour chaque client.
18. Calculez le stock total disponible pour chaque catégorie de produit.
19. Affichez la moyenne des montants des commandes par mois.
20. Listez les villes avec le nombre de clients dans chaque ville.

#### Niveau 5 : Requêtes avec jointures

21. Affichez les détails des commandes avec le nom du produit et le prix unitaire.
22. Listez les commandes avec le nom du client et le montant total.
23. Affichez les produits commandés par chaque client.
24. Listez les clients qui ont commandé des produits de la catégorie "Électronique".
25. Affichez les commandes avec le nom du client et la date de commande.

#### Niveau 6 : Requêtes avancées

26. Trouvez les clients qui n'ont jamais passé de commande.
27. Listez les produits qui n'ont jamais été commandés.
28. Affichez les clients ayant passé plus de 5 commandes.
29. Listez les produits les plus commandés (par quantité totale).
30. Affichez les clients ayant dépensé plus de 1000 euros.

#### Niveau 7 : Sous-requêtes

31. Affichez les produits dont le prix est supérieur au prix moyen des produits.
32. Listez les clients ayant passé une commande d'un montant supérieur à la moyenne des commandes.
33. Trouvez les produits commandés uniquement par un seul client.
34. Affichez les commandes contenant plus de 3 produits différents.
35. Listez les clients ayant commandé tous les produits d'une catégorie donnée.

#### Niveau 8 : Requêtes complexes

36. Affichez les 3 clients ayant dépensé le plus.
37. Listez les produits les moins commandés (par quantité totale).
38. Affichez les commandes avec le montant total et le nombre de produits commandés.
39. Trouvez les clients ayant passé des commandes dans au moins 3 mois différents.
40. Listez les produits dont le stock est inférieur à la quantité totale commandée.

Bonne chance avec ces exercices ! Assurez-vous de bien comprendre les relations entre les tables avant de commencer.

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
