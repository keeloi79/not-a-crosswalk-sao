# Memory Map: Flash Persistence Logic

The **Not Just a Crosswalk SAO** uses the internal Flash memory of the CH32V003 to store user preferences. This ensures that once a palette or effect is chosen, it is "locked in" and will survive even if the badge is disconnected from its power source.

---

## 📍 Flash Layout

The CH32V003F4P6 features **16 KB of Flash memory**. To avoid interfering with the application code, the settings are stored in the very last page of the memory space.

*   **Flash Start Address:** `0x08000000`
    
*   **Settings Page Address:** `0x08003FC0`
    
*   **Page Size:** 64 Bytes

---

## 🏗 Data Structure

The state is packed into a single **32-bit word** (4 bytes) to minimize Flash write cycles and ensure atomic updates.

| **Byte Offset** | **Content** | **Description** |
| --- | --- | --- |
| **0x00** | `effect_index` | The index of the currently active animation (0–18). |
| **0x01** | `palette_index` | The index of the currently active color flag (0–13). |
| **0x02** | `0x00` | Reserved for future use (e.g., brightness level). |
| **0x03** | `0x00` | Reserved/Padding. |

---

## 🔄 Software Flow

### 1. The Save Trigger (`SAVE_SETTINGS`)

Whenever a button interrupt is detected on **PD2** (Palette) or **PD3** (Effect), the system immediately commits the new state to Flash.

1.  **Unlock:** The Flash controller is unlocked for write access.
    
2.  **Erase:** The 64-byte page at `0x08003FC0` is erased (set to all `1`s).
    
3.  **Program:** The new 32-bit word is written.
    
4.  **Lock:** The Flash controller is locked to prevent accidental corruption.

---

### 2. The Restore Process (`LOAD_SETTINGS`)

On boot, immediately after the **Startup Rainbow Splash**, the system reads the word at the settings address.

*   If the address contains `0xFFFFFFFF`, the Flash is empty, and the badge defaults to the Rainbow Flag (Palette 0).
    
*   If a valid value is found, the `palette_index` and `effect_index` are updated, and the `idle_timer` is synced to ensure the correct behavior (Static vs. Animation).

---

## 🛠 Stability & Endurance

*   **Persistence as Protest:** By writing to the Flash, we ensure that the visibility of the LGBTQ+ colors cannot be "reset" by a simple power cycle.
    
*   **Wear Leveling:** Since writes only occur on physical button presses, the 10,000+ cycle endurance of the CH32V003 Flash is more than sufficient for years of conference use.
