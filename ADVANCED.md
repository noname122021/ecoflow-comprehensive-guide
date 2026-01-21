# Advanced EcoFlow Configuration & Hacks

This guide covers advanced usage, including automation and potential hidden resets.

## 🤖 Home Assistant Automation: Solar Excess Charging
Maximize your solar investment by only charging your EcoFlow when you have *excess* solar power, instead of pulling from the grid.

### The Logic
1.  **Monitor**: Read your Home Energy Meter (e.g., Shelly EM, Emporia Vue) to see "Grid Export".
2.  **Trigger**: If Export > 200W for > 1 min -> Start EcoFlow Charging.
3.  **Control**:
    *   **Method A (Smart Plug)**: Turn ON a smart plug powering the EcoFlow AC input.
    *   **Method B (Direct API)**: Use the `hassio-ecoflow-cloud` integration to set `acChgCfg_D2` (AC Charge Speed) dynamically.

### Example Automation (YAML)
```yaml
alias: EcoFlow Solar Excess Charge
trigger:
  - platform: numeric_state
    entity_id: sensor.grid_power
    below: -300  # Negative value usually means export
    for: "00:01:00"
action:
  - service: switch.turn_on
    target:
      entity_id: switch.ecoflow_ac_input
  - service: number.set_value
    target:
      entity_id: number.ecoflow_delta_max_ac_charging_power
    data:
      value: 400
```

---

## 🔁 Hard Resets & Key Combinations
EcoFlow devices generally lack a visual "service menu", but they use button combos for hard resets.

### 1. The "Long Press" (General Reset)
*   **Target**: All Delta/River units.
*   **Action**: Unplug EVERYTHING (Inputs/Outputs). Hold the main yellow **Power Button** for **10-15 seconds**.
*   **Result**: Cold reboot of the BMS and LCD communication.

### 2. IoT Reset (Wi-Fi/Bluetooth)
*   **Target**: Delta 2, Delta Max, Delta Pro.
*   **Action**: Hold the **IoT Button** (or pair button) for **3-10 seconds** until the Wi-Fi icon flashes.
*   **Use Case**: Moving the device to a new Wi-Fi network or if the app refuses to connect.

### 3. DC + Main (River Pro Reset)
*   **Target**: River Pro (Older).
*   **Action**: Unplug unit. Hold **LED Light Button** + **DC Button** simultaneously for 10s.

### 4. BMS Calibration (The "Drain & Fill")
*   **Issue**: Screen shows 30% but unit dies instantly.
*   **Fix**:
    1.  Charge to 100% until input watts hit 0.
    2.  Discharge to 0% until unit shuts off completely.
    3.  Wait 2 hours (thermal normalization).
    4.  Charge uninterrupted back to 100%.
    *   *This recalibrates the SoC (State of Charge) algorithm.*

---

## 🔒 Service Ports
Most units have a hidden **Micro-USB** or **USB-C** port often covered by a plastic flap (sometimes near the handle or inside the lid of older units).
*   **Purpose**: Factory firmware flashing.
*   **Usability**: Generally encrypted/protected. Not a user-accessible console without specific proprietary tools.
