## 🛠️ Programming Hardware

- **Debugger:** WCH-LinkE (RISC-V Edition)
- **Clip:** 2.54mm Single Row 6-Pin Pogo Test Clip

## 🗺️ Wiring Map: WCH-LinkE to SAO

The Crosswalk SAO v8 uses a 6-pad programming header labeled H1 on the back of the PCB. Connect your WCH-LinkE to the pogo clip according to this 1:1 mapping:

| Pogo Pin | SAO Pad (H1) | WCH-LinkE Connection | Function |
|----------|--------------|------------------------|----------|
| 1        | 5V           | 5V                     | 5V VCC |
| 2        | NRST         | NRST                   | Hardware Reset |
| 3        | UART_TX      | RX                     | Serial Debug Output |
| 4        | UART_RX      | TX                     | Serial Command Input |
| 5        | SWIO         | SWIOS                  | Single-Wire Interface Data |
| 6        | GND          | GND                    | Ground Reference |


## ⚡ Powering the Badge During Flash

The CH32V003 must be powered to accept the firmware.

- **Preferred:** Power via the USB-C port (5V standalone).
- **Alternative:** Power via the SAO header (3.3V from host).

**Note:** The AO3401A MOSFET will automatically manage the power path switching if both are connected.

## 💻 Flashing Procedure

1. **Align Pogo Pins:** Place the 6-pin clip securely onto the H1 pads.
2. **MounRiver Studio Setup:**
   - Ensure the project is set for the CH32V003 target.
   - Verify the WCH-Link is in RISC-V (RV) mode.
3. **Download:** Initiate the flash. The LEDs will execute the Startup Rainbow Splash upon a successful write and reset.

## 🛡️ Hardware Safety

Each of the 6 pins is protected by a TPD1E05U06DPYR-ES ESD diode. This protects the SWIO and UART lines from the static transients often generated when applying pogo pins in the field.
