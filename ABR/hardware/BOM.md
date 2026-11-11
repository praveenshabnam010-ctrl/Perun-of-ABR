# Bill of Materials

**Status: proposed.** No components have been purchased, acquired or tested. Prices and availability have not been verified. This is not a final bill of materials.

## Status legend

| Status | Meaning |
| --- | --- |
| Proposed | Considered, but not selected or acquired |
| Selected | Chosen for the build, but not yet acquired |
| Acquired | Physically obtained |
| Tested | Verified working in the current design |

## Proposed components

| Item | Proposed part | Purpose | Interface | Quantity | Status | Cost and availability | Notes |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Main controller | Arduino Uno R3 | Runs the firmware | — | 1 | Proposed, not acquired | To be verified | Confirm board variant |
| Environmental sensor | BME280 | Temperature, relative humidity and pressure | I2C | 1 | Proposed, not acquired | To be verified | Confirm module voltage and address |
| Light sensor | BH1750 | Light intensity | I2C | 1 | Proposed, not acquired | To be verified | Confirm module variant and address |
| Real-time clock | DS3231 | Time-stamped measurements | I2C | 1 | Proposed, not acquired | To be verified | Confirm battery and module variant |
| Storage | MicroSD module | Local data logging | SPI | 1 | Proposed, not acquired | To be verified | Confirm logic voltage and level shifting |
| Display | 2.4-inch ILI9341 TFT | Local display | SPI | 1 | Proposed, not acquired | To be verified | Confirm module voltage and control pins |
| Rain gauge | Tipping-bucket rain gauge | Rainfall measurement | GPIO interrupt | 1 | Proposed, not acquired | To be verified | Confirm resolution and output type |

## Verification before purchase

- [ ] Check local availability.
- [ ] Check the current price.
- [ ] Check the datasheet and logic levels.
- [ ] Check the module variant and pinout.
- [ ] Check compatibility with the Arduino Uno R3.
- [ ] Check the power requirements.
- [ ] Record the exact module ordered.
- [ ] Update this file with the verified information.

## Notes

- Clones and variants can differ. Verify the specific board that is received.
- Do not substitute parts without checking compatibility and updating the documentation.
- No prices are recorded because none have been verified.
- No purchases have been made.
