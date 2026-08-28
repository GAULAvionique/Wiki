![[FW_GPS.png]]
# Description
Traqueur GPS le plus répandu. Fait partie de la famille Featherweight et partage l'application Bluetooth. Se configure avec un cellulaire par Bluetooth, et lorsqu'on s'éloigne hors de portée, communique par Lora 915 MHz avec une ground station  (qui communique par bluetooth avec le cellulaire). La ground station est donc essentiellement un relais pour l'application BT.
Le nombre de scrubs qui ont été causés par cette abomination est franchement insultant. L'ironie de la chose c'est que c'est aussi le standard de la communauté, donc assez difficile de s'en départir. En effet, dans un monde où il n'existe aucun traqueur GPS pour fusées amateur fiables, on doit se contenter du moins pire: le Featherweight GPS tracker.
*To be fair*, quand tu suis les règles non écrites (détaillées plus bas), ils ne sont pas si pire que ça.
# Specs

# Expérience
### Problèmes courants
Attention à la polarité des borniers **surtout sur la ground station**. La polarité des borniers sur la ground station et sur les trackers n'est pas la même. Donc en gros ne démontez jamais la ground station. Si vous devez la charger, faites le par USB. Pour ce qui est des trackers, une inversion de polarité le brise automatiquement. Un peu comme pour les Blue Raven, il faut suivre les règles suivantes pour les configurer :
- Utiliser seulement un cellulaire à la fois et d'une fois à l'autre. Pour changer de cellulaire, oubliez le traqueur sur l'ancien.
- Remplir complètement le nom des trackers (utiliser touts les 11 caractères)
- Pour vérifier si le traqueur a bien un fix GPS, il faut passer par une ground station (même si on est connecté par bluetooth au traqueur)
- Ne pas interrompre les téléchargements, ou appuyer sur le bouton pause si ça doit être fait.
Problèmes courants :
**Pas de fix GPS :**
- Vérifier qu'une ground station est bien connectée au traqueur.
- Vérifier le placement de l'antenne GPS. **L'antenne GPS est la patch de céramique sur le traqueur, et non l'antenne qui s'y visse!!!**. La patch est directionnelle, et doit être pointée vers l'extérieur de la fusée et avoir une vue claire de l'extérieur et du ciel.
- Attendre au moins 5 mins, ça peut être long.
- Vérifier que le traqueur n'est pas brisé. Vérifier la consommation de courant. S'il consomme plus de 100mA, c'est probablement qu'il est brisé. 
**Pas de communication LoRa :**
- Vérifier que l'antenne est bien vissée (traqueur et GS).
- Vérifier que le port de l'antenne est compatible si ce n'est pas l'antenne d'origine (attention SMA et RP-SMA, ce n'est pas parce que ça se visse que c'est compatible).
- Vérifier le Line of Sight
- Vérifier le placement de l'antenne dans la baie et dans la fusée (ne pas oublier que la fibre de carbone bloque le rayonnement RF).
### Avantages
- Répandu donc beaucoup de support.
- Ironiquement la solution COTS GPS la moins chère.
### Inconvénients
- Pas fiables

# Mode emploi
# Liens
- [Page FW GPS tracker](https://www.featherweightaltimeters.com/original-gps-tracker.html)