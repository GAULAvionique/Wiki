# Catégories d'altitude et défis

## Vue d'ensemble

L'altitude est la métrique primaire dans les compétitions de fuséologie. Elle détermine la catégorie de vol, les défis techniques, et les exigences réglementaires. Plus on va haut, plus les problèmes s'accumulent : récupération, tracking, effets du Mach, réglementation, et conditions environnementales extrêmes.

> [!info]
> Dans les compétitions comme l'IREC (Intercollegiate Rocket Engineering Competition), les catégories d'altitude sont les critères de classification principaux. Le choix de la catégorie détermine le budget, la complexité, et l'équipement nécessaire.

Pour chaque catégorie, il faut considérer :

- **Propulsion** : type et nombre de moteurs nécessaires
- **Récupération** : complexité du système de déploiement
- **Avionique** : besoins en tracking et en senseurs
- **Réglementation** : permis, waivers, NOTAM
- **Déscente** : vitesse et durée de la phase de descente

---

## 1 000 ft AGL (300 m)

### Description

Niveau d'entrée pour la fuséologie amateur. Accessible avec des fusées de type model rocket et mid-power.

### Propulsion typique

Moteurs de la catégorie A à E (impulsion totale de 2,5 à 160 N·s).

### Défis principaux

- Altitude minimale atteinte avec des moteurs d'entrée de gamme
- Récupération simple : parachute unique ou streamer
- Peu de risques liés au vent (altitude faible = temps de vol court)

### Usage typique

- Premiers vols d'équipe
- Concours d'egg lofting (transport d'un oeuf)
- Validation de la stabilité de conception

> [!info]
> Cette catégorie est idéale pour apprendre les bases sans investir dans du matériel coûteux. Un bon moyen de vérifier qu'une fusée est stable avant de passer à plus haut.

---

## 3 000 ft AGL (914 m)

### Description

Catégorie standard pour les compétitions étudiantes de niveau intermédiaire.

### Propulsion typique

Moteurs de la catégorie E à G (impulsion totale de 80 à 640 N·s).

### Défis principaux

- Nécessite un système de tracking fiable pour retrouver la fusée
- Vérification de la stabilité avant vol obligatoire (parachute de sécurité, stabilité statique)
- La récupération commence à nécessiter un peu de planification

### Usage typique

- Compétitions étudiantes intermédiaires
- Apprentissage des systèmes de récupération
- Premiers pas vers le high-power

---

## 10 000 ft AGL (3 048 m)

### Description

Catégorie standard de l'IREC. C'est la catégorie la plus accessible en high-power.

### Propulsion typique

Moteurs de la catégorie H à J (impulsion totale de 160 à 1 280 N·s).

### Défis principaux

- **Dual-deployment recommandé** : déploiement d'un drogue à l'apogée et d'un parachute principal plus bas
- **GPS tracking essentiel** : la fusée peut dériver significativement avec le vent
- **Dérive au vent** : il faut calculer la zone d'atterrissage en fonction du profil de vent
- **Systèmes de récupération complexes** : shear pins, charges pyrotechniques séparées

> [!info]
> C'est la catégorie dans laquelle la plupart des équipes étudiantes débutent en high-power. Il faut prévoir un budget significativement plus élevé que pour les catégories 1 000 ft et 3 000 ft.

### Considérations spécifiques

- Le temps de vol total dépasse souvent 5 minutes
- La zone de récupération peut être à plus de 1 km du pas de tir
- Perdre la fusée est possible sans GPS fiable
- Ne jamais compétitionner en 10k COTS à l'IREC. Il y a beaucoup trop d'équipes inscrites, c'est un sale bordel

---

## 30 000 ft AGL (9 144 m)

### Description

Catégorie avancée de l'IREC. Représente un défi technique majeur.

### Propulsion typique

Moteurs de la catégorie K à M (impulsion totale de 1 280 à 10 240 N·s).

### Défis principaux

