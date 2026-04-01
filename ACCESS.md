table à ajouter

- commande (date montant_total)
  - commande_id (clef_primaire)
  - client_id (clef étrangère) --> même nom que la table d'origine
  - commande_montant
  - commande_date
- detail_commande (ref_article ; quantités )
  - detail_commande_id (clef primaire)
  - commande_id (clef étrangère)
  - detail_commande_ref (refet)
  - detail\*quantite
    - detail_remise

Ajouts des élément dans une table déjà faite

- selection dans le ruban pour modifier la table (Accueil -> Affichage -> mode création)
- ajout clef primaire avec explication de l'id
- explication des parametres en bas de access
- explication de l'auto-incrementation
- CTRL + S pour sauvegarder

1-CREATION D'UNE TABLE

1 - créer pour activer le ruban
2 - dans le ruban création de table
3 - création de l'id clef primaire en premier
4 - création des autres champs
5 - CTRL + S pour save la table et donc la nommer

Autre tuto création de la base de donnée et gestion COURS :

https://www.youtube.com/watch?v=4FXcl0hmn40&list=PLpQBnWleLAas1yqMbmVGJl1WHX-z-jhQs

2-IMPORTATION D'UN FICHIER EXCEL:

- Donées externes
  -> nouvelle source de données
  --> A partir d'un fichier
  ---> EXCEL

3-REDIMENSIONNER LES CHAMPS

- changer la taille du nombre de caractére 255 à 5 (code postal) par exemple

4-FORMATER LES CHAMPS (dans la ligne format)"c'est du confort visuel"

- imposer un affichage dans affichage des attribut de la table on peut dans format imposer un formatage de texte par exemple
- (@) c'est par défaut : > à la place de @ majusule ou minuscule
- 0" g" (0 c'est le nombre standard concatené avec une chaine de caractère ce n'est que de l'affichage)
- format : date()

5-LISTE DEROULANTE (securise la saisie de l'information)

- monsieur ou madame : liste de choix dans les propriétés du champ
  - origine source : on choisit listes de valeurs
  - dans la zone contenu : idique les choix (syntaxe : "Monsieur";"Madame")
  - limiter à liste : OUI (limite à l'utilisation de monsieur madame) NON permet de fairte des preset
  - liste déroulante en fonction d'une autre table : liste choix
    - controle : zone de liste deroulante
    - origine : table/requetes
    - contenu : le nom de la table
    - colonne lié : la colonne affichée (valeur rentré)
    - nbre colonne : nombre de colonne affiché dans la liste
