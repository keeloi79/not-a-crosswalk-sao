# Electrical Safety & Compliance

This project is an advanced Simple Add-On (SAO) designed for use in the Defcon/Conference ecosystem. While every effort has been made to ensure host compatibility, users should be aware of the following electrical specifications and safety features.

---

## ⚡ SAO 1.69bis / V2.0 Power Compliance

The **Not Just a Crosswalk SAO** is designed to operate within the standard power envelopes of modern badges.

*   **Input Voltage:** Accepts a standard **3.3V** via the SAO connector.
    
*   **Current Management:** To prevent brown-outs on host badges, the firmware utilizes a **Startup Rainbow Splash** that gradually ramps up brightness, avoiding a massive inrush current spike.
    
*   **Internal Boost:** The badge uses an **MT3608L Boost Converter** to step the 3.3V SAO rail up to **5V** specifically for the LED array.

---

## 🛡️ Hardware Safety Features

This hardware incorporates several "conference-hardened" safety mechanisms to protect itself and the host badge:

*   **Dual Power Isolation:** An **AO3401A P-Channel MOSFET** is used to automatically disable the boost converter when **5V USB-C** power is detected. This prevents the 5V USB rail from back-feeding into the host badge's 3.3V rail.
    
*   **ESD Protection:** All exposed test points, buttons, and programming pads are protected by **TPD1E05U06DPYR-ES ESD diodes** to prevent damage from static discharge in crowded environments.
    
*   **Bulk Capacitance:** The circuit includes **47µF bulk capacitors** and a **20-capacitor decoupling array** (100nF each) to smooth out current surges and reduce electrical noise on the host power lines.

---

## 💾 Software Persistence

The mission of visibility is supported by technical persistence.

*   **Flash Wear Leveling:** The badge writes to the **CH32V003's internal Flash (0x08003FC0)** only when a button is pressed to change a setting. This minimizes the risk of Flash degradation over the life of the badge.
    
*   **Non-Blocking Logic:** The main loop is designed to ensure button interrupts are handled immediately, preventing the badge from becoming unresponsive.

---

## ⚖️ Liability

This project is provided "as is" under the **MIT License**. While the hardware and firmware have been rigorously tested on the **Crosswalk SAO v8** revision, the developers are not responsible for damage to host badges or secondary hardware resulting from improper assembly or modification.

This file demonstrates that you’ve considered the electrical reality of the SAO ecosystem—especially the risks of 5V back-feeding and current spikes.
