---
aliases:
  - erreurs
  - leçons
  - antipatterns
tags:
  - erreur
  - apprentissage
  - sécurité
created: 2026-09-14
---

# Erreurs courantes des débutants

> [!info] Philosophie
> Chaque erreur est une leçon. Celle-ci en sauve d'autres. Ce document compile les erreurs les plus fréquentes observées dans la communauté et au sein du GAUL. Apprenez des erreurs des autres pour éviter de les répéter.

---

## Stabilisation et conception

### 1. Sous-stabilisation

**Symptôme** : La fusée devient instable en vol, effectue des vrilles, s'écarte de la trajectoire prévue.

**Cause** : Le centre de gravité (CG) est trop près du centre de pression (CP), ou le CG est derrière le CP.

**Solutions** :
- Ajouter du lest dans le nez
- Augmenter la surface des ailerons
- Vérifier le positionnement des batteries et composants lourds

> [!warning] Règle d'or
> Le CG doit être situé à **au moins 1 calibre** (1× le diamètre du tube) devant le CP pour une stabilité adéquate.

### 2. Sur-stabilisation

**Symptôme** : La fusée pénètre fortement le vent, atterrit loin en aval du terrain de lancement (downrange).

**Cause** : Le CG est trop loin vers l'avant, la fusée se comporte comme une girouette.

**Solutions** :
- Réduire le lest dans le nez
- Réduire la surface des ailerons
- Réévaluer le design dans OpenRocket

### 3. Ailerons mal alignés

**Symptôme** : La fusée effectue des spirales en montée.

**Cause** : Même un léger désalignement des ailerons crée un moment de rotation.

**Solutions** :
- Utiliser un jig d'alignement pendant le collage
- Vérifier avec une règle et un fil à plomb
- Laisser l'époxy prendre pendant que la fusée est sous tension

### 4. Mauvais adhésif

**Symptôme** : Ailerons détachés en vol, structure dégradée.

**Cause** : Utilisation de colle chaude (*hot glue*) ou de colle qui ne supporte pas les vibrations.

**Solutions** :
- Utiliser de l'**époxy** pour toutes les connexions structurelles
- La colle chaude n'est acceptable que pour des fixations temporaires au sol
- Pour les composites, utiliser la résine West System ou équivalent

---

## Moteur

### 5. Sur-puissance (TWR trop élevé)

**Symptôme** : La fusée accélère trop vite, dépasse les capacités structurales, le rail n'est pas assez long.

**Cause** : Moteur trop puissant pour la masse et la structure de la fusée.

**Solutions** :
- Calculer le **rapport thrust-weight (TWR)** avant chaque vol
- Vérifier que la vitesse de sortie du rail est supérieure à 15 m/s
- Respecter la règle du **TWR minimum de 5:1**

### 6. Sous-puissance

**Symptôme** : La fusée pénètre le vent (weathercocks), atterrit près du terrain, n'atteint pas l'altitude visée.

**Cause** : Moteur trop faible pour la masse de la fusée.

**Solutions** :
- Utiliser un moteur plus puissant
- Alléger la fusée
- Re-simuler dans OpenRocket

### 7. Mauvais choix de délai

**Symptôme** :
- Délai trop court → déploiement pendant l'ascension (parachute déchiré)
- Délai trop long → déploiement après la retombée (parachute déployé à basse vitesse ou impact)

**Cause** : Calcul incorrect du délai de combustion.

**Solutions** :
- Utiliser le simulateur pour calculer le temps entre burnout et apogée
- Choisir le délai le plus proche du calcul (délais standards : 3, 5, 7, 10 secondes)
- En cas de doute, choisir un délai légèrement plus long (degré de sécurité)

### 8. Problèmes d'allumeur

**Symptôme** : Le moteur ne démarre pas (ignition failure).

**Cause** : Allumeur mal inséré, mal sécurisé, ou inadapté au type de propergol.

**Solutions** :
- Insérer l'allumeur jusqu'au fond du grain
- Sécuriser avec du ruban adhésif haute température
- Vérifier la compatibilité allumeur/propergol

### 9. O-ring pincé

**Symptôme** : CATO au lancement (rupture catastrophique du moteur rechargeable).

**Cause** : L'anneau en caoutchouc (O-ring) est pincé lors du réassemblage.

**Solutions** :
- Vérifier l'absence de debris sur l'O-ring
- Appliquer une fine couche de graisse silicone
- Suivre le manuel d'assemblage du fabricant à la lettre

---

## Récupération

### 10. Mauvais dosage de poudre noire

**Symptôme** :
- Trop de poudre → dommages structuraux, parachute déchiré
- Pas assez → pas de déploiement, lawn dart

