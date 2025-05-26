
## Exercice 4 : Effectuer des requêtes d'agrégation

Effectuez des requêtes d'agrégation pour calculer des statistiques sur les données.

> aside: positive
> Exemple : Calculez le nombre total de réservations effectuées sur une période donnée, ou encore le nombre d'utilisateurs ayant emprunté du matériel donné.
>

1. Requête d’aggrégation pour calculer le nombre total de réservations effectuées sur une période donnée

SELECT COUNT(*) AS Nombre_Reservations
FROM Reservation
WHERE Date_Emprunt BETWEEN '2025-03-01' AND '2025-04-30';

2. Requête d’aggrégation pour calculer le nombre d’utilisateur ayant emprunté du matériel
SELECT COUNT(DISTINCT ID_Etudiant) AS Nombre_Utilisateurs
FROM Reservation;


