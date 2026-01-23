# EcoFlow Internal Repair & Teardown Analysis

This document compiles technical information from community teardowns, Reddit user reports, and repair attempts.

> [!DANGER]
> **HIGH VOLTAGE**: Opening an EcoFlow unit exposes you to lethal 220V/110V AC and high-amperage DC. Capacitors can hold charge for hours. This information is for educational purposes only.

## 🧱 PowerStream / STREAM series Microinverter Failures
The PowerStream (and its successor, the **EcoFlow STREAM Microinverter**) are sophisticated grid-tie units, but high power density in a small passively cooled shell leads to reliability issues.

### Common Failure Modes
1.  **"0 Watt Output"**: Unit is online but pushes 0W to grid despite solar input.
    *   *Cause*: Often a firmware hang or MPPT throttling due to heat.
    *   *Fix*: Disconnect PV + Battery, wait 10 mins, reconnect. Add active cooling (fan).
2.  **Dead Unit (No LEDs)**:
    *   *Cause*: Internal power supply failure or blown protection fuse after grid surge.
    *   *Observation*: Teardowns reveal a blown SMD fuse near the grid connector or battery input.
3.  **Error Code "12" ("Not connected to grid")**:
    *   *Symptom*: Unit displays "Not connected to grid" even when physically plugged in. No power output.
    *   *Cause*: Often a hardware failure in the grid-tie synchronization circuit or a blown AC-side protection component (GDT/GaN ICs). 
4.  **Overheating Throttling**:
    *   The unit is passively cooled. Pushing 800W for long periods > 25°C ambient causes throttling to 600W or shutdown.
    *   *Mod*: Users attach PC fans to the back heatsink metal.

### Internal Components (Teardown Data)
*   **MCU**: **ESP32-C3-mini-1U** (Espressif).
*   **Power Stage ICs**: **LMG3411** (Texas Instruments Gallium Nitride / GaN power stages). These are high-performance but prone to catastrophic failure during surges.
*   **Protection (GSC300)**: A **Gas Discharge Tube (GDT)**. It should be open-circuit (no continuity) during normal operation. Continuity indicates it has failed and is shorting the grid.
*   **Fuses**: A **20A 72V SMD fuse** is located near the battery connector and is a common failure point.
*   **Waterproofing**: The internal PCB is heavily potted with a dielectric "sticky substance" (resin).
    *   *Repairability*: **Very Low**. The board is held by 10 Philips screws after removing the 5 Torx 10 cover screws, but it is effectively glued into the shell.
*   **Debug Interfaces**: Exposed **UART** and **JTAG** pads are present on the PCB near the Bluetooth label.

---

## ⚡️ Voltage Mods & 110V/220V Accidents

### 🛠 Overvoltage Repair Sequence (110V Unit -> 220V Grid)
If the unit smelled like smoke and died after plugging into 220V:

1.  **Safety First**: Ensure battery is disconnected from the mainboard.
2.  **Inspect Varistor (MOV)**: Look for a small blue/orange disc near the AC input. It will likely be charred or split. 
    *   *Function*: It shorts to blow the fuse.
3.  **Check AC Fuse**: Ceramic fuse on the mainboard. Replace only *after* checking MOVs.
4.  **Inverter Tracing**: Check the H-Bridge MOSFETs (IGBTs). If they are shorted (0 Ohms between Drain/Source), simple fuse replacement will just blow again.
5.  **Logic Power Supply**: Often a small buck converter (PWM chip) powers the logic from the AC line. If this is dead, the unit won't even wake up with the battery.

*Repair success rate for overvoltage is ~10-20% without board replacement due to multi-layer PCB damage.*

### Can I convert a 110V unit to 220V?
*   **Answer**: **NO**.
*   **Reason**:
    1.  **Hardware**: The internal inverter transformer and capacitors are sized for the specific voltage/frequency.
    2.  **Firmware**: The region is hard-coded.
*   **Workaround**: Use the **EcoFlow PowerStream** or **STREAM Microinverter**. They accept high-voltage DC from the battery and invert it to local grid voltage (220V), bypassing the Delta's internal 110V inverter.

---

## 🧩 Component Identi-kit
Parts identified in various teardowns (River/Delta series).

### Connectors
*   **XT150**: High current battery interconnects.
*   **XT60i**: Solar input (The extra pin is for "Smart Generator" detection).

### Chips & FETs (Verified Part Numbers)
*   **Main MCU**: GigaDevice `GD32F303RCT6A` (ARM Cortex-M4) - Logic/Controller.
*   **Gate Drivers**: `NSI6602` (Isolated dual-channel, common in Delta Max/Pro inverter stages).
*   **Wi-Fi/BT**: 
    *   Espressif `ESP32-C6` or `ESP32-WROVER` (Delta/River series).
    *   Espressif `ESP32-C3-mini-1U` (PowerStream).
*   **Current Sense Amps**: `TP181A3-CR` / `INA199` / `INA210` (Gain 200, used for shunts).
*   **Inverter Switchers / Power Stages**: 
    *   `LMG3411` (TI GaN Power Stage, found in PowerStream).
    *   `YGW60N65F1` (650V 60A IGBT, often found in Delta Max/Pro output stages).
    *   `CR MICRO HGQ065NE4A` (High-efficiency MOSFET, used for USB-C PD stages in River 3).
*   **Display Driver**: i-Core (LQFP48 package).

### Board Reference Numbers
*   **Delta Pro BMS**: `MR500-UV-BMS-V1.0.3`.
*   **River 2 Max PD**: `MR610-UV-PD-V1.0.3`.

### Structure & Modules
*   **Potting (The "Goo")**: Most newer units (PowerStream, River 2) use heavy silicone potting for vibration and moisture resistance. 
    *   *Repair Tip*: Use heat and plastic picks. AVOID solvents which can melt component markings.
*   **Modular Fans**: EcoFlow uses standard 4-pin PWM fans. If yours is noisy, you can replace with a Noctua equivalent *if* the start voltage matches.
