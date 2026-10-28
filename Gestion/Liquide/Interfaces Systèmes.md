Mis à jour le 27 octobre 2026
# Interface GSE 

| **Interface**      | **Capteur**              | **Modèle**  | **Lien**                                                                                                                                                                                                                                                                          |
| ------------------ | ------------------------ | ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Valve 1            | Servo-moteur             | 35kg servo  | [url](https://www.digikey.ca/en/products/detail/dfrobot/SER0067/23028647)                                                                                                                                                                                                         |
| Valve 2            | Servo-moteur             | 35kg servo  | [url](https://www.digikey.ca/en/products/detail/dfrobot/SER0067/23028647)                                                                                                                                                                                                         |
| Valve 3            | Valve solénoïde          | NC 12VDC 8W | [url](https://ussolid.com/products/1-2-high-pressure-solenoid-valve-160-bar-stainless-steel-12v-dc-high-pressure-high-temperature-solenoid-valve-76-356-f-normally-closed?pr_prod_strat=jac&pr_rec_id=9b78d2abe&pr_rec_pid=8925905256703&pr_ref_pid=8925905158399&pr_seq=uniform) |
| Poids fill tank    | Load cell                |             | [url]()                                                                                                                                                                                                                                                                           |
| Poussée moteur     | Load cell                |             | [url]()                                                                                                                                                                                                                                                                           |
| Pression fill tank | Capteur pression 4-20 mA |             | [url]()                                                                                                                                                                                                                                                                           |
| Allumage           | Igniter                  |             | [url]()                                                                                                                                                                                                                                                                           |

# Interface Moteur
| **Interface**           | **Capteur**              | **Modèle** | **Lien**                                                                  |
| ----------------------- | ------------------------ | ---------- | ------------------------------------------------------------------------- |
| Valve 1                 | Servo-moteur             | 35kg servo | [url](https://www.digikey.ca/en/products/detail/dfrobot/SER0067/23028647) |
| Valve 2                 | Servo-moteur             | 35kg servo | [url](https://www.digikey.ca/en/products/detail/dfrobot/SER0067/23028647) |
| Valve 3                 | Servo-moteur             | 35kg servo | [url](https://www.digikey.ca/en/products/detail/dfrobot/SER0067/23028647) |
| Pression fill tank      | Capteur pression 4-20 mA |            | [url]()                                                                   |
| Pression thrust chamber | Capteur pression 4-20 mA |            | [url]()                                                                   |
| Température chambre     |                          |            |                                                                           |

# Fréquence récolte données
Ces fréquences sont valides pour le static fire seulement (certaines sont réduites ou non incluses pour un vrai vol)

| **Mesure**                 | **Fréquence** |
| -------------------------- | ------------- |
| Poussée moteur (load cell) | 10 kHz        |
| Pression thrust chamber    | 10 kHz        |
| Température                | 1 kHz         |
| Poids fill tank            | < 10 Hz       |
| Pression fill tank         | < 10 Hz       |
| Pression NO2 tank          | < 10 Hz       |
# Notions de sécurité : 
- Igniter : 
	- The igniter must have two independent inhibits separating it physically and electrically from its power source;  
    - Igniter leads must be locked out, shorted, and grounded while personnel are nearby. 
    - The pad/test-stand lockout must make it physically impossible to fire the igniter while personnel are present, while still allowing remote safety-critical functions such as tank venting and monitoring. 
    - An automated open-loop sequence that opens valves after commanding ignition without confirmation is prohibited. 
- 2 Valves moteur main 
	- The main propellant valves cannot open until nominal igniter operation is confirmed. (i.e. il faut un moyen de confirmer que l'igniter est allumé, continuité?)