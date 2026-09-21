# Anatomie d'une fusée

> [!info]
> Comprendre l'anatomie d'une fusée est la première étape pour concevoir, construire et maintenir un véhicule de launch. Ce page détaille chaque composant majeur d'une fusée de rocketry amateur, des ailettes au nez.

---

## Vue d'ensemble

Voici une représentation simplifiée d'une fusée de haute puissance à double déploiement (dual-deployment) :

```
┌─────────────┐
│   Nosecone   │ ← Nez aérodynamique + logement payload
│─────────────│
│   Payload    │ ← Section charge utile (si applicable)
│─────────────│
│  Parachute   │ ← Parachute principal (main)
│   (main)     │
│─────────────│
│   E-bay      │ ← Baie avionique (altimètres, GPS, batteries)
│─────────────│
│  Parachute   │ ← Drogue (petit parachute)
│  (drogue)    │
│─────────────│
│ Motor Mount  │ ← Tube moteur + centering rings
│─────────────│
│   Fins       │ ← Ailettes de stabilisation
│─────────────│
│  Boat tail   │ ← Rétrécissement arrière (optionnel)
└─────────────┘
```

Les composants sont intégrés dans le **body tube** (corps) qui constitue la structure principale. Chaque section a un rôle précis, et leur intégration doit être soignée pour garantir la sécurité et la performance.
![[structure1.png]]
![[structure2.png]]
---

## Nez (Nosecone)

### Rôle

Le nez est la première surface aérodynamique que l'air rencontre. Son rôle est double :
1. **Réduire la traînée** en guidant l'air autour de la fusée
2. **Loger la charge utile** (payload) : altimètres, capteurs, caméras

### Types de nez

| Forme | Description | Performance | Difficulté de fabrication |
|---|---|---|---|
| **Ogive** | Courbe tangentielle au corps | Bonne en subsonique | Moyenne |
| **Von Kármán** | Forme mathématiquement optimale | Excellente en supersonique | Élevée |
| **Conical** | Forme conique droite | Moyenne | Facile |
| **Parabolic** | Courbe parabolique | Bonne | Moyenne |
| **Blunt** | Nez arrondi | Médiocre | Très facile |

### Composants du nez

- **Shoulder** : partie cylindrique qui s'insère dans le body tube — assure l'alignement et la connexion
- **Bulkhead** : paroi séparatrice qui isole le payload des gaz d'éjection
- **Payload bay** : espace réservé pour les instruments — calculer le volume nécessaire avant de choisir le nez

> [!info]
> Le shoulder doit être suffisamment long (≥ 1 diamètre) pour assurer une connexion stable. Un shoulder trop court peut provoquer un décollement en vol.

---

## Corps (Airframe)

### Tube de corps (Body tube)

Le body tube constitue la structure principale. Il relie toutes les sections et fournit la surface aérodynamique de base.

#### Matériaux

| Matériau | Avantages | Inconvénients | Utilisation |
|---|---|---|---|
| **Cardboard** | Léger, pas cher, facile à couper | Fragile, sensible à l'humidité | Model rocketry, débutants |
| **Phenolic** | Résistant, bonne finition | Fragile, cassant | Mid-power, début HPR |
| **Fiberglass** | Très résistant, durable, imperméable | Lourd, coûteux | HPR, compétition |
| **Carbon fiber** | Extrêmement résistant, très léger | Très coûteux, fragile aux impacts | Compétition, records |

### Conventions de diamètre

| Désignation | Diamètre (mm) | Utilisation typique |
|---|---|---|
| BT-20 | 18 | Model rocketry (Estes) |
| BT-50 | 29 | Model rocketry, mid-power |
| BT-60 | 54 | Mid-power, début HPR |
| 4" | 102 | HPR standard, compétition |
| 5,4" | 137 | HPR moyen, payload |
| 7,5" | 190 | Grand HPR, rockets scientifiques |

### Couplers (Raccords)

Les couplers sont des tubes de diamètre légèrement inférieur qui relient deux sections de body tube. Ils sont essentiels pour :
- Joindre les sections de la fusée
- Maintenir l'alignement
- Permettre la séparation pour le déploiement du parachute

