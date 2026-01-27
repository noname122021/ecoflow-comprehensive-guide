# ⚠️ The Delta 3 Incompatibility Trap (2-Pin vs 4-Pin)

This section documents a specific hardware failure point encountered by users trying to mix **Gen 2/3 (Delta 2/3)** power stations with **Max Plus / Ultra Plus** extra batteries.

## 🚨 The Situation
Many users (especially in Ukraine during energy crises) purchase a standard **Delta 3** (1kWh) and later buy a **DELTA 3 Max Plus Smart Extra Battery** thinking they are compatible because of the "Delta 3" brand name.

### The Conflict:
*   **Delta 3 (Standard)**: Uses the "Classic" Extra Battery port with **2 large power pins** (XT150 based).
*   **Delta 3 Max Plus EB**: Uses the "New Generation" connector with **4 pins** (2 power + 2 signal/activation integrated into one large block).
*   **The Result**: The physical cables **do not fit**, and the official adapters sold by EcoFlow (like the Smart Generator Adapter) do NOT bridge this specific gap.

---

## 🛠 Why the Support Advice Fails
Official support often recommends:
1.  "Buy a Delta 3 Max main unit" ($1000+).
2.  "Buy the Smart Generator Adapter" ($100).
    *   *Reality*: The Smart Generator Adapter is 2-pin female to 4-pin male, but it is wired for the **Smart Generator**, not for battery expansion. Even if you physically connect it, the BMS usually won't perform the handshake.

---

## ⚙️ The Solution: DIY Activation Hack

If you have a **Delta 3 Max Plus EB** (4-pin) and want to use it with an older station or a 3rd party inverter, you need to "wake up" the battery.

### 4-Pin Cable Pinout (Tentative)
Based on current community research, the 4-pin connector on the Delta 3 Max Plus Extra Battery carries:
*   **2 Large Terminals**: Main DC Power (+ / -).
*   **2 Small Signal Pins**: Used for the BMS handshake.

### The "Wake Up" Logic:
1.  **Identity Check**: Just like the [LFP Adapter](teardowns/LFP_ADAPTER.md), these batteries require a signal to close the internal relay.
2.  **Activation**: Bridging the two signal pins (using a specific resistor or direct short, depending on the exact BMS version) allows the battery to output its 51.2V nominal voltage.
3.  **Physical Adapter**: You will need to build/buy an **XT150 (2-pin)** to **4-pin proprietary** converter. Since EcoFlow doesn't sell one, users are modifying their existing cables.

## ⛓️ The Official Workaround: The "Adapter Chain"
Community experts (Linspyre/Ecoholics) have confirmed that while they don't fit directly, you *can* connect a Delta Pro 3 / Max Plus EB to a standard Delta 3 using a specific chain of official accessories. 

**The chain is expensive (~$250+) but preserves Smart BMS features and charging.**

### The Connection Sequence:
1.  **Delta Pro 3 EB** (Female 4-pin port)
2.  **Standard DP3 EB Cable** (Male/Male 4-pin) — *Comes with the battery*
3.  **EcoFlow Delta Pro to Smart Generator Adapter** 
    *   **Model:** DELTAProTG
    *   **Specs:** 42-58.8V DC, Female 4-pin to Female Infinity Port
    *   **Weight:** 0.35 lb (160g)
    *   **Price:** ~$100 USD
4.  **EcoFlow XT150 Cable** (Male/Male 2-pin)
    *   **Part Numbers:** 606523 / BTY9GPR
    *   **Wire Gauge:** 14 AWG stranded copper (for 1-2m lengths)
    *   **Current Rating:** 15A sustained
    *   **Available Lengths:** 0.4m, 1m, 2m
    *   **Price:** ~$30-50 USD depending on length
5.  **Delta 3 Station** (Female 2-pin port)

> [!TIP]
> This "daisy chain" of adapters allows the digital BMS signals to be correctly mapped back to the 2-pin interface of the older Delta 3. This resolves the **Charging Challenge** mentioned below.

> [!WARNING]
> **Space Requirements**: This cable chain is rigid and bulky. You will need approximately **30-40 cm (12-16 inches)** of clearance behind your battery and station to allow the cables to bend naturally without stressing the connectors. Forcing the cables into tight spaces can damage the ports.

---

## 🔋 The Charging Challenge (DIY Only)
If you decide to go the **DIY route** (building your own cable instead of the $250 adapter chain):
*   **Bidirectional failure**: While the Delta 3 can *take* power via a modified port, it usually refuses to *send* charging current back to the battery without a verified CAN bus handshake.
*   **The Solution**: Use a standalone **48V (58.4V Peak) LiFePO4 AC Charger**. Connect this charger directly to your extra battery via your custom cable. 

---

## 📈 Recommendation for the User
If you are in this situation, you have two paths:

### Path A: The Official Way (Keep Warranty)
Buy the **Smart Generator Adapter** and a standard **XT150 cable**. Connect them in the sequence described above. This is the only way to get full Smart features and automatic charging/discharging.

### Path B: The DIY Way (Save Money)
Read these sections:
1.  **[Extra Battery Port Hack](EXTRA_BATTERY.md)**: To understand the "Resistor Trick" for the station.
2.  **[LFP Battery Adapter Teardown](../teardowns/LFP_ADAPTER.md)**: For the bridge logic (Pins 4-5) to wake up the battery.
3.  **[Cables & Pinouts](CABLES.md)**: To identify terminals.

**Final Advice for Ukraine Backout scenarios:**
Do not return the battery if shipping is impossible. It is a high-quality LFP pack. You can treat it as a "dumb" 51.2V battery by tapping into the main terminals and using the activation hack, then feeding that power into your Delta 3's solar input (XT60) or its Extra Battery port via the resistor hack.
