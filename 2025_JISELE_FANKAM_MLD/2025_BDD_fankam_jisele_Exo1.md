Quetion1: image:exo1_1


Cette base de données permet la location de matériel à Polytech. elle permet egalement de gérer les emprunts réalisés par les étudiants. Elle comprend les entités Étudiant, Matériel, date (renommer location plus tard). L'entité Étudiant contient les informations des utilisateurs du service, tandis que Matériel regroupe les équipements disponibles à la location. Location relie les étudiants aux matériels loués, en enregistrant les dates de prêt et de retour.
Ainsi, un étudiant peut faire plusieurs emprunts, chaque emprunt concerne un seul matériel, et a une seule date. Chaque emprunt est bien rattaché à un étudiant, un matériel et une date existants. de plus, les dates sont cohérentes, le matériel n’est pas réservé plusieurs fois simultanément.



Code de creatoion de la DB

### Ajout de données dans la table « Utilisateur » 
1.1
la table utilisateur contient une clé d'identification unique, une numero etudiant, le nom et prenom ainsi que le mail et la promo. sa creation nous est facilite par looping
1.2

CREATE TABLE Utilisateur (
    ID SERIAL PRIMARY KEY,
    Numero_Etudiant VARCHAR(20) UNIQUE NOT NULL,
    Nom VARCHAR(50),
    Prenom VARCHAR(50),
    Mail VARCHAR(100),
    Promo VARCHAR(20)
);

1.3
INSERT INTO Utilisateur (Numero_Etudiant, Nom, Prenom, Mail, Promo) VALUES
('ETU001', 'Martin', 'Alice', 'alice.martin@etu.univ-tours.fr', 'ING3'),
('ETU002', 'Durand', 'Louis', 'louis.durand@etu.univ-tours.fr', 'ING4'),
('ETU003', 'Petit', 'Clara', 'clara.petit@etu.univ-tours.fr', 'ING5'),
('ETU004', 'Moreau', 'Tom', 'tom.moreau@etu.univ-tours.fr', 'ING3'),
('ETU005', 'Lemoine', 'Emma', 'emma.lemoine@etu.univ-tours.fr', 'ING2'),
('ETU006', 'Leroy', 'Hugo', 'hugo.leroy@etu.univ-tours.fr', 'ING3'),
('ETU007', 'Roux', 'Lina', 'lina.roux@etu.univ-tours.fr', 'ING4'),
('ETU008', 'Fournier', 'Leo', 'leo.fournier@etu.univ-tours.fr', 'ING5'),
('ETU009', 'Garnier', 'Sophie', 'sophie.garnier@etu.univ-tours.fr', 'ING2'),
('ETU010', 'Chevalier', 'Lucas', 'lucas.chevalier@etu.univ-tours.fr', 'ING3');



### Ajout de données dans la table « Matériel »
1.1
Elle contient une cle primaire, un nom, et une description textuelle de l'etat de l'objet
1.2
-- Table Materiel
CREATE TABLE Materiel (
    ID SERIAL PRIMARY KEY,
    Nom VARCHAR(100),
    Description TEXT,
    Quantite_Disponible INT CHECK (Quantite_Disponible >= 0)
);
1.3
INSERT INTO Materiel (Nom, Description, Quantite_Disponible) VALUES
('Caméra HD', 'Caméra Sony 4K pour projets vidéo', 5),
('Microphone', 'Microphone cravate avec câble USB', 10),
('Trépied', 'Trépied ajustable 1m80', 7),
('Projecteur', 'Vidéoprojecteur HD Epson', 3),
('Tablette graphique', 'Wacom Intuos S pour dessin numérique', 4),
('Casque VR', 'Casque Oculus Quest 2', 2),
('Raspberry Pi', 'Modèle 4B 4Go RAM', 8),
('Arduino Uno', 'Kit de base avec capteurs', 6),
('PC portable', 'Dell XPS prêt pour programmation', 5),
('Enceinte Bluetooth', 'Enceinte JBL Flip 5', 9);

### Ajout de données dans la table « Réservation » 
1.1
la table reervation contient un ID etudiant, un id materiel, une date d'emprunt, une date de retour ainsi qu'un etat de retour
1.2
-- Table Reservation
CREATE TABLE Reservation (
    ID_Etudiant INT,
    ID_Materiel INT,
    Date_Emprunt DATE,
    Date_Retour DATE,
    Etat_Retour VARCHAR(100),
    PRIMARY KEY (ID_Etudiant, ID_Materiel, Date_Emprunt),
    FOREIGN KEY (ID_Etudiant) REFERENCES Utilisateur(ID),
    FOREIGN KEY (ID_Materiel) REFERENCES Materiel(ID)
);

1.3
INSERT INTO Reservation (ID_Etudiant, ID_Materiel, Date_Emprunt, Date_Retour, Etat_Retour) VALUES
(1, 1, '2025-05-10', '2025-05-12', 'Bon'),
(2, 2, '2025-05-11', '2025-05-13', 'Bon'),
(3, 3, '2025-05-09', '2025-05-11', 'Cassé'),
(4, 4, '2025-05-08', '2025-05-10', 'Bon'),
(5, 5, '2025-05-07', '2025-05-09', 'Manquant');



