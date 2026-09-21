---
aliases: []
tags:
  - electronique
  - SRAD
  - avionique
created: 2026-09-14
---

# Électronique SRAD (Student Researched And Designed)

## Introduction

L'électronique SRAD désigne les systèmes électroniques **conçus et développés par les étudiants** eux-mêmes, par opposition aux systèmes COTS (*Commercial Off-The-Shelf*) achetés prêts à l'emploi. Au sein du GAUL, le développement SRAD est au coeur de notre mission éducative.

### Pourquoi construire du SRAD?

| Avantage               | Description                                               |
| ---------------------- | --------------------------------------------------------- |
| Valeur éducative       | Comprendre chaque sous-système en profondeur              |
| Personnalisation       | Adapter l'électronique exactement au besoin de la mission |
| Avantage compétitif    | Fonctionnalités sur mesure non disponibles en COTS        |
| Maîtrise technologique | Capacité de dépannage et de réparation en terrain         |
| Pour le flex           | C'est cool                                                |

### COTS vs SRAD

| Critère | COTS | SRAD |
|---|---|---|
| Temps de développement | Immédiat | Long (semaines/mois) |
| Fiabilité | Validée par le fabricant | À valider soi-même |
| Coût unitaire | Souvent élevé | Composants bon marché |
| Flexibilité | Limitée | Totale |
| Support technique | Garantie | Interne à l'équipe |

> [!info] Règle GAUL
> Pour les vols critiques ou les premiers vols d'un véhicule, privilégier les systèmes COTS éprouvés. Le SRAD est idéal pour les sous-systèmes où un besoin spécifique existe.

### Systèmes SRAD du GAUL

- **ODBlix** : ordinateur de vol principal, conçu et assemblé par l'équipe
- **IdéFIX** : balise de localisation 433 MHz

---

## Microcontrôleurs populaires

| MCU     | Fabricant          | Périphériques                 | Usage typique                   |
| ------- | ------------------ | ----------------------------- | ------------------------------- |
| STM32   | STMicroelectronics | CAN, SPI, I2C, UART, ADC, FPU | ODBlix (GAUL), flight computers |
| ESP32   | Espressif          | WiFi, BLE, SPI, I2C, ADC      | Télémétrie sans fil, trackers   |
| ATmega  | Microchip          | SPI, I2C, UART, ADC           | Débutants, Rocketry Club        |
| Teensy  | NXP                | USB, SPI, I2C, CAN, ADC       | Calculs intensifs, community    |
| RP2040  | Raspberry Pi       | SPI, I2C, PIO, ADC            | Projets flexibles, bas coût     |
| STM32L4 | STMicroelectronics | Low-power, SPI, I2C, ADC      | Applications autonomie longue   |

### STM32F4 (GAUL ODBlix)

Le coeur de l'ODBlix repose sur un **STM32F405**. Points forts:

- Processeur ARM Cortex-M4 avec **FPU** (Floating Point Unit)
- Bibliothèque **HAL** (*Hardware Abstraction Layer*) de STMicroelectronics
- Fréquence de 168 MHz — suffisant pour du filtrage de Kalman en temps réel
- Nombreux timers pour le contrôle de l'armement pyrotechnique
- Consommation maîtrisable en mode veille

### ESP32

Intéressant pour la **télémétrie** grâce au WiFi et BLE intégrés. Dual-core. Très bon marché. Cependant, la consommation WiFi est élevée — à considérer pour l'autonomie batterie.

### Arduino (ATmega328P)

Idéal pour **apprendre** mais trop limité pour du HPR sérieux: seulement 32 KB de Flash, 2 KB de RAM, pas de FPU, fréquence faible. Utile pour des bancs d'essai ou des projets pédagogiques.

### Teensy (NXP)

Puissant (600 MHz), excellente communauté. Le **Teensy 4.1** est un candidat sérieux pour les ordinateurs de vol SRAD. La bibliothèque Arduino est supportée.

### RP2040

Nouveau, bon marché, très flexible grâce au **PIO** (*Programmable I/O*). Idéal pour des projets où la souplesse de pilotage de périphériques est importante.

---

## Capteurs (Sensors)

### Capteurs de pression barométrique

> [!info] Usage principal
> Le baromètre est le capteur le plus critique pour la récupération. Il fournit l'altitude par rapport au sol et déclenche le déploiement des parachutes.

| Capteur | Plage | Résolution | Précision | Interface |
|---|---|---|---|---|
| BMP388 | 300-1250 hPa | 0.5 Pa | ±0.5 hPa | SPI / I2C |
| MS5607 | 10-1200 hPa | 0.012 mbar | ±1.5 hPa | I2C |
| MS5611 | 10-1200 hPa | 0.012 mbar | ±1.5 hPa | SPI / I2C |
| BMP280 | 300-1100 hPa | 0.18 Pa | ±1 hPa | SPI / I2C |
| BMP581 | 300-1250 hPa | 0.03 Pa | ±0.5 hPa | SPI / I2C |
### Inertial Measurement Units (IMU)

