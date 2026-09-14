![[SLCF.png]]
# Description
Vieux altimètre seulement baromètrique très "basic". Basic mais aussi **ultra fiable**. Cet altimètre a fait littéralement tous les vols du GAUL depuis son re-début et n'a **JAMAIS** mal fonctionné. Le huitième jour, Dieu a créé le stratologger. Quand le soleil va exploser et détruire notre système solaire, la seule chose qui va rester est le stratologger. Lorsque l'univers cessera d'exister, le stratologger va encore être en train d'enregistrer des données. Cette chose est le sole survivor de la baie avionique d'Ozyman (sustainer IREC 2026), où littéralement rien n'a survécu sauf le stratologger, qui fonctionnait encore. Bref, le GOAT.
Évidemment, on ne peut jamais être parfait, cet altimètre est aussi une relique des temps anciens (genre 2017). Son créateur est trop occupé à répondre aux prières du monde entier, il ne s'occupe donc plus du support du stratologger. Ils sont extrêmement difficile à se procurer, et l'application à utiliser pour le programmer fonctionne uniquement sur windows 10 (La méthode courante est d'utiliser une machine virtuelle pour le programmer).
# Specs

| Paramètre | Valeur |
|---|---|
| Fabricant | PerfectFlite (Andover, NH, USA) |
| Type | Altimètre barométrique, double déploiement + enregistreur |
| Capteur | Capteur de pression de précision + ADC 24 bits sigma-delta |
| Altitude max | 100 000 ft MSL |
| Résolution altitude | 1 ft jusqu'à 38 000 ft ; < 2 ft jusqu'à 52 000 ft ; < 5 ft jusqu'à 72 000 ft |
| Précision | ±(0,1% lecture + 1 ft) typique ; étalonnage ±0,05% typ. |
| Dimensions | 2,0" × 0,84" × 0,5" (50,8 × 21,3 × 12,7 mm) — tient dans un tube 24 mm |
| Masse | 0,38 oz (~10,8 g) |
| Alimentation | 4 V à 16 V (nominale 9 V), polarité inversée sans dommage |
| Consommation | ~1,5 mA |
| Courant max sortie pyro | 5 A (courant fourni par la batterie) |
| Durée sortie pyro | 1,0 seconde |
| Canaux pyro | 2 : apogée/drogue + principale |
| Délai apogée | 0 à 5 s (config par ordinateur) |
| Altitude déploiement main | 100 à 9 999 ft par pas de 1 ft (PC) ou 100 ft (terrain) |
| 9 préréglages usine | 300 · 500 · **700 (défaut)** · 900 · 1100 · 1300 · 1500 · 1700 · 2500 ft |
| Détection lancement | 160 à 300 ft AGL (défaut 160 ft) |
| Enregistrement | Altitude, température, voltage — **20 Hz**, **16 vols** × >18 min |
| Mach | MachLock automatique (pas de mach delay à régler) |
| Brownout | Tolère plusieurs secondes de coupure d'alimentation |
| Voltmètre | Annonce le voltage batterie au démarrage |
| Sirène localisation | 0 à 120 s (défaut 5 s) ; ~3 mois sur pile 9V alcaline en mode veille |
| Température fonctionnement | −40 °C à +85 °C |
| Télémétrie série | 9 600 bps, 8N1, niveau 3,3 V CMOS, texte ASCII (altitude) |
| Programmation | Bouton PROG (préréglages terrain) ou ordinateur via kit DT4U + logiciel DataCap |
| Codes d'erreur | 1=coupure totale, 2=coupure momentanée, 3=drogue >6A, 4=main >6A, 5=mémoire flash, 6=capteur |
| Prix | ~65-70 $ US (vente directe PerfectFliteDirect) |
| Garantie | 3 ans / 36 mois |

# Expérience
### Problèmes courants
- Le logiciel pour le programmer et sortir les données de vol fonctionne uniquement sur windows 10. On a roulé le logiciel sur une machine virtuelle pour le faire fonctionner.
### Avantages
- Ultra fiable
- Simple à utiliser
- 9 préréglages terrain (pas besoin d'ordinateur pour les vols standards)
- MachLock automatique
- Brownout tolérant (coupures de tension)
- 16 vols en mémoire
- Très abordable
### Inconvénients
- Assez limité, peut seulement être utilisé pour le double déploiement de base
- Mesure uniquement l'altitude barométrique
- Application uniquement sur windows 10
- Très difficile à acheter (voir impossible) — production limitée
- Firmware non modifiable par l'utilisateur
- Pas de navigation inertielle

# Liens
- [Page officielle](http://www.perfectflite.com/SLCF.html)
- [Manuel utilisateur (PDF)](http://www.perfectflite.com/Downloads/StratoLoggerCF%20manual.pdf)
- [Fiche caractéristiques (PDF)](http://www.perfectflite.com/Downloads/StratoLoggerCF%20info.pdf)
- [Téléchargements (DataCap, drivers)](http://www.perfectflite.com/Download.html)
- [Boutique directe (~65 $ US)](https://perfectflitedirect.com)