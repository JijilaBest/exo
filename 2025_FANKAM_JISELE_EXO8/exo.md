### Instructions

1. Mettez à jour le modèle de données existant en ajoutant une nouvelle table "disponibilite" avec les colonnes suivantes : 

* ``id_disponibilite`` (clé primaire)
* ``id_materiel`` (clé étrangère référençant la table "materiel") 
* ``date_debut`` (date de début de la disponibilité) 
* ``date_fin`` (date de fin de la disponibilité) 

CREATE TABLE Disponibilite (
    ID_Disponibilite SERIAL PRIMARY KEY,
    ID_Materiel INT REFERENCES Materiel(ID),
    Date_Debut DATE,
    Date_Fin DATE
);

2. Modifiez la table "reservation" en ajoutant une nouvelle colonne "id_disponibilite" (clé étrangère référençant la table "disponibilite"). 
ALTER TABLE Reservation ADD COLUMN ID_Disponibilite INT REFERENCES Disponibilite(ID_Disponibilite);

3. Modifiez les contraintes SQL existantes pour prendre en compte les contraintes de disponibilité lors de la création et de la mise à jour des réservations.
   SELECT * FROM Disponibilite 
WHERE ID_Materiel = 1 
  AND Date_Debut <= '2025-06-10' 
  AND Date_Fin >= '2025-06-15'; 

5. Implémentez une fonctionnalité permettant de vérifier la disponibilité d'un matériel pour une période donnée avant de permettre la réservation. Si le matériel n'est pas disponible, affichez un message d'erreur approprié. 
INSERT INTO Reservation (ID_Etudiant, ID_Materiel, Date_Emprunt, Date_Retour, ID_Disponibilite)
VALUES (1, 1, '2025-06-10', '2025-06-15', 1);

Vous pouvez afficher la disponibilité par exemple grâce à l'instruction ``CASE``.
