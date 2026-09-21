# Types de moteurs

> [!info]
> Les moteurs de fusée sont le coeur de tout véhicule de launch. Leur sélection détermine les performances, la durée du vol, et la complexité du projet. Ce page couvre les trois grandes familles de moteurs utilisées en rocketry amateur et compétition.

---

## Introduction

Le moteur est le composant qui transforme l'énergie chimique en poussée. La classification fondamentale repose sur l'état de l'ergol :

| Type | Ergol solide | Ergol liquide | Hybride |
|---|---|---|---|
| Principe | Grain solide qui brûle | Deux ergols liquides injectés | Carburant solide + oxydant liquide |
| Complexité | Faible | Élevée | Moyenne |
| Réutilisation | Variable | Oui | Oui |
| Performance | Bonne à excellente | Excellente | Moyenne |

Les moteurs sont aussi classés par leur **impulse totale**, de la classe A (0-2,5 N·s) jusqu'à la classe O (et au-delà pour les moteurs expérimentaux). Chaque lettre représente une plage d'impulse exactement double de la précédente.

---

## Moteurs solides

### Principe de fonctionnement

Un moteur solide contient un **grain de propergol** moulé ou pressé dans un boîtier. Une fois allumé, la surface du grain brûle, produisant des gaz qui s'échappent par une **tuyère** (nozzle) de forme convergente-divergente. La poussée est générée par le principe d'action-réaction de Newton.

> [!info]
> Le propergol solide ne peut pas être arrêté une fois allumé. C'est pourquoi les moteurs solides sont parfois surnommés "des fusées dans des fusées."

### Types de propergol

#### Poudre noire (Black powder)

- Composition : salpêtre (KNO3) ~75%, charbon ~15%, soufre ~10%
- Utilisation : model rocketry, faible puissance
- Moteurs typiques : Estes A8-3, B6-4, C6-5
- Impulse spécifique (Isp) : ~80 s
- Limites : pression de chambre faible, performance plafonnée, tendance à détoner si la granulométrie est mauvaise

#### APCP (Ammonium Perchlorate Composite Propellant)

- Composition : perchlorate d'ammonium (AP) ~68-70%, aluminium ~16-20%, liant HTPB ~10-14%
- Utilisation : high-power rocketry, compétition
- Isp : 200-260 s
- Avantages : haute performance, grains de grande taille possible, combustion stable
- Inconvénients : traitementighazard, coût élevé, explosif si confiné

### Configurations de grains

La forme du grain détermine la courbe de poussée (thrust profile) du moteur.

| Configuration | Description | Profil de poussée |
|---|---|---|
| **BATES** | Grains cylindriques avec perforation centrale, segments séparés | Plate, constante — le plus courant en HPR |
| **Finocyl** | Grain cylindrique avec perforation en forme de F | Progressif, augmentation de surface de combustion |
| **Star** | Perforation en étoile | Dégressif ou neutre selon le nombre de branches |
| **C-slot** | Grain avec une rainure en C | Régressif, surface de combustion diminue |

> [!info]
> La configuration BATES est la plus utilisée dans les moteurs COTS et les propergols SRAD car elle offre un profil de poussée prévisible et facile à modéliser.

### Classes d'impulse

| Classe | Désignation | Impulse totale (N·s) | Utilisation typique                   |
| ------ | ----------- | -------------------- | ------------------------------------- |
| A      | Low Power   | 0 - 2,5              | Model rocketry, premiers vols         |
| B      | Low Power   | 2,5 - 5,0            | Model rocketry, petit gabarit         |
| C      | Low Power   | 5,0 - 10             | Model rocketry, début de range        |
| D      | Mid Power   | 10 - 20              | Mid-power, premiers HPR               |
| E      | Mid Power   | 20 - 40              | Mid-power, payload flights            |
| F      | Mid Power   | 40 - 80              | HPR niveau 1, début compétition       |
| G      | High Power  | 80 - 160             | HPR niveau 1-2                        |
| H      | High Power  | 160 - 320            | HPR niveau 1-2, compétition           |
| I      | High Power  | 320 - 640            | HPR niveau 2, compétition             |
| J      | High Power  | 640 - 1280           | HPR niveau 2, Hautes performances     |
| K      | High Power  | 1280 - 2560          | HPR niveau 2-3                        |
| L      | High Power  | 2560 - 5120          | HPR niveau 3, championnats            |
| M      | High Power  | 5120 - 10240         | HPR niveau 3, véhicules lourds        |
| N      | High Power  | 10240 - 20480        | Grandes fusées, rockets Scientifiques |
| O      | High Power  | 20480 - 40960        | Extrême, recherche avancée            |

> [!info]
> Au-delà de la classe O, les moteurs sont considérés comme "grands moteurs" (CTO - Certificate of Test Organization) et nécessitent des autorisations spéciales.

