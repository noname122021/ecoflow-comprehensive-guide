# EcoFlow Compatibility & Interoperability Matrix

This document defines what connects to what within the EcoFlow ecosystem.

## 🔋 Extra Battery (EB) Compatibility

Can I plug a battery from `Model X` into `Model Y`?

| Main Unit | Compatible Extra Batteries | Notes |
| :--- | :--- | :--- |
| **Delta 2** | Delta 2 EB | Can technically use Delta Max EB (Capacity display might be buggy). |
| **Delta 2 Max** | Delta 2 Max EB, Delta 2 EB, Delta Max EB | Highly versatile. Treats Delta 2 EB as a generic expansion. |
| **Delta Max** | Delta Max EB, Delta 2 EB (Firmware limited) | Best to stick with matching EB. |
| **Delta Pro** | Delta Pro EB | **Proprietary Voltage**. Cannot use generic Delta batteries. |
| **Delta Pro 3** | Delta Pro 3 EB, Delta Pro EB (with adapter) | Backwards compatible with original Pro batteries. |
| **Delta 3 Plus / Max**| Delta 3 Plus/Max EB, Delta 2/Max EB, **Pro 3 EB¹** | ¹ *Requires multi-step adapter chain (see below).* |
| **River 2 Series**| NONE | River 2 series units are **not** expandable (sealed). |
| **River Pro (Old)**| River Pro EB | 専用 cable required. |

> **Hack Note**: See `hardware/EXTRA_BATTERY.md` for how to bypass these limits using the "Resistor Hack" to connect generic 48V batteries to **Delta 2 / Delta Max** ports.
>
> **The "Bridge" Solution**: To connect a **Delta Pro 3 Extra Battery** to a **Delta 3 Plus/Max** (or Delta 2/Max), you need: 
> `Pro 3 EB` -> `EB Cable` -> `Smart Generator Adapter` -> `XT150 Cable` -> `Main Unit`.
>
> **Power Kit Batteries (2kWh / 5kWh)**: These are **NOT** directly compatible with Delta/River units via a simple cable. They require the **Power Hub** OR the **LFP Battery Polarity Adapter** (making them a generic 48V source, which then requires the Resistor Hack to feed a Delta unit).

## ☀️ Solar Panel Compatibility

Can I use Solar Panel X with Power Station Y?

**Rule of Thumb:**
1.  **Voltage (Voc)**: Must be **BELOW** the Power Station's limit. (Exceeding Voc = Instant Damage).
2.  **Amperage (Imp)**: Can be higher (Station will just clip it).
3.  **Connector**: Most Panels are MC4. EcoFlow is XT60/XT60i. Use an adapter.

### Input Limits Table

| Unit | Max Voltage (Voc) | Max Input (W) | Connector |
| :--- | :--- | :--- | :--- |
| **River 2** | 30V | 110W | XT60 |
| **River 2 Max** | 50V | 220W | XT60 |
| **River 2 Pro** | 50V | 220W | XT60 |
| **Delta Mini** | 75V | 300W | XT60 |
| **Delta (OG)** | 65V | 400W | XT60 |
| **Delta 2** | 60V | 500W | XT60i |
| **Delta Max** | 100V | 800W (Dual Port) | XT60i |
| **Delta 2 Max** | 60V (x2 Ports) | 1000W (500W x2) | XT60i |
| **Delta Pro** | 150V | 1600W | XT60i (High Voltage) |

## 🔌 Charging & Grid-Tie Accessories

| Main Unit | **PowerStream** (Microinverter) | **Alternator Charger** (800W) | Notes |
| :--- | :--- | :--- | :--- |
| **Delta Pro 3** | ✅ | ✅ | Alt Charger needs adapter. |
| **Delta 3 Plus / Max**| ✅ | ✅ | Direct XT150 connection. |
| **Delta Pro** | ✅ (Needs Cable) | ✅ (Needs Adapter) | PowerStream needs BKW-DeltaPro cable. |
| **Delta 2 Max** | ✅ (Needs Cable) | ✅ (Direct XT150) | Best match for Alternator Charger (Fast charge). |
| **Delta 2** | ✅ (Needs Cable) | ✅ (Direct XT150) | |
| **Delta Max** | ✅ (Needs Cable) | ✅ (Direct XT150) | |
| **River 2 Series**| ✅ (Needs Cable) | ✅ (Via XT60 adapter) | Alt Charger output (800W) might exceed River input limits! Check specs. |

## ⚙️ Smart Generator Compatibility

*   **Smart Generator (Dual Fuel)**:
    *   **Direct Connect**: Works efficiently with Delta Pro & Delta Max / 2 Max via the Extra Battery Port.
    *   **Auto-Start**: Only works if connected via the dedicated cable which passes data.
    *   **Generic Use**: Can charge ANY station via the AC outlet on the generator (inefficient conversion).

---

## 💻 Software / Protocol Compatibility

| Device | Bluetooth | Wi-Fi | Matter/HomeKit | Local MQTT (Port 6500) |
| :--- | :--- | :--- | :--- | :--- |
| **Delta (OG)** | ❌ | ❌ | ❌ | ❌ |
| **River (OG)** | ❌ | ✅ | ❌ | ✅ |
| **Delta 2 / Max**| ✅ | ✅ | ❌ | ✅ |
| **Delta Pro** | ✅ | ✅ | ❌ | ✅ |
| **River 2** | ✅ | ✅ | ❌ | ✅ |
| **Delta Pro 3** | ✅ | ✅ | ✅ (Some regions) | ❓ (New Encryption?) |
| **PowerStream** | ✅ | ✅ | ✅ (Plug Integration)| ✅ |
| **Alternator Chg**| ✅ | ✅ | ❌ | ❓ |

