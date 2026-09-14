![[Blue_raven.png]]
# Description
Altimètre haut de gamme avec données barométriques, et d'IMU. Il se programme et s'arme par Bluetooth et fait partie de l'écosystème Featherweight. Ses quatres canaux de pyro sont programmables (la programmation costum est très flexible et avancée). Cet altimètre est idéal pour les vols avancés (staging, vols exo-atmosphériques, payload déployable, etc) tout en étant (relativement) abordable. Le Blue Raven 2 (version actuelle) ajoute une sécurité matérielle contre les déclenchements accidentels lors de la mise sous tension et des capteurs inertiels améliorés.
# Specs

| Paramètre | Valeur |
|---|---|
| Fabricant | Featherweight Altimeters |
| Dimensions | 46 × 20 × 12 mm (1,8" × 0,8" × 0,48") |
| Masse | 6,8 g (0,24 oz) |
| Alimentation | Li-Po 3,7V à 16V (batterie externe) |
| Mémoire flash | 2 vols stockés (le plus ancien est effacé) |
| Capteurs IMU | Accéléromètre 3 axes haute gamme ±320 G (BR2) / ±400 G (BR1) |
| | Accéléromètre 3 axes haute résolution ±32 G |
| | Gyroscope 3 axes ±4000 °/s (BR2) |
| Capteur barométrique | Plage 10–1200 mbar, précision ±0,3% |
| | Altitude max fiable : ~45 000 ft (13 716 m) |
| Capteur température | Haute précision, intégré |
| Échantillonnage HR | 500 Hz : accéléromètres, gyroscope, quaternion d'attitude, courant de sortie, entrée analogique |
| Échantillonnage LR | 50 Hz : inclinaison, vitesse, baromètre, température, tension, continuité, logique déploiement |
| Sorties pyro | **4 sorties** à 25 A, compatible 1 cellule LiPo à 16V, circuit open-drain, limitation courant intégrée |
| Fonctions déploiement | 22 événements de vol configurables par sortie, Primaire + Secondaire indépendants par canal |
| Navigation inertielle | 6DOF : trajectoire 3D, vitesse horizontale, pertes d'inclinaison, taux de roulis |
| Montage | **N'importe quelle orientation**, y compris à plat |
| Connectivité | Bluetooth (BLE) — app "Featherweight UI" (iOS/Android) |
| Interface USB | Connexion série USB (port à trous traversants) |
| Mise à jour firmware | OTA via Bluetooth depuis l'application |
| Commutateur | Interrupteur magnétique intégré (version 1") ou externe (standard) |
| Compatibilité | Tous les accessoires Raven4 (trous 4-40, av-bay, PowerPerch) |
| Prix | **175 $** (standard) / 200-475 $ selon options |

# Expérience
### Problèmes courants
Les produits Featherweight sont particulièrement frustrants à utiliser. L'application BT n'est pas très permissive et bogue fréquemment. C'est aussi possible de complètement briser l'appareil en appuyant sur un mauvais bouton lors des updates firmware (IREC 2026). Il faut donc être très patient et faire attention lors des manipulations. Voici quelques conseils d'utilisations :
- Ne jamais utiliser plus d'un cellulaire pour les configurer, surtout pas en même temps! Si quelqu'un d'autre veut s'y connecter, le dernier utilisateur doit oublier l'appareil sur son cellulaire.
- Ne pas interrompre les téléchargements. Si un téléchargement doit être interrompu, cliquer sur le bouton pause.
- Être patient avec l'app et attendre qu'elle réponde.

Problèmes connus forums :
- **Déclenchements accidentels au démarrage (v1)** : corrigé sur le Blue Raven 2 avec protection matérielle.
- **Téléchargement Bluetooth instable en extérieur** : déconnexions surtout avec plusieurs dispositifs FW simultanés. Déconnecter BT avant d'approcher la fusée.
- **« Unauthorized User »** : si le firmware n'est pas réinitialisé entre utilisateurs. App ouverte avant de brancher l'alimentation.
- **Données corrompues** : cas rares de fichiers HR corrompus après téléchargements multiples.

### Avantages
- 4 Pyros (staging, airstart, payload, etc.)
- Déploiement des pyros très flexible (22 événements)
- IMU complète 6DOF (pas uniquement barométrique)
- Petit et léger
- Bluetooth
- Navigation inertielle avancée
### Inconvénients
- Cher (quand même moins cher que les compétiteurs)
- Application ne donne pas beaucoup de contrôle, surtout sur les données de vol
- Application USB désuète
- Fragile (risque de brick avec updates firmware)

# Liens
- [Page Blue Raven](https://www.featherweightaltimeters.com/blue-raven-altimeter.html)
- [Manuel utilisateur (PDF)](https://www.featherweightaltimeters.com/uploads/1/0/9/5/109510427/blue_raven_users_manual_2025_sept_10.pdf)
- [Boutique Featherweight](https://www.featherweightaltimeters.com/store/p25/Blue_Raven_Permalink.html)
- [Madcow Rocketry](https://www.madcowrocketry.com/featherweight-blue-raven/)
- [Apogee Components](https://www.apogeerockets.com/Electronics-Payloads/Dual-Deployment/Blue-Raven-Altimeter)
- [Rocketry Forum — révisions/bugs](https://www.rocketryforum.com/threads/blue-raven-revisions.197405/)