| Capteur | Axes | Plage accéléromètre | Bande passante | Interface |
|---|---|---|---|---|
| BNO055 | 9-DOF (accel + gyro + magneto) | ±16 g | Programmable | I2C |
| ADXL345 | 3 axes accéléromètre | ±16 g | 1600 Hz | SPI / I2C |
| ADXL382 | 3 axes accéléromètre | ±200 g | 1600 Hz | SPI |
| MPU6050 | 6-DOF (accel + gyro) | ±16 g | Programmable | I2C |
| ICM-42688-P | 6-DOF (accel + gyro) | ±32 g | 6400 Hz | SPI / I2C |

> [!info] BNO055
> Le BNO055 intègre un processeur de fusion de capteurs (*sensor fusion*) interne. Il fournit directement des quaternions et des angles d'Euler sans avoir à implémenter soi-même le filtre de Kalman pour la fusion gyro/accéléro.

> [!warning] ADXL382 pour le HPR
> Un accéléromètre standard de ±16 g est insuffisant pendant l'accélération. Utiliser un capteur **high-G** comme l'ADXL382 (±200 g) pour les phases propulsées.

### Capteurs de température

| Capteur | Plage | Précision | Interface |
|---|---|---|---|
| TMP36 | -40 a +125 °C | ±2 °C | Analogique |
| DS18B20 | -55 a +125 °C | ±0.5 °C | 1-Wire |
| BMP388 (intégré) | -40 a +85 °C | ±1 °C | SPI / I2C |

### Capteurs de tension/courant

| Capteur | Mesure | Précision | Interface |
|---|---|---|---|
| INA219 | Tension + courant | ±1 % | I2C |
| INA260 | Tension + courant | ±1 % | I2C |
| Diviseur de tension (RC) | Tension | ±5 % | Analogique |

---

## Conception de PCB

### Outils de conception

| Outil           | Type                   | Avantages                                         |
| --------------- | ---------------------- | ------------------------------------------------- |
| KiCad (GAUL)    | Gratuit, open-source   | Communauté active, pas de limites de taille       |
| Altium Designer | Commercial             | Industriel, schémas avancés                       |
| Eagle           | Commercial ( Autodesk) | Intégration avec les librairies SparkFun/Adafruit |

### Considérations pour la rocketry

#### Résistance aux vibrations

Les vibrations du vol sont destructrices. Mesures:

- **Conformal coating** : vernis protecteur sur les composants soumis (soudures, CMS)
- **Conformal potting** : enrobage complet de la section critique avec une résine
- Composants à fixation solide (pas de CMS fragiles sans renforcement)
- Colle chaude sur les grosse composantes (condensateurs, inductances, connecteurs, etc.)

#### Composants notés high-G

Vérifier que chaque composant est capable de supporter les **20-50G** de la phase propulsive:

- Condensateurs céramique de préférence
- Éviter les composants à broches fragiles
- Soudure reflow de préférence au lait

#### Condensateurs de découplage

> [!warning] Découplage
> Placer un condensateur de 100 nF au plus près de chaque broche d'alimentation de chaque IC. Un condensaire bulk de 10 µF par rail d'alimentation est également requis.

#### Plans de masse (Ground planes)

- Utiliser un plan de masse continu sous les composants numériques
- Séparer les masses analogiques et numériques si possible
- Via de connexion entre les plans si séparation

#### Connecteurs

| Connecteur                     | Usage               | Avantage               |
| ------------------------------ | ------------------- | ---------------------- |
| JST-SH                         | Connectique interne | Compact, verrouillable |
| Molex MicroFit 3.0             | Connectique interne | Très compact, fiable   |
| Bornes à vis (screw terminals) | Champ, maintenance  | Sans soudure, robuste  |
| D-sub 9 pins                   | Interface externe   | Standard, robuste      |

### PCB d'armement du GAUL

Le PCB d'armement (*arming board*) gère:
- La distribution de la puissance
- La séquence d'armement
- L'alimentation des canaux pyro
- La logique de contiguïté (*continuity check*)

---

## Télémétrie

### Protocole MavLink

Le GAUL utilise le protocole **MavLink** pour la communication entre l'ODBlix et la station au sol.
- Protocole au niveau des données / structure des paquets. Par au niveau de la modulation, etc.
- Protocole léger, orienté UAV/rocketry
- Messages structurés avec CRC
- Supporte la commande et le télémétrie (bidirectionnel)

### Modules LoRa

| Paramètre | Valeur |
|---|---|
| Fréquence | 915 MHz (Canada) |
| Portée | 10+ km en vol |
| Débit | Jusqu'à 50 kbps |
| Puissance TX | Jusqu'à 20 dBm |

LoRa est idéal pour le **tracker de localisation** grâce à sa portée exceptionnelle.

### Format de données

Les trames de télémétrie contiennent:

1. En-tête (sync bytes)
2. Identification du message (Header)
3. Données (altitude, vitesse, position GPS, état, voltage...)
4. **CRC checksum** pour la validation d'intégrité

### Station au sol

