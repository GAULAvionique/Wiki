# Systèmes de récupération

> [!info]
> Le système de récupération est le système le plus critique après le moteur. Une fusée sans récupération efficace est une fusée perdue — ou pire, un danger pour les personnes et les biens. Ce page couvre les différents types de récupération, les mécanismes de déploiement, et les bonnes pratiques.

---

## Introduction

La récupération a pour objectif de ramener la fusée au sol de manière contrôlée et sécuritaire, en limitant la vitesse d'atterrissage et la dérive latérale.

| Méthode | Description | Utilisation | Vitesse d'atterrissage |
|---|---|---|---|
| **Parachute** | Surface aérodynamique qui freine la chute | HPR, compétition | < 5 m/s |
| **Streamer** | Ruban plastique/mylar qui augmente la traînée | Model rocketry, basse puissance | 5-15 m/s |
| **Tumble** | Instabilité délibérée, haute traînée | Model rocketry, très basse puissance | 10-20 m/s |
| **Planeur** (Glider) | La fusée vole comme un planeur après le boost | Planeurs-fusées | Variable |
| **Balistique** | Retour sans parachute (ultra-light) | Micro rocketry | > 20 m/s |

> [!warning]
> La récupération balistique (sans parachute) n'est acceptable que pour les très petites fusées. Pour tout véhicule de plus de 500 g, un système de récupération est obligatoire.

---

## Dual-deployment (Standard HPR)

### Le standard de la haute puissance

Le **dual-deployment** est le système de récupération standard pour les fusées de haute puissance. Il utilise deux parachutes déployés à des moments différents pour optimiser la descente.

### Séquence de déploiement

1. **Allumage** : le moteur brûle, la fusée monte
2. **Burnout** : extinction du moteur, début du coast phase
3. **Apogée** : la fusée atteint son point le plus haut
4. **Drogue deployment** : le drogue est déployé à l'apogée — freine la descente sans trop de surface
5. **Descente sous drogue** : descente contrôlée à 20-40 m/s
6. **Main deployment** : à une altitude prédétablie (généralement 200-300 m), le parachute principal est déployé
7. **Descente sous main** : descente lente à < 11 m/s
8. **Atterrissage** : contact au sol à vitesse sécuritaire

### Drogue vs Main

| Paramètre | Drogue | Main (Principal) |
|---|---|---|
| **Taille** | Petit (12-24") | Grand (48-120") |
| **But** | Freiner la descente initiale | Atterrissage doux |
| **Vitesse de descente** | 20-40 m/s | < 11 m/s |
| **Déploiement** | À l'apogée | À altitude prédétablie |
| **Durée de vie** | Tout le vol de descente | Dernière phase |

### Configuration type (fusée 4", 6-7 lb)

| Composant | Taille | Quantité |
|---|---|---|
| Drogue | 12" (spherical ou ribless) | 1 |
| Main | 60" (elliptical ou toroidal) | 1 |
| Altimètre | Anywell EggFinder, PerfectFlite | 2 |
| Batterie | LiPo 9V ou 3,7V | 2 |
| E-match | Talon, MJG | 2 |
| Charge ejection | Poudre noire FFFfg | 1-3 g par charge |

> [!info]
> La redondance est essentielle. Deux altimètres indépendants, deux batteries, deux charges d'éjection. Si un système échoue, l'autre assure le déploiement.

### Règles de calcul