### Fabricants

| Fabricant | Pays | Spécialité |
|---|---|---|
| **Aerotech** | USA | Large gamme COTS,	reloadable, grain AP |
| **Cesaroni (CTI)** | Canada | ProXX, Igniter, bonne réputation |
| **Estes** | USA | Model rocketry, poudre noire |
| **LinzX** | Europe | Moteurs experiments, high-impulse |
| **Klima** | Rép. Tchèque | Propergol composite, training motors |

### Moteurs rechargeables vs usage unique

**Usage unique (single-use)** :
- Le moteur entier est un seul boîtier non réutilisable
- Exemples : Estes A8-3, Aerotech RMS 29/240
- Avantage : simplicité, pas de maintenance
- Inconvénient : coût à long terme, déchets

**Rechargeable (reloadable)** :
- Le boîtier (casing) est réutilisable
- On insère un nouveau grain + dissociateur + O-rings
- Exemples : Aerotech RMS, CTI Pro38, CTI Pro54
- Avantage : coût réduit par vol, personnalisation
- Inconvénient : maintenance obligatoire, inspection

### Systèmes de retard (Delay charges)

Les moteurs à retard contiennent une charge de **propergol à combustion lente** entre le propergol principal et la charge d'éjection. Elle permet le **coast phase** — le temps entre l'extinction du moteur et le déploiement du parachute.

Exemple : un **C6-5** brûle pendant ~1,6 s, puis a un retard de 5 s avant l'éjection.

> [!warning]
> Un retard trop long signifie que le rocket descend avant le déploiement. Un retard trop court signifie le déploiement sous poussée. Choisir le retard adapté à la hauteur visée.

### Allumeurs (E-matches) et systèmes d'allumage

| Type                         | Description                               | Utilisation      |
| ---------------------------- | ----------------------------------------- | ---------------- |
| **Estes plug-in**            | Connecteur simple, allumage électrique    | Model rocketry   |
| **E-match (MS20004, Talon)** | Allumeur électrique Standardisé           | HPR, pyrotechnic |
| **Bridgewire**               | Fil résistif dans un composition sensible | Moteurs COTS     |

> [!info]
> Les allumeurs électriques fonctionnent par courant. Il faut toujours vérifier la résistance de l'allumeur et s'assurer que la batterie fournit suffisamment de courant pour un allumage fiable.

---

## Moteurs hybrides

### Principe de fonctionnement

Un moteur hybride utilise un **carburant solide** (généralement un plastique comme le HTPB ou l'ABS) et un **oxydant liquide ou gazeux** (le plus souvent du N2O — protoxyde d'azote). L'oxydant est injecté dans la chambre de combustion où il réagit avec le carburant solide.

```
Oxydant liquide (N2O) → injection → chambre de combustion → carburant solide (HTPB/ABS) → gaz d'échappement → tuyère
```

### Paires courantes

| Carburant | Oxydant | Performance | Notes |
|---|---|---|---|
| HTPB | N2O | Bonne | Propergol composite classique, chambre haute pression |
| ABS | N2O | Moyenne | Simpler, bon pour débuter |
| LDPE | N2O | Moyenne | Low-density polyethylene, facile à usiner |
| Paraffine | N2O | Variable | Melt-cast, cherche alternative au HTPB |

### Options commerciales

| Fabricant | Produit | Type | Impulse |
|---|---|---|---|
| **SCRAM** | SCRAM 54 | N2O/ABS | J-K |
| **Contrail** | Contrail H | N2O/HTPB | G-J |
| **Hypertek** | Hypertek J350 | N2O/HTPB | J |
| **LOC/Precision** | LOC Hybrids | N2O/HTPB | F-J |

### Avantages

- **Sécurité de stockage** : le N2O n'est pas un carburant — pas de risque de combustion spontanée
- **Réutilisable** : le boîtier et le carburant solide peuvent être réutilisés
- **Réglable (certains)** : on peut moduler le débit d'oxydant pour varier la poussée
- **Éducation** : excellent pour enseigner les systèmes de propulsion plus avancés

### Inconvénients

- **Complexité** : nécessite un système de injection, valves, réservoir
- **Poids** : le réservoir d'oxydant ajoute de la masse sèche
- **Performance inférieure** : l'Isp est généralement plus basse qu'un moteur solide APCP équivalent
- **Température** : le N2O se stocke sous pression, risque de surge

---

## Moteurs liquides

### Principe de fonctionnement

Un moteur liquide (bipropellant) injecte deux ergols séparés — un **carburant** et un **oxydant** — dans une chambre de combustion. La réaction chimique produit des gaz à haute vitesse qui sont accélérés par la tuyère.

### Types d'ergols bipropellants

