---
aliases: []
tags:
  - alimentation
  - baie-avionique
  - avionique
created: 2026-09-14
---

# Systèmes d'alimentation et baie avionique

## Introduction

L'alimentation électrique est le **sang** de l'avionique. Une batterie morte signifie un ordinateur de vol inactif, des charges pyrotechniques inopérantes, et potentiellement une **lawn dart** (descente non contrôlée). Le dimensionnement et la gestion de l'alimentation sont des tâches critiques.

> [!info] Principe fondamental
> Chaque milliampère-heure (mAh) compte. Un budget énergétique rigoureux est la base d'un vol réussi.

---

## Types de batteries

| Type                 | Tension nominale | Capacite typique | Poids      | Usage courant              | Avantages / inconvenients                  |
| -------------------- | ---------------- | ---------------- | ---------- | -------------------------- | ------------------------------------------ |
| LiPo 1S              | 3.7 V            | 100-800 mAh      | 3-25 g     | Altimetres, GPS, trackers  | Leger, rechargeable / delicate, BMS requis |
| LiPo 2S              | 7.4 V            | 300-2200 mAh     | 15-100 g   | Télémétrie, actionneurs    | Bonne autonomie / plus lourd               |
| LiPo 3S              | 11.1 V           | 1000-5000 mAh    | 80-300 g   | Servos, actionneurs lourds | Courant élevé / poids élevé                |
| Lithium 9V (LiFePO4) | 8-9V             | 1200 mAh         | 35 g       | Altimetres                 | Leger, longue duree / cher                 |
| Alcaline 9V          | 9V               | 500-600 mAh      | 45 g       | Altimetres basiques        | Simple, bon marche / lourd, self-discharge |
| AAA lithium          | 1.5V x3          | 1200 mAh         | 15 g       | Tracker Spotrace           | Léger / non rechargeable                   |
| NiMH                 | 1.2V x N         | Variable         | Plus lourd | Applications rechargeables | Beaucoup de cycles / poids                 |

> [!warning] LiPo
> Les batteries LiPo sont souvent interdites ou déconseillées. On peut utiliser à la place des cellules **Li-Ion 18650**. Même tension et capacité similaire, mais plus safe.

---

## Calcul de capacite

### Budget energetique

Le premier pas est de calculer la **consommation totale** de tous les composants :

| Composant | Courant typique | Cycle de service | Energie |
|---|---|---|---|
| Altimetre (Blue Raven) | 15 mA continu | 100 % (2h de vol) | 30 mAh |
| Module LoRa (emission) | 120 mA | 10 % (TX periodique) | 24 mAh |
| IMU + MCU | 30 mA | 100 % | 60 mAh |
| LED d'armement | 20 mA | 5 % | 2 mAh |
| Charges pyro x2 | 1.5 A | 0.01 % (0.5s) | 0.15 mAh |
| **Total** | | | **~116 mAh** |

### Facteur de securité


$$C_{batterie} = C_{total} \times k_{securite}$$

Avec $k_{securite} = 2$ a $3$. Pour l'exemple ci-dessus, il faut donc une batterie d'au moins **230 a 350 mAh**.

### Autonomie

$$\text{Autonomie (h)} = \frac{C_{batterie}}{I_{moyenne}}$$

Exemple avec une LiPo 1S 450 mAh et une consommation moyenne de 58 mA:

$$\text{Autonomie} = \frac{450}{58} = 7.76 \text{ h}$$

---

## Regulation de tension

### Regulateurs lineaires (LDO)

- **Principe** : dissipe l'excédent de tension en chaleur
- **Avantages** : simples, faible bruit, pas d'inducteur requis
- **Inconvenients** : faible rendement quand la difference d'entree/sortie est grande
- **Usage** : alimentation de capteurs sensibles (barometre, IMU)

| LDO | Entree | Sortie | Courant max | Dropout |
|---|---|---|---|---|
| MCP1700 | 2.7-6.0 V | 3.3 V | 250 mA | 178 mV |
| AMS1117 | 4.5-12 V | 3.3/5.0 V | 800 mA | 1.1 V |

### Regulateurs a commutation (BEC/Buck)

- **Principe** : convertit la tension par commutation rapide (inducteur + MOSFET)
- **Avantages** : rendement élevé (85-95 %)
- **Inconvenients** : bruit de commutation, plus complexe, inducteur requis
- **Usage** : alimentation de systems a forte consommation (servos, actionneurs)

| BEC | Entree | Sortie | Courant max | Rendement |
|---|---|---|---|---|
| UBEC (Turnigy) | 7-26 V | 5/6 V | 3A | 90 % |
| Pololu 5V step-down | 3.5-30 V | 5 V | 500 mA | 85 % |

> [!info] Quand utiliser quoi
> Pour des capteurs analogiques sensibles (barometre), preferer un LDO. Les LDO sont aussi corrects pour alimenter des périphériques à faible consomation. Pour alimenter des servos ou des modules a forte consommation, utiliser un switching regulator (Buck).

---
## Securite des batteries

### Stockage LiPo

| Parametre | Valeur |
|---|---|
| Tension de stockage | 3.8 V par cellule (40-60 % SOC) |
| Temperature de stockage | 20-25 °C |
| Duree maximale | 3 mois a stockage, 1 an maximum |
| Tension minimale en vol | 3.0 V par cellule |

### Consignes de securite

