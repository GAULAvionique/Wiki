# Physique et aérodynamique

> [!info]
> Comprendre les forces et les principes physiques qui agissent sur une fusée est essentiel pour concevoir un véhicule capable d'atteindre l'altitude cible de manière sécuritaire et efficace. Cette page couvre les fondamentaux de la mécanique de vol et de l'aérodynamique appliqués à la rocketry amateur.

---

## Les forces en vol

Quatre forces principales agissent sur une fusée en vol. Leur équilibre détermine la trajectoire, la stabilité et la performance du véhicule.

| Force | Symbole | Direction | Origine |
|---|---|---|---|
| **Poussée** (Thrust) | T | Vers le haut (direction du vol) | Moteur, réaction des gaz d'échappement |
| **Poids** (Weight) | W | Vers le bas (centre de gravité) | Gravité terrestre, masse du véhicule |
| **Traînée** (Drag) | D | Opposée à la direction du mouvement | Frottement de l'air sur la surface |
| **Portance** (Lift) | L | Perpendiculaire à la direction du mouvement | Différence de pression sur les surfaces aérodynamiques |

> [!info]
> La portance est généralement négligeable pour une fusée en vol vertical. Elle devient importante lors du vol à angle d'attaque (weathercocking) ou pour les planeurs-fusées.

### Lois de Newton en contexte

- **1ère loi** : une fusée en mouvement reste en mouvement (inertie) — c'est le principe du coast phase après extinction du moteur
- **2ème loi** : F = ma — la poussée du moteur doit vaincre le poids et la traînée pour accélérer la fusée
- **3ème loi** : les gaz d'échappement poussent vers le bas, la fusée monte vers le haut

---

## Rapport poussée/poids (TWR — Thrust-to-Weight Ratio)

### Définition

$$
\text{TWR} = \frac{T}{m \times g}
$$

Où :
- T = poussée moyenne du moteur (N)
- m = masse totale au décollage (kg)
- g = gravité terrestre (9,81 m/s²)

### Valeurs recommandées

| TWR            | Conséquence                                   | Recommandation                             |
| -------------- | --------------------------------------------- | ------------------------------------------ |
| < 3:1          | Fusée ne s'élève pas clairement.              | Trop faible — changer de moteur            |
| 3:1 - 5:1      | Montée acceptable mais lente                  | Acceptable pour les débutants              |
| **5:1 - 10:1** | **Zone optimale** — bonne montée, contrôlable | **Recommandé pour la plupart des projets** |
| 10:1 - 15:1    | Montée rapide, stress structurel              | Acceptable si la structure est conçue pour |
| > 15:1         | Risque de dommages structurels, flambage      | Trop élevé — réduire la poussée            |

> [!warning]
> Un TWR trop faible est souvent plus dangereux qu'un TWR élevé. Une fusée qui monte lentement est sujette au weathercocking (dérive vers le vent) et peut devenir instable.

### Comment calculer

1. Trouver la poussée moyenne du moteur dans les données du fabricant
2. Peser la fusée complète (carburant inclus)
3. Diviser la poussée par (masse × 9,81)

**Exemple** : Fusée de 2 kg avec un moteur Aerotech L1295 (poussée moyenne ~4000 N)
TWR = 4000 / (2 × 9,81) = **203:1** — fusée très performante

---

## Stabilité — CG vs CP

### Définitions

**Centre de gravité (CG — Center of Gravity)**
- Point d'équilibre de la fusée — l'endroit où elle "pend" si on la suspend par une ficelle
- Déterminé par la distribution de masse (moteur, propergol, avionique, structure)
- Se déplace vers l'arrière à mesure que le propergol brûle

**Centre de pression (CP — Center of Pressure)**
- Point où les forces aérodynamiques sont concentrées
- Déterminé par la géométrie de la fusée (nez, corps, ailettes)
- Reste relativement fixe pendant le vol

### Marge de stabilité

La marge de stabilité est la distance entre le CG et le CP, exprimée en **calibres** (multiples du diamètre du corps).

$$
\text{Marge} = \frac{\text{CG} - \text{CP}}{d}
$$

Où d = diamètre du corps (calibre).

