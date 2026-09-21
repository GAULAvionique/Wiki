# Avionique générale — Altimètres et GPS

## Introduction

L'**avionique** (avionics) désigne l'ensemble des systèmes électroniques embarqués dans une fusée. Dans la fuséologie amateur, l'avionique remplit trois fonctions critiques :

1. **Déploiement de récupération** : déclencher les charges pyrotechniques aux bonnes altitudes
2. **Tracking** : localiser la fusée en vol et après atterrissage
3. **Données de vol** : enregistrer les paramètres pour analyse post-vol

### COTS vs SRAD

- **COTS** (Commercial Off-The-Shelf) : produits commerciaux prêts à l'emploi (Featherweight, Perfectflite, etc.)
- **SRAD** (Student-Researched and Developed) : systèmes conçus et fabriqués par les étudiants (à GAUL, c'est un objectif à long terme)

> [!info]
> Les systèmes COTS sont recommandés pour les débutants car ils sont fiables, testés, et supportés. Les systèmes SRAD offrent plus de flexibilité mais nécessitent une expertise significative en électronique et en programmation.

---

## Altimètres barométriques

### Principe de fonctionnement

Les altimètres barométriques mesurent la **pression atmosphérique ambiante** et la convertissent en altitude using la formule barométrique simplifiée :

```
h = (1 - (P / P0) ^ 0.190284) × 44 330
```

Où :
- **h** = altitude en mètres
- **P** = pression mesurée (Pa)
- **P0** = pression de référence au niveau de la mer (101 325 Pa)

### Limitations

- **Météo** : les changements de pression atmosphérique affectent les lectures
- **Température** : les variations de température introduisent des erreurs
- **Haute altitude** : au-delà de ~45 000 ft, la pression est trop faible pour des mesures fiables avec des capteurs conventionnels
- **Étanchéité** : les fuites d'air dans la section avionique faussent les lectures

### Paramètres clés

| Paramètre | Description | Importance |
|---|---|---|
| Taux d'échantillonnage | Nombre de mesures par seconde | Plus le taux est élevé, plus la précision temporelle est bonne |
| Résolution | Variation minimale détectable | 1 ft ou moins est suffisant pour la plupart des applications |
| Précision | Écart entre la mesure et la vraie altitude | ±5 ft est typique pour les altimètres COTS |
| Plage de mesure | Altitude minimale et maximale | Vérifier que la plage couvre l'altitude visée |

> [!info]
> Un taux d'échantillonnage de 20 Hz (20 mesures par seconde) est généralement suffisant pour les fusées amateur. Pour les vols supersoniques, 100 Hz ou plus est recommandé.

---

## Altimètres inertiels (IMU)

### Accéléromètres

Les accéléromètres mesurent les **forces d'accélération** le long de trois axes (X, Y, Z). En vol, ils mesurent :

- L'accélération du moteur (phase de boost)
- La gravité (phase de coast et de descente)
- Les accélérations laterales (vent, turbulence)

### Gyroscopes

Les gyroscopes mesurent les **vitesses de rotation** autour de trois axes. Ils permettent de détecter :

- Les rotations de la fusée (roll, pitch, yaw)
- Les oscillations instables
- L'orientation de la fusée dans l'espace

### Intégration pour obtenir vitesse et position

En intégrant les données de l'accéléromètre, on obtient la **vitesse**. En intégrant la vitesse, on obtient la **position** (altitude).

> [!info]
> Le problème majeur de l'intégration est la **dérive** (drift). Les petites erreurs de mesure s'accumulent avec le temps, rendant les données de position peu fiables après seulement quelques secondes. C'est pourquoi un IMU seul ne suffit pas pour mesurer l'altitude.

### Pourquoi un IMU seul est insuffisant

- La dérive de position après 10 secondes peut atteindre plusieurs centaines de mètres
- Les accéléromètres ont un bruit de fond qui s'intègre en erreur croissante
- Sans correction externe (baromètre, GPS), les données deviennent rapidement inutilisables

---

## Fusion de données — Filtre de Kalman

### Pourquoi la fusion de données?

Chaque capteur a ses forces et ses faiblesses :

| Capteur | Forces | Faiblesses |
|---|---|---|
| Baromètre | Précis à basse altitude, pas de dérive | Sensible à la météo, limité en haute altitude |
| IMU | Haute fréquence, pas sensible à la météo | Dérive importante, erreurs cumulatives |
| GPS | Précis en position, pas de dérive | Faible fréquence, nécessite vue du ciel |

La **fusion de données** combine les forces de chaque capteur pour obtenir une estimation meilleure que chaque capteur individuellement.

### Concept du filtre de Kalman

Le filtre de Kalman fonctionne en deux étapes qui se répètent en boucle :

1. **Prédiction** : utiliser le modèle physique et les données IMU pour prédire l'état suivant
2. **Mise à jour** : corriger la prédiction avec les mesures du baromètre et/ou du GPS

> [!info]
> Le filtre de Kalman est optimal au sens du moindre carré pour les systèmes linéaires avec du bruit gaussien. Dans la pratique, les systèmes réels ne sont pas parfaitement linéaires, mais le filtre reste très efficace.

### Référence

Pour une explication détaillée de l'implémentation du filtre de Kalman dans le contexte de la fuséologie, consulter le document interne de GAUL sur les filtres de Kalman.

---

## Altimètres COTS populaires

### Tableau comparatif

| Produit | Fabricant | Canaux pyro | Capteurs | Bluetooth | Gamme de prix |
|---|---|---|---|---|---|
| Blue Raven | Featherweight | 4 | Baro + IMU | Oui | ~175 $ USD |
| Blue Jay Plus | Featherweight | 2 | Baro + IMU | Oui | ~105 $ USD |
| Stratologger CF | Perfectflite | 2 | Baro uniquement | Non | ~50 $ USD |
| RRC3+ | Missileworks | 3 | Baro uniquement | Oui | ~80 $ USD |
| EasyMini | Altus Metrum | 2 | Baro uniquement | Non (serial) | ~60 $ USD |
| EggTimer | EggTimer | Variable | Baro uniquement | Non | ~30-80 $ USD |

### Détails par produit

#### Featherweight Blue Raven

- 4 canaux pyrotechniques indépendants
- IMU 6 axes (accéléromètre + gyroscope 3 axes)
- Bluetooth pour configuration et lecture
- Enregistrement de données haute fréquence
- Compatible avec l'application Featherweight

#### Featherweight Blue Jay Plus

- Version compacte du Blue Raven
- 2 canaux pyrotechniques
- IMU intégré
- Bluetooth
- Idéal pour les fusées de petite taille

#### Perfectflite Stratologger CF

> [!info]
> Le Stratologger CF est l'un des altimètres les plus fiables du marché. Il est utilisé par des centaines d'équipes à travers le monde. Sa simplicité est sa force.

- 2 canaux de déploiement (drogue + main)
- Baromètre seul (pas d'IMU)
- Ultra-fiable, sans Bluetooth ni fonctionnalités avancées
- Prix très abordable

#### Missileworks RRC3+

- 3 canaux pyrotechniques
- Bluetooth pour configuration
- Interface utilisateur conviviale
- Bon rapport qualité-prix

#### Altus Metrum EasyMini

- 2 canaux pyrotechniques
- Communication par câble (pas de Bluetooth)
- Design compact et léger
- Alternative abordable

#### EggTimer Altimeters

> [!info]
> Les EggTimer sont des altimètres DIY (Do It Yourself) à prix très abordable. Ils sont idéaux pour les équipes avec un budget limité ou qui souhaitent apprendre l'électronique embarquée.

- Kit à souder soi-même
- Diverse configurations disponibles
- Prix de départ très bas (~30 $ USD)

---

## GPS — Principe

### Comment fonctionne le GPS?

Le **GPS** (Global Positioning System) utilise un réseau de **24+ satellites** en orbite terrestre pour déterminer la position d'un récepteur sur Terre.

### Trilatération

La position est calculée par **trilatération** :

1. Le récepteur mesure le temps de propagation du signal de chaque satellite
2. En connaissant la vitesse de la lumière, on calcule la distance à chaque satellite
3. Avec les distances à 3+ satellites, on détermine la position 3D

### Fréquence et signal

- **Fréquence L1** : 1 575,42 MHz (fréquence principale pour les récepteurs civils)
- **Code C/A** (Coarse/Acquisition) : code de signal civilian

### Précision

- **Précision civilian typique** : ~3 mètres en conditions favorables
- **Avec DGPS** (Differential GPS) : < 1 mètre
- **Avec RTK** (Real-Time Kinematic) : < 2 cm (utilisé en géomatique, pas en fuséologie)

### Limites COCOM

> [!info]
> Les récepteurs GPS civils sont limités par les **régulations COCOM** (Coordinating Committee for Multilateral Export Controls) :
> - **Altitude maximale** : 60 000 ft (18 288 m)
> - **Vitesse maximale** : 1 000 nœuds (1 852 km/h)
>
> Au-delà de ces limites, le GPS peut cesser de fonctionner. C'est un problème majeur pour les fusées atteignant des altitudes > 60 000 ft ou des vitesses supersoniques.

---

## Télémesure radio

### LoRa (915 MHz ISM band)

- **Portée** : jusqu'à 50+ km en vol (ligne de vue)
- **Puissance** : faible (158 mW pour le Swift)
- **Modulation** : LoRa (Long Range), modulation à spectre étalé
- **Usage** : standard pour les trackeurs Featherweight
- **Bande ISM** : 915 MHz au Canada/États-Unis (license-free)

### 70cm HAM (430 MHz)

- **Portée** : variable selon la puissance et l'antenne
- **Licence** : nécessite une licence d'amateur ( Advanced en Canada)
- **Usage** : telemetry radio pour les données de vol en temps réel
- **Avantage** : plus de puissance disponible, meilleure portée en conditions défavorables


### Data logging vs telemetry

| Type | Description | Usage |
|---|---|---|
| Data logging | Enregistrement des données sur carte mémoire | Analyse post-vol |
| Telemetry | Transmission des données en temps réel | Tracking, monitoring en vol |

> [!info]
> Idéalement, une fusée utilise les deux : un data logger pour les données détaillées et un système de telemetry pour le tracking en temps réel.

---

## Traceurs GPS COTS

### Tableau comparatif

| Produit | Portée | Fréquence | Fonctionnalités | Prix |
|---|---|---|---|---|
| Featherweight GPS Tracker | 50+ km | LoRa 915 MHz | u-blox M10, haute sensibilité | ~160 $ USD |
| Featherweight Swift | 50+ km | LoRa 915 MHz | 158 mW TX, amélioré | ~170 $ USD |
| EggFinder | Variable | 70cm HAM | DIY, abordable | ~50-100 $ USD |
| Spotrace | Global | Satellite (Globalstar) | Couverture mondiale, abonnement | ~80 $ USD + frais |

### Featherweight GPS Tracker

- Récepteur **u-blox M10** haute sensibilité
- Transmission **LoRa** à 915 MHz
- Portée en vol : 50+ km en ligne de vue
- Compatible avec l'application Featherweight
- Intégration facile avec les altimètres Featherweight

### Featherweight Swift

> [!info]
> Le Swift est la dernière génération de traceurs GPS Featherweight. Il offre une puissance de transmission de **158 mW** pour une portée améliorée.

- Même fréquence que le GPS Tracker (LoRa 915 MHz)
- Puissance de transmission accrue
- Design optimisé pour la fuséologie

### EggFinder

- Système **DIY** (Do It Yourself)
- Récepteur GPS + émetteur radio
- Nécessite une licence HAM pour la fréquence 70cm
- Alternative très abordable

### Spotrace

> [!info]
> Spotrace utilise le réseau **satellite Globalstar** pour une couverture mondiale. C'est une excellente option de backup pour les vols à haute altitude où le GPS LoRa peut être limité par les régulations COCOM.

- Couverture mondiale via satellites
- Nécessite un abonnement mensuel
- Idéal comme système de backup

---

## Antennes

### Types d'antennes

| Type | Description | Usage typique |
|---|---|---|
| Whip | Tige droite, omnidirectionnelle | Traceurs portables, antennes de base |
| Monopole | Tige avec ground plane | Montage sur fusée |
| Dipole | Deux éléments symétriques | Receptors, stations au sol |
| Yagi | Directionnelle, gain élevé | Tracking directionnel au sol |
| Patch | Directionnelle, compacte | Réception satellite |
| Helical | Circulairement polarisée | Communications satellite |

### SMA vs RP-SMA

> [!info]
> Les connecteurs **SMA** et **RP-SMA** se ressemblent visuellement mais sont **incompatibles**. C'est un piège très courant pour les débutants.
> - **SMA** : broche mâle au centre du connecteur
> - **RP-SMA** (Reverse Polarity) : trou femelle au centre du connecteur
>
> Vérifiez toujours la polarité avant d'acheter des antennes ou des câbles.

### Line-of-sight (ligne de vue)

- Les signaux radio à haute fréquence (915 MHz, 430 MHz) nécessitent une **ligne de vue** entre l'émetteur et le récepteur
- Les obstacles (montagnes, bâtiments, arbres) bloquent ou atténuent le signal
- Plus la fréquence est élevée, plus la ligne de vue est critique

### Fibre de carbone et RF

> [!info]
> La **fibre de carbone** bloque les signaux RF. Si l'antenne est placée à l'intérieur d'un tubeau en fibre de carbone, le signal sera significativement atténué. Pour les fusées en fibre de carbone, l'antenne doit être placée à l'extérieur ou dans une section non-carbone.

### Placement des antennes dans la structure

- **Antennes de traceur** : orientées vers le haut (vers le ciel) pour une meilleure réception satellite
- **Antennes au sol** : orientées vers la trajectoire de vol prévue
- **Éviter** : placement près de composants métalliques, batteries, ou moteurs
- **Distance minimale** : au moins 1/4 de longueur d'onde (~7 cm pour 915 MHz) entre l'antenne et toute surface conductrice

### Considérations pour GAUL

Pour les fusées de GAUL, les recommandations sont :

- Utiliser de moins en moins la bande 915 MHz (très occupée lors des compétitions)
- Configurer un Spotrace comme backup pour tous les vols 
- Vérifier la compatibilité SMA/RP-SMA avant chaque assemblage
- Tester la portée radio au sol avant le lancement
