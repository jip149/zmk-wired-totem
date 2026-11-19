# TOTEM — ZMK Config

Wired split keyboard firmware for the [TOTEM](https://github.com/GEIGEIGEIST/TOTEM) (38 keys) using Seeeduino XIAO RP2040 MCUs connected via TRRS cable.

TRRS must be custom-made, with tip and base crossed. This is because the PCBs are symmetrical. Without a cross-cable, RP2040 UART cannot be used and PIO UART must be used. PIO UART does not handle interrupts, and ZMK polling mode is less reliable.

If you absolutely want a standard cross-cable, see [https://github.com/smjothen/zmk-wired-totem]

## Hardware

- **MCU:** Seeeduino XIAO RP2040 (both halves)
- **Connection:** Wired split via custom TRRS cable with tip and base crossed
- **Central half:** Central half is the right one, because for some reason left central does not work on my keeb

## Keymap

Keymap is unmodified from the origin repository, but I don’t use it and it is untested.

## Building

Requires [ZMK](https://zmk.dev) toolchain, Zephyr SDK, and Python venv with west.

```bash
# Build both halves + generate keymap diagram
make

# Build individual halves
make left
make right

# Regenerate keymap diagram only
make draw

# Flash (hold BOOT button on XIAO while plugging USB)
make flash-left
make flash-right

# Clean build artifacts
make clean
```
