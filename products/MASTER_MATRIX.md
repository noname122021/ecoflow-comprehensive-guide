## 🟥 DELTA Series (High Power / Home Backup)

| Product Name | Release | Capacity | Batt. Chemistry | Price (Launch/Avg) | Output (AC) | Solar Input (Max) | Expansion Units |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :--- |
| **DELTA Pro 3** | 2024 | 4096 Wh | LFP | $3,699 / $3,299 | 4000W | 2600W | DP3 EB, DP EB |
| **DELTA 3 Plus** | 2024 | 1024 Wh | LFP | $999 / $799 | 1800W | 500W | DP3 EB |
| **DELTA 2 Max** | 2023 | 2048 Wh | LFP | $1,899 / $1,599 | 2400W | 1000W | D2M EB, D2 EB, DM EB |
| **DELTA 2** | 2022 | 1024 Wh | LFP | $999 / $649 | 1800W | 500W | D2 EB, DM EB |
| **DELTA Pro** | 2021 | 3600 Wh | LFP | $3,699 / $2,500 | 3600W | 1600W | DP EB |
| **DELTA Max 2000** | 2021 | 2016 Wh | NCM | $2,099 / $1,299 | 2400W | 800W | DM EB |
| **DELTA Max 1600** | 2021 | 1612 Wh | NCM | $1,799 / $1,099 | 2000W | 800W | DM EB |
| **DELTA Mini** | 2021 | 882 Wh | NCM | $999 / $699 | 1400W | 300W | None |
| **DELTA 1300** | 2019 | 1260 Wh | NCM | $1,399 / $899 | 1800W | 400W | None |

## 🟦 RIVER Series (Portable / Camping)

| Product Name | Release | Capacity | Batt. Chemistry | Price (Launch/Avg) | Output (AC) | Solar Input (Max) | Expansion Units |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :--- |
| **RIVER 3** | 2024 | 245 Wh | LFP | $239 / $199 | 300W | 110W | None |
| **RIVER 3 Plus / Max**| 2024 | 286 / 572Wh | LFP | $300-$500 | 600W | 220W | R3 Max EB |
| **RIVER 2 Pro** | 2022 | 768 Wh | LFP | $599 / $479 | 800W | 220W | None |
| **RIVER 2 Max** | 2022 | 512 Wh | LFP | $469 / $349 | 500W | 220W | None |
| **RIVER 2** | 2022 | 256 Wh | LFP | $299 / $199 | 300W | 110W | None |
| **RIVER mini** | 2022 | 210 Wh | NCM | $349 / $249 | 300W | 100W | None |
| **RIVER Pro** | 2020 | 720 Wh | NCM | $649 / $449 | 600W | 200W | River Pro EB |
| **RIVER Max** | 2020 | 576 Wh | NCM | $549 / $399 | 600W | 200W | Included module |
| **RIVER (Original)** | 2020 | 288 Wh | NCM | $349 / $249 | 600W | 200W | River EB |

## 🛠 Infrastructure & Generators

| Product Name | Release | Type | Compatibility | Price |
| :--- | :---: | :---: | :---: | :---: |
| **Smart Generator**| 2022/24| Dual Fuel | Delta Max/Pro/D2M | $1,599 |
| **Power Kit Hub** | 2022 | Modular | 2kWh/5kWh Batteries | $3,000+ |


## 🔗 Connection Combinations (What works with what?)

### 1. Extra Battery Connections
*   **Detailed View**: See the **[Extra Battery Compatibility Matrix](BATTERY_COMPATIBILITY.md)**.
*   **Delta Series**:
    *   **Delta 2** -> [Delta 2 EB] OR [Delta 2 Max EB]
    *   **Delta 2 Max** -> [Delta 2 Max EB] OR [Delta 2 EB] OR [Delta Max EB]
    *   **Delta Pro** -> [Delta Pro EB] (Proprietary)
    *   **Delta Pro 3** -> [DP3 EB] OR [DP EB] (via Adapter)
*   **River Series**:
    *   **River 1 (Original)** -> Modular "Bolt-on" battery module.
    *   **River Pro** -> Specific [River Pro EB].
    *   **River 2 Series** -> **NO** expansion ports. Must use PowerStream or solar for capacity buffer.
    *   **River 3 Plus/Max** -> Supports specific R3 Extra Battery.


### 2. Charging Combos
*   **Alternator Charger (800W)** -> Works natively with Delta 2, Delta 2 Max, Delta Max (XT150).
    *   *Adapter needed for*: Delta Pro, Delta Pro 3.
*   **PowerStream** -> Works with ALL Delta and River units. 
    *   *Efficiency Tip*: Use BKW-DeltaPro cable for best power throughput (600W-800W).

### 3. Smart Generator Auto-Start
*   **Supported by**: Delta Max, Delta Pro, Delta 2 Max, Power Kits.
*   **Cable**: Uses the Extra Battery port cable (with data pins).

### ⚠️ Safety Warning: No Station-to-Station
**NEVER** connect two power stations together using the Extra Battery (XT150) ports (e.g., Delta 2 to Delta Max). These ports are designed for passive battery slaves. Connecting two active "Masters" will lead to back-feeding, BMS damage, or fire.

## 🛠 Hackable Pairs
*   **Delta 2** + **Generic 48V Server Rack Battery**: Possible via "Resistor Hack" (See [Hardware Mods](../hardware/EXTRA_BATTERY.md)).
*   **EcoFlow BLADE EB**: The robotic mower extra battery is actually a high-quality LFP battery compatible with Delta 2.
*   **EcoFlow 5kWh LFP Battery** + **Victron Inverter**: Possible via [Polarity Adapter](ECOSYSTEM.md).
