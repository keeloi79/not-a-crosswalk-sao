# Programming Guide

This guide explains how to flash the "Not Just a Crosswalk" firmware onto the CH32V003 F4P6 microcontroller using the integrated pogo-pin interface.

## 🛠️ Required Tools

- **WCH-LinkE Programmer:** The standard debugger for RISC-V CH32V series MCUs.
- **Pogo Pin Adapter:** A 5-pin pogo clip or jig compatible with the H1 Pogo Clip Pads.

## 🛠️ MounRiver Studio (MRS)

The official IDE for building and downloading the firmware.

## 🔌 Hardware Connection

Connect your WCH-LinkE to the Pogo Clip Pads on the back of the PCB as follows:

| Pogo Pad Label | WCH-LinkE Pin | Function |
|----------------|---------------|----------|
| GND            | GND           | Ground Reference |
| SWIO           | SWIOS         | Single-Wire Interface (Data) |
| NRST           | NRST          | Hardware Reset |
| UART_TX        | RX            | Optional: Debug Output |
| UART_RX        | TX            | Optional: Debug Input |

**Note:** The badge can be powered via the USB-C port or the SAO header during programming.

## 🖥️ Software Steps

1. **Open Project:** Launch MounRiver Studio and import the project from the `/firmware` directory.
2. **Build:** Click the Project -> Build All (Hammer icon) to generate the `.elf` and `.hex` files.
3. **Flash:**
   - Click the Download (Blue arrow) icon.
   - If the MCU is read-protected, MRS will prompt you to unprotect it. Select **Yes**.
   - The IDE will erase the Flash at `0x08000000` and write the new firmware.
4. **Verify:** Upon completion, the badge will execute the Startup Rainbow Splash, fading the 18 LEDs from 0 to full brightness.

## 🛠️ Troubleshooting

- **Connection Failed:** Ensure the pogo pins are making firm, vertical contact with the HD-P2254-11 pads.
- **Power Issue:** If programming via the SAO header, ensure the host badge is providing a stable 3.3V to the Bulk3V3 rail.
- **Flash Error:** If the `LOAD_SETTINGS` function fails to find data, ensure you have not accidentally protected the specific `0x08003FC0` Flash page.