**Cause** : Dosage non testé, ou estimation théorique erronée.

**Solutions** :
- **TOUJOURS effectuer un test au sol** (*ground test*) avant le vol
- La poudre noire est dosée en grammes selon le diamètre du tube
- Règle empirique : 1 gramme par pouce de diamètre pour la drogue, 2× pour le main
- Varier le dosage entre les tests, pas pendant le vol

### 11. Parachute mal plié

**Symptôme** : Le parachute ne s'ouvre pas correctement, ou s'ouvre violemment.

**Cause** : Pliage trop serré (ne s'ouvre pas) ou trop lâche (ouverture violente).

**Solutions** :
- Pratiquer le pliage au sol
- Utiliser un **sac de déploiement** (*deployment bag*)
- Plier en accord avec les instructions du fabricant
- Tester le déploiement au sol avec des poids simulant le vent

### 12. Câble de choc trop court

**Symptôme** : Le nez percute le tube principal lors du déploiement (*zipper*).

**Cause** : Le câble de choc est trop court par rapport à la longueur de la fusée.

**Solutions** :
- Utiliser un câble d'au moins **1,5 à 2× la longueur du tube principal**
- Pour le dual-deploy, prévoir un câble adéquat pour chaque section
- Tester la longueur au sol en simulant le déploiement

### 13. Pas de protection thermique

**Symptôme** : Les gaz d'éjection brûlent le parachute.

**Cause** : Absence de protection entre les charges d'éjection et les parachutes.

**Solutions** :
- Utiliser de l'**étoupe** (*dog barf*), un piston, ou du Nomex
- Vérifier que la protection couvre bien la zone exposée
- Pour le dual-deploy, chaque parachute doit avoir sa propre protection

### 14. Shear pins trop forts

**Symptôme** : Les charges d'éjection ne parviennent pas à casser les goupilles, pas de déploiement.

**Cause** : Utilisation de goupilles trop résistantes (trop gros diamètre, mauvais matériau).

**Solutions** :
- Utiliser des goupilles en **nylon calibré adéquat** (souvent #2 ou #4)
- Tester la force de cisaillement au sol
- En cas de doute, les goupilles les plus faibles sont les plus sûres

---

## Électronique

### 15. Mauvaises connectiques

**Symptôme** : Un connecteur se détache pendant le vol, système en panne.

**Cause** : Connecteurs non verrouillables, absence de rétention.

**Solutions** :
- Utiliser des connecteurs **verrouillables** (JST-SH, Molex)
- Ajouter de la **rétention mécanique** (ruban, collier de serrage)
- Tester les connexions avec des vibrations simulées

### 16. Problèmes de batterie

**Symptôme** : Alimentation instable, resets du MCU, déploiement échoué.

**Cause** : Batterie faible, mauvais type, non chargée, ou déconnectée.

**Solutions** :
- Vérifier la tension de la batterie **avant chaque vol**
- Utiliser des batteries **fraîchement chargées**
- Ne jamais utiliser de batteries stockées depuis longtemps
- Prévoir des batteries de rechange sur le terrain

### 17. Pas de tests au sol

**Symptôme** : Découverte de problèmes en vol, impossibilité de les corriger.

**Cause** : Confiance excessive, manque de temps, oubli.

**Solutions** :
- **Ne jamais voler sans avoir effectué un test au sol complet**
- Tester toutes les charges d'éjection avec les mêmes masses
- Tester la télémétrie en conditions réelles
- Test de continuité des canaux pyro avant l'armement

### 18. Altimètre mal configuré

**Symptôme** : Déploiement à la mauvaise altitude, déploiement intempestif, non-déploiement.

**Cause** : Paramètres d'altitude d'ouverture du main mal configurés.

**Solutions** :
- Vérifier et re-vérifier les paramètres avant chaque vol
- Faire un *continuity check* (test de continuité) au sol
- S'assurer que l'altimètre est correctement calibré
- Documenter les paramètres de chaque vol

### 19. Câblage qui se déconnecte

**Symptôme** : Perte de signal, alimentation coupée, données corrompues.

**Cause** : Vibrations + forces G = fils lâches, connecteurs desserrés.

**Solutions** :
- Utiliser des colliers de serrage (*zip ties*) pour fixer les fils
- Appliquer de la *strain relief* aux points de connexion
- Utiliser des connecteurs verrouillables
- Tester les connexions sous vibration

---

## Opérations

### 20. Launch Fever

**Symptôme** : Lancement dans des conditions marginales par impatience.

**Cause** : Enthousiasme, pression temporelle, FOMO.

**Solutions** :
- Si le vent est supérieur à **30 km/h** → ATTENDRE
- Si le plafond nuageux est bas → ATTENDRE
- Si les conditions ne sont pas idéales → ATTENDRE
- **Un vol annulé est toujours préférable à un vol raté**

### 21. Pas de simulation

**Symptôme** : Comportement inattendu en vol, altitude non atteinte, trajectoire erratique.

**Cause** : Vol sans simulation préalable, design non validé.

**Solutions** :
- **Toujours simuler dans OpenRocket avant de voler**
- Exporter et archiver les rapports de simulation
- Comparer les données de vol réelles aux simulations

### 22. Ignorer le TWR minimum de 5:1

**Symptôme** : Weathercocking sévère, instabilité, performance dégradée.

**Cause** : Moteur trop faible pour la masse.

**Solutions** :
- Vérifier le TWR minimum de **5:1** avant chaque configuration
- Utiliser des moteurs plus puissants si le TWR est insuffisant
- Alléger la fusée si nécessaire

### 23. Précipitation

**Symptôme** : Oubli de détails de sécurité, erreurs d'assemblage, perte de pièces.

**Cause** : Rush, manque de temps, pression.

**Solutions** :
- Utiliser une **checklist de vol**
- Prévoir plus de temps que nécessaire
- Déléguer les tâches pour éviter la surcharge
- Relire le travail de chaque membre

### 24. Trop de complexité

**Symptôme** : Le système est trop complexe pour la première expérience, plus de temps passé à déboguer qu'à voler.

**Cause** : Ambition excessive pour un premier projet.

**Solutions** :
- **Commencer simple** — un altimètre, un déploiement, un système basique
- Ajouter de la complexité progressivement à chaque mission
- Le dual-deploy n'est pas nécessaire pour les premiers vols HPR

### 25. Confiance sans expérience

**Symptôme** : Erreurs de jugement, sous-estimation des risques.

**Cause** : Manque d'expérience combiné à une confiance excessive.

**Solutions** :
- Respecter les lois de la physique et les mathématiques, pas les intuitions
- Écouter les membres expérimentés
- Assister à des vols d'autres équipes avant de voler soi-même
- Lire ce guide et les ressources recommandées

---

## Leçons du GAUL

### IREC 2025 — Altera

> [!warning] Leçon : Test de staging
> Un verrouillage de tilt (*tilt lockout*) sur le deuxième étage a empêché le staging correct.
>
> **Leçon tirée** : Tester la logique de staging de manière exhaustive, y compris les cas limites. Implémenter des tests automatisés pour valider chaque condition de staging.

### LC 2026 — Connectique RF

> [!warning] Leçon : Vérification des connecteurs
> Une incompatibilité entre connecteurs SMA et RP-SMA a empêché la communication télémétrie.
>
> **Leçon tirée** : Vérifier **tous** les connecteurs RF avant le vol. Disposer d'adaptateurs de rechange sur le terrain. Documenter exactement quel type de connecteur est utilisé sur chaque module.

### LC 2026 — Surchauffe RunCam

> [!warning] Leçon : Gestion thermique
> La caméra RunCam a surchauffé dans la baie avionique, provoquant une perte de signal vidéo.
>
> **Leçon tirée** : Séparer l'alimentation de la caméra, l'activer tardivement (seulement en phase de récupération), et prévoir une ventilation si possible.

### LC 2026 — Checksum MavLink

> [!warning] Leçon : Validation du protocole
> La corruption du checksum MavLink a provoqué des données de télémétrie inutilisables.
>
> **Leçon tirée** : Valider intégralement le protocole de télémétrie en conditions réelles. Implémenter des tests de corruption de données. Utiliser des mécanismes de redondance dans la vérification des trames.

### LC 2026 — PCB d'armement

> [!warning] Leçon : Redondance
> Un seul PCB d'armement représentait un **point de défaillance unique** (*single point of failure*).
>
> **Leçon tirée** : Utiliser des PCB d'armement redondants. Chaque système critique doit avoir un backup. La redondance n'est pas un luxe, c'est une nécessité pour les missions critiques.

---

## Checklist de prévention

> [!info] Avant chaque vol
> - [ ] Simulation OpenRocket terminée et valide
> - [ ] TWR entre 5:1 et 15:1
> - [ ] CG/CP stables et valides
> - [ ] Test au sol des charges d'éjection effectué
> - [ ] Batteries chargées et vérifiées
> - [ ] Connectiques verrouillées
> - [ ] Ailerons alignés et collés à l'époxy
> - [ ] Paramètres d'altimètre vérifiés
> - [ ] Câble de choc adéquat
> - [ ] Protection thermique installée
> - [ ] Checklist de vol complétée