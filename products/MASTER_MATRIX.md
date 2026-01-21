# EcoFlow Master Device & Compatibility Matrix

| Product Name | Release | Capacity | Batt. Chemistry | Price (Launch/Avg) | Output (AC) | Solar Input (Max) | Expansion Units |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :--- |
| **DELTA Pro 3** | 2024 | 4096 Wh | LFP | $3,699 / $3,299 | 4000W | 2600W | DP3 EB, DP EB |
| **DELTA 3 Plus** | 2024 | 1024 Wh | LFP | $999 / $799 | 1800W | 500W | DP3 EB |
| **DELTA 2 Max** | 2023 | 2048 Wh | LFP | $1,899 / $1,599 | 2400W | 1000W | D2M EB, D2 EB, DM EB |
| **RIVER 2 Pro** | 2022 | 768 Wh | LFP | $599 / $479 | 800W | 220W | None |
| **DELTA 2** | 2022 | 1024 Wh | LFP | $999 / $649 | 1800W | 500W | D2 EB, DM EB |
| **Smart Generator**| 2022 | 5.4 kWh (Gas)| N/A | $1,599 | 1800W | N/A | Pairs with Delta Max/Pro |
| **Power Kit Hub** | 2022 | Modular | LFP (Ext) | $3,000+ | 3600W | 4800W | 2kWh / 5kWh LFP Batt |
| **DELTA Pro** | 2021 | 3600 Wh | LFP | $3,699 / $2,500 | 3600W | 1600W | DP EB |
| **DELTA Max 2000** | 2021 | 2016 Wh | NCM | $2,099 / $1,299 | 2400W | 800W | DM EB |
| **DELTA Mini** | 2021 | 882 Wh | NCM | $999 / $699 | 1400W | 300W | None |
| **RIVER Pro** | 2020 | 720 Wh | NCM | $649 / $449 | 600W | 200W | River Pro EB |
| **DELTA 1300** | 2019 | 1260 Wh | NCM | $1,399 / $899 | 1800W | 400W | None |

## 🔗 Connection Combinations (What works with what?)

### 1. The "Infinite" Battery Chain (Delta Series)
*   **Detailed View**: See the **[Extra Battery Compatibility Matrix](BATTERY_COMPATIBILITY.md)** for V1, V2, and V3 differences.
*   **Delta 2** -> [Delta 2 Extra Battery] OR [Delta 2 Max EB]
*   **Delta 2 Max** -> [Delta 2 Max EB] OR [Delta 2 EB] OR [Delta Max EB]
*   **Delta Pro** -> [Delta Pro Extra Battery] (Proprietary cable)
*   **Delta Pro 3** -> [DP3 Extra Battery] OR [DP Extra Battery] (via Adapter)

### 2. Charging Combos
*   **Alternator Charger (800W)** -> Works natively with Delta 2, Delta 2 Max, Delta Max (XT150).
    *   *Adapter needed for*: Delta Pro, Delta Pro 3.
*   **PowerStream** -> Works with ALL Delta and River units. 
    *   *Efficiency Tip*: Use BKW-DeltaPro cable for best power throughput (600W-800W).

### 3. Smart Generator Auto-Start
*   **Supported by**: Delta Max, Delta Pro, Delta 2 Max, Power Kits.
*   **Cable**: Uses the Extra Battery port cable (with data pins).

## 🛠 Hackable Pairs
*   **Delta 2** + **Generic 48V Server Rack Battery**: Possible via "Resistor Hack" (See [Hardware Mods](../hardware/EXTRA_BATTERY.md)).
*   **EcoFlow 5kWh LFP Battery** + **Victron Inverter**: Possible via [Polarity Adapter](ECOSYSTEM.md).
