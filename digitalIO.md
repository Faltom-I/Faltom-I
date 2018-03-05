# DigitalIO

## Objectif

Pour maintenir la cohérence et la modularité du système, chaque carte devra comporter une entrée et une sortie de type *DigitalIO*. Celle-ci a pour but d'être facilement intégrable car n'obligeant pas d'élément programmable.

## Connectique
 - TODO
 
## Pinout

### Digital IO: input (connecteur Jin)

| Numéro de pin | Direction | Type      | Nom   | Description      |
|---------------|-----------|-----------|-------|------------------|
| 1             | Entrée    | Puissance | GND   | GND              |
| 2             | Entrée    | Puissance | 5V    | +5V (100 mA max) |
| 4             | Entrée    | Logique   | SCK   | Horloge des registres à décalage |
| 5             | Entrée    | Logique   | MOSI  | Entrée des registres à décalage  |
| 6             | Sortie    | Logique   | MISO  | Sortie des registres à décalage  |
| 7             | Entrée    | Logique   | SET   | Application des registres à décalage de sortie  |
| 8             | Entrée    | Logique   | LATCH | Mémorisaton des registres à décalage en entrée  |
| 9             | Sortie    | Logique   | TX    | Bus Uart (3v3)  |
| 10            | Entrée    | Logique   | RX    | Bus Uart (3v3)  |

### Digital IO: output (connecteur Jout)

| Numéro de pin | Direction | Type      | Nom   | Description      |
|---------------|-----------|-----------|-------|------------------|
| 1             | Sortie    | Puissance | GND   | GND              |
| 2             | Sortie    | Puissance | 5V    | +5V (100 mA max) |
| 4             | Sortie    | Logique   | SCK   | Horloge des registres à décalage |
| 5             | Sortie    | Logique   | MOSI  | Entrée des registres à décalage  |
| 6             | Entrée    | Logique   | MISO  | Sortie des registres à décalage  |
| 7             | Sortie    | Logique   | SET   | Application des registres à décalage de sortie  |
| 8             | Sortie    | Logique   | LATCH | Mémorisaton des registres à décalage en entrée  |
| 9             | Entrée    | Logique   | TX    | Bus Uart (3v3)  |
| 10            | Sortie    | Logique   | RX    | Bus Uart (3v3)  |

 ## 
