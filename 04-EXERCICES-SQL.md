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



## Données exemple

### Table Produits

| id_produit | nom | categorie | prix | stock |
|---|---|---|---|---|
| 1 | Laptop Dell | Électronique | 899.99 | 15 |
| 2 | Souris Logitech | Électronique | 29.99 | 50 |
| 3 | Chaise Bureau | Mobilier | 199.99 | 8 |
| 4 | Clavier Mécanique | Électronique | 149.99 | 25 |
| 5 | Moniteur LG 27" | Électronique | 349.99 | 12 |
| 6 | Bureau Bois | Mobilier | 459.99 | 5 |
| 7 | Lampe LED | Accessoires | 39.99 | 40 |
| 8 | Webcam HD | Électronique | 79.99 | 0 |
| 9 | Casque Audio | Électronique | 119.99 | 22 |
| 10 | Tapis Souris | Accessoires | 14.99 | 100 |

### Table Clients

| id_client | nom | email | ville | pays |
|---|---|---|---|---|
| 1 | Jean Dupont | jean.dupont@mail.com | Paris | France |
| 2 | Marie Martin | marie.martin@mail.com | Lyon | France |
| 3 | Pierre Bernard | pierre.bernard@mail.com | Marseille | France |
| 4 | Sophie Laurent | sophie.laurent@mail.com | Toulouse | France |
| 5 | Luc Moreau | luc.moreau@mail.com | Amsterdam | Pays-Bas |
| 6 | Isabelle Dubois | isabelle.dubois@mail.com | Bruxelles | Belgique |
| 7 | Marc Petit | marc.petit@mail.com | Genève | Suisse |
| 8 | Claudine Nicolas | claudine.nicolas@mail.com | Berlin | Allemagne |
| 9 | Robert Lefevre | robert.lefevre@mail.com | Madrid | Espagne |
| 10 | Véronique Girard | veronique.girard@mail.com | Bordeaux | France |

### Table Commandes

| id_commande | id_client | date_commande | montant_total |
|---|---|---|---|
| 1 | 1 | 2023-01-15 | 1259.96 |
| 2 | 2 | 2023-02-20 | 449.97 |
| 3 | 1 | 2023-03-10 | 299.99 |
| 4 | 3 | 2023-04-05 | 879.98 |
| 5 | 4 | 2023-05-12 | 159.98 |
| 6 | 5 | 2023-06-18 | 569.96 |
| 7 | 2 | 2023-07-22 | 199.99 |
| 8 | 6 | 2023-08-30 | 1019.95 |
| 9 | 7 | 2023-09-14 | 349.99 |
| 10 | 1 | 2023-10-25 | 689.97 |

### Table Details_Commandes

| id_commande | id_produit | quantite | prix_unitaire |
|---|---|---|---|
| 1 | 1 | 1 | 899.99 |
| 1 | 2 | 1 | 29.99 |
| 1 | 7 | 8 | 39.99 |
| 2 | 3 | 2 | 199.99 |
| 2 | 7 | 1 | 39.99 |
| 3 | 5 | 1 | 349.99 |
| 4 | 1 | 1 | 899.99 |
| 5 | 4 | 1 | 149.99 |
| 6 | 3 | 2 | 199.99 |
| 10 | 9 | 2 | 119.99 |


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
