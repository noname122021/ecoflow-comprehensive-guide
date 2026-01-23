# EcoFlow Extra Battery (EB) Compatibility Matrix

This matrix defines which power stations (Main Units) can accept which Extra Batteries. 

## 🔋 DELTA Series Compatibility

| Extra Battery Model | Capacity | Chemistry | **DELTA 2** | **DELTA 2 Max** | **DELTA Max (1600)** | **DELTA Max (2000)** | **DELTA Pro** | **DELTA Pro 3** |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **DELTA 2 EB** | 1024 Wh | LFP | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ |
| **DELTA 2 Max EB**| 2048 Wh | LFP | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ |
| **DELTA Max EB** | 2016 Wh | NCM | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ |
| **DELTA Pro EB** | 3600 Wh | LFP | ❌ | ❌ | ❌ | ❌ | ✅ | ✅¹ |
| **DELTA Pro 3 EB**| 4096 Wh | LFP | ❌ | ❌ | ❌ | ❌ | ✅ | ✅ |
| **DELTA 3 Plus EB**| 1024 Wh | LFP | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ |
| **BLADE EB** | 1024 Wh | LFP | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ |

## 🔋 RIVER Series Compatibility

The RIVER series is mostly standalone. Only specific models support expansion via dedicated battery modules.

| Extra Battery Model | Capacity | Main Unit | Connection Type |
| :--- | :---: | :--- | :--- |
| **RIVER EB Module** | 288 Wh | RIVER (Original) | Bolt-on (Internal Bus) |
| **RIVER Pro EB** | 720 Wh | RIVER Pro (Original)| Proprietary External Cable |
| **RIVER 3 Max EB** | 245 Wh | RIVER 3 Plus | Proprietary External Cable |

> **Note**: The **RIVER mini** and **RIVER 2** series (2, Max, Pro) have **NO** extra battery ports. They are designed as fixed-capacity units.

¹ *Requires the DELTA Pro to DELTA Pro 3 Adapter cable.*
² *Requires the multi-step adapter chain (see below).*
*   ***Important Note on DELTA Max 1600***: Newer LFP-based batteries (Delta 2 EB, Delta 2 Max EB) are generally **incompatible** with the 1600W model due to firmware limitations and high discharge risks (The 1C Rule).

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
2.  **Sequential Behavior**: When mixing NCM and LFP batteries, the system operates as follows:
    *   **Discharge**: The **Main Unit** usually discharges first and hits 0% before the Extra Battery starts providing significant power (or vice versa, depending on SoC logic).
    *   **Charge**: The **Main Unit** charges last. The Extra Battery is topped up first to maximize its dedicated storage.
3.  **No "Station-to-Station"**: **NEVER** connect two Power Stations together via the Extra Battery ports (e.g., Delta 2 to Delta Max). This can cause back-feeding and irreversible damage to both BMS units.
4.  **Pro vs. Rest**: The "Pro" line (Pro 1, Pro 3, Ultra) uses a physically larger and electrically different connector than the "Standard Delta" line. They are **NOT** interchangeable without specific EcoFlow adapters.
5.  **BLADE EB Secret**: The robotic mower battery (BLADE EB) is electrically identical to a Delta 2 EB and works perfectly with the Delta 2 station using a standard XT150 cable.

---

## 🔌 Cross-Generation Adapter Chain

Connecting a **Pro-tier** battery (Delta Pro / Delta Pro 3 EB) to a **Standard-tier** station (Delta 2 / Delta 2 Max / Delta 3 Plus / Delta 3 Max) is possible but requires a specific chain of adapters because of the different physical connectors (4-pin vs XT150).

### The "Bridge" Sequence:
![Pro 3 EB to Delta 3 Chain](./pro3_eb_to_delta3_chain.jpg)

1.  **Extra Battery** (e.g., DELTA Pro 3 EB) - *Port: Female (4-pin)*
2.  **EB Cable** (In-box with battery) - *Connectors: Male / Male (4-pin)*
3.  **EcoFlow Delta Pro to Smart Generator Adapter** - *In: Female (4-pin) / Out: Female (XT150)*
4.  **XT150 Cable** (Standard) - *Connectors: Male / Male (XT150)*
5.  **Power Station** (e.g., DELTA 3 Plus) - *Port: Female (XT150)*

> **Why this works**: Small stations (Delta 2, 3 Plus, 2 Max) use a 48V-60V battery bus via XT150. Pro batteries also operate in a compatible range (though Pro 3 is "high voltage", its expansion port is adapted for generator/older EBs). The Smart Generator Adapter acts as the physical bridge between the heavy-duty 4-pin EcoFlow connector and the standard XT150.