> [!warning]
> Les couplers doivent être collés avec de la époxy structurale (pas de cyanoacrylate). Un coupler mal collé peut se séparer en vol sous la force de l'éjection.

---

## Baie avionique (E-bay)

### Rôle

La E-bay (avionics bay) est le cerveau de la fusée. Elle contient tous les systèmes électroniques nécessaires au vol sécuritaire et à la récupération.

### Composants typiques

| Composant | Rôle | Notes |
|---|---|---|
| **Altimètre** | Mesure l'altitude et déclenche le déploiement | Au moins 2 pour la redondance |
| **GPS tracker** | Localisation en temps réel | Essentiel pour la récupération |
| **Flight computer** | Enregistrement des données, contrôle des systèmes | RocketJS, PerfectFlite, Clover |
| **Batteries** | Alimentation électrique | Lithium-ion ou lithium-polymer |
| **Wiring** | Connexions entre composants | Fil AWG 22-26, soudure de qualité |
| **Antenna** | Émission de données GPS/radio | Placement critique pour la réception |

### Montage sur sled

Le **sled** (patin) est un plateau qui maintient les composants électroniques en place. Il est généralement fabriqué en plywood ou en plastique et est fixé entre les deux bulkheads.

### Bulkheads avec eye bolts

Les bulkheads sont des disques (plywood, fiberglass, ou carbon fiber) qui ferment les deux extrémités de la E-bay. Chaque bulkhead est équipé :
- D'un **eye bolt** pour attacher le harnais et le shock cord
- De trous pour le passage du fil de l'allumeur
- D'unJoint torique (O-ring) pour l'étanchéité

### Shear pins

Les shear pins sont des épingles en nylon qui maintiennent les sections assemblées pendant la montée. Ils sont conçus pour se casser sous la force des charges d'éjection, permettant la séparation.

> [!info]
> Utiliser des shear pins de la bonne taille : trop épais = ne cassent pas = pas de déploiement ; trop fins = cassent prématurément = séparation en vol. Pour un 4", commencer avec des épingles de 2 mm.

### Câblage et placement des antennes

- Les fils doivent être suffisamment longs pour permettre la séparation sans tension
- Les antennes GPS doivent être orientées vers le ciel (pas de blindage par le carburant)
- Utiliser du fil hauteflexibilité (silicone-coated) pour résister aux vibrations

---

## Ailettes (Fins)

### Rôle

Les ailettes assurent la **stabilité aérodynamique** de la fusée. Elles déplacent le centre de pression (CP) vers l'arrière, assurant que le CG reste devant le CP.

### Techniques de montage

| Méthode | Description | Avantages | Inconvénients |
|---|---|---|---|
| **Through-the-wall** | L'ailette traverse le body tube et se fixe au motor mount | Très résistant, transfert de charge | Plus complexe à fabriquer |
| **Surface mount** | L'ailette est collée directement sur le body tube | Simple | Moins résistant, dépend de la colle |

### Centering rings

Les centering rings maintiennent le motor mount tube centré dans le body tube. Ils sont généralement en plywood ou fiberglass et sont fixés avec de la époxy.

### Matériaux des ailettes

| Matériau | Épaisseur typique | Résistance | Utilisation |
|---|---|---|---|
| **Plywood** | 3-6 mm | Moyenne | Mid-power, HPR débutant |
| **Fiberglass** | 1,5-3 mm | Élevée | HPR, compétition |
| **Carbon fiber** | 1-2 mm | Très élevée | Compétition, supersonique |

> [!warning]
> L'alignement des ailettes est critique. Une ailette mal alignée provoque une rotation de la fusée en vol, réduisant les performances et pouvant causer l'instabilité. Utiliser un jig d'alignement.

---

## Propulsion (Motor mount)

### Tube moteur (Motor mount tube)

Le tube moteur est le composant qui contient le moteur. Il est centré dans le body tube par les centering rings.

### Retenue de moteur (Motor retainer)

| Type | Description | Avantages |
|---|---|---|
| **Aeropack retainer** | Bague vissée sur l'arrière du motor mount | Standard de l'industrie, fiable |
| **Threaded retainer** | Bague à vis | Bonne retention, facile à utiliser |
| ** friction fit** | Le moteur est maintenu par friction | Simple mais moins fiable |

### Motor tube centering