| Oxydant | Carburant | Avantages | Inconvénients |
|---|---|---|---|
| **LOX** (oxygène liquide) | Éthanol / IPA | Haute performance, combustion propre | Cryogénique, stockage difficile |
| **N2O** | IPA (isopropanol) | Stockage ambiant, faible coût | Performance moyenne |
| **H2O2** (peroxyde d'hydrogène) | IPA | Pas de danger cryogénique | Décomposition, catalyseur nécessaire |
| **LOX** | Kérosène (RP-1) | Haute densité énergétique | Coke, nettoyage |

### Systèmes d'alimentation (Feed systems)

| Système | Description | Avantages | Inconvénients |
|---|---|---|---|
| **Pressure-fed** | Gaz inerte (hélium) pousse les ergols dans la chambre | Simple, fiable | Poids du réservoir haute pression |
| **Pump-fed** | Pompe centrifuge ou helique alimente la chambre | Haute performance, réservoirs légers | Complexe, coûteux, risque de cavitation |

> [!info]
> Les systèmes pressure-fed sont utilisés dans la majorité des projets SRAD en compétition car leur fiabilité est bien établie et leur complexité est maîtrisable.

### Types d'injecteurs

| Type | Principe | Utilisation |
|---|---|---|
| **Showerhead** | Jets parallèles à travers des trous | Simple, bonne atomisation |
| **Pintle** | Carburant autour d'une pointe centrale, oxydant en couronne | Régulable, Space X Merlin |
| **Impinging** | Jets qui se croisent pour mélanger | Haute performance, combustion stable |

### Refroidissement régénératif (Regenerative cooling)

Le carburant (ou l'oxydant) circule dans des canaux autour de la chambre de combustion avant d'être injecté. Il absorbe la chaleur des parois et se préchauffe en même temps.

> [!info]
> Le refroidissement régénératif est indispensable pour les moteurs à combustion soutenue (>5 s). Sans lui, la chambre fond.

### Exemples notables

- **Waterloo Polaris** (Université de Waterloo) : LOX/IPA, record mondial de hauteur pour un propergol student — 63 497 pieds (19 354 m)
- **Sherbrooke Launch Canada 2026** : Premier moteur régénératif à voler au Canada. Sherb remporte la première place dans la catégorie advanced.
- **GAUL Marmotte** : N2O/IPA, projet SRAD en développement
- Nombreux projets IREC dans la catégorie liquid propulsion

---

## COTS vs SRAD

### Définitions

| Terme | Signification | Exemple |
|---|---|---|
| **COTS** (Commercial Off-The-Shelf) | Moteur acheté à un fabricant commercial | Aerotech L1295, CTI Cesiaroni J350 |
| **SRAD** (Student Researched And Designed) | Moteur conçu, fabriqué et testé par les étudiants | Projet GAUL Marmotte |

### Pourquoi le SRAD compte

- **Fun** : Pour le fun
- **Disponibilité** : Il n'existe pas vraiment de moteur liquide ou hybride COTS. Si on veut faire voler un moteur liquide, pas le choix de le développer.
- **Valeur éducative** : concevoir un moteur développe des compétences en propulsion, chimie des propergols, mécanique, et tests
- **Points de compétition** : à l'IREC, les projets SRAD reçoivent des points supplémentaires dans le scoring
- **Innovation** : les équipes SRAD peuvent explorer des concepts novateurs (nouveaux propergols, configurations de grain, systèmes de refroidissement)
- **Fiabilité** : un moteur SRAD bien conçu et testé est tout aussi fiable qu'un COTS

### Exigences SRAD

#### IREC (Spaceport America Cup)

- Tous les moteurs doivent être conçus par les étudiants de l'équipe
- Les propergols doivent être fabriqués par les étudiants (pas de rachat de propergol fini)
- Soumission obligatoire d'un dossier technique incluant :
  - Analyse de combustion (RASAero, OpenMotor, ou BurnSim)
  - Courbes de poussée prédites
  - Analyse structurelle du boîtier
  - Plan de tests (static fire)

#### Launch Canada

- Catégories similaires, mais plus de liberté sur les niveaux de SRAD
- Les moteurs COTS sont acceptés dans certaines catégories
- Les projets SRAD reçoivent un bonus dans le scoring

> [!warning]
> Avant de construire un moteur SRAD, vérifiez les règlements de la compétition et les lois locales sur la détention et fabrication de propergols solides. Au Québec, un permis de la Sûreté du Québec peut être requis pour les propergols explosives.

---

## Résumé

| Critère | Solide | Hybride | Liquide |
|---|---|---|---|
| Complexité | Faible | Moyenne | Élevée |
| Réutilisabilité | Variable | Oui | Oui |
| Performance (Isp) | 200-260 s | 150-220 s | 250-350 s |
| Sécurité de stockage | Modérée | Bonne | Variable |
| Coût | Faible-moyen | Moyen | Élevé |
| Usage recommandé | Compétition, HPR | Éducation, début | Recherche, records |
