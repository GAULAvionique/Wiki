# Baie Avionique ELERRINA 2027
# Description
Elerrina 2027 (nom sujet à changement) est une révision d'Elerrina 2026 qui sera lancée à Launch Canada 2027. L'objectif est de réussir le vol échoué en 2027, soit un vol à deux étages visant plus de 100k pieds. Pour ce faire, l'équipe mécanique prévoit une rampe de lancement "costum" ainsi que quelques révisions à la fusée. En avionique, on prévoit une révision complète de la baie, réglant entre autres les problèmes suivants :
- Assemblage compliqué et non pratique
- Les E-match ne sont pas accessibles sans démonter la baie
- Les batteries sont mal gérées (non démontables, difficiles à charger sans démonter la baie)
- Les antennes à l'intérieur de la baie perdent beaucoup de leur efficacité
- Mieux caractériser / simuler les antennes
- Le seul PCB d'armement est interdit, ce qui nécessite une switch magnétique en plus
- Les caméras (énergivores) sont sur le même circuit que la télémétrie, qui réduit beaucoup la durée de vie de celle-ci
- La durée de vie des caméras est limitée par l'espace sur la carte SD, il n'est donc pas intelligent de les mettre sur la même switch que la télémétrie (on veut pouvoir les allumer le plus tard possible)
- On veut possiblement un cordon ombilical sur la rampe pour le power, et un autre pour allumer les caméras
- Les deux caméras "stackées" ont surchauffées dans la baie
# TODO
- Description
- CONOPS / Usecase diagram
- Charte
- Requirements
- Risk management
- Échéancier / Milestones
- System design