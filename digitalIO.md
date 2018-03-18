# DigitalIO

## Objectif

Pour maintenir la cohérence, la modularité du système et la découverte automatique de sa configuration, chaque carte devra comporter une entrée et une sortie de type *DigitalIO*. Celle-ci a pour but d'être facilement intégrable car n'obligeant pas d'élément programmable.

## Connectique

La carte doit avoir deux connecteurs (**Jin** et **Jout**) de type MicroFit 3.0 mâle 12 contacts. Les références de ces composant peuvent être chez Molex:
 - 43045-1201 pour une version traversante
 - 43045-1209 pour une version CMS
 
## Pinout

### Digital IO: input (connecteur Jin)

| Numéro de pin | Direction | Type      | Nom   | Description      |
|---------------|-----------|-----------|-------|------------------|
| 1             | Entrée    | Puissance | GND   | GND              |
| 2             | Entrée    | Puissance | 5V    | +5V (100 mA max) |
| 3             |           |           |       | Non connecté  |
| 4             | Entrée    | Logique   | SCK   | Horloge des registres à décalage (5v) |
| 5             | Entrée    | Logique   | MOSI  | Entrée des registres à décalage  (5v) |
| 6             | Sortie    | Logique   | MISO  | Sortie des registres à décalage  (5v) |
| 7             | Entrée    | Logique   | SET   | Application des registres à décalage de sortie  (5v) |
| 8             | Entrée    | Logique   | LATCH | Mémorisaton des registres à décalage en entrée  (5v) |
| 9             | Sortie    | Logique   | TX    | Bus Uart (3v3)  |
| 10            | Entrée    | Logique   | RX    | Bus Uart (3v3)  |
| 11            | Sortie    | Logique   | INT   | Interrupt line (5v) |
| 12            |           |           |       | Non connecté  |

### Digital IO: output (connecteur Jout)

| Numéro de pin | Direction | Type      | Nom   | Description      |
|---------------|-----------|-----------|-------|------------------|
| 1             | Sortie    | Puissance | GND   | GND              |
| 2             | Sortie    | Puissance | 5V    | +5V (100 mA max) |
| 3             |           |           |       | Non connecté  |
| 4             | Sortie    | Logique   | SCK   | Horloge des registres à décalage (5v) |
| 5             | Sortie    | Logique   | MOSI  | Entrée des registres à décalage  (5v) |
| 6             | Entrée    | Logique   | MISO  | Sortie des registres à décalage  (5v) |
| 7             | Sortie    | Logique   | SET   | Application des registres à décalage de sortie  (5v) |
| 8             | Entrée    | Logique   | LATCH | Mémorisaton des registres à décalage en entrée  (5v) |
| 9             | Entrée    | Logique   | RX    | Bus Uart (3v3)  |
| 10            | Sortie    | Logique   | TX    | Bus Uart (3v3)  |
| 11            | Entrée    | Logique   | INT   | Interrupt line (5v) |
| 12            | -         | -         | -     | Non connecté  |

 ## Registres à décalage
  
 ### Registres en entrée
 
La carte doit avoir au minimum un registre à décalage en entrée dans le but d'identifier la carte et ses capacités. Ce registre est nommé **RGCONF**. La définition de ce registre est la suivante :

| Bit | Description |
|-----|-------------|
| 0   | Doit toujours être à 1 si c'est le premier registre à décalage en entrée de la carte. Doit être à 0 dans le cas contraire. |
| 1   | Doit toujours être à 1 si c'est un registre à décalage configurant les capacités de la carte. Doit être à 0 dans le cas contraire. |
| 2   | Doit être à 1 si la carte supporte la liaison UART. Doit être à 0 dans le cas contraire. |
| 3   | Bit 0 du numéro d'indentification de la carte. |
| 4   | Bit 1 du numéro d'indentification de la carte. |
| 5   | Bit 2 du numéro d'indentification de la carte. |
| 6   | Bit 3 du numéro d'indentification de la carte. |
| 7   | Bit 4 du numéro d'indentification de la carte. |

Ensuite la carte peut avoir entre 0 et n registre(s) en entrée définissant le nombre de registres en sorties que la carte posssède. Ces registres sont nommés **ROCONF**. La définition de ces registres est la suivante :

| Bit | Description |
|-----|-------------|
| 0   | Toujours à 0. |
| 1   | Toujours à 1. |
| 2   | Bit 0 du nombre de registres en sortie. |
| 3   | Bit 1 du nombre de registres en sortie. |
| 4   | Bit 2 du nombre de registres en sortie. |
| 5   | Bit 3 du nombre de registres en sortie. |
| 6   | Bit 4 du nombre de registres en sortie. |
| 7   | Bit 5 du nombre de registres en sortie. |

En cas de multiples registres **ROCONF**, le nombre de registres est le suivant :

Nregistres = (ROCONF0 << 0) | (ROCONF1 << 6) | ... | (ROCONFn << 6*n)

Enfin la carte peut avoir entre 0 et n registre(s) en entrée définissant le nombre de registres en entrée (autres que **RGCONF**, **RICONFI** et **ROCONF**) que la carte posssède. Ces registres sont nommés **RICONF**. La définition de ces registres est la suivante :

| Bit | Description |
|-----|-------------|
| 0   | Toujours à 0. |
| 1   | Toujours à 1. |
| 2   | Bit 0 du nombre de registres en entrée (en dehors de ceux de configuration). |
| 3   | Bit 1 du nombre de registres en entrée (en dehors de ceux de configuration). |
| 4   | Bit 2 du nombre de registres en entrée (en dehors de ceux de configuration). |
| 5   | Bit 3 du nombre de registres en entrée (en dehors de ceux de configuration). |
| 6   | Bit 4 du nombre de registres en entrée (en dehors de ceux de configuration). |
| 7   | Bit 5 du nombre de registres en entrée (en dehors de ceux de configuration). |

En cas de multiples registres **RICONF**, le nombre de registres est le suivant :

Nregistres = (RICONF0 << 0) | (RICONF1 << 6) | ... | (RICONFn << 6*n) 
