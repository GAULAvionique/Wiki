![[easymini.png]]
# Description

L'EasyMini est un altimètre miniature barométrique à double déploiement avec enregistrement de vol, fabriqué par **Altus Metrum** (communauté open-source fondée par Bdale Garbee et Keith Packard). Il tient dans un tube coupleur de 24 mm et pèse moins de 7 g, ce qui en fait l'un des plus petits altimètres double-déploiement du marché. Il détecte l'apogée et l'altitude de descente par pression barométrique (capteur MS5607) avec un filtre de Kalman, éliminant tout besoin de « Mach delay ». Il enregistre les données de vol en mémoire flash SPI et se télécharge par port micro-USB, sans kit de transfert propriétaire. Matériel (licence TAPR Open Hardware) et firmware (GPL v2 via AltOS) sont entièrement open source. Version actuelle : 3.0.

# Specs

| Paramètre | Valeur |
|---|---|
| Fabricant | Altus Metrum |
| Type | Altimètre barométrique, double déploiement + enregistreur |
| Version actuelle | v3.0 (même specs utilisateur, chip différent des versions précédentes) |
| Processeur (v3.0) | NXP LPC11U24 (ARM Cortex-M0, 32 kB flash, 8 kB RAM, USB 2.0) |
| Capteur barométrique | Measurement Specialties/TE MS5607 (ADC 24 bits delta-sigma, résolution ~20 cm) |
| Altitude max | 100 000 ft MSL (~30 480 m) |
| Dimensions PCB | 38 × 20 mm (1,5" × 0,8"), hauteur ~15 mm — conçu pour tube 24 mm |
| Masse | 6,5 g (0,23 oz) |
| Alimentation | 3,7 à 12 V (LiPo 1S via JST ou bornier pour pile 9 V) |
| Batterie pyro séparée | Oui (broches dédiées, ≤ 15 V) |
| Canaux pyro | 2 : apogée (drogue) + principale |
| Durée allumage pyro | 50 ms fixe (non modifiable sans re-flash) |
| Télémétrie radio | Aucune |
| Mémoire enregistrement | ~10 min de données (100 s/s montée, 10 s/s descente) |
| Données enregistrées | Altitude, pression/température, voltage, continuité igniteur, états, apogée, vitesse max, temps montée/descente |
| Filtre Mach | Filtre de Kalman — aucun « mach delay » à régler |
| Détection lancement | ~20 m AGL en 5 s |
| Modes déploiement | Dual Deploy, Apogée seul, Apogée Redondant, Main Redondant, Booster |
| Config par défaut | Drogue à l'apogée, main à 250 m (820 ft) |
| Connectivité | Micro-USB (USB 2.0) |
| Logiciel | AltOS / AltosUI (Windows, Linux, Mac) |
| Firmware | Auto-programmable par USB ; v3.0 requiert AltOS ≥ 1.9.12 |
| Annonce au sol | Bip/volt au démarrage + bips de continuité (1 = apogée, 2 = main, 3 = les deux, « brap » = aucune) |
| Prix | ~80 $ US |
| Licence | Matériel TAPR Open Hardware, logiciel GPL v2 |

# Expérience
### Problèmes courants
- **Beeper anémique** : à peine audible une fois dans la fusée sur le pas de tir. Faire des ground tests obligatoires.
- **USB tricky** : il faut brancher le câble USB **avant** d'alimenter pour entrer en mode « idle » (sinon le PC ne détecte pas l'appareil).
- **50 ms de pyro fixes** : suffisant pour les e-matches basse tension, mais limite pour certains allumeurs. Modifiable seulement par re-flash.
- **Polarité des batteries JST** : les batteries RC tiers (ex. Tenergy pour Featherweight) ont une polarité inversée et sont incompatibles.
- **Apogee Lockout bug** (corrigé) : pouvait parfois empêcher la charge de drogue de se déclencher.
- **Config moins intuitive** que d'autres appareils — nécessite AltOSUI.
### Avantages
- Extrêmement petit et léger (6,5 g, tient dans un 24 mm)
- Open source (matériel + firmware)
- USB intégré (pas de kit de transfert)
- Filtre de Kalman (pas de mach delay)
- Polyvalent (5 modes de déploiement)
### Inconvénients
- Pyro limité à 50 ms
- Pas de télémétrie
- Beeper faible
- App AltOSUI moins intuitive que l'app Featherweight
- Impossible de configurer finement les altitudes sans AltOSUI

# Liens
- [Page officielle](https://altusmetrum.org/EasyMini)
- [Manuel EasyMini (HTML)](https://altusmetrum.org/AltOS/doc/easymini.html)
- [Logiciel AltOS/AltosUI](https://altusmetrum.org/AltOS/)
- [Achat boutique officielle (~80 $ US)](https://shop.gag.com)
- [Revue Apogee Rockets](https://www.apogeerockets.com/Electronics-Payloads/Dual-Deployment/EasyMini)