![[blue_jay_plus.png]]
# Description
Altimètre intermédiaire de la famille Featherweight, positionné entre le Blue Jay standard (entrée de gamme) et le Blue Raven (haut de gamme). Conçu pour le double déploiement. La version "plus" permet de configurer la charge "main" pour permettre une programmation custom, et surtout d'activer les sorties **avant l'apogée** — essentiel pour les vols multi-étages et airstarts. Cet altimètre a par exemple été utilisé dans le Booster d'Alterra à l'IREC 2025 pour déployer le main à l'apogée (permis à l'époque), ainsi que la charge de séparation à la montée.
# Specs

| Paramètre | Valeur |
|---|---|
| Fabricant | Featherweight Altimeters |
| Dimensions | 37 × 16,5 mm (1,45" × 0,65") |
| Masse | 4,7 g |
| Facteur de forme | Compact — compatible tube BT-20 (18 mm) |
| Alimentation | 3V–12V (1 cellule LiPo recommandée) |
| Consommation | 15 mA |
| Consommation veille | ~0,02 mA (interrupteur magnétique ouvert) |
| Autonomie batterie 180 mAh | ~6% par semaine en veille |
| Capteurs IMU | Accéléromètre 3 axes haute résolution ±32 G |
| | Accéléromètre 3 axes haute gamme ±320 G |
| | Gyroscope 3 axes ±4000 °/s |
| Capteur barométrique | Plage 10–1200 mbar, fiable jusqu'à ~35 000 ft, lisible jusqu'à ~75 000 ft+ |
| Échantillonnage | 50 Hz : accéléromètres, gyroscope, navigation inertielle, baromètre, température, inclinaison, vitesse, tension, continuité |
| Sorties pyro | **2 sorties** (Apo + Main), bornes à vis, **1 A max**, protection brownout |
| | Convient uniquement pour e-matches (pas d'allumeurs/mèches — temps de maintien 15 ms) |
| Fonctions déploiement | 22 événements de vol configurables, **avant et après apogée** (spécifique au Plus) |
| Détection d'apogée | Multi-capteurs à 2/3 voix : baromètre + gyroscope + accéléromètre |
| Sécurité | Détection vol instable < 2s après décollage → déclenchement immédiat |
| Switch magnétique | Intégré, portée ~2" (aimant rare-terre inclus) |
| Connectivité | Bluetooth (BLE) — app "Featherweight UI" (iOS/Android) |
| Mise à jour firmware | OTA via Bluetooth |
| Montage | Trous 4-40, **n'importe quelle orientation** |
| Données résumées | Altitude max, vitesse max, accélérations, temps propulsion, temps apogée, durée de vol |
| Prix | ~105 $ US |

**Différences avec le Blue Jay standard :** Le standard n'a que ±32 G (pas de ±320 G), des gyros ±2200 °/s (pas de ±4000), et ne permet PAS les sorties avant apogée (après apogée uniquement). Le Plus coûte 105 $ vs 75 $.

# Expérience
### Problèmes courants
Les switch magnétiques sont souvent réputées pour ne pas être fiables (s'allument ou s'éteignent par accident, plusieurs switch dans une même baie pose problème). C'est pour ça que sur celui qu'on avais, nous avions shorté la switch en soudant un fil dessus.
De plus, comme les Raven, les Blue Jay sont frustrants à utiliser avec l'application. On pense que notre Blue Jay a été brisé en effectuant une update firmware.
- **Calibration accéléromètre** : si mal calibré, peut détecter un faux décollage et déclencher prématurément. Calibrer via l'app avant chaque vol.
- **Pas de supercondensateur de rétention** : seulement ~15 ms en cas de perte d'alimentation. Convient aux e-matches mais pas aux allumeurs AP.
- **Courant de sortie limité à 1 A** : ne peut pas allumer de starters standard — uniquement des e-matches.
### Avantages
- Pas cher
- Simple à utiliser
- 2 channels configurables (avant ET après apogée)
- Navigation inertielle 6DOF
- Très compact et léger
### Inconvénients
- Seulement 2 channels (ne permet pas double déploiement plus charge)
- Courant limité à 1 A (e-matches uniquement)
- Application Featherweight frustrante

# Liens
- [Page Blue Jay](https://www.featherweightaltimeters.com/blue-jay-altimeter.html)
- [Manuel utilisateur (PDF)](https://www.featherweightaltimeters.com/uploads/1/0/9/5/109510427/blue_jay_users_manual_2026_apr_18.pdf)
- [Apogee Components](https://www.apogeerockets.com/index.php?main_page=product_info&products_id=3342)
- [Wildman Rocketry](https://wildmanrocketry.com/products/blue-jay-altimeter-plus)