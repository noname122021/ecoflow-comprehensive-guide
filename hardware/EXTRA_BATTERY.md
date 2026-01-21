# EcoFlow Extra Battery Port Hacking

> [!WARNING]
> **HIGH VOLTAGE DANGER**: This guide involves working with high-voltage DC electricity (up to 60V+ and 100A+). 
> *   **Risk of severe injury or death.**
> *   **Risk of fire.**
> *   **Voiding of warranty.**
> Proceed only if you are a qualified electrician or expert in DC power systems. You accept full responsibility for any damage.

## The Goal
To connect generic 3rd-party batteries (typically 48V LiFePO4 server rack batteries) to the "Extra Battery" port of EcoFlow Delta 2, Delta Max, and Delta 2 Max units, expanding capacity at a fraction of the cost of official EcoFlow batteries.

## The Problem
EcoFlow's Extra Battery port is not just a power input; it's a smart port. When you plug in a cable, the BMS (Battery Management System) expects to talk to a slave BMS in the extra battery. If it doesn't receive the correct data signal, the port remains inactive (relay open), and no power flows.

## The Solution: "The Resistor Hack"
The community has discovered that on many models (Delta 2, Delta Max), the activation signal is relatively simple. The system detects a battery presence by checking for resistance on specific data pins.

### Principle
By bridging the "Enable" or "Sense" pin to Ground (or sometimes a logic 3.3V rail, depending on revision) with a specific resistor, we can trick the main unit's BMS into closing the relay and accepting power from the port.

### Required Components
- **XT150 Connectors** (or Amass XT150): The main power connectors used by EcoFlow.
- **1k Ohm Resistor** (1/4 watt is fine).
- **8 AWG Silicone Wire**: For the main +/- power lines.
- **Smaller gauge wire (22-24 AWG)**: For the resistor bridge.
- **Connectors**: Bullet connectors or soldering equipment.

### Pinout Analysis (General)
The Extra Battery port typically has 2 large pins (Power) and smaller pins (Data) in the middle or side.

**XT150 Connector Layout:**
- **Positive (+)**: Red housing.
- **Negative (-)**: Black housing.
- **Data Pins**: Located between or integrated into the connector housing.

> [!NOTE]
> Precise pin mapping differs slightly between Delta 2 and Delta 2 Max. 

**The Hack Logic:**
1.  **Identify the Signal Pins**: There are usually 4-6 small pins.
2.  **The Bridge**: Connect **Pin 4** (often the 'Enable' pin) to **Pin 5** (Ground) via the **1k Ohm Resistor**.
    *   *Note: Pin numbering is unofficial. Always check resistance with a multimeter on a real cable if possible.*

### Step-by-Step Implementation

1.  **Prepare the Cable**: Solder your XT150+ and XT150- connectors to your 8 AWG wire.
2.  **Install the Resistor**:
    *   Locate the data pins.
    *   Solder the 1k Ohm resistor between the two activation pins.
    *   Insulate heavily!
3.  **Connection Sequence (CRITICAL)**:
    *   **Voltage Match**: Ensure your external 48V battery is at a *similar voltage* to the EcoFlow's internal battery.
        *   *If the EcoFlow is at 100% (58V) and your external battery is at 50% (48V), connecting them will cause massive inrush current, potentially melting wires or welding relays.*
    *   **Connect**: Plug the modified cable into the EcoFlow.
    *   **Verify**: Look for the "Extra Battery" icon on the EcoFlow screen. It may show a generic bar or simple connected status.

## Limitations & Risks
1.  **No Data Reading**: The EcoFlow will NOT know the precise percentage of your external battery. It will just see voltage.
2.  **Charging**: The EcoFlow *might* try to charge the external battery if the internal voltage is higher. This can be dangerous if the external battery doesn't have its own high-quality BMS to handle the current.
3.  **Inaccurate State of Charge (SoC)**: The main unit's remaining time/percentage calculation will be wrong because it doesn't account for the extra capacity correctly.

## Compatible Batteries
- **48V LiFePO4 typically recommended.**
- 15S or 16S configurations matching the EcoFlow's operating voltage range (~40V to 58.4V).
