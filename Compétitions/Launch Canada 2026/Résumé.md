![[photo_equipe_LC_2026.png]]
# Objectif et contexte
Launch Canada 2026 se déroule du 15 au 22 août 2026 à Timmins en Ontario. Le GAUL participe dans la catégorie Advanced avec un projet double stage visant 97 000 pieds d'altitude. L'objectif est de briser le record Canadien d'altitude d'une fusée amateur universitaire. On nomme la fusée "Elerrína", d'après le plus haut sommet de l'univers du Seigneur des anneaux.

Avant même le début de la compétition, la catégorie advanced est marquée par une grande pression venant des organisateurs (dont le tristement célèbre *Peter*) pour que tout soit "flight ready" le plus en avance possible. Quelques équipes sont disqualifiées de la compétition. Le GAUL arrive à démontrer ses qualifications.

Le GAUL arrive à lancer le premier jour, soit Lundi. Malheureusement, le tilt lockout empêche le 2e étage de s'allumer (voir plus bas pour plus de détails). Autrement, les deux étages ont des vols nominaux, et sont récupérés complètement intacts.

Découragés d'avoir encore en leur possession le N1000 du sustainer (moteur de l'IREC qui ne s'était pas allumé non plus), l'équipe du GAUL décide de relancer leur sustainer seul, ce qu'elle fait le Jeudi de la compétition. Encore une fois, le vol est nominal et la fusée est retrouvée intacte. Un point marquant de ce 2e vol est le test réussi de l'ordinateur de bord ODBlixv2.


# Déroulement vol de compétition (2 étages)
### Dimanche soir
On assemble les deux baies avioniques au complet en suivant les checklists. Tous les ordinateurs et appareils COTS sont programmés aux bonnes fréquences et aux bons paramètres. Les ematch sont mises durant l'assemblage. Tous les câbles sont sécurisés avec du masking tape. Les charges de poudre noire sont aussi installées durant la soirée. Fin du travail vers 1h du matin.

