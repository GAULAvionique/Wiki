![[FW_GPS.png]]
# Description
Traqueur GPS le plus répandu dans la communauté rocketry. Fait partie de la famille Featherweight et partage l'app Bluetooth. Fabriqué par Adrian Adamson (Featherweight Altimeters, USA). Utilise un module GPS u-blox M10 de dernière génération combiné à une radio LoRa 915 MHz pour transmettre les coordonnées en temps réel depuis la fusée jusqu'au sol. Le système nécessite deux composants : un tracker embarqué dans la fusée et une station au sol (Ground Station) reliée par Bluetooth à une application smartphone (iOS/Android). Sa portée radio LoRa est exceptionnelle — démontré pour des vols dépassant 137 000 pieds (41 km) d'altitude avec les antennes standard. Le nombre de scrubs qui ont été causés par cette abomination est franchement insultant. L'ironie de la chose c'est que c'est aussi le standard de la communauté, donc assez difficile de s'en départir. En effet, dans un monde où il n'existe aucun traqueur GPS pour fusées amateur fiables, on doit se contenter du moins pire: le Featherweight GPS tracker. *To be fair*, quand tu suis les règles non écrites (détaillées plus bas), ils ne sont pas si pire que ça.
# Specs

| Paramètre | Valeur |
|---|---|
| Fabricant | Featherweight Altimeters (Adrian Adamson) |
| Module GPS | u-blox M10 |
| Constellations | GPS, GLONASS, Galileo, BeiDou — simultanées |
| Solutions GPS | 10 par seconde |
| Altitude GPS max | 80 km (262 467 pieds) |
| Vitesse max | 500 m/s (Mach 1,45) |
| Antenne radio | LoRa 915 MHz, connecteur SMA (pas RP-SMA) |
| Puissance TX radio | 100 mW (original) / 158 mW (Swift) |
| Protocole radio | LoRa — bidirectionnel avec acknowledge |
| Canaux | 56 canaux (original) / +240 canaux (Swift) |
| Portée démontrée | >137 000 pieds (41 km) altitude, >145 900 pieds (44 km) portée totale |
| Sensibilité RX au sol | -133 dBm |
| Dimensions tracker | 42 mm × 20 mm × 13 mm (original) ; 33,5 mm × 20 mm (Swift) |
| Longueur totale avec antenne | ~104 mm (4,1") |
| Masse tracker | 15 g (avec antenne, sans batterie) |
| Alimentation | 3,4V – 4,5V DC via bornier à vis |
| Batterie recommandée | LiPo 1S (4,1V), 400 mAh (min. 150 mAh) |
| Courant consommé | 60 mA (TX off), 112 mA (TX on), ~86 mA moyen |
| Autonomie tracker | ~16h (original, 400 mAh) / ~7h (Swift, 400 mAh) |
| Batterie station sol | 850 mAh (GS v2) ou 2 Ah (ancienne GS) |
| Autonomie station sol | ~21h (GS v2, 850 mAh) / ~50h (GS v2, 2 Ah) |
| Interface BT | Bluetooth — app "Featherweight UI" (iOS et Android) |
| Données enregistrées | Position GPS 3D, vitesse, force du signal — 10 échantillons/s |
| Export | Fichier .kml (Google Earth) |
| Mode perdu | Oui — relay par tout tracker Featherweight avec vue dégagée |
| Firmware | Mises à jour OTA via l'app |
| Approuvé records | Oui — Tripoli altitude record attempts |
| Prix tracker | ~160-171 USD (unité seule) |
| Prix système complet | ~440-574 USD (GS + tracker + batterie) |

# Expérience
### Problèmes courants
Attention à la polarité des borniers **surtout sur la ground station**. La polarité des borniers sur la ground station et sur les trackers n'est pas la même. Donc en gros ne démontez jamais la ground station. Si vous devez la charger, faites le par USB. Pour ce qui est des trackers, une inversion de polarité le brise automatiquement. Un peu comme pour les Blue Raven, il faut suivre les règles suivantes pour les configurer :
- Utiliser seulement un cellulaire à la fois et d'une fois à l'autre. Pour changer de cellulaire, oubliez le traqueur sur l'ancien.
- Remplir complètement le nom des trackers (utiliser tous les 11 caractères)
- Pour vérifier si le traqueur a bien un fix GPS, il faut passer par une ground station (même si on est connecté par bluetooth au traqueur)
- Ne pas interrompre les téléchargements, ou appuyer sur le bouton pause si ça doit être fait.

Problèmes courants :
**Pas de fix GPS :**
- Vérifier qu'une ground station est bien connectée au traqueur.
- Vérifier le placement de l'antenne GPS. **L'antenne GPS est la patch de céramique sur le traqueur, et non l'antenne qui s'y visse!!!**. La patch est directionnelle, et doit être pointée vers l'extérieur de la fusée et avoir une vue claire de l'extérieur et du ciel.
- Attendre au moins 5 mins, ça peut être long.
- Vérifier que le traqueur n'est pas brisé. Vérifier la consommation de courant. S'il consomme plus de 100mA, c'est probablement qu'il est brisé. 
**Pas de communication LoRa :**
- Vérifier que l'antenne est bien vissée (traqueur et GS).
- Vérifier que le port de l'antenne est compatible si ce n'est pas l'antenne d'origine (attention SMA et RP-SMA, ce n'est pas parce que ça se visse que c'est compatible).
- Vérifier le Line of Sight
- Vérifier le placement de l'antenne dans la baie et dans la fusée (ne pas oublier que la fibre de carbone bloque le rayonnement RF).

Problèmes connus forums :
- **Connectique SMA** : pins centraux d'antennes défectueux observés — vérifier visuellement avant chaque vol.
- **SMA vs RP-SMA** : peuvent physiquement s'emboîter mais ne fonctionnent pas ensemble — toujours vérifier.
- **Bluetooth instable** : déconnexions BLE aléatoires, surtout lors de mises à jour iOS.
- **Mises à jour forcées** : l'app peut forcer une mise à jour firmware au terrain sans option de sauter.
- **Antenne SMA fragile** : les soudures peuvent casser lors d'impacts violents.
- **Grandes concentrations** : problèmes de canaux et d'interférences BT lors de gros lancements.

### Avantages
- Répandu donc beaucoup de support
- Portée exceptionnelle (LoRa 915 MHz)
- Ironiquement la solution COTS GPS la moins chère
- Multi-constellations (GPS/GLONASS/Galileo/BeiDou)
- Approuvé pour les records Tripoli
### Inconvénients
- Pas fiables (réputation bien établie)
- Application Bluetooth frustrante et buguée
- SMA vs RP-SMA source d'erreur courante
- Prix du système complet élevé (~500 $)

# Liens
- [Page FW GPS tracker](https://www.featherweightaltimeters.com/original-gps-tracker.html)
- [Swift Tracker](https://www.featherweightaltimeters.com/swift-tracker.html)
- [Manuel PDF](https://www.featherweightaltimeters.com/uploads/1/0/9/5/109510427/gps_tracker_manual_2025feb20.pdf)
- [Forum — problèmes antennes](https://www.rocketryforum.com/threads/check-your-featherweight-tracker-antenna.176021/)
- [Forum — problèmes BT](https://www.rocketryforum.com/threads/problems-with-my-featherweight-tracker.194877/)
- [Apogee Rockets](https://www.apogeerockets.com/Electronics-Payloads/Rocket-Locators/Featherweight-GPS-Tracker-1-pk)