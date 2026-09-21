# Armement et redondance

## Introduction

L'armement est le processus par lequel les systèmes pyrotechniques d'une fusée passent de l'état inactif à l'état prêt à fonctionner. La sécurité liée à l'armement est l'un des aspects les plus critiques de la fuséologie.

### Principe fondamental

> [!info]
> Le principe de base est simple : **l'électronique est OFF jusqu'à l'armement intentionnel**. Aucun système pyrotechnique ne doit être actif avant que le personnel autorisé n'ait effectué l'armement de manière délibérée et contrôlée.

### Règle d'or

**Ne jamais travailler sur un système armé.** Si un ajustement est nécessaire, le système doit d'abord être désarmé.

---

## Mécanismes d'armement

### Pull-pin switches (interrupteurs à broche)

- **Principe** : une broche physique est insérée dans un interrupteur. Le retrait de la broche active le circuit.
- **Avantage** : simple, mécanique, fiable
- **Inconvénient** : 
	- peut être retirée accidentellement si mal fixée
	- doit insérer la baie dans le fuselage armée, ou trouver un moyen de contourner
	- l'accélération et les vibrations peuvent faire "bouncer" l'interrupteur
- **Usage** : très courant dans les fusées amateur

### Push-pin switches (interrupteurs à broche)

- **Principe** : Une vis est insérée dans un trou et active les interrupteurs.
- **Avantage** : 
	- La vis reste durant le vol et garde les interrupteurs pressés. Moins de chances que ceux-ci "bouncent".
	- Robuste et solide
	- Ne s'enlève pas facilement
- **Inconvénient** : 
	- Peu courant, donc design costum nécessaire

### Magnetic switches (interrupteurs magnétiques)

- **Principe** : un aimant externe active/désactive l'interrupteur à travers la paroi de la fusée
- **Avantage** : aucun contact physique nécessaire, pas de trou dans l'airframe
- **Inconvénient** : 
	- nécessite un aimant de force appropriée, peut être activé accidentellement par des objets magnétiques
	- si plus d'une switch magnétique est utilisée, activer l'une peut désactiver l'autre (très courant)

### Key switches (interrupteurs à clé)

- **Principe** : une clé physique doit être insérée pour activer le circuit
- **Avantage** : très sûr, impossible à activer accidentellement
- **Inconvénient** : 
	- nécessite la gestion physique des clés
	- nécessite une "trape" pour avoir accès à la baie
- **Usage** : utilisé sur certains altimètres (Missileworks RRC3+)

### Timer-based (activation par minuteur)

- **Principe** : le système s'active automatiquement après un délai prédéfini
- **Avantage** : pas d'intervention physique nécessaire au moment du lancement
- **Inconvénient** : moins de contrôle, risque d'activation prématurée si le minuteur est mal configuré
- **Usage** : moins courant, utilisé dans certains projets spécifiques

### Software arming (activation logicielle)

- **Principe** : l'armement se fait via une application Bluetooth ou une interface logicielle
- **Avantage** : flexible, permet des configurations multiples
- **Inconvénient** : 
	- nécessite un appareil compatible, dépend de la connectivité Bluetooth
	- ne compte pas comme un "vrai" armement. Ne pas seulement utiliser cette méthode.
- **Usage** : standard avec les systèmes Featherweight

### Tableau comparatif

| Type       | Fiabilité  | Complexité | Coût     | Sécurité   |
| ---------- | ---------- | ---------- | -------- | ---------- |
| Pull-pin   | Haute      | Basse      | Très bas | Moyenne    |
| Magnetic   | Haute      | Moyenne    | Moyen    | Haute      |
| Key switch | Très haute | Basse      | Moyen    | Très haute |
| Timer      | Moyenne    | Moyenne    | Bas      | Moyenne    |
| Software   | Haute      | Haute      | Variable | Haute      |

> [!info]
> Le choix du mécanisme d'armement dépend du type de fusée, du budget, et des préférences de l'équipe. Pour les compétitions, un système à clé ou magnétique est recommandé pour la sécurité.
> Le GAUL utilise généralement des **Push-pins**

---

## Vérification de continuité

### Définition

La **continuité** vérifie que le circuit pyrotechnique est complet et que le courant peut circuler de la batterie à l'e-match (electro-explosive device).

### Méthode de vérification

#### Multimètre

- Mesurer la **résistance** du circuit : elle doit être de **1 à 2 ohmes** pour un e-match en bon état
- Si la résistance est infinie (open circuit) : il y a un problème de connexion
- Si la résistance est nulle (short circuit) : il y a un court-circuit

#### Indicateurs intégrés

La plupart des altimètres ont des indicateurs de continuité intégrés :

- **LED** : s'allume quand le circuit est complet
- **Bip sonore** : émet un son quand le circuit est complet
- **Affichage** : certains altimètres affichent l'état de continuité sur un écran ou via Bluetooth

---

## Redondance — Pourquoi?

### Concept de point de défaillance unique

> [!info]
> Un **point de défaillance unique** (Single Point of Failure) est un composant dont la défaillance entraîne la perte totale de la mission. Dans une fusée sans redondance, un altimètre défaillant signifie pas de déploiement de parachute = destruction de la fusée.

