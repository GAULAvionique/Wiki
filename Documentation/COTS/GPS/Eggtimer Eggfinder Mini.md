![[eggfinder.png]]
![[eggtimer_rx_dongle.png]]
# Description
L'Eggfinder Mini est un émetteur GPS de traçage miniature pour fusées, fabriqué par **Eggtimer Rocketry** (California, USA). Il fait partie de la famille Eggfinder qui comprend un émetteur (TX) dans la fusée et un récepteur au sol (LCD Receiver). Le Mini est fonctionnellement identique au Eggfinder TX standard, mais dans un format drastiquement réduit (0,7" × 3,25" incluant l'antenne), suffisamment petit pour tenir dans un body tube de 24 mm. Il émet sur la bande ISM 900 MHz licence-free à 100 mW avec un module Hope RF HM-TRP, et diffuse des données NMEA GPS (latitude/longitude) une fois par seconde vers un récepteur au sol. Produit en kit à souder (difficulté 3/5), c'est le système de tracking GPS le moins cher du marché. Le module GPS Quectel est pré-monté en usine.

**Attention :** Puisqu'on doit les assembler et souder à la main (commercially designed), les produits Eggtimer ne comptent pas comme du COTS en compétition à moins qu'ils n'aient été flight tested.

# Specs

| Paramètre | Valeur |
|---|---|
| Fabricant | Eggtimer Rocketry |
| Type | Émetteur GPS de traçage (transmitter uniquement — pas d'altimètre baro intégré) |
| Module GPS | Quectel (pré-monté en usine, module leadless SMD) |
| Fréquence radio | 900 MHz ISM (licence-free USA), modèles EU (869 MHz) et AUS (921 MHz) |
| Module RF | Hope RF HM-TRP (FSK, half-duplex) |
| Puissance TX | 100 mW |
| Combinaisons fréquence/ID | 72 (programmable via câble pairing avec LCD Receiver) |
| Mise à jour GPS | 1 Hz (1 position/seconde) |
| Format données | NMEA 0183 (série) |
| Portée typique | > 6 miles (9,7 km) en ligne de mire |
| Antenne émission | Antenne vissée 2,4 dB gain (stubby, incluse) |
| Antenne GPS | Intégrée au module Quectel (efficacité réduite vs TX standard) |
| Dimensions (carte) | ~18 mm × 83 mm (0,7" × 3,25") **incluant** l'antenne |
| Format compatible | Body tube 24 mm et plus |
| Masse | Estimé ~5-8 g (carte + antenne, non confirmé officiellement) |
| Alimentation recommandée | LiPo 2S 7,4V (≥ 300 mAh) ou LiPo 1S 3,7V (≥ 300 mAh) |
| Courant fonctionnement | 70-100 mA |
| Batterie 9V alkaline | **Non recommandée** (capacité et courant insuffisants pour GPS) |
| Assemblage | Kit à souder, difficulté 3/5 ; module GPS pré-monté |
| Datalogger | Non supporté (pas de place pour OpenLog sur le Mini) |
| Récepteur requis | Eggfinder LCD Receiver (kit ~55 $) |
| Accessoires au sol | LCD-GPS Module (navigation, ~40 $), Voice Module (annonces vocales, ~20 $) |
| Programmation fréquence | Via câble de pairing 3 conducteurs inclus, connecté au LCD Receiver |
| Prix | ~75 $ (kit TX seul) ; ~125-130 $ (set Mini + LCD) |

# Expérience
### Problèmes courants
- **Acquisition GPS lente** : temps de fixation GPS de 5 à 20 minutes en conditions de ciel dégagé, à cause de l'antenne GPS intégrée plus petite. Allumer le tracker peu avant le lancement.
- **Antenne RF loin de tout conducteur** : pas de contact avec le métal, carbone, ou allthreads. Le carbone fibre bloque les signaux radio.
- **Pas de batterie 9V alkaline** : les piles 9V ne fournissent ni la capacité ni le courant suffisants pour un module GPS. Utiliser du LiPo.
- **Fabrication en kit** : nécessite des compétences de soudure.
### Avantages
- Moins cher que Featherweight
- Programmation plus robuste (pas d'app Bluetooth qui bug et change la programmation)
- Format très compact (24 mm)
- 72 combinaisons fréquence/ID
### Inconvénients
- Doit assembler et souder manuellement
- Antenne GPS intégrée = acquisition lente
- Pas de datalogger intégré
- Pas de Bluetooth (ground station nécessaire)
- Pas d'altimètre barométrique

# Liens
- [Site officiel Eggtimer Rocketry](https://eggtimerrocketry.com/)
- [Page Eggfinder GPS Tracking System](https://eggtimerrocketry.com/home/eggfinder-gps-tracking-system)
- [FAQ Eggfinder GPS](https://eggtimerrocketry.com/eggfinder-gps-faqs)
- [Manuel d'assemblage Mini (PDF)](https://eggtimerrocketry.com/wp-content/uploads/2025/03/Eggfinder-Mini-Assembly-Manual-C3b.pdf)
- [Achat (catalogue)](https://eggtimerrocketry.com/purchase)