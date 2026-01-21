# EcoFlow Ecosystem & Accessories History

This document catalogs the "Eco-system" products that go beyond the basic power stations.

## ☀️ PowerStream (Balcony Solar System) (May 2023)
*   **Type**: Microinverter (Grid-Tied).
*   **Specs**: 800W AC Output (Grid) / 800W PV Input.
*   **Battery Port**: 600W DC Input/Output. Connects to almost ALL EcoFlow power stations (Delta/River) acting as a massive battery buffer.
*   **Unique Feature**: Feeds solar to your home grid (Base load) and stores excess in the battery.
*   **Compatibility**: Needs specific BKW cables for Delta/River.

## 🚗 Alternator Charger (June 2024)
*   **Type**: DC-DC Charger (Input from Car Alternator).
*   **Specs**: 800W Charging Speed.
*   **Input**: 11V-35V (Works with 12V/24V systems).
*   **Output**: 40V-60V (Targeting Delta 2/Max/Pro battery voltage).
*   **Key Advantage**: Charges a Delta 2 Max in ~2.5 hours while driving (vs 8+ hours on cig lighter).
*   **Tech**: GaN (Gallium Nitride) for compactness.
*   **Reverse Charging**: Can maintaining vehicle battery from the Power Station (Jump Start/Trickle).

## 🧊 Smart Devices (Glacier, Wave, Blade)

In 2023, EcoFlow expanded into "Smart Devices" that use their battery tech.

### EcoFlow WAVE 2 (May 2023)
*   **Type**: Portable Air Conditioner & Heater.
*   **Performance**: 5100 BTU Cooling / 6100 BTU Heating.
*   **Battery**: Uses add-on battery (1159Wh) or connects to Delta 2/Max/Pro.
*   **Runtime**: ~8 hours (Eco Mode).
*   **Refrigerant**: R290 (Green).

### EcoFlow GLACIER (April 2023)
*   **Type**: Portable Fridge/Freezer + Ice Maker.
*   **Key Feature**: Integrated Ice Maker (18 cubes in 12 mins).
*   **Battery**: 298Wh plug-in battery (optional).
*   **Cooling**: Dual Zone (-25°C to 10°C).

### EcoFlow BLADE (April 2023)
*   **Type**: Robotic Lawnmower with Lawn Sweeping Kit.
*   **Key Tech**: RTK GPS (No perimeter wire needed).
*   **Status**: Mixed reception due to complexity and navigation issues compared to competitors.

---

## ⚙️ Generators (Dual Fuel)

Smart generators designed to auto-start and charge the power stations efficiently.

### Smart Generator 4000 (Dual Fuel) (2024)
*   **Output**: 4000W Peak / 3200W Continuous.
*   **Fuel**: Gasoline + LPG (Propane).
*   **Efficiency**: 40% fuel savings vs traditional generators when paired with Delta Pro 3.
*   **Connectivity**: App control, Auto-Start when Delta battery hits X%.

### Smart Generator (Original Dual Fuel) (Dec 2022)
*   **Output**: 1800W (Gas) / 1600W (LPG).
*   **Engine**: 80cc 4-stroke.
*   **Integration**: Seamless DC charging for Delta Pro/Max (Higher efficiency than AC charging).

---

## 🚐 Power Kits & Standalone LFP Batteries

The "Power Kit" system is modular, but some components (batteries) are useful standalone.

### Standalone LFP Batteries (2kWh / 5kWh)
*   **Chemistry**: LiFePO4 (LFP) - 3000-3500 cycles.
*   **Voltage**: 51.2V Nominal (16S).
*   **Capacity & Form Factor**:
    *   **2kWh**: 40Ah | ~17.1 kg (37.7 lbs) | 348 x 198 x 285 mm.
    *   **5kWh**: 100Ah | ~40.6 kg (89.5 lbs) | 500 x 260 x 300 mm.
*   **Features**: Built-in BMS, Auto-Heating (works down to -20°C).
*   **LFP Battery Polarity Adapter**:
    *   *Purpose*: Adapts the proprietary EcoFlow battery port to standard terminals & CAN Bus.
    *   *Communication (RJ45 CAN Port Pinout)*:
        *   **Pin 1**: Wake / 12V Trigger
        *   **Pin 2**: CAN High (H)
        *   **Pin 5**: CAN Low (L)
        *   **Pin 6**: Ground (GND)
    *   *Note*: Requires an **RJ45 Terminator** on the last battery in the chain for stable comms.
*   **Power Hub**: The 5-in-1 brain (Inverter + DC-DC + MPPT) usually required if not using the Polarity Adapter.

### Power Kit System Architecture (Mid-2022)
*   **Power Hub**: Combines 2x MPPT, DC-DC Charger, Inverter, and DC-DC Converter.
    *   *Input*: Solar (4800W), Alternator (1000W), Shore Power (3000W).
    *   *Output*: 3600W AC (120V).
