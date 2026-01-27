# EcoFlow Hacking & Advanced Usage Guide

Welcome to the unofficial guide for modifying, hacking, and deeply integrating EcoFlow power stations.

> **[Quick Project Walkthrough (Summary of Work)](WALKTHROUGH.md)**

> [!CAUTION]
> **DISCLAIMER:** This information is for educational purposes only. Modifying your device involves working with **high-voltage DC electricity**, which can be lethal. Modifications will almost certainly **void your warranty**. Use this information at your own risk.

## 📚 Documentation Sections

### 🛠 Hardware Modifications
*   **[Extra Battery Port Hack](hardware/EXTRA_BATTERY.md)**: How to connect cheap 48V server rack LiFePO4 batteries to your Delta 2/Max/Pro instead of buying expensive official extra batteries.
*   **[Cables & Pinouts](hardware/CABLES.md)**: Details on the XT150 and XT60 connectors used for solar and battery expansion.
*   **[Repair & Teardowns](hardware/REPAIR_TEARDOWN.md)**: Info on "PowerStream" failures, 110V vs 220V accidents, and internal chip usage.
*   **[Delta 3 Incompatibility Trap](hardware/DELTA3_MAX_PLUS_TRAP.md)**: **CRITICAL** for Delta 3 owners trying to connect Max Plus Extra Batteries (2-pin vs 4-pin issue).

### 🧬 Teardowns & Disassembly
*   **[LFP Battery Adapter](teardowns/LFP_ADAPTER.md)**: Activating Delta Pro batteries without the official adapter (Pin 4-5 short).

### 📊 Product Database
*   **[Device Image Gallery](products/GALLERY.md)**: Official images for all supported devices.
*   **[Master Combination Matrix](products/MASTER_MATRIX.md)**: The ultimate table of all devices, specs, prices, and connection combos.
*   **[Extra Battery Compatibility](products/BATTERY_COMPATIBILITY.md)**: Specfic matrix for V1, V2, and V3 batteries and their cross-compatibility.
*   **[Device History & Specs](products/DEVICE_LIST.md)**: Detailed breakdown of River/Delta/STREAM generations.
*   **[Ecosystem: Accessories & Solar](products/ECOSYSTEM.md)**
    *   Technical details on **PowerStream**, **STREAM Series**, **Alternator Charger**, and **Standalone LFP Batteries**.
*   **[Compatibility Matrix](products/COMPATIBILITY.md)**: Technical input/output limits and cable types.
*   **[Emergency Usage & Blackout Guide](usage/EMERGENCY_BACKUP.md)**: Critical info on STREAM Ultra limitations, switching speeds, and backup strategy.

### 💻 Software & Protocols
*   **[Protocols (MQTT & Protobuf)](software/PROTOCOLS.md)**: Deep dive into how EcoFlow devices talk to the cloud and how you can intercept/decode these messages for Home Assistant or local control.
*   **[Advanced Automation & Resets](ADVANCED.md)**: Solar excess charging scripts (Home Assistant) and hard reset key combinations for troubleshooting.

## 🚀 Quick Start for Hackers
1.  **Want cheap storage?**: Go straight to the [Extra Battery Hack](hardware/EXTRA_BATTERY.md).
2.  **Want Home Assistant integration?**: Check the [Protocols](software/PROTOCOLS.md) section and look for the `ioBroker` or `hassio-ecoflow-cloud` projects referenced there.

## Community Resources
*   [r/Ecoflow_community](https://www.reddit.com/r/Ecoflow_community/)
*   [DIY Solar Power Forum](https://diysolarforum.com/)
*   [local-powerstream (tomvd)](https://github.com/tomvd/local-powerstream) - Local control via MQTT redirection.
*   [EcoFlow-CanBus-Reverse-Engineering (bulldog5046)](https://github.com/bulldog5046/EcoFlow-CanBus-Reverse-Engineering) - Hardware CAN signals.
*   [hassio-ecoflow (vwt12eh8)](https://github.com/vwt12eh8/hassio-ecoflow) - Home Assistant local/cloud integration.
*   [GitHub Topic: EcoFlow](https://github.com/topics/ecoflow)
