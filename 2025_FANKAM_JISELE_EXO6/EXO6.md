
## Exercice 6 : Supprimer des données

Effectuez des requêtes DELETE pour supprimer des données dans les tables.
> aside: positive
> Exemple : supprimez une réservation existante ou encore retirer un utilisateur du système.
>

1. Requête de suppression d’une réservation existante
DELETE FROM reservation
WHERE ID = 5;

2. Requête de suppression d'une réservation ou la date de retour prévue est passée.
 DELETE FROM reservation
WHERE Date_Retour < CURRENT_DATE;