| Marge | Statut | Comportement |
|---|---|---|
| < 0 | **Instable** | La fusée tourne (tumbling), dangereuse |
| 0 - 0,5 cal | Marginale | Oscillations, vol imprévisible |
| **1 - 2 cal** | **Optimale** | Vol stable, bonnes performances |
| 2 - 3 cal | Stable | Possible weathercocking |
| > 3 cal | **Trop stable** | Weathercocking sévère, perte d'altitude |

> [!info]
> La règle d'or en rocketry amateur : le CG doit être au moins **1 calibre** (1 diamètre) devant le CP. Pour les compétitions IREC, 1,5 à 2 calibres est souvent visé.

### Équations de Barrowman

Les équations de Barrowman permettent de calculer approximativement la position du CP en fonction de la géométrie de la fusée. Elles prennent en compte :

- La contribution du nez (nosecone)
- La contribution des ailettes (fins)
- La contribution du corps (body tube)

> [!info]
> Les équations de Barrowman sont une approximation valable en vol subsonique. Pour des vitesses supersoniques, des méthodes CFD (Computational Fluid Dynamics) sont nécessaires. Voir les ressources externes pour le calcul détaillé.

### Comment déplacer le CG

- **Ajouter du poids dans le nez** — la méthode la plus simple et la plus courante
- Déplacer les batteries ou l'avionique vers l'avant
- Utiliser un nez en matériau plus dense

### Comment déplacer le CP

- **Augmenter la taille des ailettes** — déplace le CP vers l'arrière
- Modifier la forme des ailettes (plus de surface = plus de portance)
- Ajouter des ailettes supplémentaires (non conventionnel)

---

## Aérodynamique

### Coefficient de traînée (Cd) et types de traînée

La traînée totale est la somme de plusieurs composantes :

| Type de traînée | Origine | Réduction |
|---|---|---|
| **Pressure drag** | Différence de pression avant/après la fusée | Forme aérodynamique, nez effilé |
| **Friction drag** | Frottement de l'air sur la surface | Surface lisse, finition soignée |
| **Base drag** | Dépression à l'arrière (queue) | Boat tail, forme effilée |
| **Interference drag** | Interactions entre composants (ailettes/corps) | Finition des jonctions, fillets |

> [!info]
> Pour une fuséetypique, le Cd varie entre 0,3 et 0,7 selon la vitesse et la géométrie. Le Cd n'est pas constant — il varie avec le nombre de Mach.

### Formes d'ailettes (Fin shapes)

| Forme | Avantages | Inconvénients | Utilisation |
|---|---|---|---|
| **Clipped delta** | Bon compromis stabilité/traînée, simple à fabriquer | — | Le plus courant en HPR |
| **Trapezoidal** | Bonnes performances, surface optimisée | Complexité de fabrication | Compétition |
| **Swept** | Réduit la traînée à haute vitesse | Moins de stabilité à basse vitesse | Vol supersonique |
| **Elliptical** | Traînée minimale théorique | Difficile à fabriquer | Recherche |

### Flapping des ailettes (Fin flutter)

Le fin flutter est une vibration aérodynamique destructive qui se produit lorsqu'une onde de choc ou une pression excessive fait fléchir les ailettes. Pour le prévenir :

- **Épaisseur minimale** : les ailettes doivent être assez épaisses pour résister aux forces aérodynamiques
- **Matériau** : le carburant offre la meilleure rigidité, suivi de la fiberglass, puis du plywood
- **Geometric** : les ailettes avec un bord d'attaque effilé sont moins sujettes au flutter

> [!warning]
> Le fin flutter peut détruire les ailettes en vol, causant la perte totale du véhicule. Pour les vols supersoniques, les ailettes en carburant ou fiberglass sont fortement recommandées.

### Formes de nez (Nosecone shapes)

| Forme | Description | Performance | Utilisation |
|---|---|---|---|
| **Ogive** | Courbure tangentielle au corps | Bonne | Le plus courant |
| **Von Kármán** | Forme optimale pour le supersonique | Excellente | Vol supersonique, compétition |
| **Conical** | Forme conique droite | Moyenne | Simple à fabriquer |
| **Parabolic** | Forme parabolique | Bonne | Alternative à l'ogive |
| **Blunt** | Nez arrondi | Médiocre | Payloads, pas de vol rapide |

### Ratio de finesse (Fineness ratio)

Le ratio de finesse est le rapport longueur/diamètre du corps de la fusée.

- **Faible (< 10)** : fusée courte et large, plus stable mais plus traînante
- **Optimal (15-25)** : bon compromis stabilité/traînée
- **Élevé (> 30)** : fusée longue et fine, bonnes performances mais risque de flambage

