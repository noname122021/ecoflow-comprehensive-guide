# EcoFlow Extra Battery (EB) Compatibility Matrix

This matrix defines which power stations (Main Units) can accept which Extra Batteries. 

## 🔋 DELTA Series Compatibility

| Extra Battery Model | Capacity | Chemistry | **DELTA 2** | **DELTA 2 Max** | **DELTA Max** | **DELTA Pro** | **DELTA Pro 3** |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **DELTA 2 EB** | 1024 Wh | LFP | ✅ | ✅ | ✅ | ❌ | ❌ |
| **DELTA 2 Max EB**| 2048 Wh | LFP | ✅ | ✅ | ✅ | ❌ | ❌ |
| **DELTA Max EB** | 2016 Wh | NCM | ✅ | ✅ | ✅ | ❌ | ❌ |
| **DELTA Pro EB** | 3600 Wh | LFP | ❌ | ❌ | ❌ | ✅ | ✅¹ |
| **DELTA Pro 3 EB**| 4096 Wh | LFP | ❌ | ❌ | ❌ | ✅ | ✅ |
| **DELTA 3 Plus EB**| 1024 Wh | LFP | ✅ | ✅ | ✅ | ❌ | ❌ |

¹ *Requires the DELTA Pro to DELTA Pro 3 Adapter cable.*

---

## 🏗 Generations Explained

### Version 1 (V1) - The NCM Era
*   **Models**: DELTA Max EB (2016Wh), RIVER Pro EB (720Wh).
*   **Chemistry**: NCM (Lithium Nickel Cobalt Manganese).
*   **Lifespan**: ~800 cycles to 80%.
*   **Compatibility**: Can be used with V2 units (like Delta 2 Max), but the battery will drain/charge at its native NCM speed, which is slower than LFP.

### Version 2 (V2) - The LFP Era
*   **Models**: DELTA 2 EB, DELTA 2 Max EB, DELTA Pro EB.
*   **Chemistry**: LFP (LiFePO4).
*   **Lifespan**: 3000+ cycles to 80%.
*   **Compatibility**: "Universal" within the Delta 2/Max family.

### Version 3 (V3) - The Pro 3 Era
*   **Models**: DELTA Pro 3 EB, DELTA 3 Plus EB.
*   **Chemistry**: LFP.
*   **Key Change**: High-voltage architecture in Pro 3.
*   **Backwards Compatibility**: Pro 3 batteries can work with Pro 1 units using a specific cable adapter.

---

## ⚠️ Important Rules for Mixing
1.  **Ports limit**: 
    *   **DELTA 2**: Only 1 Extra Battery port.
    *   **DELTA 2 Max / DELTA Max**: 2 Extra Battery ports. Can mix different batteries (e.g., 1x Delta 2 EB + 1x Delta Max EB).
2.  **Sequential Behavior**: When mixing NCM and LFP batteries, the system often discharges the LFP battery first (higher efficiency) and then the NCM, or vice versa depending on firmware.
3.  **Pro vs. Rest**: The "Pro" line (Pro 1, Pro 3, Ultra) uses a physically larger and electrically different connector than the "Standard Delta" line. They are **NOT** interchangeable without specific EcoFlow adapters.
4.  **DELTA Pro Ultra**: Uses a unique 5+8 pin connector. It is currently isolated from the rest of the Delta ecosystem batteries.