### Lundi 5h-6h  -  Airnbn
En suivant la checklist pré-départ, durant l'étape où on doit vérifier la tension de chaque circuit, on short accidentellement le + et le - du circuit de télémétrie (ODB, IdéFIX, caméras, Featherweight). Ce short éteint visuellement tout ce qui se trouve sur la partie droite du PCB d'armement (ODB, IdéFIX, FW), mais pas les caméras.
![[pcb_armement_saute.png]]
On suspecte qu'un immense pic de courant aurait fait fondre la petite trace qui achemine tout le 7v4 à la partie droite du PCB. La batteries à une ÉNORME capacité de courant, soit ~20Ah.
![[bottleneck_pcb_armement.png]]
### Lundi 8h-11h  -  Table de travail
La programmation des Blue Raven est vérifiée et approuvée par les juges. Les règles de LC indiquent un titl angle lockout de maximum 15 degrés. Or, nos simulations montrent qu'avec la rampe de lancement de 6 degrés, on arrive très près, voir plus loin que ce 15 degrés.
On demande aux organisateurs si on peut augmenter la limite à 20 degrés (come à l'IREC), ou si on peut réduire l'angle de la rampe de lancement. On nous permet de réduire l'angle de la rampe à 4 degrés (mais garder la limite du lockout à 15 degrés).
### Lundi 11h-12h  -  Launchpad
L'armement de la fusée se passe correctement. Malheureusement, un des trackers GPS change son channel sur le channel voisin, nous empêchant alors de communiquer par LoRa avec. On remarque ce problème alors que nous sommes en train de partir, donc pas le temps de le régler.
Pour la télémétrie SRAD, elle semble fonctionner pour un certain temps, puis cesse complètement un peu après que le 2e étage soit allumé. On ne reçoit que des paquets Mavlink corrompu à la station de base. Aucune solution n'est envisagée, on abandonne la télémétrie SRAD.
### Lundi 12h-12h30  -  Viewing area
À cause du problème précédent, un des étages n'a aucune télémétrie (autre que Spotrace). On décide alors d'annuler le lancement.
### Lundi 15h-16h  -  Launchpad
On retourne au launchpad pour régler le problème des featherweight GPS tracker. Il faut faire attention de ne pas les laisser allumer trop longtemps, puisqu'ils sont sur le même circuit que l'ODB, qu'IdéFIX et que les caméras. L'autonomie en batterie dérange moins, c'est surtout la capacité de stockage sur les cartes SD qui dérange (on ne pensait pas avoir plus de 2-3h).
### Lundi 16h-17h  -  Viewing area
*Peter* edge le lancement pendant 40 longues minutes, alors qu'il attends que les volontaires ferment une route. La fusée lance et on aperçoit une 2e traînée de fumée dans le ciel. Tout le monde est convaincu que le 2e étage a bien allumé. Or, ce qui semblait être le 2e étage était en fait le "smoke grain" du booster qui avait simplement un délai d'allumage.
La télémétrie sur les featherweight est perdue presque immédiatement après le lancement, et à tout jamais. On se rend compte après, que l'antenne utilisée n'avait pas le bon connecteur (SMA femelle à SMA-RP mâle)... Par fort. On avait en effet décidé d'utiliser l'ancienne antenne Yagi de la SAS pour avoir plus de portée. On avais pas vérifié que les connecteurs étaient bien compatibles (puisqu'ils se vissaient correctement ensemble).
Les deux spotrace clutch et nous envoient les positions finales des deux étages.
### Lundi 17h-19h30  -  Recovery
Les deux étages ont une recovery nominale (drogue et main) et atterrissent dans la forêt. Le booster reste coincé dans le haut d'un arbre, et le sustainer plonge au travers des arbres et atterrit sur le sol.
Le sustainer est retrouvé et récupéré la soirée même. Le booster est aussi retrouvé durant la soirée, mais on doit attendre au lendemain pour pouvoir le récupérer. Note intéressante, même après une nuit complète allumés, tous les circuits fonctionnaient encore lorsque le booster fut récupéré.
La caméra du booster a bien capturée le vol. Les deux caméras du sustainer par contre ont arrêté d'enregistrer un peu avant le début du vol. On suspecte qu'elles auraient surchauffés (problème courant chez les RunCam).


# Déroulement vol de sport (sustainer seulement)

### Mercredi soir
Les baies avioniques sont encore montées. On change le PCB d'armement du sustainer, recharge et change les batteries, et on ré-assemble le tout avec les nouvelles ematch. On ne met qu'une seule caméra, pour éviter qu'elle ne surchauffe encore. On programme les altimètres.
### Jeudi 9h-12h  -  Table de travail
On installe les charges de poudre noire et insère la baie dans le sustainer.
### Jeudi 12h-13h  -  Launchpad
Tout l'armement se passe comme prévu. La télémétrie SRAD ne fonctionne toujours pas (même après des modifications dans le code), encore des problèmes avec le checksum de Mavlink.
### Jeudi ~13h  -  Viewing area
On lance la fusée. La télémétrie du FW GPS coupe (mach lock). On monte sur la tour de contrôle pour avoir un meilleur signal et on obtient un 'ping' à 22 000 pieds avec une descente de 170 ft/s (drogue nominal). On suit ensuite la descente jusqu'à voir le déploiement du main, puis la position finale.
### Jeudi 18h-20h  -  Recovery
Il n'y avais plus de Walkie-Talkie de disponibles lorsque nous voulions partir. Nous avons donc du attendre le retour d'une équipe. De plus, puisque nous étions atterit dans une zone balistique, nous avons aussi du attendre que les lancements soient finis. On attends près de 6h au final avant de pouvoir aller chercher la fusée.
La fusée étant atterrie dans un arbre, on doit couper l'arbre pour la récupérer. Évidemment, en faisant cela, la fusée se coince dans un arbre adjacent et ainsi de suite. On doit couper 4 arbres pour finalement la récupérer.
On attends ODBlix ainsi que le Stratologger sonner (preuve qu'ils ont fonctionné). Tous les circuits sont encore allumés, et on peut extraire les données de vol sur place. L'altitude atteinte selon nos GPS est de 33 501 ft!

