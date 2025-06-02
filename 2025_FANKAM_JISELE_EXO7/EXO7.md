
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
WHERE R.id_etudiant IS NULL;

3. Afficher les équipements ayant été emprunté plus de 3 fois
SELECT M.id, M.nom, COUNT(R.id_etudiant) AS Nombre_Emprunts
FROM Materiel M
JOIN Reservation R ON M.ID = R.ID_Materiel
GROUP BY M.id, M.nom
HAVING COUNT(R.id_etudiant) > 3;

4. Afficher le nombre d’emprunts pour chaque utilisateur, ordonné par numéro d'étudiant. Les utilisateurs n'ayant pas de réservations en cours doivent également être affichés avec la valeur 0 dans le nombre d'emprunts.
SELECT U.id, U.nom, U.prenom, COUNT(R.id_etudiant) AS Nombre_Emprunts
FROM Utilisateur U
LEFT JOIN Reservation R ON U.ID = R.ID_Etudiant
GROUP BY U.id, U.nom, U.prenom
ORDER BY U.ID;


> aside: positive
> Aide : Assurez-vous d’avoir tous les pré-requis avant de penser à tester vos requêtes.
>