**Taille du drogue** :
- Règle empirique : 1 pouce de diamètre par livre de masse (1" par 0,45 kg)
- Pour 6 lb : drogue de 12" avec un Cd de ~1,5
- Vitesse de descente sous drogue : 25-35 m/s

**Taille du main** :
- Pour une vitesse d'atterrissage < 5 m/s : surface = (2 × poids × g) / (ρ × Cd × v²)
- Pour 6 lb (2,7 kg), Cd ~1,4 : ~60" de diamètre

**Calcul de la charge de poudre noire** :
- Volume du compartiment × pression requise (0,5-1,0 bar)
- Pour un 4" : ~1/4 tsp (1,5 g) de FFFfg
- Ajuster par essai (static fire test)

---

## Drogueless recovery

### Principe

Pas de drogue déployé à l'apogée. La fusée repose uniquement sur la traînée de l'airframe pour freiner la descente.

### Avantages

- **Simplicité** : pas de mécanisme de séparation nécessaire
- **Fiabilité** : moins de composants = moins de risques
- **Coût** : pas de drogue, pas de charge d'éjection supplémentaire

### Inconvénients

- **Descente plus longue** : la traînée de l'airframe est faible, la descente est lente
- **Dérive** : plus de temps dans l'air = plus de dérive latérale sous le vent
- **Pas de contrôle** : la descente n'est pas active

### Quand l'utiliser

- Vols < 1000 m d'apogée
- Fusées légères (< 1 kg)
- Environnement vent faible
- Compétitions où la simplicité est valorisée

---

## Tumble recovery

### Principe

La fusée est délibérément rendue instable après le burnout. L'instabilité provoque une rotation qui augmente considérablement la traînée, freinant la chute.

### Avantages

- Aucun mécanisme mobile
- Aucune énergie requise
- Simple à mettre en place

### Inconvénients

- **Risque d'atterrissage sur le nez** : la fusée peut atterrir pointe en bas
- **Vitesse d'atterrissage élevée** : peut endommager la fusée
- **Pas de contrôle** : la trajectoire de descente est imprévisible

> [!info]
> Le tumble recovery est couramment utilisé dans les model rockets avec un moteur à retard. Le déploiement du parachute est déclenché par la charge de retard du moteur.

---

## Streamer

### Principe

Un ruban de plastique ou de mylar est attaché à la fusée. Il déploie en vol, augmentant la traînée et réduisant la vitesse de descente.

### Caractéristiques

| Paramètre | Valeur |
|---|---|
| Matériau | Mylar, polyéthylène |
| Longueur | 30-100 cm |
| Largeur | 2-5 cm |
| Masse | < 10 g |
| Vitesse de descente | 5-15 m/s |

### Avantages

- Léger, ne pénalise pas la hauteur
- Simple, pas de mécanisme
- Moins de dérive qu'un free-flight

### Inconvénients

- Vitesse d'atterrissage plus élevée qu'un parachute
- Pas adapté aux fusées lourdes
- Le streamer peut se tordre et perdre son efficacité

---

## Planeurs-fusées (Rocket Gliders)

### Concept

Un planeur-fusée (boost-glider) est un véhicule qui monte sous propulsion puis plane pour atterrir. La phase de vol se divise en deux : boost (fusée) et glide (planeur).

### Variantes

| Type | Position du moteur | Comportement |
|---|---|---|
| **Front-engine** | Moteur à l'avant | Montée verticale, plane vers l'avant |
| **Rear-engine** | Moteur à l'arrière | Montée verticale, plane vers l'arrière |
| **Pop-pod** | Moteur dans un pod amovible | Pod se détache, la fusée plane |

> [!info]
> Les planeurs-fusées sont une excellente façon d'apprendre l'aérodynamique et les principes de vol. Ils sont souvent utilisés dans les concours de model rocketry.

---

## Mécanismes de déploiement

### Poudre noire (Black powder charges)

La méthode la plus courante pour le déploiement des parachutes.

| Paramètre | Recommandation |
|---|---|
| Type | FFFfg (très fin, grain fin) |
| Quantité initiale | 1/4 tsp (~1,5 g) pour un tube 4" |
| Conteneur | Capsule de déploiement (deployment cap) |
| Allumage | E-match, courant > 500 mA |

#### Calcul de la charge

1. Mesurer le volume du compartiment à pressuriser
2. Viser une pression de 0,5-1,0 bar (7-15 psi)
3. Utiliser la formule : masse = (pression × volume) / (constante du propergol)
4. Ajuster par essai en static fire

> [!warning]
> Trop de poudre noire = dommages à la structure, coupe des shock cords, déchire les parachutes. Pas assez = pas de déploiement. Toujours tester avant le vol.

### Déploiement CO2

| Paramètre | Description |
|---|---|
| Principe | Cartouche CO2 percée par un mécanisme pyrotechnique |
| Avantages | Plus constant que la poudre noire, pas de flamme |
| Inconvénients | Plus lourd, plus coûteux, cartouche jetable |
| Utilisation | Compétition, systèmes critiques |

### Shear pins (Épingles de cisaillement)

Les shear pins maintiennent les sections assemblées pendant la montée. Ils sont conçus pour se casser sous la force des charges d'éjection.

| Matériau | Diamètre | Force de rupture | Utilisation |
|---|---|---|---|
| **Nylon** | 1-3 mm | 10-50 N | Standard pour HPR |
| **Plastic** | 1-2 mm | 5-30 N | Model rocketry |

> [!info]
> Utiliser exactement le même nombre et type de shear pins à chaque vol. Un shear pin manquant = séparation précoce ; un shear pin en trop = pas de séparation.

### Conteneur de charge d'éjection (Ejection charge containment)

La charge de poudre noire doit être contenue dans un espace clos pour développer la pression nécessaire au déploiement. Les **deployment caps** (bouchons de déploiement) assurent cette étanchéité.

---

## Line cutters

### Principe

Un line cutter est un mécanisme qui coupe une corde de rétention pour libérer un parachute replié. Il est utilisé dans les systèmes dual-deployment où le main est maintenu replié pendant la descente sous drogue.

### Quand l'utiliser

- Dual-deployment avec main replié
- Air-start (allumage en vol)
- Systèmes où le déploiement doit être retardé

### Types

| Type | Description | Avantages | Inconvénients |
|---|---|---|---|
| **Mécanique** | Ressort + lame, déclenché par timer | Pas de pyrotechnique | Moins fiable |
| **Pyrotechnique** | Petite charge qui coupe la corde | Fiable, rapide | Pyrotechnique, maintenance |

---

## Harnais et câbles de choc (Harness and shock cords)

### Matériaux

| Matériau | Résistance | Élasticité | Résistance chaleur | Utilisation |
|---|---|---|---|---|
| **Kevlar** | Très élevée | Faible | Excellente | HPR, charges d'éjection |
| **Tubular nylon** | Élevée | Élevée | Moyenne | Harnais principal, absorption de choc |
| **Dacron** | Élevée | Moyenne | Bonne | Alternative au nylon |

### Longueur

- **Shock cord** : 3-5 fois la longueur de la fusée
- **Harness** : dépend de la configuration, mais suffisant pour permettre la séparation complète

> [!info]
> Un shock cord trop court = le parachute s'ouvre trop près de la fusée, risque de dommages. Un shock cord trop long = enroulement, risque de nœuds.

---

## Protection des charges de déploiement

Les charges de poudre noire produisent des flammes et des particules chaudes qui peuvent endommager les parachutes et les cords. La protection est essentielle.

| Méthode | Description | Efficacité |
|---|---|---|
| **Dog barf / cellulose wadding** | Papier de soie ou cellulose placé sur la charge | Bonne, standard |
| **Protect-a-Pak** | Capsule en fibreglass qui contient la charge | Excellente |
| **Piston deployment** | Un piston pousse le parachute hors du tube | Excellente |
| **Nomex blankets** | Couverture en Nomex placée sur le parachute | Bonne |

> [!warning]
> Ne jamais utiliser de papier journal comme protection — il peut prendre feu. Utiliser uniquement des matériaux ignifugés (Nomex, cellulose traitée).

---

## Récupération en milieu difficile

### Eau

- **Action immédiate** : récupérer la fusée le plus rapidement possible
- **Risque** : court-circuits, dommages aux électroniques, corrosion
- **Prévention** : étanchéité des compartiments électroniques, sacs étanches
- **Après** : séchage complet avant de reconnecter les batteries

### Arbres

- **Perche télescopique** : pour les branches accessibles (< 10 m)
- **Fronde + ligne de pêche** : lancer un poids au-dessus de la branche, tirer la fusée
- **Arboriste** : en dernier recours, faire appel à un professionnel
- **JAMAIS** : grimper soi-même si le risque est élevé
- **Au pire** : Couper l'arbre (et rien dire)

### Falaises et terrains escarpés

- **GPS tracking** : savoir exactement où atterrit la fusée
- **Drones** : repérage aérien pour localiser la fusée
- **Coordination radio** : maintenir le contact avec l'équipe au sol

### Lignes électriques

> [!danger]
> Ne JAMAIS tenter de récupérer une fusée accrochée aux lignes électriques. Contacter le service d'urgence de la compagnie d'électricité. Le courant peut être mortel, même sans contact direct.

### Coordination terrain

- **Radio** : maintain le contact avec le range control et l'équipe
- **GPS** : tracker en temps réel (eg. Featherweight, EggFinder)
- **Plans** : connaître le terrain, les accès, les obstacles
- **Vent** : calculer la dérive prévisible avant le lancement

---

## Récapitulatif — Sélection du système de récupération

| Critère | Simple parachute | Dual-deployment | Drogueless | Tumble | Streamer |
|---|---|---|---|---|---|
| Complexité | Faible | Élevée | Faible | Très faible | Très faible |
| Coût | Faible | Moyen | Faible | Nul | Nul |
| Contrôle de descente | Bon | Excellent | Moyen | Faible | Faible |
| Adapté HPR | Oui | Oui (standard) | Non | Non | Non |
| Risque de perte | Moyen | Faible | Moyen | Élevé | Élevé |
| Dérive | Moyenne | Faible | Élevée | Variable | Variable |