- **Toujours** charger avec un chargeur equilibreur (*balance charger*)
- **Toujours** utiliser un sac ignifuge pendant la charge
- **Ne jamais** stocker chargee ou dechargee
- **Ne jamais** utiliser une batterie gonflee (*swollen*) — risque d'incendie
- **Couper** l'alimentation en cas d'odeur anormale ou de fumee
- **Recycler** les batteries usees correctement

> [!warning] Batterie gonflee
> Une batterie gonflee signifie une degradation interne. Risque d'incendie ou d'explosion. **Ne pas utiliser**, ne pas percer, placer dans un sac ignifuge et recycler.

---

## Conception de la baie avionique (E-bay)

### Objectifs

La baie avionique (ou **E-bay** pour *Electronics Bay*) a pour roles:

1. **Proteger** les electroniques contre les vibrations, la chaleur et les forces G
2. **Permettre** le deploiement des parachutes (logement des charges pyro)
3. **Faciliter** l'acces pour la maintenance et la configuration

### Composants typiques

| Composant | Role | Materials courants |
|---|---|---|
| Bulkheads (cloisons) | Separation structurale, fixation | Fiberglass, contreplaque |
| Coupler | Assemblage dans le tube principal | Fiberglass, cardboard |
| Sled | Support des electroniques | Fiberglass, impression 3D |
| Standoffs | Fixation et espacement des PCB | Aluminium, nylon |
| Visserie | Assemblage | Acier inoxydable, nylon |

---

## Layout de la baie

### Schema type (vue en coupe)

```
+============================================================+
|                    COUPLER (tube d'assemblage)              |
|                                                             |
|  +-----------+     +-----------+     +-----------+          |
|  | BULKHEAD |     |   SLED    |     | BULKHEAD |          |
|  | (charge  |     |           |     | (charge  |          |
|  |  drogue) |     | [Batterie]|     |  main)   |          |
|  |          |     | [Altimetre|     |          |          |
|  +----------+     |  /MavLink]|     +----------+          |
|                   | [ODBlix]  |                            |
|                   | [Tracker] |                            |
|                   +-----------+                            |
|                                                             |
+============================================================+
```

### Principes de placement

| Principe | Justification |
|---|---|
| Altimetre vertical | Meilleure lecture barometrique (orifice oriente vers l'exterieur) |
| Batterie accessible | Remplacement rapide en terrain |
| Câbles sans tension | Eviter la rupture par vibration |
| Antenne eloignee du carbone | Le carbone bloque les RF |
| Antenne avec vue claire | Orientation preferentielle vers le haut/bas |

### Isolation des vibrations

- Mousse EVA sous les PCB sensibles
- Montages en silicone pour les acceléromètres
- Impact sur la lecture du barometre : le bruit de vibration degrade la precision

> [!info] Test de vibration
> Avant le premier vol, valider que les lectures du barometre sont stables en simulant des vibrations (table vibrante ou test moteur au sol).

---

## Accessibilite et maintenance

### Conception pour le terrain

| Principe | Implementation |
|---|---|
| Accès rapide | Vis a tete hexagonale (pas de tournevis philips) |
| Bornes a vis | Changer la batterie sans soudure |
| Marquage des câbles | Etiquettes ou codes couleur |
| Design modulaire | Retirer un module sans desassemblage complet |

### Bornes a vis vs soudure

| Critere | Bornes a vis | Soude |
|---|---|---|
| Facilite d'utilisation en terrain | Excellente | Mauvaise |
| Resistance aux vibrations | Bonne (avec frein de vis) | Excellente |
| Fiabilite long terme | Bonne | Excellente |
| Flexibilite de configuration | Excellente | Limitée |

### Marquage des cables

Utiliser un **marqueur de fil** ou des **etiquettes shrink-wrap** sur chaque cable. Convention GAUL:
- Rouge : VCC / positif
- Noir : GND / masse
---

## Exemples de baies avioniques

### Baie simple (altimetre unique)

Configuration basique pour un vol de niveau 1:

- 1 altimetre COTS (Blue Raven ou eg equivalant)
- 1 batterie LiPo 1S
- 2 charges pyro (drogue + main)
- 1 connecteur d'armement

> Avantages : simplicite, fiabilite, poids reduit.
> Inconvenients : pas de redondance.

### Baie double (altimetre redondant)

Configuration pour le HPR:

- 2 altimetres independants (chacun a sa batterie)
- Chaque altimetre pilote ses propres charges
- Logique OR : si l'un echoue, l'autre prend le relais

> Avantages : fiabilité élev.e, backup en cas de défaillance.
> Inconvénients : poids, complexité, coût.

### Approche GAUL : leçons d'Altera et LC 2026

Le GAUL a tire des lecons importantes de ses missions precedentes:

| Mission | Lecon                                          | Amelioration                                            |
| ------- | ---------------------------------------------- | ------------------------------------------------------- |
| LC 2026 | Incompatibilite antenne SMA/RP-SMA             | Verification de tous les connecteurs RF avant vol       |
| LC 2026 | Surchauffe RunCam dans la baie                 | Separation de l'alimentation camera, activation tardive |
| LC 2026 | PCB d'armement seul refusé par la compétition. | Utiliser des PCB d'armement redondants                  |

> [!info] Philosophie GAUL
> Chaque mission genere des lecons. Documenter et appliquer ces lecons est ce qui distingue une equipe qui progresse d'une equipe qui repete les memes erreurs.
