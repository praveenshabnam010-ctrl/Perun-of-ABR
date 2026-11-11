# Bill of Materials

**Status: proposed.** No components have been purchased, acquired or tested. Prices and availability have not been verified. This is not a final bill of materials.

---

## Status legend

| Status | Meaning |
|--------|---------|
| Proposed | Considered, but not selected or acquired |
| Selected | Chosen for the build, but not yet acquired |
| Acquired | Physically obtained |
| Tested | Verified working in the current design |

---

## Core components

| Item | Proposed part | Purpose | Interface | Qty | Power rail | Status | Notes |
|------|---------------|---------|-----------|-----|------------|--------|-------|
| Main controller | Arduino Uno R3 | Runs the firmware | — | 1 | External 5 V | Proposed, not acquired | Confirm board variant and logic level |
| Environmental sensor | BME280 | Temperature, relative humidity and pressure | I²C | 1 | 3.3 V | Proposed, not acquired | Confirm module voltage, regulator and I²C address |
| Light sensor | BH1750 | Light intensity | I²C | 1 | 3.3 V | Proposed, not acquired | Confirm module variant and I²C address |
| Real-time clock | DS3231 | Timestamped measurements | I²C | 1 | 5 V | Proposed, not acquired | Confirm module variant, battery type and I²C address |
| Display | 2.4-inch ILI9341 TFT | Local readout | SPI | 1 | 3.3 V logic | Proposed, not acquired | Confirm module voltage, level shifting and control pin layout |
| Data storage | MicroSD card module | Local data logging | SPI | 1 | 3.3 V logic | Proposed, not acquired | Confirm logic voltage and level shifting |
| Storage media | MicroSD card (8–16 GB) | Holds logged data | — | 1 | — | Proposed, not acquired | FAT32 format required for Arduino SD library |
| Rain gauge | Tipping-bucket rain gauge | Rainfall measurement | GPIO interrupt | 1 | — | Proposed, not acquired | Confirm resolution, output type and debounce requirements |

---

## Supporting components

| Item | Purpose | Qty | Status | Notes |
|------|---------|-----|--------|-------|
| Breadboard or perfboard | Prototyping and permanent assembly | 1 | Proposed, not acquired | Breadboard for prototyping; perfboard for permanent build |
| Jumper wires | Connections between components | As needed | Proposed, not acquired | Male-to-male and male-to-female |
| Logic-level shifter | Converts 5 V signals to 3.3 V for 3.3 V modules | As needed | Proposed, not acquired | Required if modules are not 5 V tolerant; verify before purchase |
| Voltage regulator | Provides stable 3.3 V if the Uno's rail is insufficient | As needed | Proposed, not acquired | Determine based on current requirements of all 3.3 V modules |
| Regulated 5 V power supply | Powers the Arduino and station | 1 | Proposed, not acquired | Must supply sufficient current for all components; verify |
| Weather-resistant enclosure | Protects electronics outdoors | 1 | Proposed, not acquired | Size and material depend on the final assembly |
| Cable glands | Sealed entry points for sensor cables | As needed | Proposed, not acquired | Match to enclosure and cable diameters |
| Connectors and mounting hardware | Securing and connecting components | As needed | Proposed, not acquired | Determine based on enclosure and sensor placement |

---

## Verification before purchase

- [ ] Check local availability of each component.
- [ ] Check the current price.
- [ ] Check the datasheet and confirm the logic level of each module.
- [ ] Check the module variant and pinout.
- [ ] Confirm compatibility with the Arduino Uno R3.
- [ ] Check power requirements and confirm the power supply can meet them.
- [ ] Determine whether level shifters or external regulators are needed.
- [ ] Record the exact module ordered once purchased.
- [ ] Update this file with verified information after purchase.

---

## Notes

- Clone and third-party module variants can differ significantly from one another. Always verify the specific board that is received.
- Do not substitute components without checking compatibility and updating the documentation.
- No prices are recorded because none have been verified.
- No purchases have been made.
- The Arduino Uno R3 operates at 5 V logic. Several proposed modules operate at 3.3 V logic. Level shifting may be required; do not assume 3.3 V modules are 5 V tolerant.
