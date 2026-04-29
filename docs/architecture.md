# Architecture

## Code organization
- `src/main.cpp`: Original firmware logic (preserved) using keypad scanning and direct GPIO LED control.
- `include/`: Reserved for future headers.
- `docs/wiring.md`: Hardware mapping and wiring explanation.

## Runtime flow
1. **Global configuration**
   - Defines keypad layout matrix (`keys[4][4]`).
   - Defines GPIO arrays for LEDs, keypad rows, and keypad columns.
2. **Initialization (`setup`)**
   - Configures all LED pins as outputs.
   - Initializes all LEDs to `LOW` (off).
3. **Main loop (`loop`)**
   - Reads one key event using `keypad.getKey()`.
   - If a valid key is present, applies a `switch` action to set corresponding LEDs.
   - Waits 10 ms (`delay(10)`) between iterations.

## Notes on platform/tooling
- The provided firmware is Arduino-style C++ (uses `Keypad.h`, `setup()`, `loop()`, `pinMode()`, etc.).
- On Pico W, build/run is typically done via an Arduino RP2040 core (or Wokwi Arduino runtime), not plain pico-sdk API calls.
- No Wi-Fi logic is present in the current firmware.

## Assumptions documented
- The board target is Pico W, but pin behavior is identical for GPIO usage vs Pico in this project.
- The wiring interpretation is based directly on the supplied `diagram.json` connections.