Le tube moteur doit être parfaitement centré et aligné avec l'axe de la fusée. Les centering rings avant et arrière assurent cette concentricité.

### Motor block (Buttée de moteur)

Le motor block empêche le moteur de glisser vers l'avant sous la poussée. Il est généralement un anneau de bois ou de métal collé à l'intérieur du motor mount tube.

---

## Recovery (Récupération)

### Points de montage

Les points de fixation du système de récupération sont les **eye bolts** vissés dans les bulkheads de la E-bay. Ils doivent supporter les forces de déploiement (parachute + choc).

### Shock cord (Câble de choc)

Le shock cord absorbe le choc du déploiement du parachute. Il est généralement attaché entre le eye bolt du bulkhead et le parachute.

| Matériau | Avantages | Inconvénients |
|---|---|---|
| **Kevlar** | Résistant à la chaleur, très résistant | Rigide, moins d'élasticité |
| **Tubular nylon** | Élastique, absorbe bien le choc | Sensible à la chaleur |

### Harness / Bridle

Le harnais relie les différents points de fixation (bulkheads, parachute, moteur). Il distribue les forces de déploiement sur la structure.

### Mécanisme de déploiement

Le déploiement est déclenché par des **charges de poudre noire** qui gonflent les compartiments et poussent les parachutes à l'extérieur. Voir le chapitre sur les systèmes de récupération pour les détails.

---

## Queue (Boat tail / Aft section)

### Boat tail

Le boat tail est un rétrécissement conique à l'arrière de la fusée. Il réduit la **base drag** en diminuant la zone de dépression derrière la fusée.

- Angle optimal : 7-15 degrés
- Réduction de traînée : 10-20%
- Se justifie pour les vols à haute vitesse

### Rail buttons

Les rail buttons sont des saillies sur le corps de la fusée qui s'insèrent dans les rails de lancement. Ils maintiennent la fusée alignée pendant la montée sur le rail.

> [!info]
> Placer les rail buttons au centre de gravité et au centre de pression pour un alignement optimal. Deux buttons suffisent généralement.

### Aft closure

La fermeture arrière protège le moteur et les composants internes. Elle peut être intégrée au boat tail ou être un composant séparé.

---

## Schémas de cas types

### 1. Fusée simple monostade (Model rocket)

```
┌──────────┐
│ Nosecone  │
│──────────│
│ Body tube│
│──────────│
│  Engine  │ ← Moteur poudre noire (Estes)
│──────────│
│   Fins   │ ← 3-4 ailettes
└──────────┘
```

- Récupération : parachute simple ou streamer
- Alimentation : batterie miniature ou inertie
- Utilisation : model rocketry, éducation

### 2. Fusée mid-power à déploiement simple

```
┌──────────┐
│ Nosecone  │
│──────────│
│ Payload  │ ← Capteurs, caméra
│──────────│
│ Parachute│ ← Parachute unique
│──────────│
│ Body tube│
│──────────│
│  Fins    │
│──────────│
│  Motor   │ ← Moteur rechargeable (Aerotech RMS)
└──────────┘
```

- Récupération : parachute simple, déploiement à l'apogée
- Alimentation : altimètre unique + batterie
- Utilisation : HPR niveau 1, vol scientifique

### 3. Fusée HPR à double déploiement avec E-bay

```
┌──────────┐
│ Nosecone  │
│──────────│
│ Payload  │ ← Instruments scientifiques
│──────────│
│  Main    │ ← Parachute principal (60")
│──────────│
│  E-bay   │ ← 2 altimètres, GPS, batteries
│──────────│
│  Drogue  │ ← Drogue (12")
│──────────│
│Body tube │
│──────────│
│  Fins    │ ← Ailettes through-the-wall
│──────────│
│  Motor   │ ← Moteur grande impulsion (L-N)
│──────────│
│Boat tail │
└──────────┘
```

- Récupération : dual-deployment, drogue à l'apogée, main à 300 m
- Alimentation : 2 altimètres redondants, 2 batteries
- Utilisation : compétition IREC, vols scientifiques

> [!info]
> La configuration dual-deployment est le standard pour les fusées de haute puissance. Elle minimise la dérive latérale en limitant le temps de descente sous le parachute principal.
