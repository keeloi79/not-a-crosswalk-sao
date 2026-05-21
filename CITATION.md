# The Case for Visibility

This document catalogs the systemic removal of LGBTQ+ rainbow crosswalks, documenting both the recent 2025–2026 state-led removals and the long-standing federal "safety compliance" pressure used to justify the erasure of queer spaces.

---

## 🏛 The Federal Precedent: FHWA and the MUTCD

The removal of rainbow crosswalks is often framed as a technical necessity based on the **Manual on Uniform Traffic Control Devices (MUTCD)**. This federal standard has been used for years as a tool to pressure local municipalities into removing inclusive art.

*   **Ames, Iowa (2019):** In one of the earliest high-profile federal interventions, the Trump administration's Federal Highway Administration (FHWA) directed the city of Ames to remove its rainbow crosswalks, claiming they were non-compliant. In a rare act of defiance, the city council voted to keep them, arguing the FHWA had no legal authority to force removal on local streets.
    
*   **Lexington, Kentucky:** The FHWA issued similar requests to Lexington, citing "pedestrian safety concerns" over the non-standard colors, leading to a protracted debate over local vs. federal control of city aesthetics.

---

## 🏛 2025–2026: The New Wave of Erasure

Beginning in 2025, state and federal initiatives shifted from "requests" to mandatory "removal deadlines," leading to a nationwide reduction in visibility.

### 🦀 Maryland: Infrastructure as Erasure

*   **Salisbury (November 2025):** Mayor Randy Taylor announced that the city's rainbow crosswalks would be repaved and returned to "standard markings." While framed as a routine repaving project, the move followed a trend of municipalities using maintenance schedules to bypass community opposition to the removal of pride symbols.

---

### 🤠 Texas: The 2026 Removal Campaign

*   **Dallas (Oak Lawn/Cedar Springs - March 2026):** In a move described by residents as an "attempt to demoralize," decorative rainbow crosswalks in Dallas's primary LGBTQ+ district were stripped and repaved as part of a sudden compliance sweep.
    
*   **Houston (Montrose - 2024–2026):** The six-mile Westheimer improvement project, which broke ground in May 2024, resulted in the "standardization" of intersections in the Montrose neighborhood, effectively phasing out neighborhood-specific decorative markings in the name of transit optimization.

---

## 💻 The Engineering Response: Digital Persistence

While physical landmarks can be paved over, the **"Not Just a Crosswalk" SAO** utilizes hardware-level persistence to ensure these symbols remain lit and unerasable.

1.  **Non-Volatile Memory:** By utilizing the **CH32V003's internal Flash (address `0x08003FC0`)**, the badge "remembers" its identity through power cycles.
    
2.  **Logic-Based Resistance:** The `LOAD_SETTINGS` function ensures that even if the badge is disconnected, the user's chosen colors are restored the moment power returns—acting as a digital landmark that cannot be "paved over".
    
3.  **Firmware Integrity:** The **Startup Rainbow Splash** reinforces the core mission every time the hardware is initialized, asserting visibility before a single line of animation logic begins.
