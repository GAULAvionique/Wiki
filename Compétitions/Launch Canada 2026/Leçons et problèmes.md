# 2 FW Trackers se sont mis sur la même fréquence
### Description
Au moment où on devais s'éloigner de la fusée, une mauvaise manipulation dans l'appli Featherweigth met les deux trackers sur le même channel. Nous n'avons pas le temps de régler la situation avant de partir. La télémétrie pour un des deux étages était donc inexistante.
### Problème
C'est un problème avec l'UI de Featherweight assez courant. Il se produit souvent lorsque qu'on switch d'un tracker à l'autre avec la ground station. Les chances que ça se produise sont plus grandes si les deux trackers sont sur la même fréquence, dans deux channels différents (ex 11A et 11B).
### Solution
Nous avons mis les trackers sur deux fréquences et channels différents (11A et 12B). Dans le futur, il est mieux d'utiliser deux ground station pour éviter de switcher d'un tracker à un autre avec la même ground station.
# Perte de communication avec FW tracker lors du lancement
### Description
Lors du lancement, on perd la télémétrie FW à 8000 pieds. On ne la retrouve jamais
### Problème
En prévision de la très haute altitude, nous avions remplacé l'antenne omnidirectionnelle par l'ancienne antenne Yagi de la SAS. Cette antenne avait une connexion SMA-RP plutôt que SMA normale. Les deux connections ne sont pas compatibles, mais se vissent tout de même parfaitement ensemble.
### Solution
Ne pas être un gros épais. Regarder que la connexion est correcte avant de connecter quelque chose. 

# RunCam overheat dans la fusée
### Description
Lors du lancement de compétition, la seule caméra du booster fonctionne, alors que les deux caméras du sustainer n'ont pas capturé le footage. Pourtant, avec les deux caméras on observe le footage de la première tentative de lancement au complet (armement, attente, désarmement). On observe aussi la deuxième tentative (armement et attente). Environ 10 minutes avant le vrai lancement, on voit des bugs sur les dernières minutes de la vidéo, puis plus rien. Le prochain footage est lorsqu'on ré-arme la fusée pour avoir l'altitude.
### Problème
Les deux caméras stackées l'une par dessus l'autre ont surchauffés dans la fusée. La fusée a passée la journée sur le pad au soleil tappant. Le fuselage est rouge foncé, ce qui n'aide pas. C'est un problème connu des runcams.
### Solution
Mettre un heatsink sur les caméras. Ne pas les stacker les unes sur les autres (ou en mettre une seule). Délayer au maximum l'allumage des caméras.
# Stress au niveau de la capacité des cartes SD des batteries
### Description
Edge Canada porte bien son nom. La fusée a du passer un bon 2 heures armée sur le pad avant de finalement décoller. À ce moment, on pense que le facteur limitant est la capacité de la carte SD des batteries, on calcule environ 2-3h d'autonomie. On stress alors beaucoup, pensant que les caméras n'auront presque plus de stockage.
### Problème
En réalité, nous avions au moins 6 heures d'autonomie (preuve, lors du lancement de compétition, on voit le lancement à 12h, et la récupération à 6h). Toutefois, ça dépend toujours de la carte SD utilisée. Le fait de devoir armer les caméras avant de partir est à la source de cette crainte.
### Solution
Utiliser un système de "cordon ombilical" serait pertinent. Une corde attachée au sol "arrache" le dispositif d'armement de la caméra lors du lancement et allume la caméra seulement une fois que la fusée est partie.
# Stress au niveau des batteries du circuit de télémétrie
### Description
Le circuit principal de télémétrie prévoyais 9h d'autonomie. On donne alors un 3-4h max sur le pad comme condition no-go, pour permettre la recovery. On stress encore beaucoup au niveau de l'autonomie de la baie.
### Problème
Ce qui consomme le plus (et limite donc le plus l'autonomie) sont les caméras. Mettre les caméras sur le même circuit que le circuit de télémétrie n'était pas une bonne idée. On découvre plus tard que le circuit de télémétrie avait plus de 24h d'autonomie (oups).
### Solution
Même si au final on aurait été correct. On ne devrait pas mettre les caméras sur un circuit aussi critique.