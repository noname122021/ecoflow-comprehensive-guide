# EcoFlow Cables & Pinouts

## XT150 Extra Battery Connector
The "Extra Battery" cable uses a modified XT150 connector with additional data pins.

### Connector Anatomy
*   **Male/Female polarity**: Standard XT150 gender rules apply.
*   **Main Terminals**:
    *   **Red Housing**: Positive (+) 48V DC.
    *   **Black Housing**: Negative (-) Ground.
*   **Data Pins**:
    *   Located in the center or side of the custom housing.
    *   **Pin 4 & 5**: Key detection pins (Bridge with 1k resistor to activate).

## Solar Input (XT60)
The standard solar input uses an XT60 (yellow) connector.
*   **Input Limits**: Respect the VOC (Voltage Open Circuit) limit of your specific unit (e.g., 60V for Delta 2, 100V for Delta Pro).
*   **Over-paneling**: You can exceed the *Amperage* (the MPPT will just clip it), but **never** exceed the *Voltage*.

## Universal Compatibility
*   **Cable Types**: EcoFlow sells different cables for Delta vs. River series. They are largely electrically compatible for power, but data capabilities (like Smart Generator auto-start) might rely on specific pinouts.