- Réception via module LoRa/FSK connecté à un PC
- Affichage en temps réel (Python, Mission Planner, ou logiciel custom)
- Enregistrement des données pour analyse post-vol

---

## Architecture logicielle

### Machine à états finis (FSM)

L'ordinateur de vol gère les phases du vol via une **FSM** (*Finite State Machine*):

```
Ground → Armed → Boost → Coast → Apogee → Drogue → Main → Landed → Recovery
```

| État | Description | Action |
|---|---|---|
| Ground | Au sol, alimenté | Tests POST, attente armement |
| Armed | Armé, prêt à lancer | Surveillance accéléromètre |
| Boost | Phase propulsive | Ignorer baromètre (bruit), logger données |
| Coast | Après burnout, ascension | Attendre apogée |
| Apogee | Point culminant | Déclencher drogue |
| Drogue | Descente avec drogue | Stabiliser, attendre altitude main |
| Main | Déploiement du main | Ralentir la descente |
| Landed | Au sol | Logger état final, couper armement |
| Recovery | En attente de récupération | Télémétrie de localisation active |

### Ordonnanceur fréquentiel (Scheduler)

Plutôt que des `delay()` ou des interruptions partout, l'ODBlix utilise un **ordonnanceur temps-réel**:

- Tâches périodiques déclenchées par timer
- Exemple : baromètre à 50 Hz, IMU à 200 Hz, télémétrie à 10 Hz, log à 50 Hz
- Priorités assignées à chaque tâche
- Détection de débordement de temps (*overrun*)

### Journalisation de données (Data Logging)

| Support | Avantage | Inconvénient |
|---|---|---|
| Carte SD | Grande capacité, retire facilement | Mécanique, vibrations |
| EEPROM | Simple, fiable | Capacité limitée |
| Flash interne MCU | Rapide | Taille limitée, loss si reset |

### Watchdog timer

Le **watchdog timer** réinitialise le MCU si le logiciel ne répond pas dans le temps imparti. C'est une protection contre les hangs logiciels. Impératif en vol.

---

## Filtre de Kalman (résumé)

> [!info] Document détaillé
> Ce paragraphe est un résumé. Le GAUL dispose d'un document complet sur l'implémentation du filtre de Kalman pour l'estimation d'altitude.

### Pourquoi un filtre de Kalman?

Le baromètre fournit une altitude **bruitée** et avec un **décalage temporel**. L'accéléromètre fournit une accélération **qui dérive**. Le filtre de Kalman **fusionne** ces deux sources pour obtenir une estimation précise et fiable.

### Vecteur d'état

$$x = \begin{bmatrix} p \\ v \\ a \end{bmatrix}$$

- $p$ : position (altitude)
- $v$ : vitesse verticale
- $a$ : accélération

### Étape de prédiction

À partir des données IMU (accéléromètre), on prédit la nouvelle position et vitesse via les équations de mouvement.

### Étape de mise à jour

On corrige la prédiction avec la mesure barométrique, pondérée par les covariances de bruit.

### Importance

Sans filtre de Kalman:
- L'altitude baro seule est trop lente et bruitée pour un déploiement fiable
- L'accéléromètre seul dérive inexorablement
- La fusion permet un déploiement **précis à la bonne altitude**

---

## Défis de l'électronique SRAD

### Vibrations

Les vibrations mécaniques peuvent:

- Desserrent les connecteurs et les soudures
- Corrompre les lectures de capteurs (bruit haute fréquence)
- Casser des composants fragiles (CMS mal soudés)

**Solutions** : conformal coating, fixation solide des connecteurs,condensateurs de découplage, filtrage logiciel.

### Forces G

Pendant la phase propulsive, les forces atteignent **20-50 G**. Conséquences:

- Composants fragiles se détachent
- Les accus perdent temporairement leur tension
- Les condensateurs électrolytiques peuvent échouer

**Solutions** : composants notés high-G, montage solide, test en centrifugeuse.

### Compatibilité électromagnétique (EMI)

Les moteurs à propergol créent un bruit électrique significatif, surtout avec les systèmes d'allumage pyrotechnique.

**Solutions** : blindage, câblage torsadé, séparation logique/analogique, filtrage EMI.

### Alimentation

- Capacité batterie limitée par le poids
- Courants de pointe lors du déploiement pyrotechnique
- Chute de tension sous charge

**Solutions** : dimensionnement adéquat, découplage massif, vérification de la tension minimale.

### Température

- Froid extrême en altitude (jusqu'a -40 °C en stratosphère)
- Chaleur des charges d'éjection

**Solutions** : composants extended-range, isolation thermique, placement strategique.

### Stratégie de test

| Type de test | Description |
|---|---|
| Test au sol (ground test) | Vérifier le fonctionnement complet sans vol |
| Test de vibration | Simuler les vibrations de vol sur table vibrante |
| Vol de qualification | Premier vol avec charge réduite |
| POST (Power-On Self-Test) | Vérification automatique au démarrage |

> [!warning] Règle absolue
> Ne jamais voler sans avoir effectué un **test au sol complet** de tous les systèmes critiques. Un test au sol raté signifie un vol compromis.
