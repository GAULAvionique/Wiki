---
titre: Filtre de Kalman
---
---
# Filtre de Kalman : Fusion Baromètre & IMU

L'ordinateur de bord utilise un filtre de Kalman étendu simplifié à une dimension (verticale) pour estimer l'altitude et la vitesse verticale de la fusée. Ce filtre fusionne les données d'accélération (IMU/High-G) et de pression (Baromètre).

## 1. Architecture des États

Le vecteur d'état $\mathbf{x}$ contient 3 variables :
$$ \mathbf{x} = \begin{bmatrix} z \\ v \\ a_{bias} \end{bmatrix} = \begin{bmatrix} \text{Altitude (m)} \\ \text{Vitesse verticale (m/s)} \\ \text{Biais d'accélération (m/s}^2\text{)} \end{bmatrix} $$

La matrice de covariance de l'erreur $\mathbf{P}$ est une matrice $3 \times 3$.

---

## 2. Étape 1 : Initialisation (`KalmanNav_Init`)

Avant le vol, le filtre accumule 50 échantillons (définis par `KALMAN_NAV_SAMPLE_NB`) du baromètre pour estimer le bruit de mesure statique et définir l'altitude de référence (zéro).

1. **Calcul de la variance initiale ($R_{static}$)** :
   $$ Variance = \frac{1}{N} \sum_{i=1}^{N} (z_i - \mu)^2 $$
   *(Où $\mu$ est la moyenne `mean_alt`. Une variance minimale de $0.01$ est forcée pour éviter une confiance absolue aveugle)*.

2. **Matrice de covariance initiale ($\mathbf{P}_0$)** :
   $$ \mathbf{P}_0 = \begin{bmatrix} R_{static} & 0 & 0 \\ 0 & 10.0 & 0 \\ 0 & 0 & 1.0 \end{bmatrix} $$
   *(Confiance forte en l'altitude initiale, incertitude modérée sur la vitesse, confiance raisonnable sur le biais)*.

3. **Bruits de processus ($\mathbf{Q}$)** :
   - $Q_{accel} = 0.5$ (Bruit sur l'accélération).
   - $Q_{bias} = 0.001$ (Dérive lente du biais).

---

## 3. Étape 2 : Prédiction (`KalmanNav_Predict`)

Cette étape utilise les données de l'accéléromètre (High-G ou IMU standard selon l'intensité de la vitesse) pour estimer le nouvel état **avant** d'avoir une nouvelle lecture du baromètre. Elle s'exécute à haute fréquence (> 200 Hz) et utilise le module DWT matériel du STM32 pour permettre une base de temps système (SysTick) en microseconde.

Soit $\Delta t$ le temps écoulé depuis la dernière prédiction.

1. **Estimation de l'accélération réelle ($a$)** :
   $$ a = a_{world\_z} - a_{bias} $$

2. **Mise à jour de l'état (Modèle cinématique)** :
   $$ z_{k|k-1} = z_{k-1} + v_{k-1} \cdot \Delta t + 0.5 \cdot a \cdot \Delta t^2 $$
   $$ v_{k|k-1} = v_{k-1} + a \cdot \Delta t $$

3. **Mise à jour de la Covariance ($\mathbf{P} = \mathbf{F}\mathbf{P}\mathbf{F}^T + \mathbf{Q}$)** :
   La matrice de transition $\mathbf{F}$ est :
   $$ \mathbf{F} = \begin{bmatrix} 1 & \Delta t & -0.5\Delta t^2 \\ 0 & 1 & -\Delta t \\ 0 & 0 & 1 \end{bmatrix} $$
   
   Le code développe cette multiplication matricielle à la main pour optimiser les performances :
   - $P_{00}^{new} = P_{00} + \Delta t(P_{10} + P_{01} + \Delta t P_{11}) - 0.5\Delta t^2(P_{20} + P_{02} + \Delta t P_{21} + \Delta t P_{12}) + 0.25\Delta t^4 P_{22} + Q_{accel} \cdot 0.25\Delta t^4$
   - $P_{01}^{new} = P_{01} + \Delta t P_{11} - 0.5\Delta t^2 P_{21} - \Delta t P_{02} - \Delta t^2 P_{12} + 0.5\Delta t^3 P_{22}$
   - $P_{02}^{new} = P_{02} + \Delta t P_{12} - 0.5\Delta t^2 P_{22}$
   - $P_{11}^{new} = P_{11} - \Delta t(P_{21} + P_{12}) + \Delta t^2 P_{22} + Q_{accel} \cdot \Delta t^2$
   - $P_{12}^{new} = P_{12} - \Delta t P_{22}$
   - $P_{22}^{new} = P_{22} + Q_{bias} \cdot \Delta t$

---

## 4. Étape 3 : Mise à jour (`KalmanNav_Update`)

Lorsqu'une nouvelle mesure d'altitude ($z_{mesuré}$) arrive du baromètre (~50 Hz), le filtre corrige sa prédiction.

1. **Ajustement Dynamique du Bruit de Mesure ($R_{alt}$)** :
   La confiance envers le baromètre s'ajuste dynamiquement selon les conditions de vol :
   - **En dessous de 60 000 m (Cas normal)** : $R_{alt} = R_{static} \cdot 0.1$ (Haute confiance au baro).
   - **Au-dessus de 60 000 m** : $R_{alt} = R_{static} \cdot 10.0$ (Basse pression, baro bruyant, confiance modérée).
   - **Mode Mach Lock ou > 90 000 m** : $R_{alt} = 1000.0$ (Pénalité extrême, les ondes de choc faussent le baro, le filtre se fie presque exclusivement à l'IMU).

2. **Calcul de l'Innovation ($y$)** :
   $$ y = z_{mesuré} - z_{prédit} $$

3. **Protection contre les Spikes (Règle des 3-Sigma)** :
   $$ S = P_{00} + R_{alt} $$
   Si $y^2 > 9 \cdot S$ **ET** $y^2 > 10000.0$, la mesure est considérée comme aberrante (spike). La mise à jour est ignorée, mais l'incertitude ($P_{00}, P_{11}$) est artificiellement augmentée (avec un plafond à 1000.0) pour forcer le filtre à converger plus vite lors des prochaines mesures valides.

4. **Gain de Kalman ($\mathbf{K}$)** :
   $$ \mathbf{K} = \mathbf{P}\mathbf{H}^T (\mathbf{H}\mathbf{P}\mathbf{H}^T + \mathbf{R})^{-1} $$
   Où $\mathbf{H} = \begin{bmatrix} 1 & 0 & 0 \end{bmatrix}$, simplifiant la matrice :
   $$ K_0 = \frac{P_{00}}{S} \quad K_1 = \frac{P_{10}}{S} \quad K_2 = \frac{P_{20}}{S} $$

5. **Mise à jour de l'État** :
   $$ z_{final} = z_{prédit} + K_0 \cdot y $$
   $$ v_{final} = v_{prédit} + K_1 \cdot y $$
   $$ a_{bias\_final} = a_{bias\_prédit} + K_2 \cdot y $$

6. **Mise à jour de la Covariance ($\mathbf{P} = (\mathbf{I} - \mathbf{K}\mathbf{H})\mathbf{P}$)** :
   - $P_{00} = P_{00} - K_0 \cdot P_{00}$
   - $P_{01} = P_{01} - K_0 \cdot P_{01}$
   ... et ainsi de suite pour toute la matrice, suivie d'un forçage de symétrie ($P_{ij} = (P_{ij} + P_{ji}) / 2$) pour éviter les dérives numériques.

---

## 4.5. Transition Dynamique des Capteurs (Handoff IMU vs High-G) 
Avant même d'injecter l'accélération verticale dans le filtre de Kalman, l'ordinateur de bord doit choisir le capteur le plus approprié pour la situation de vol actuelle. L'avionique possède deux capteurs distincts : 
1. **BNO055** : Très précis, faible bruit, mais sature rapidement (souvent autour de 4G) en mode fusion de données.
2. **ADXL382** : Capable d'encaisser des chocs extrêmes (jusqu'à 60G), mais beaucoup plus bruyant et moins précis à basse vitesse. Le code effectue une sélection conditionnelle basée sur un seuil défini dans la configuration. Par défaut, ce seuil a été défini à 3G.

---

## 5. Justifications Mathématiques et Physiques des Constantes

Les valeurs numériques utilisées dans cet algorithme découlent des principes de la physique atmosphérique, des statistiques et des caractéristiques des capteurs MEMS :

### L'Initialisation
*   **50 échantillons (`KALMAN_NAV_SAMPLE_NB = 50`) :** À une fréquence de rafraîchissement d'environ 50 Hz, cela correspond à une seconde d'acquisition. C'est un compromis idéal pour lisser le bruit gaussien au sol et obtenir un "zéro" d'altitude AGL précis.
*   **Variance minimale de `0.01` $(m^2)$ :** Si la fusée est parfaitement immobile, la variance mathématique pourrait être de 0. Une telle valeur forcerait une confiance de 100% au baromètre, provoquant des divisions par zéro ou un verrouillage du filtre. Cette valeur limite agit comme une sécurité mathématique.

### La Matrice de Covariance Initiale ($\mathbf{P}_0$)
*   **Vitesse de `10.0` $(m^2/s^2)$ :** Équivaut à un écart-type d'environ $\pm 3.16$ m/s ($\sqrt{10}$). Donne au filtre le "mou" nécessaire pour accepter des variations de vitesse rapides au décollage (vibrations, rafales) sans rejeter immédiatement la donnée.
*   **Biais d'accélération de `1.0` $(m^2/s^4)$ :** Tolère l'erreur de zéro inhérente aux accéléromètres au repos (liée à la soudure, la température, ou un léger désaxement sur la rampe) de $\pm 1$ m/s².

### Les Bruits de Processus ($\mathbf{Q}$)
*   **Bruit sur l'accélération ($Q_{accel} = 0.5$) $(m^2/s^4)$:** Les turbulences et les vibrations du moteur sont massives. Cette valeur empêche le filtre de trop lisser les données et l'autorise à réagir rapidement lors des événements dynamiques (déploiements, fin de combustion).
*   **Dérive du biais ($Q_{bias} = 0.001$) $(m^2/s^5)$:** L'erreur matérielle d'un IMU dérive avec la température, mais très lentement. Une valeur très faible force le filtre à ne modifier ce biais que progressivement au fil des minutes.

### L'Ajustement Dynamique du Baromètre ($R_{alt}$)
*   **Multiplicateur `0.1` (Vol < 60 km) :** Le flux d'air aérodynamique lisse naturellement les fluctuations de pression par rapport au sol. Réduire l'incertitude du baromètre donne au capteur l'autorité nécessaire pour corriger la dérive inévitable de l'accéléromètre.
*   **Seuil `ALT_60K_M` (60 km) et Multiplicateur `10.0` :** Dans la mésosphère, la densité de l'air est extrêmement faible (< 0,1% du niveau de la mer). Une infime variation de pression équivaut à des sauts de plusieurs dizaines de mètres, rendant le capteur très bruyant. Le multiplicateur diminue drastiquement sa pondération.
*   **Seuil `ALT_90K_M` (90 km) et Mach Lock (Pénalité de `1000.0`) $(m^2)$ :** En approchant de la ligne de Kármán, la pression est quasi-nulle. De même, franchir le mur du son génère une onde de choc qui sature la baie électronique de pressions aberrantes. La pénalité extrême coupe pratiquement le signal barométrique (Gain $\approx 0$), forçant la fusée à naviguer de manière purement inertielle.

### La Protection contre les Anomalies (Spikes)
*   **Règle des 3-Sigma (`y^2 > 9 * S`) :** En distribution normale, 99.7% des erreurs capteurs se trouvent sous 3 écarts-types ($3\sigma$). La variance est $\sigma^2$, donc $(3\sigma)^2 = 9\sigma^2$ (`9 * S`). Une erreur dépassant ce seuil est considérée comme une anomalie physique (explosion, coupure de vent extrême), et non du bruit.
*   **Le plafond `10000.0` (100 mètres) $(m^2)$ :** $10000$ est le carré de $100$ mètres. Cette condition évite que le filtre ne rejette des données lors d'un authentique mouvement violent. Pour qu'une donnée soit supprimée, l'écart doit être non seulement statistiquement improbable, mais aussi représenter un saut d'altitude instantané absurde (> 100 m).

---

> [!info] 📊 Ratio de Confiance Baromètre vs Accéléromètre
>
> Le filtre de Kalman agit comme un "arbitre" intelligent qui change son ratio de confiance selon l'environnement de la fusée :
> 
> - **Au pas de tir (Statique) :** Le baromètre est roi. L'ordinateur prend 50 mesures pour définir le niveau zéro et évaluer le "bruit" ambiant. L'accéléromètre calibre son biais de gravité.
> - **Ascension subsonique (< 60 km) :** C'est l'équilibre parfait. L'accéléromètre est très réactif et détecte le mouvement instantané (à 200 Hz). Mais les capteurs dérivent avec le temps. Le baromètre intervient à 50 Hz comme une ancre solide pour "remettre à zéro" la dérive de l'accéléromètre. Confiance : **Élevée au Baro (R_alt = 0.1 * statique)**, modérée à l'accéléromètre (qui sert à boucher les trous).
> - **Passage du mur du son (Mach Lock) :** Le baromètre devient "fou". L'onde de choc crée des pressions absurdes à l'intérieur de l'avionique. Le système détecte l'événement, active le flag `is_machlock`, et applique une pénalité monstrueuse au baro ($R_{alt} = 1000.0$). Confiance : **~99% Accéléromètre (High-G)**, ~1% Baro. Le vol se fait en aveugle inertiel.
> - **Très haute altitude (60 km à 90 km) :** L'air est si rare que le capteur de pression manque de résolution (bruit massif). Confiance : **Modérée à l'Accéléromètre**, faible au baro ($R_{alt} = 10.0 * statique$).
> - **Au-delà de 90 km (Espace) :** Le baromètre est inutile. La pression est quasi-nulle. Comme en Mach Lock, le filtre coupe le baromètre ($R_{alt} = 1000.0$) et navigue **uniquement à l'inertiel (100% Accéléromètre)**.
> - **Anomalies (Spikes) :** Si un trou d'air ou un déploiement crée une pointe de pression violente défiant les lois de la physique (Vitesse impossible > Règle des 3-Sigma), le filtre ignore la mesure barométrique sur le coup, mais augmente son humilité (élargit son P) pour la prochaine mesure.