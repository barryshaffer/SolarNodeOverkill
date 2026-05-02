# SolarNodeOverkill

> **Meshtastic Solar Node** — A robust, Meshtastic mesh radio node powered by a 12 VDC / 20 W solar charge system and monitored with an embedded MCU, supporting a RAK 1 W LoRa device. Intened to serve as a self sustained Rooftop / Backyard base Client.

---

## Table of Contents

1. [Overview](#overview)
2. [Features](#features)
3. [Repository Structure](#repository-structure)
4. [Build Illustrations](#build-illustrations)
5. [Schematics](#schematics)
6. [Bill of Materials](#bill-of-materials)
7. [3D Print Files](#3d-print-files)
8. [Assembly Instructions](#assembly-instructions)
9. [Configuration](#configuration)
10. [Contributing](#contributing)
11. [License](#license)

---

## Overview
SolarNodeOverkill is the result of two years of trial, error, and heat-induced frustration. After watching standard Lithium-ion setups melt under the brutal Arizona sun, I built this to actually survive the summer.

### The "Heat-Proof" Strategy
I swapped Li-ion for 12V LiFePO₄ batteries because they’re affordable, easy to find, and—most importantly—can handle higher charging temps without throwing a fit.

To keep things from cooking, I added an ESP32 to act as a thermal babysitter. If the enclosure gets too hot:

- It kicks on an exhaust fan to pull out the heat.

- If things get dangerous, it kills the charging entirely to save the battery.

### The Tech Stack
**The Power:** A 20W monocrystalline solar panel, a dedicated 10A charge controller, and a 12V 6AH LiFePO₄ battery. A 12V-to-5V buck transformer feeds the RAK and ESP32.

**The Brain:** A XIAO ESP32-C6 for monitoring Temp, Current and Voltage as well as controlling enclosure fans and charge disconnect relays. HomeAssistant integration for data logging.    

**The Radio:** A RAK 1W LoRa module for more reliable long-range comms.

### The Build
Everything—except the radio—is tucked into a weatherproof box using custom 3D-printed mounts. To get the best possible signal, the RAK module is mounted directly to a 5.8dBi antenna at the very top of the mast, cutting out the signal loss you'd get from a long cable.

<!-- TODO: Add a hero photo of the completed node -->
![Completed Node](images/hero_complete_node.jpg)

---

## Features

- **20 W solar input** via a 20 V solar panel with PWM charge controller
- **12 V battery bank** (LiFePO₄) for extended multi-cloudy day operation
- **RAK WisNode 1 W LoRa radio** running Meshtastic firmware
- **ESP32 monitoring node** for remote telemetry (voltage, current, temperature)
- **Weatherproof enclosure** with 3D-printed internal mounts
- **Easy connectorised assembly** — no soldering required for the main power harness

---

## Repository Structure

```
SolarNodeOverkill/
├── README.md               ← You are here
├── images/                 ← Build photos and illustrations
├── schematics/             ← Electrical schematics and wiring diagrams
├── bom/                    ← Bill of materials (CSV / spreadsheet)
└── 3d_prints/              ← STL / 3MF files for printed parts
```

---

## Build Illustrations

> _Replace each placeholder link below with the actual image file once it is added to the `images/` folder._

### Complete Assembly

<!-- TODO: Add completed assembly photo -->
![Complete Assembly](images/build_complete_assembly.jpg)

### Enclosure Overview

<!-- TODO: Add enclosure photo showing external layout -->
![Enclosure Overview](images/build_enclosure_overview.jpg)

### Electronics Bay

<!-- TODO: Add photo of internal electronics layout -->
![Electronics Bay](images/build_electronics_bay.jpg)

### Solar Panel Mounting

<!-- TODO: Add photo / diagram of solar panel mount -->
![Solar Panel Mount](images/build_solar_panel_mount.jpg)

### Wiring Harness Detail

<!-- TODO: Add close-up photo of wiring harness and connectors -->
![Wiring Harness](images/build_wiring_harness.jpg)

---

## Schematics

> All schematic source files are stored in the [`schematics/`](schematics/) folder.

| File | Description |
|------|-------------|
| [`schematics/solar_charge_system.pdf`](schematics/solar_charge_system.pdf) | Full solar charge and power distribution schematic |
| [`schematics/esp32_monitor.pdf`](schematics/esp32_monitor.pdf) | ESP32 monitoring node schematic |
| [`schematics/rak_radio_wiring.pdf`](schematics/rak_radio_wiring.pdf) | RAK 1 W LoRa radio wiring diagram |
| [`schematics/solar_charge_system.kicad_sch`](schematics/solar_charge_system.kicad_sch) | KiCad schematic source — solar charge system |
| [`schematics/esp32_monitor.kicad_sch`](schematics/esp32_monitor.kicad_sch) | KiCad schematic source — ESP32 monitor |

<!-- TODO: Embed schematic preview images once exported -->
![Solar Charge Schematic Preview](images/schematic_solar_charge_preview.png)

---

## Bill of Materials

> The full BOM spreadsheet is available at [`bom/bom.csv`](bom/bom.csv).

| # | Component | Description | Qty | Unit Cost (USD) | Supplier / Part # |
|---|-----------|-------------|-----|-----------------|-------------------|
| 1 | Solar Panel | 20 W, 12 V monocrystalline | 1 | <!-- TODO --> | <!-- TODO --> |
| 2 | Solar Charge Controller | MPPT or PWM, 12 V, ≥ 10 A | 1 | <!-- TODO --> | <!-- TODO --> |
| 3 | Battery | 12 V LiFePO₄, ≥ 20 Ah | 1 | <!-- TODO --> | <!-- TODO --> |
| 4 | RAK WisNode LoRa Radio | RAK Wireless 1 W LoRa module | 1 | <!-- TODO --> | <!-- TODO --> |
| 5 | ESP32 Development Board | ESP32-DevKitC or equivalent | 1 | <!-- TODO --> | <!-- TODO --> |
| 6 | Voltage / Current Sensor | INA226 or INA219 module | 1 | <!-- TODO --> | <!-- TODO --> |
| 7 | Buck Converter (5 V) | 12 V → 5 V, ≥ 3 A | 1 | <!-- TODO --> | <!-- TODO --> |
| 8 | Weatherproof Enclosure | IP65 ABS box, ≥ 200×150×75 mm | 1 | <!-- TODO --> | <!-- TODO --> |
| 9 | LoRa Antenna | 915 MHz (or regional freq.), N/SMA | 1 | <!-- TODO --> | <!-- TODO --> |
| 10 | Cable Glands | PG-7 or PG-9, waterproof | 4 | <!-- TODO --> | <!-- TODO --> |
| 11 | Anderson Powerpole Connectors | 30 A, red/black pairs | 1 pkg | <!-- TODO --> | <!-- TODO --> |
| 12 | Printed Parts | See [3D Print Files](#3d-print-files) | — | — | This repo |
| 13 | Misc. Hardware | M3/M4 screws, standoffs, zip ties | 1 lot | <!-- TODO --> | <!-- TODO --> |

---

## 3D Print Files

> All print files are stored in the [`3d_prints/`](3d_prints/) folder. Recommended slicer settings are noted per part.

| File | Description | Material | Layer Height | Infill |
|------|-------------|----------|--------------|--------|
| [`3d_prints/enclosure_din_rail_mount.stl`](3d_prints/enclosure_din_rail_mount.stl) | DIN-rail clip for mounting inside enclosure | PETG | 0.2 mm | 40 % |
| [`3d_prints/esp32_carrier_tray.stl`](3d_prints/esp32_carrier_tray.stl) | Tray holding the ESP32 dev board | PETG | 0.2 mm | 30 % |
| [`3d_prints/rak_radio_bracket.stl`](3d_prints/rak_radio_bracket.stl) | Bracket securing the RAK radio module | PETG | 0.2 mm | 30 % |
| [`3d_prints/battery_cradle.stl`](3d_prints/battery_cradle.stl) | Cradle holding the 12 V battery pack | PETG | 0.2 mm | 40 % |
| [`3d_prints/solar_panel_tilt_mount.stl`](3d_prints/solar_panel_tilt_mount.stl) | Adjustable tilt mount for the solar panel | PETG/ASA | 0.2 mm | 50 % |
| [`3d_prints/cable_management_clips.stl`](3d_prints/cable_management_clips.stl) | Interior wire routing clips | PETG | 0.2 mm | 20 % |

<!-- TODO: Add render / preview images of printed parts -->
![3D Print Preview](images/3d_prints_preview.png)

---

## Assembly Instructions

> _Detailed step-by-step instructions will be added here. Follow the numbered steps and refer to the linked images._

### Step 1 — Print All Parts

<!-- TODO: Add instructions for printing and post-processing parts -->
1. Download all STL files from the [`3d_prints/`](3d_prints/) folder.
2. Slice using the settings in the table above.
3. Print and remove supports as needed.

### Step 2 — Prepare the Enclosure

<!-- TODO: Add instructions and photo for drilling cable gland holes -->
1. Mark and drill holes for cable glands on the enclosure (see [wiring diagram](schematics/solar_charge_system.pdf)).
2. Install cable glands and confirm watertight fit.

![Enclosure Preparation](images/assembly_step2_enclosure_prep.jpg)

### Step 3 — Install Printed Mounts

<!-- TODO: Add instructions and photo for mounting printed parts inside enclosure -->
1. Attach the DIN-rail mount to the enclosure base.
2. Snap the component trays and brackets onto the DIN rail.

![Mount Installation](images/assembly_step3_mounts.jpg)

### Step 4 — Wire the Power System

<!-- TODO: Add instructions and photo for power wiring -->
1. Connect the battery to the charge controller following the schematic [`schematics/solar_charge_system.pdf`](schematics/solar_charge_system.pdf).
2. Wire the solar panel leads through the cable gland to the charge controller solar input.
3. Connect the 5 V buck converter to the 12 V load terminals.

![Power Wiring](images/assembly_step4_power_wiring.jpg)

### Step 5 — Install the ESP32 Monitor

<!-- TODO: Add instructions and photo for ESP32 wiring -->
1. Mount the ESP32 board in its carrier tray.
2. Connect the INA226 sensor in-line with the battery positive lead.
3. Wire I²C (SDA/SCL) and power from the buck converter to the ESP32.

![ESP32 Install](images/assembly_step5_esp32.jpg)

### Step 6 — Install the RAK Radio

<!-- TODO: Add instructions and photo for RAK radio installation -->
1. Seat the RAK LoRa module in its bracket.
2. Connect the antenna cable and route the antenna lead through a cable gland.
3. Wire power and UART to the ESP32 or dedicated 5 V rail.

![RAK Radio Install](images/assembly_step6_rak_radio.jpg)

### Step 7 — Final Checks and Weatherproofing

<!-- TODO: Add instructions for final checks -->
1. Verify all connections against the wiring diagrams.
2. Power on and confirm charge controller LED indicators and Meshtastic radio boot.
3. Torque all cable gland locknuts and close the enclosure.

---

## Configuration

### Meshtastic Radio (RAK module)

<!-- TODO: Add Meshtastic configuration instructions and screenshots -->
1. Flash the latest Meshtastic firmware via the [Meshtastic Flasher](https://flasher.meshtastic.org/).
2. Configure channel, region, and device role using the Meshtastic app or CLI.

### ESP32 Monitor Firmware

<!-- TODO: Add firmware flashing and configuration instructions -->
1. Open the firmware project (link TBD) in PlatformIO or Arduino IDE.
2. Edit `config.h` to set your Wi-Fi credentials and MQTT broker address.
3. Flash to the ESP32 over USB.

---

## Contributing

Contributions are welcome!  Please open an issue or pull request for:

- Corrected schematics or BOM entries
- Improved 3D print files
- Additional build photos
- Documentation improvements

---

## License

<!-- TODO: Choose and add a license -->
_License TBD — see [LICENSE](LICENSE) file once added._
