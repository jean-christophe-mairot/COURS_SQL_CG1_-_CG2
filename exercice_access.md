# Exercice : Création d'une table Fournisseur dans Access

## Objectif
Créer une table nommée **Fournisseur** dans une base de données Access avec les champs suivants :

### Champs de la table
| Nom du champ       | Type de données       | Description                          |
|--------------------|-----------------------|--------------------------------------|
| ID_Fournisseur     | NuméroAuto (Clé primaire) | Identifiant unique du fournisseur.   |
| Nom_Fournisseur    | Texte court          | Nom du fournisseur.                  |
| Adresse            | Texte long           | Adresse complète du fournisseur.     |
| Téléphone          | Texte court          | Numéro de téléphone du fournisseur.  |
| Email              | Texte court          | Adresse email du fournisseur.        |
| Date_Enregistrement| Date/Heure           | Date d'ajout du fournisseur.         |

## Étapes à suivre
1. Ouvrez Microsoft Access et créez une nouvelle base de données.
2. Accédez à l'onglet **Créer** et cliquez sur **Table**.
3. Ajoutez les champs mentionnés dans le tableau ci-dessus :
    - Définissez **ID_Fournisseur** comme clé primaire.
    - Assurez-vous de choisir les types de données appropriés.
4. Enregistrez la table sous le nom **Fournisseur**.
5. Ajoutez quelques enregistrements pour tester la table.

## Exemples d'enregistrements

Voici 10 exemples d'enregistrements que vous pouvez ajouter à la table **Fournisseur** :

| ID_Fournisseur | Nom_Fournisseur       | Adresse                          | Téléphone     | Email                     | Date_Enregistrement |
|----------------|-----------------------|----------------------------------|---------------|---------------------------|---------------------|
| 1              | Fournitures ABC       | 123 Rue Principale, Paris       | 0123456789    | contact@abc.fr            | 2025-01-15          |
| 2              | Matériaux XYZ         | 45 Avenue des Champs, Lyon      | 0987654321    | info@xyz.com              | 2025-01-16          |
| 3              | BureauPro             | 78 Boulevard Haussmann, Paris   | 0678901234    | support@bureaupro.fr      | 2025-01-17          |
| 4              | TechnoServices        | 12 Rue de l'Industrie, Lille    | 0654321987    | contact@technoservices.fr | 2025-01-18          |
| 5              | Papeterie Plus        | 34 Rue des Écoles, Marseille    | 0612345678    | ventes@papeterieplus.fr   | 2025-01-19          |
| 6              | Fournitures Globales  | 56 Rue Lafayette, Bordeaux      | 0623456789    | global@fournitures.com    | 2025-01-20          |
| 7              | Équipements Modernes  | 90 Rue de la Paix, Toulouse     | 0634567890    | contact@equipements.fr    | 2025-01-21          |
| 8              | Solutions Fournitures | 22 Rue des Lilas, Nantes        | 0645678901    | solutions@fournitures.fr  | 2025-01-22          |
| 9              | Accessoires Pro       | 11 Rue des Fleurs, Strasbourg   | 0656789012    | accessoires@pro.fr        | 2025-01-23          |
| 10             | Matériel et Co.       | 67 Rue des Entrepreneurs, Nice  | 0667890123    | contact@materieletco.fr   | 2025-01-24          |



## Résultat attendu
Une table **Fournisseur** correctement structurée et prête à être utilisée dans votre base de données Access.


<!-- ************************************** remarques *************************************-->
## Remarque
Vous pouvez personnaliser les champs ou ajouter des contraintes supplémentaires selon vos besoins.

## Exemples de Contraintes

Voici quelques exemples de contraintes que vous pouvez ajouter pour améliorer l'intégrité des données dans votre table **Fournisseur** :

### Contraintes de validation
- **Nom_Fournisseur** : Assurez-vous que ce champ ne soit pas vide (valeur obligatoire).
- **Téléphone** : Utilisez une règle de validation pour garantir que le numéro respecte un format spécifique (par exemple, `\d{10}` pour un numéro à 10 chiffres).
- **Email** : Ajoutez une règle de validation pour vérifier que l'adresse email est dans un format valide (par exemple, contient `@` et un domaine).

### Contraintes d'unicité
- **Email** : Assurez-vous que chaque fournisseur ait une adresse email unique.
- **Téléphone** : Si applicable, imposez l'unicité pour éviter les doublons.

### Contraintes de longueur
- **Nom_Fournisseur** : Limitez la longueur à 50 caractères maximum.
- **Téléphone** : Limitez la longueur à 15 caractères pour éviter les entrées excessives.

### Contraintes de valeurs par défaut
- **Date_Enregistrement** : Définissez la valeur par défaut sur la date actuelle (`Date()` dans Access).

### Contraintes de relations
- Si vous avez d'autres tables (par exemple, une table **Produits**), vous pouvez établir des relations entre **Fournisseur** et ces tables en utilisant des clés étrangères.

Ces contraintes permettent de garantir la qualité et la cohérence des données dans votre base de données.