- **Régime transsonique/supersonique** : la fusée peut atteindre Mach 1,2 à Mach 2,0
- **Charges structurales** : forces aérodynamiques importantes en phase de boost
- **Taux de descente élevé** : même avec dual-deployment, la vitesse de descente peut être élevée
- **Capteurs barométriques limités** : l'air est trop raréfié au-dessus de ~40 000 ft pour des altimètres barométriques conventionnels
- **GPS obligatoire** : tracking par GPS nécessaire pour la récupération
- **Line cutters** : souvent utilisés pour séparer les sections de la fusée à des altitudes spécifiques

### Niveau GAUL : Altera

> [!info]
> La fusée **Altera** de GAUL a atteint **30 402 ft (9 268 m)** à l'IREC 2025, atteignant une vitesse de **Mach 1,8**. Cela place GAUL parmi les équipes les plus performantes au Canada.

### Considérations spécifiques

- Nécessite des tests sol robustes (ground testing des charges pyrotechniques)
- La phase de boost dure 3 à 8 secondes selon le moteur
- La phase de coast (montée par inertie) peut durer 15 à 30 secondes
- Le temps de vol total peut dépasser 10 minutes

---

## 45 000 ft AGL (13 716 m)

### Description

Catégorie la plus élevée de l'IREC, dans la catégorie multi-stage.

### Propulsion typique

Moteurs de la catégorie L à O, souvent en configuration multi-stage (2 à 3 étages).

### Défis principaux

- **Staging en altitude** : le second étage doit s'allumer après la séparation du premier, à des conditions environnementales extrêmes
- **Conditions stratosphériques** : pression quasi-nulle, températures de -50°C à -70°C
- **Taux de descente très élevé** : même avec un bon système de récupération, la descente depuis 45 000 ft est longue
- **Systèmes de récupération multiples** : dual-deployment obligatoire, souvent avec des line cutters et des charges pyrotechniques pour chaque étape

> [!info]
> Presque toutes les équipes qui visent 45 000 ft utilisent une configuration multi-stage. Atteindre cette altitude avec un seul étage est difficile et nécessite un moteur à très haute impulsion.

### Considérations spécifiques

- La conception du système de staging est l'un des défis les plus complexes
- Il faut gérer la séparation mécanique, l'allumage du second étage, et la récupération de chaque étape
- Les testing requirements sont considérablement plus élevés

---

## 100 000 ft+ (30 480 m+)

### Description

