# 🌑 Emergency Power & Blackout Strategy

This guide details how different EcoFlow ecosystems behave when the grid goes down. Not all "backup" devices work the same way.

## 🧭 Which System Are You Using?

EcoFlow products fall into four distinct "Emergency Tiers". 

### Tier 1: Portable Grab-and-Go (RIVER Series)
*   **Behavior**: These are manual. When the power goes out, you plug your phone/laptop/router into the station.
*   **EPS Mode**: Most RIVER 2/3 units support "Emergency Power Supply" (30ms switch). 
    *   *Risk*: 30ms is slow. Desktop PCs might reboot, but fridges and TVs will stay on.
*   **Blackout Strategy**: Keep it 100% charged under a desk. Use **DC ports (USB)** as much as possible to avoid the ~7W inverter drain.

### Tier 2: Home Backup (DELTA 2 / Max / Pro)
*   **Behavior**: High-capacity units that can sit between the wall and your appliances permanently.
*   **UPS Mode**: 10ms switch time. Safe for gaming PCs, iMacs, and servers.
*   **Blackout Strategy**: Use the **AC Always-On** setting in the app if you have a medical device (CPAP), but remember this consumes ~15W/hour of battery even if the device is off.

### Tier 3: Solar-First / Balcony (PowerStream & STREAM Ultra)
*   **Behavior**: These are "Grid-Following". They **STOP** outputting to your house wiring during a blackout for safety.
*   **The Paradox**: You have 2-10kWh of battery, but your wall outlets are dead.
*   **Blackout Strategy**: You MUST use the AC outlets located **on the device itself**. 
    *   *STREAM Ultra Link*: **[Detailed STREAM Ultra Blackout Guide](#-stream-ultra-specifics)**

### Tier 4: Whole-Home Infallible (DELTA Pro Ultra / Power Kits)
*   **Behavior**: Professional installation. These use a **Smart Home Panel 2**.
*   **Switch Time**: 20ms (Panel) or **0ms (Online UPS)** if a DPU is directly connected.
*   **Blackout Strategy**: Do nothing. The house stays powered automatically.

---

## ⚡ Comparison Matrix: Blackout Performance

| Feature | RIVER 2/3 | DELTA 2/Max | STREAM Ultra | DELTA Pro Ultra |
| :--- | :---: | :---: | :---: | :---: |
| **Switch Time** | 30ms (EPS) | 10ms (UPS) | **~3 seconds** | **0ms - 20ms** |
| **Whole House?**| No | Via Manual Transfer | No | ✅ Yes (Auto) |
| **Idle Drain** | ~7W | ~15W | ~30-40W | ~12W (Standby) |
| **Pass-through**| 300W-800W | 1200W-2400W | 2300W | 7200W |
| **Battery Type**| LFP | LFP | LFP | LFP |

---

## 🏗️ STREAM Ultra Specifics
Since the STREAM Ultra is often misunderstood as a "Whole Home UPS", remember these three rules:
1.  **Anti-Islanding**: It will not power your home network/wiring during a blackout.
2.  **Manual Intervention**: You must physically move plugs to the Ultra's own outlets.
3.  **Power Drop**: In bypass (grid on), you get 2300W. On battery (grid off), you may be limited to **~800W** per unit. 

---

## 📉 Efficiency & Runtime during Blackouts
In a long blackout, every watt counts. The **Inverter** is your enemy.

### The "Vampire" Inverter Cost
Even if you plug in nothing, turning on the AC outlets drains the battery:
*   **RIVER 2**: Drains ~5-10% capacity overnight just staying "on".
*   **STREAM Ultra**: Drains **~24-30% of its battery in 24 hours** just sitting idle with AC enabled.

**Pro Hack**: Use **USB-C to DC** or **USB-C to Surface/MagSafe** adapters to charge laptops. This bypasses the AC inverter entirely, extending your runtime by **25-40%**.

### Runtime Calculation
`Hours = (Capacity Wh * 0.85) / (Appliance Watts + Inverter Idle Watts)`

*Example: 50W Fridge on DELTA 2 (1024Wh):*
`1024 * 0.85 / (50 + 15) = 13.3 Hours`
*(Without considering idle drain, you might wrongly expect 17 hours).*

---

## 🔋 Cold Weather Warning
If your EcoFlow is in a garage or balcony:
*   **LFP batteries cannot CHARGE below 0°C (32°F).** 
*   They can *discharge* down to -20°C, but they won't take solar/AC power until they warm up. 
*   **Tech Tip**: Most DELTA and STREAM Ultra units have **auto-heating**—they will use a bit of battery to warm themselves up if they detect a charge source, but this takes time.
