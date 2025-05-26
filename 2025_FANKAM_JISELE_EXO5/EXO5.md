## Exercice 5 : Mettre à jour les données

Effectuez des requêtes ``UPDATE`` pour mettre à jour les données dans les tables.

> aside: positive
> Exemple : Modifiez la quantité disponible d'un matériel après un emprunt, ou encore annuler une réservation existante.
>

1. Requête de modification de la quantité disponible d’un matériel

UPDATE Materiel
SET Quantite_Disponible = Quantite_Disponible - 1
WHERE ID = 3;

2. Requête de modification de la quantité de tous les matériels qui sont en cours d'emprunt et la date de retour prévue dans plus de 2 jours.

UPDATE Materiel
SET Quantite_Disponible = Quantite_Disponible - 1
WHERE ID IN (
    SELECT R.ID_Materiel
    FROM Reservation R
    WHERE R.Date_Retour > CURRENT_DATE + INTERVAL '2 days'
);

Vous pouvez utiliser dans PostgreSQL l' instruction
``current_date`` pour avoir la date du jour.

Pour comparer deux dates, vous pouvez utiliser l'instruction ``ìnterval``.

Ex.:

```sql
select CURRENT_DATE

select INTERVAL '80 days';
```
