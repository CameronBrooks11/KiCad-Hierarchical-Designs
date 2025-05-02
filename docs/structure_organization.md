# Structure and Organization

## Naming Convention

The goal of this naming convention, although seemingly pedantic, is to balance **readability**, **reusability**, and **clarity** across schematic modules. The convention is designed to scale to many files without ambiguity while remaining human-readable in both a previously hierarchical and now flattened folder structure.

### General Format

`<category>_<main_part>_<role>[_<details>]`

- All filenames begin with a **category prefix** (e.g., `adc_`, `power_`, `digital_`) reflecting their original folder.
- Use **lowercase** and **underscores** by default.
- Underscores (`_`) represent **spaces**.
- Dashes (`-`) represent **slashed relationships** or physical division (e.g., `vin-vout`, `tx-rx`, `spi-sd`).
- **CamelCase is allowed** _only_ to:
  - Distinguish unit designations or protocols clearly (e.g., `usbC`, `sdram32MiB`, `vRefMid`).
  - Express meaning that would otherwise be ambiguous with underscores or dashes.
- Acronyms (e.g., `adc`, `mcu`, `ldo`) remain **lowercase**, unless clarity is improved with mixed case (e.g., `sdram32MiB` instead of `sdram_32mib`).

### Examples

| File Name                                       | Meaning                               |
| ----------------------------------------------- | ------------------------------------- |
| `microcontrollers_mcu_stm32f405_rgtx.kicad_sch` | STM32F405-based microcontroller core  |
| `interface_usbC_interface.kicad_sch`            | USB-C interface connector or circuit  |
| `power_fet_switch_nopd.kicad_sch`               | FET-based switch with no pulldown     |
| `adc_diff_spi_ads1220.kicad_sch`                | Differential SPI ADC using ADS1220    |
| `memory_sdram32MiB_module.kicad_sch`            | 32 MiB SDRAM memory module            |
| `power_voltage_divider_5v-3v3.kicad_sch`        | Voltage divider from 5V to 3.3V       |
| `digital_tx-rx_level_shifter.kicad_sch`         | Level shifter between TX and RX lines |

## 📁 Folder Layout

The design has been **flattened**: all schematic files now reside directly in the `kicad-hierarchical-designs/` directory, with the **category encoded as a prefix** in each filename.

| Category Prefix     | Description                                                    |
| ------------------- | -------------------------------------------------------------- |
| `adc_`              | ADCs for various signal types (RTD, thermocouple, diff, etc.)  |
| `analog_`           | Analog frontends, filters, amplifiers, and signal conditioning |
| `digital_`          | Digital logic, IO, displays, debounce, level shifting          |
| `interface_`        | USB, UART, CAN, SPI, SD, transceivers, STLink, etc.            |
| `memory_`           | EEPROMs, SDRAM, QSPI flash, and memory ICs                     |
| `microcontrollers_` | MCU subsystems (STM32, ATmega, ESP32, etc.)                    |
| `power_`            | Regulators, converters, protection, motor drivers, switches    |
| `sensor_`           | Sensor frontends and interface ICs (IMUs, DHT, etc.)           |

## 🔄 Expansion Plan

If future reorganization or folder structure is needed, names can still be parsed based on prefixes. Possible subtyping through the third section of the filename can allow:

- `power_ldo_...`, `power_dcdc_...`, `power_charger_...`
- `interface_usb_...`, `interface_can_...`, `interface_uart_...`
- `adc_diff_...`, `adc_rtd_...`, `adc_thermocouple_...`

## 🧩 Reuse

Each `.kicad_sch` file in this repository is a **modular, reusable hierarchical sheet**, intended to be imported into other KiCad projects via **relative paths**. All designs conform to consistent naming and interface standards for ease of reuse and integration.
