![[RRC3.png]]
# Description
Le RRC3+ est la dernière génération du Rocket Recovery Controller, un altimètre barométrique dual-deploy produit par **Missile Works Corporation** (Lyons, CO, USA). Lancé en mai 2024, il succède au RRC3 « Classic » avec un facteur de forme réduit (65 mm × 25,5 mm au lieu de 99,5 mm × 23,5 mm). Il offre **trois canaux pyrotechniques** — Drogue, Main et Auxiliary — ce qui le distingue de la plupart des altimètres dual-deploy de sa catégorie. Le canal Aux est entièrement programmable pour le staging, les airstarts, l'allumage de grappe, ou des événements de secours. Il supporte l'enregistrement multi-vols (7 vols), le streaming de télémétrie en temps réel, et est compatible avec un écosystème d'accessoires (LCD Terminal, UDC USB, Bluetooth HC-06, système RTx GPS/Telemetry). Livré prêt à voler avec une simple pile 9V.

# Specs

| Paramètre | Valeur |
|---|---|
| Fabricant | Missile Works Corporation |
| Type | Altimètre barométrique, double déploiement + enregistreur |
| Processeur | MSP430, 16 MHz, 16 bits |
| Mémoire | 4 Mbit SST Flash |
| Capteur barométrique | MSI MS5607, ADC ΔΣ 24 bits |
| Altitude max | 100 000 ft MSL (version Xtreme) / 40 000 ft (standard) |
| Dimensions | 65 mm × 25,5 mm (2,56" × 1,0") |
| Masse | ~14 g |
| Alimentation | 3,5 à 10,0 VDC (optimisé pour pile 9V alkaline) |
| Courant quiescent | 6 mA @ 9V |
| Courant fonctionnement | 35 mA @ 9V (piezo + LED actifs) |
| Alimentation pyro | Séparée de la logique (jusqu'à 30VDC max) |
| Canaux de sortie | 3 : Drogue, Main, Auxiliary |
| Courant tir Drogue/Main | 2 A pendant 1 s (IntelliFET) |
| Courant tir Aux | 4 A pendant 1 s (IntelliFET) |
| Modes Aux | One-Shot, Latched, Repeat (programmable) |
| Enregistrement | 7 vols, ~28 min de données par vol |
| Fréquence échantillonnage | 20 Hz (altitude/vitesse), 1 Hz (température/tension) |
| Télémétrie série | 0,5 ou 1 Hz, 9600 bps, flux configurable |
| Feedback | Buzzer magnétique 85 dB + LED rouge |
| Programmation | DIP switches + bouton (terrain), mDACS (PC), LCD Terminal, ou Bluetooth HC-06 |
| Logiciel PC | mDACS v1.61 (Windows) |
| Accessoires | LCD Terminal, UDC USB, Bluetooth HC-06, RTx GPS/Telemetry |
| Armement | Barométrique (altitude AGL définie) |
| Altitude min armement | 100 ft AGL (ajustable) |
| Paramètres par défaut | Armement : 300 ft AGL, Main : 500 ft AGL |
| Prix | ~75 $ US |

# Expérience
### Problèmes courants
**Attention :** Allumer et fermer le RRC3+ rapidement (avant qu'il ne finisse de booter) peut brick l'altimètre à vie. Le cycle d'initialisation barométrique dure 10 secondes au démarrage. Il faut **attendre au moins 10 secondes** entre deux mises sous tension.

**Attention :** Ne pas dépasser 10VDC sur l'alimentation logique — risque de dommage.

À Launch Canada 2026, il est utilisé dans le sustainer. Quelque chose de louche s'est passé avec le logging et les statistiques de vol (639 ft d'apogée, et aucun log). Il faudrait donc vérifier s'il n'est pas brisé.

- **Condensateur de brownout** : sur la version « Xtreme », le condensateur électrolytique est remplacé par un type à diélectrique solide pour les opérations en vide.
- **Batterie non sécurisée** : peut se détacher lors des événements de récupération.
### Avantages
- Simple et pas cher
- 3e channel configurable (staging, airstart, etc.)
- Enregistrement multi-vols (7 vols)
- Télémétrie série en temps réel
- Écosystème d'accessoires complet
- Buzzer loud 85 dB
### Inconvénients
- Possiblement brisé et donc moins fiable (à vérifier)
- Seulement barométrique
- Risque de brick si power-cycle trop rapide
- Ne pas dépasser 10VDC
- Plus gros que le Stratologger CF

# Liens
- [Site officiel MissileWorks](https://www.missileworks.com/rrc3)
- [Manuel utilisateur RRC3+ (PDF)](https://www.apogeerockets.com/downloads/PDFs/RRC3-user-manual.pdf)
- [Manuel mDACS (PDF)](https://www.apogeerockets.com/downloads/PDFs/mDACS-usb-io-user-manual.pdf)
- [Téléchargements (mDACS, manuals)](https://www.missileworks.com/downloads)
- [Achat LOC Precision (~75 $)](https://locprecision.com/products/missile-works-rrc3)