### Instructions

1. Mettez à jour le modèle de données existant en ajoutant une nouvelle table "disponibilite" avec les colonnes suivantes : 

* ``id_disponibilite`` (clé primaire)
* ``id_materiel`` (clé étrangère référençant la table "materiel") 
* ``date_debut`` (date de début de la disponibilité) 
* ``date_fin`` (date de fin de la disponibilité) 

2. Modifiez la table "reservation" en ajoutant une nouvelle colonne "id_disponibilite" (clé étrangère référençant la table "disponibilite"). 

3. Modifiez les contraintes SQL existantes pour prendre en compte les contraintes de disponibilité lors de la création et de la mise à jour des réservations. 

4. Implémentez une fonctionnalité permettant de vérifier la disponibilité d'un matériel pour une période donnée avant de permettre la réservation. Si le matériel n'est pas disponible, affichez un message d'erreur approprié. 

Vous pouvez afficher la disponibilité par exemple grâce à l'instruction ``CASE``.
