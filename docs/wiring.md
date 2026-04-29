# Wiring (Raspberry Pi Pico W)

## Overview
This project connects a **4x4 matrix keypad** to a **Raspberry Pi Pico W** and drives **12 LEDs** based on key presses.

> Diagrama (resumen breve): Un Raspberry Pi Pico conectado a un teclado matricial 4x4 y 12 LEDs con resistencias limitadoras de corriente. El teclado usa 8 GPIO (4 filas + 4 columnas), cada LED se controla por un GPIO dedicado, y todos comparten GND; además, las filas del keypad tienen pull-up a 3V3.

## Components list (derived from `diagram.json`)
- 1x Raspberry Pi Pico / Pico W board
- 1x 4x4 membrane keypad
- 12x LEDs (8 blue + 4 red in the Wokwi diagram)
- 12x 220Ω resistors (LED current limiting)
- 4x 1kΩ resistors (keypad row pull-ups to 3V3)
- Jumper wires / breadboard wiring

## GPIO mapping

### Keypad pins
| Keypad Signal | Pico GPIO |
|---|---|
| C1 | GP19 |
| C2 | GP18 |
| C3 | GP17 |
| C4 | GP16 |
| R1 | GP26 |
| R2 | GP22 |
| R3 | GP21 |
| R4 | GP20 |

### LED outputs
| Logical LED | GPIO | Wokwi Label |
|---|---:|---|
| LED1 | GP11 | 1 |
| LED2 | GP10 | 2 |
| LED3 | GP9  | 3 |
| LED4 | GP8  | 4 |
| LED5 | GP7  | 5 |
| LED6 | GP6  | 6 |
| LED7 | GP5  | 7 |
| LED8 | GP4  | 8 |
| LED9 | GP3  | A |
| LED10 | GP2 | B |
| LED11 | GP28 | C |
| LED12 | GP27 | D |

## Power and grounding
- LED cathodes are tied to GND.
- Each LED anode goes through a 220Ω resistor to its GPIO.
- Keypad row signals (R1..R4) are additionally pulled up to 3V3 with 1kΩ resistors in the provided diagram.

## Behavioral mapping summary
- Keys `1..8` control LEDs 1..8 individually ON.
- Key `9` turns LEDs 1..8 ON.
- Key `0` turns LEDs 1..8 OFF.
- Keys `A..D` control LEDs 9..12 individually ON.
- Key `*` turns LEDs 9..12 ON.
- Key `#` turns LEDs 9..12 OFF.