### Boat tail

Le boat tail est un rétrécissement conique à l'arrière de la fusée. Il réduit la **base drag** en diminuant la zone de dépression à l'arrière.

- Réduction de traînée de 10-20%
- Angle optimal : 7-15 degrés
- Se justifie surtout pour les vols à haute vitesse

---

## Régimes de vitesse

| Régime | Nombre de Mach | Caractéristiques |
|---|---|---|
| **Subsonic** | < 0,8 | Aérodynamique classique, Cd relativement constant |
| **Transsonic** | 0,8 - 1,2 | Zone de instabilité, onde de choc partielle, "transonic shimmy" |
| **Supersonic** | 1,2 - 5 | Onde de choc complète, Cd augmente puis diminue, shock diamonds |
| **Hypersonic** | > 5 | Ionisation de l'air, chauffage extrême, plasma |

> [!warning]
> La zone transsonique est la plus dangereuse pour les fusées amateurs. Les forces aérodynamiques changent de manière imprévisible, et les ailettes peuvent subir des charges inattendues. La plupart des fusées amateur devraient rester en subsonique pour des raisons de sécurité.

---

## Mécanique de vol

### Phases d'un vol type

1. **Ignition et montée sous poussée** (powered flight) : le moteur brûle, la fusée accélère
2. **Burnout** : extinction du moteur, début du coast phase
3. **Coast phase** : la fusée continue à monter par inertie, décélérant sous l'effet de la gravité
4. **Apogée** : point le plus haut du vol, vitesse minimale (idéalement nulle verticalement)
5. **Descente** : déploiement du parachute, atterrissage

### Profil de poussée (Thrust profile)

Le profil de poussée dépend de la configuration du grain et du type de propergol :

- **Neutre** : poussée constante pendant toute la durée de combustion (BATES)
- **Progressif** : poussée augmente (finocyl)
- **Régressif** : poussée diminue (C-slot)

> [!info]
> Le profil de poussée influence la vitesse de sortie du rail. Un profil progressif avec un pic initial est souvent préférable pour atteindre rapidement une vitesse stable.

### Dynamic pressure (Max-Q)

Le dynamic pressure q est défini comme :

$$
q = \frac{1}{2} \rho v^2
$$

Où ρ est la densité de l'air et v la vitesse. Le **Max-Q** est le point où q est maximal — c'est la charge structurelle maximale sur la fusée.

- Se produit généralement pendant la phase de poussée
- Les structures doivent être conçues pour résister à Max-Q avec une marge de sécurité

### Vitesse de sortie du rail

La fusée doit atteindre une vitesse suffisante au moment où elle quitte le rail de lancement pour être aérodynamiquement stable.

| Vitesse | Qualité | Recommandation |
|---|---|---|
| < 10 m/s | Insuffisante | Risque de weathercocking sévère |
| **15 - 25 m/s** | **Optimale** | **Recommandé pour la plupart des projets** |
| > 25 m/s | Excellente | Bon pour les vols à haute performance |

> [!info]
> La règle empirique : la vitesse de sortie du rail doit être au moins **5 fois la vitesse du vent** pour maintenir la stabilité.

---

## Calculs de base — Tableau de référence

| Formule | Expression | Description |
|---|---|---|
| **TWR** | T / (m × g) | Rapport poussée/poids |
| **Marge de stabilité** | (CG - CP) / d | Distance CG-CP en calibres |
| **Vitesse de sortie du rail** | v = √(2 × (T - W) × L / m) | L = longueur du rail |
| **Force de traînée** | D = 0,5 × ρ × v² × Cd × A | A = surface de référence |
| **Dynamic pressure** | q = 0,5 × ρ × v² | Pression dynamique |
| **Vitesse terminale** | v_t = √(2mg / (ρ × Cd × A)) | Vitesse maximale en chute libre |
| **Impulse** | I = ∫ T dt | Aire sous la courbe de poussée |
| **Isp** | Isp = T / (ṁ × g₀) | Impulse spécifique |

> [!info]
> Pour les calculs de trajectoire complets, utilisez des logiciels dédiés comme **OpenRocket**, **RASAero**, ou **RockSim**. Ces outils modélisent l'ensemble des forces et prédisent la hauteur d'apogée, la vitesse maximale, et la position du CP.
