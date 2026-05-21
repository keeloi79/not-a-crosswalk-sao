# not-a-crosswalk-sao

# "Not Just a Crosswalk" SAO project for DEFCON 34

🏳️‍🌈 The Mission: Why "Not Just a Crosswalk"?
This project is a hardware-based protest against the systemic removal and erasure of LGBTQ+ visibility in public spaces across the United States.

Between 2025 and early 2026, a series of state-level mandates and judicial rulings led to the forced removal of rainbow-painted crosswalks—symbols of inclusion and safety—in cities like Miami Beach, Austin, Gainesville, and San Antonio.

Florida: Cities were forced to race against state-imposed deadlines to remove inclusive street art.

Texas: Landmarks were removed despite legal challenges and intense community protest.

A hardware and firmware project for the DEFCON badge. This repository contains documentation, schematics, firmware, and build instructions.

## Overview

This project is a Simple Add-On (SAO) designed for Defcon 34. It features 18 WS2812-2020 LEDs, a persistent memory system for saving user preferences, and a suite of high-refresh-rate animations optimized for the RISC-V architecture.

## Features: 
- 18x side-emitting SK6812D-EC3210R LEDs: Configured for high-density complex visual patterns and impact.
- Persistent State: Automatically saves palette and effect indexes to the CH32V003 Flash memory.
- Flicker-Free Pulse: Custom-tuned PWM logic to ensure smooth "breathing" even at 1% duty cycle.
- SAO V1.69bis/V2.0 Compatible: Designed to run safely on host badge power.
- Low Power Optimization: 100% integer-based math for maximum efficiency and minimum heat.
- Microcontroller: MCU: CH32V003 F4P6 (TSSOP20) (RISC-V)
  - ESD protection: TPD1E05U06DPYR-ES ESD protection on 3V3/5V and exposed pins/pads.
  - Input Power: 3.3V via SAO Header step up to 5V or USB-C 5V.
  - Boost Converter: MT3608L steps 3.3V up to 5V to maintain full LED brightness when powered by a host badge. Uses an AO3401A P-Channel MOSFET to automatically disable the boost converter when standalone USB-C 5V power is detected
  - Decoupling: Integrated 10µF and 47µF bulk capacitance for the 3V3 and 5V rails and 18-capacitor array (100nF each) for LED stability
  - Programming: WCH-LinkE (SWIO)
  - Interface
    - LEDFX-PD3: Tactile button on PD3 for effect cycling.
    - LEDPALETTE-PD2: Tactile button on PD2 for palette changes. 
  
## Table of Contents

- [Hardware](#hardware)
- [Firmware](#firmware)
- [Build & Flash](#build-and-flash)
- [BOM](#bom)
- [Changelog](#changelog)
- [License](#license)

## Hardware

See [hardware.md](docs/HARDWARE.md) for details on components, connectors, and PCB layout.

## Firmware

See [firmware.md](docs/firmware.md) for build instructions and code structure.

## BOM & Sourcing

See [BOM.md](docs/BOM.md) for the component list. I used JLCPCB.com PCB Assembly service for this project.

# 🤝 Credits & Acknowledgments

The Not Just a Crosswalk SAO is built upon the contributions of the open-source hardware and software community. We are proud to acknowledge the following creators and tools:

## 💾 Software & Firmware

- **WS2812 Driver for CH32V003:** This project utilizes the high-performance WS2812 driver developed by Blake Sands. His work is licensed under GPLv3, which ensures that the low-level timing logic remains open for all. https://github.com/Blakesands/CH32V003

## 🛠 Hardware & Manufacturing

- **Design Tooling:** The schematics and PCB layout were designed using EasyEDA.
- **PCBA & Fabrication:** All PCBs were professionally manufactured and assembled by JLCPCB, ensuring the precision placement of the 0402/0603 SMDs and side-emitting LEDs.

## 🎨 Community & Inspiration

- **Tod Kurt (@todbot):** For the TouchwheelSAO repository structure and documentation style that I used as a basis for this project. https://github.com/todbot/TouchwheelSAO

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for version history.

## License

GPL3 License. See [LICENSE](LICENSE).
