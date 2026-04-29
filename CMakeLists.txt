cmake_minimum_required(VERSION 3.13)
project(pico_w_keypad_led C CXX)

# Note: this source uses Arduino-style APIs (setup/loop, pinMode, digitalWrite,
# delay, Keypad library). Build with an RP2040 Arduino core/toolchain or adapt
# to pico-sdk APIs if needed.

add_executable(pico_w_keypad_led
  src/main.cpp
)

target_include_directories(pico_w_keypad_led PRIVATE include)
