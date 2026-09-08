# Projet moteur liquide "Marmotte"
# Description
Le projet de moteur liquide prévoit un static fire à Launch Canada 2027 (en même temps que le vol d'Elerrina 2). Ce projet nécessite l'intégration de trois composantes, soit le moteur lui-même, le "ground-support equipement", ainsi que la station de base. D'un point de vue électronique, ceci est un projet d'envergure qui regroupe les trois sous-projets :

**Système Moteur**
Le système moteur regroupe toutes les composantes embarquées dans la fusée qui contrôle les valves et l'allumage. Ce système doit être d'une taille limitée et être conçu pour résister aux conditions d'un vol de fusée. Un premier PCB a été développé à l'hiver 2026, une 2e version sera probablement de mise.

**Système de support au sol**
Le système de support au sol contrôle l'extérieur immédiat de la fusée. Cela comprends notamment les différentes valves, la pesée, etc. Il doit communiquer avec le système moteur (connexion filiaire possible) et avec la station de base (sans fil obligatoirement). C'est le système de support au sol qui gère la majorité de la logique du moteur.

**Station de base**
La station de base est éloignée du launchpad et permet à l'équipe de contrôler le système à distance. La station de base communique avec le système de support au sol seulement. Elle permet de lire les données du moteur, et de contrôler les états de la procédure.
# TODO
- Description
- CONOPS / Usecase diagram
- Charte
- Requirements
- Risk management
- Échéanciers / Milestones