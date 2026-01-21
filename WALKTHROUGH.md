# EcoFlow Hacking Guide - Summary & Walkthrough

This repository contains a comprehensive guide for advanced EcoFlow usage, hacking, and maintenance.

## 📁 Key Documents Created

1.  **[Master Database & Matrix](products/MASTER_MATRIX.md)**
    *   Systematic table of all devices (River, Delta, Ecosystem).
    *   Includes release dates, capacities, battery chemistry (LFP vs NCM), and current pricing.
    *   Compatibility matrix for combinations (Extra batteries, Smart Generators, PowerStream).

2.  **[Hardware Hacks: Extra Battery](hardware/EXTRA_BATTERY.md)**
    *   Deep dive into the **"Resistor Hack"**.
    *   Connecting 48V server rack batteries to Delta 2/Max/Pro.
    *   Pinouts for XT150 and data lines.

3.  **[Repair & Teardowns](hardware/REPAIR_TEARDOWN.md)**
    *   Detailed list of **ICs and Semiconductors** (GD32, ESP32, MOSFET types).
    *   Step-by-step **Overvoltage Repair Sequence** for 110V units plugged into 220V.
    *   PowerStream failure analysis (cooling, potting, fuses).

4.  **[Ecosystem: Accessories & Power Kits](products/ECOSYSTEM.md)**
    *   Technical details on **PowerStream**, **Alternator Charger**, and **Standalone LFP Batteries**.
    *   **LFP Polarity Adapter** pinouts and CAN Bus logic.

5.  **[Software & Protocols](software/PROTOCOLS.md)**
    *   MQTT (Port 6500) and Protobuf payload structures.
    *   **Direct Connection Mode** (Local MQTT bypass) explanation.
    *   Link to reverse-engineering repositories.

6.  **[Advanced Automation](ADVANCED.md)**
    *   Home Assistant examples for **Solar Excess Charging**.
    *   Key combinations for device resets and BMS recalibration.

## 🎯 Project Goals Achieved
*   [x] Gathered all info from GitHub/Reddit/Forums.
*   [x] Documented the Resistor Hack and XT150 pinouts.
*   [x] Created a compatibility matrix for all EcoFlow products.
*   [x] Documented specific microchips for repair technicians.
*   [x] Explained 110V/220V conversion limits and restoration.
*   [x] Systematized the entire ecosystem with dates and specs.
