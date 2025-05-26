
## Exercice 7 : Requêtes avancées

Effectuer les requêtes suivantes :

1. Afficher tous les utilisateurs ayant emprunté au moins un équipement
SELECT DISTINCT U.ID, U.Nom, U.Prenom
FROM Utilisateur U
JOIN Reservation R ON U.ID = R.ID_Etudiant;

2. Afficher les équipements n’ayant jamais été empruntés
SELECT M.ID, M.Nom
FROM Materiel M
LEFT JOIN Reservation R ON M.ID = R.ID_Materiel
WHERE R.ID IS NULL;

3. Afficher les équipements ayant été emprunté plus de 3 fois
SELECT M.ID, M.Nom, COUNT(R.ID) AS Nombre_Emprunts
FROM Materiel M
JOIN Reservation R ON M.ID = R.ID_Materiel
GROUP BY M.ID, M.Nom
HAVING COUNT(R.ID) > 3;

4. Afficher le nombre d’emprunts pour chaque utilisateur, ordonné par numéro d'étudiant. Les utilisateurs n'ayant pas de réservations en cours doivent également être affichés avec la valeur 0 dans le nombre d'emprunts.
SELECT U.ID, U.Nom, U.Prenom, COUNT(R.ID) AS Nombre_Emprunts
FROM Utilisateur U
LEFT JOIN Reservation R ON U.ID = R.ID_Etudiant
GROUP BY U.ID, U.Nom, U.Prenom
ORDER BY U.ID;


> aside: positive
> Aide : Assurez-vous d’avoir tous les pré-requis avant de penser à tester vos requêtes.
>