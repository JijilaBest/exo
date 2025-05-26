## Exercice 3 : Effectuer des requêtes de jointure 

Effectuez des requêtes de jointure pour combiner les données de plusieurs tables. 

> aside: positive
> Exemple : Récupérez les informations sur les utilisateurs ayant effectué une réservation donnée, ou encore les informations sur le matériel emprunté par un utilisateur donné. 
>

Afficher les noms des utilisateurs et le matériel qu'ils ont emprunté
SELECT U.Nom, U.Prenom, R.Date_Emprunt, R.Date_Retour
FROM Utilisateur U
JOIN Reservation R ON U.ID = R.ID_Etudiant;