Barrière symbolique des 6 chiffres. Les "spaceshots" visent au dessus de 80km/262,467ft (ligne Karman, limite de l'espace) .

### Défis principaux

- **Aérodynamique en proche-vacuum** : les gouvernails et les ailerons deviennent inutiles au-dessus de ~80 000 ft
- **Récupération depuis des altitudes extrêmes** : la descente peut prendre 30+ minutes
- **Limites COCOM** : les GPS civils sont limités à 60 000 ft et 1 000 nœuds de vitesse (1 852 km/h), ce qui rend le tracking GPS impossible en vol supersonique à haute altitude
- **Réglementation** : nécessite des waivers spéciaux, coordination avec les autorités aéronautiques

### Objectif à long terme de GAUL

> [!info]
> **Elerrina 2027** est le projet à long terme de GAUL visant à atteindre ou dépasser 100k ft. Il est tenté en 2026 sans succès, à cause (hypothèse) de la mauvaise rampe de lancement.

### Considérations spécifiques

- Le système de tracking doit être redondant (GPS + telemetry radio + Spotrace satellite)
- La détection de l'apogée ne peut pas se faire de façon barométrique. IMU ou GPS obligatoire.
- La récupération doit être planifiée avec une grande zone d'atterrissage (potentiellement plusieurs km²)

---

## Défis par régime de vitesse

Le régime de vitesse de la fusée affecte directement la stabilité, les charges structurales, et la conception aerodynamique.

### Subsonic ( < Mach 0,8 )

Comportement aérodynamique prévisible. Les coefficients de portance et de traînée sont constants. Les calculs de stabilité sont fiables. C'est le régime le plus simple à gérer.

### Transsonique (Mach 0,8 — 1,2)

> [!info]
> Le régime transsonique est le plus dangereux pour la stabilité. C'est dans cette plage que de nombreux échecs de vol se produisent.

- **Transonic shimmy** : oscillations de la fusée dues aux changements rapides des forces aérodynamiques
- **Risque de flutter** : les gouvernails peuvent vibrer de manière incontrôlée
- **Centre de pression (CP)** : déplace rapidement vers l'arrière, ce qui peut rendre la fusée instable
- Les simulations deviennent moins fiables

### Supersonic ( > Mach 1,2 )

- **Ondes de choc** : des shocks waves se forment sur la fusée, affectant la distribution de pression
- **Effets thermiques** : le frottement génère une chaleur significative sur les surfaces avant
- **CP déplacé** : le centre de pression est plus en arrière qu'en subsonic, ce qui affecte la stabilité statique
- La conception aerodynamique doit être validée en soufflerie ou par CFD

---

## Défis de récupération par altitude

La récupération est l'un des aspects les plus critiques de la fuséologie. Le système de récupération doit être adapté à l'altitude et aux conditions de vol.

| Altitude           | Taux de descente typique | Stratégie de récupération                                   | GPS nécessaire |
| ------------------ | ------------------------ | ----------------------------------------------------------- | -------------- |
| 1 000 — 3 000 ft   | 5 — 15 m/s               | Parachute unique ou streamer                                | Non            |
| 3 000 — 10 000 ft  | 10 — 25 m/s              | Dual-deployment recommandé                                  | Recommandé     |
| 10 000 — 30 000 ft | 15 — 40 m/s              | Dual-deployment obligatoire                                 | Obligatoire    |
| 30 000 — 45 000 ft | 20 — 50 m/s              | Dual-deployment obligatoire                                 | Obligatoire    |
| 45 000 ft+         | 25 — 60 m/s              | Dual-deployment obligatoire, zone d'atterrissage très large | Obligatoire    |

> [!info]
> Le taux de descente est calculé en fonction de la masse de la fusée, du diamètre du parachute, et de la densité de l'air. Un parachute de 120 pouces carrés peut ralentir une fusée de 5 kg à ~15 m/s.

### Considérations importantes

- **Shear pins** : des petits boulons qui retiennent les sections ensemble jusqu'au déploiement pyrotechnique
- **Drogue vs Main** : le drogue est un petit parachute déployé à l'apogée pour limiter la dérive ; le main est le parachute principal déployé à basse altitude
- **Line cutters** : des dispositifs pyrotechniques qui coupent des lignes pour déployer le parachute à une altitude prédéfinie
- **Twin-deploy** : système où le drogue et le main sont dans des sections séparées, déployés à des altitudes différentes

---

## Réglementation par altitude

### Transport Canada

- **NOTAM** (Notice to Airmen) requis pour les vols au-dessus de certaines altitudes
- Classification selon le type de vol (modèle, expérimental, professionnel)
- Coordination avec les autorités aéronautiques pour les vols au-delà de 10 000 ft AGL

### Système de classification FAA (référence)

| Classe | Altitude | Exigences |
|---|---|---|
| Class 1 | < 400 ft AGL | Pas de waiver requis pour les modèles |
| Class 2 | 400 — 15 000 ft AGL | Notification aux autorités locales |
| Class 3 | > 15 000 ft AGL | Waiver requis, coordination avec les autorités |

### Waivers

- **Low-power waiver** : pour les vols < 10 000 ft AGL, généralement simple à obtenir
- **High-power waiver** : pour les vols > 10 000 ft AGL, nécessite un dossier technique détaillé
- **Ultra-high waiver** : pour les vols > 30 000 ft AGL, coordination avec NAV Canada

> [!info]
> Le processus de waiver peut prendre plusieurs semaines. Il faut planifier la soumission bien à l'avance du lancement prévu. GAUL gère ce processus pour chaque vol compétitif.

### Ressources

- [Transport Canada — Fusées modèles](https://tc.canada.ca/fr/aviation-civile)
- [Rocketry.org — Règlements canadiens](https://rocketry.org)
- [NAR — Règlements américains](https://www.nar.org)