### Principe de redondance

La redondance consiste à dupliquer les systèmes critiques pour qu'en cas de défaillance d'un composant, un autre puisse prendre le relais.

### Application en fuséologie

- **Un altimètre défaillant** → le backup déploie les parachutes
- **Un GPS défaillant** → le traceur satellite localise la fusée
- **Un e-match défaillant** → le second e-match déclenche la charge

### Exemple réel

> [!info]
> Lors d'IREC 2026, le **Blue Raven** principal a échoué en raison d'un problème logiciel. Le **Stratologger CF** de backup a correctement déployé le drogue à l'apogée et le parachute principal à 1500 ft. Sans redondance, la fusée aurait été perdue.

---

## Architecture de redondance

### Principe général

Une architecture de redondance efficace repose sur l'**indépendance** des systèmes :

- Chaque système doit être **indépendant** des autres
- Chaque système doit avoir sa propre **source d'alimentation**
- Chaque système doit avoir ses propres **canaux pyrotechniques**
- Chaque système doit avoir des **interrupeurs différents**

### Altimètres primaire et backup

- **Système primaire** : altimètre principal (ex : Blue Raven)
- **Système backup** : altimètre secondaire (ex : Stratologger CF)
- **Indépendance** : batteries séparées, e-matches séparés, charges pyrotechniques séparées, PCB d'armements séparés

### Alimentation indépendante

> [!info]
> Chaque altimètre doit avoir sa **propre batterie**. Si une batterie est défectueuse ou se décharge prématurément, seul un système est affecté. L'utilisation d'une batterie commune crée un point de défaillance unique.

### Canaux pyrotechniques indépendants

- Chaque charge pyrotechnique (drogue, main) doit avoir **deux e-matches** connectés à des altimètres différents
- Les charges pyrotechniques doivent être dans des **compartiments séparés**
- Les **shear pins** doivent être dimensionnés pour résister au déploiement d'un seul système

### Redondance GPS

| Système | Technologie | Avantage |
|---|---|---|
| Featherweight GPS | LoRa 915 MHz | Haute précision, longue portée |
| Spotrace | Satellite Globalstar | Couverture mondiale, pas de limite COCOM |

> [!info]
> En général, les traqueurs GPS "chient" souvent. C'est une bonne idée d'avoir plusieurs solutions de tracking. Par exemple Elerrina en avait 4 : Featherweight, ODB, Idéfix, Spotrace. Au final... Seulement le spotrace nous a permis de retrouver les étages...

---

## Modes de défaillance courants

### Tableau des défaillances

| Mode de défaillance                                   | Cause probable                                                                       | Mitigation                                |
| ----------------------------------------------------- | ------------------------------------------------------------------------------------ | ----------------------------------------- |
| Défaillance altimètre                                 | Batterie défectueuse, câblage lâche, composant défaillant                            | Altimètre backup indépendant              |
| Défaillance GPS                                       | Antenne déconnectée, pas de fix satellite, limite COCOM                              | Traceur satellite (Spotrace) comme backup |
| Défaillance e-match                                   | Corrosion, mauvaise connexion, e-match défaillant                                    | Deux e-matches par charge pyrotechnique   |
| Défaillance batterie                                  | Basse tension, court-circuit, vieillissement                                         | Batteries séparées, monitoring de tension |
| Défaillance d'éjection                                | Trop peu de poudre noire, charge mal positionnée                                     | Testing au sol, quantités conservatrices  |
| Défaillance alimentation lors déploiement des charges | Trop de courant pour la batterie provoque une chute de tension qui coupe l'altimètre | Test et utilisation d'une bonne batterie  |

---

## Sécurité au sol

### Règles fondamentales

1. **Ne jamais armer sur le banc d'essai** : l'armement ne se fait que sur le pas de tir, après autorisation du RSO
2. **Tester les charges pyrotechniques avant le vol** : ground testing obligatoire
3. **Manipuler les e-matches avec précaution** : ils sont sensibles à l'humidité, aux chocs, et aux décharges électrostatiques

### Ground testing (tests au sol)

> [!info]
> Les ground testing sont des tests où les charges pyrotechniques sont déclenchées au sol pour vérifier qu'elles déploient correctement les parachutes. C'est une étape **obligatoire** avant tout vol.

Protocole de ground testing :

1. Monter la fusée dans une configuration de test (sans moteur)
2. Installer les charges pyrotechniques avec les quantités prévues
3. Placer les parachutes dans les sections de déploiement
4. Armement en sécurité (hors zone de hazard)
5. Déclenchement des charges
6. Vérifier le déploiement complet des parachutes
7. Ajuster les quantités si nécessaire

### Manipulation des e-matches

- **Stockage** : dans un conteneur hermétique, à l'abri de l'humidité
- **Transport** : dans un conteneur isolé, séparés des autres composants pyrotechniques
- **Manipulation** : porter des gants, éviter les décharges électrostatiques
- **Vérification** : test de continuité en mode résistance uniquement (jamais en mode courant)
