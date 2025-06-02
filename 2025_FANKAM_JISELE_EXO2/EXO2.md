## Exercice 2 : Effectuer des requêtes de sélection

Effectuez des requêtes SELECT pour récupérer des informations sur les utilisateurs, le matériel, les réservations et les emprunts. Utilisez des clauses ``WHERE``  pour filtrer les résultats en fonction de critères spécifiques. 

> aside: negative
> Au moins 3 requêtes sont attendues (avec au moins une par table et comprenant des clauses ``WHERE``)
>


SELECT * 
FROM Utilisateur 
WHERE Promo = 'ING3';


SELECT * 
FROM Materiel 
WHERE Quantite_Disponible < 5;


SELECT ID, Nom, Prenom, Promo
FROM Utilisateur
WHERE Mail = 'clara.petit@etu.univ-tours.fr';


SELECT * FROM Reservation WHERE Etat_Retour = 'Bon';

