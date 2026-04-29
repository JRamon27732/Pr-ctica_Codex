# Pico W Keypad-to-LED Controller

A Raspberry Pi Pico W firmware project that reads a **4x4 keypad** and controls **12 LEDs** according to key input. The firmware logic has been kept functionally identical to the provided source.

## Repository structure

```text
.
├── CMakeLists.txt
├── include/
├── src/
│   └── main.cpp
└── docs/
    ├── architecture.md
    └── wiring.md
```

## Features
- 4x4 keypad scanning via GPIO row/column mapping.
- Direct LED control for 12 output channels.
- Group ON/OFF commands for LED subsets.
- Deterministic polling loop with 10ms delay.

## Hardware summary
See full mapping in [`docs/wiring.md`](docs/wiring.md).

- Board: Raspberry Pi Pico W (RP2040)
- Input: 4x4 membrane keypad
- Outputs: 12 LEDs with 220Ω series resistors
- Additional: 4x 1kΩ keypad row pull-up resistors to 3V3

## Build/flash options

### Option A: Wokwi (recommended for simulation)
1. Create a new Raspberry Pi Pico project in Wokwi.
2. Paste the provided `diagram.json` into `diagram.json` in Wokwi.
3. Use `src/main.cpp` as your sketch source (Arduino-style).
4. Start simulation and open Serial Monitor if needed.

### Option B: Real hardware (Pico W)
Because the code uses Arduino APIs (`setup/loop`, `Keypad.h`), use an **Arduino-compatible RP2040 environment**:
1. Install Arduino IDE 2.x.
2. Install an RP2040 core (e.g., “Raspberry Pi RP2040 Boards”).
3. Install the `Keypad` library from Library Manager.
4. Select board: **Raspberry Pi Pico W**.
5. Wire according to [`docs/wiring.md`](docs/wiring.md).
6. Build and upload.

## Notes about `CMakeLists.txt`
A minimal `CMakeLists.txt` is included only to provide a clean repository structure as requested. The current source is Arduino-style and is not a drop-in plain pico-sdk app without adaptation.

## Wi-Fi configuration
- No Wi-Fi functionality is used in the current firmware.
- No credentials are required or stored.

## Core logic preservation
The key handling and LED behavior were preserved from the supplied code; only repository organization and documentation were added.
