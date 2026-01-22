# EcoFlow Cables & Pinouts

## XT150 Extra Battery Connector
The "Extra Battery" cable uses a modified XT150 connector with additional data pins.

### Connector Anatomy
*   **Part Number**: `XT150-EF-F-P` (Female PCB connector).
*   **Male/Female polarity**: Standard XT150 gender rules apply.
*   **Main Terminals**:
    *   **Red Housing**: Positive (+) 48V DC.
    *   **Black Housing**: Negative (-) Ground.
*   **Data Pins (Wave 2 / Extra Battery Port)**:
    The Wave 2 PCB and many Extra Battery ports use a 6-pin data configuration:
    
    | Pin | Function | 3ft Cable Color |
    | :--- | :--- | :--- |
    | 1 | CAN-H | Violet |
    | 2 | CAN-L | Orange |
    | 3 | Wakeup | Blue |
    | 4 | SigOut | Yellow |
    | 5 | SigIn 1 | Black |
    | 6 | SigIn 2 | Red |

    *   **Activation (Resistor Trick)**: On simpler units (Delta 2/Max), bridging Pin 4 & 5 with a 1k resistor can activate the port. Newer units (PowerStream, Delta 3) often require CAN bus "heartbeat" messages.

## Solar Input (XT60)
The standard solar input uses an XT60 (yellow) connector.
*   **Input Limits**: Respect the VOC (Voltage Open Circuit) limit of your specific unit (e.g., 60V for Delta 2, 100V for Delta Pro).
*   **Over-paneling**: You can exceed the *Amperage* (the MPPT will just clip it), but **never** exceed the *Voltage*.

## Universal Compatibility
*   **Cable Types**: EcoFlow sells different cables for Delta vs. River series. They are largely electrically compatible for power, but data capabilities (like Smart Generator auto-start) might rely on specific pinouts.
*   **Regional Variants**:
    *   **Europe (BKW)**: Offers a specialized right-angle cable ([BKW-Battery-Cable-Delta-EB](https://eu.ecoflow.com/products/bkw-battery-cable-delta-eb)) for the PowerStream/Micro-inverter setup which is much more flush against the unit.
    *   **Alternator Charger**: Also features a right-angle connector, though it is often not sold separately from the full kit.
