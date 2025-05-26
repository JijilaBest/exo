## Exercice 3 : Effectuer des requêtes de jointure 

Effectuez des requêtes de jointure pour combiner les données de plusieurs tables. 

> aside: positive
> Exemple : Récupérez les informations sur les utilisateurs ayant effectué une réservation donnée, ou encore les informations sur le matériel emprunté par un utilisateur donné. 
>

 Requête de jointure sur les utilisateurs ayant effectué une réservation
SELECT U.ID, U.Nom, U.Prenom, U.Mail, R.Date_Emprunt, R.Date_Retour
FROM Utilisateur U
JOIN Reservation R ON U.ID = R.ID_Etudiant;

Requête de jointure pour récupérer les informations sur le matériel emprunté par un utilisateur donné
SELECT M.ID, M.Nom, M.Type, M.Etat, R.Date_Emprunt, R.Date_Retour
FROM Materiel M
JOIN Reservation R ON M.ID = R.ID_Materiel
WHERE R.ID_Etudiant = 1;
