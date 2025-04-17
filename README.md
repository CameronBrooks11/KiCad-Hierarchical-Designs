# KiCad-Hierarchical-Schematics

A collection of common components and their typical application circuits done in KiCad.

This is a modular library of reusable hierarchical sheets for KiCad projects. All sheets are organized by function and limited to a two-level folder structure for clarity and scalability.

## Structure & Organization

## Naming Convention

The goal of this naming convention, although seemingly pedantic, is to balance **readability**, **reusability**, and **clarity** across schematic modules. The convention is designed to scale to many files without ambiguity while remaining human-readable in a flat or hierarchical folder structure.

### General Format

`<main_part>_<role>[_<details>]`

- Use **lowercase** and **underscores** by default.
- Underscores (`_`) represent **spaces**.
- Dashes (`-`) represent **slashed relationships** or physical division (e.g., `vin-vout`, `tx-rx`, `spi-sd`).
- **CamelCase is allowed** _only_ to:
  - Distinguish unit designations or protocols clearly (e.g., `usbC`, `sdram32MiB`, etc.).
  - Express meaning that would otherwise be ambiguous with underscores or dashes.
- Acronyms (e.g., `adc`, `mcu`, `ldo`) should stay **lowercase** unless clarity is genuinely improved with mixed case (e.g., `sdram32MiB` instead of `sdram_32mib`).

### Examples

| File Name                          | Meaning                                 |
| ---------------------------------- | --------------------------------------- |
| `stm32f405_core.kicad_sch`         | STM32F405 microcontroller core          |
| `usbC_interface.kicad_sch`         | USB-C interface connector or circuit    |
| `fet_switch_nopd.kicad_sch`        | FET power switch without pulldown       |
| `adc_diff_ads1220.kicad_sch`       | Differential ADC frontend using ADS1220 |
| `sdram32MiB.kicad_sch`             | 32 MiB SDRAM module                     |
| `voltage_divider_5v-3v3.kicad_sch` | Voltage divider from 5V to 3.3V         |
| `tx-rx_level_shifter.kicad_sch`    | Level shifter between TX/RX lines       |

### 📁 Folder Structure

- `/analog` — Analog frontends and signal conditioning modules.
- `/digital` — Pure digital logic, GPIO expanders, display drivers, debounce, etc.
- `/interface` — Communication interfaces (USB, UART, CAN, RS-232, SPI, etc.).
- `/power` — Power supply circuits including regulators, converters, and switching elements.
- `/sensors` — Sensor frontends including analog/digital interfaces for ADCs and sensor ICs.
- `/microcontrollers` — Microcontroller cores, boot circuits, and supporting logic.
- `/templates` — Example top-level project sheets using combinations of the above modules.
- `/khd-master-lib.kicad_pro` — Top-level project file to manage and visualize all modules together.

### 🔄 Expansion Plan

Each main folder may include subfolders in the future if needed:

- `analog/opamp/`, `analog/instrumentation/`
- `digital/display_drivers/`, `digital/timers/`
- `interface/wireless/`, `interface/usb/`
- `power/dcdc/`, `power/linear/`, `power/protection/`
- `sensors/temp/`, `sensors/accel_gyro/`
- `microcontrollers/stm32/`, `microcontrollers/atmega/`, `microcontrollers/esp32/`

### 🧩 Reuse

Each `.kicad_sch` file in this repository is intended to be imported as a hierarchical sheet into other KiCad projects using relative paths. All designs follow modular design conventions and are compatible with modern KiCad practices.

## Acknowledgements

Many modules derived from: [williamweatherholtz/kicad_subs](https://github.com/williamweatherholtz/kicad_subs/tree/master)
