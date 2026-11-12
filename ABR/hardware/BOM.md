# ABR Weather Station — Bill of Materials (BOM)

**Status: proposed.** No components have been purchased, acquired or tested. Prices and availability have not been verified. This is not a final bill of materials.

---

## Main components (prices from Robu.in, as of 12 November 2026)

| No. | Component | Purpose | Quantity | Unit price |
|-----|-----------|---------|----------|------------|
| 1 | 2.4-inch SPI TFT Display Module (240 × 320) | Local data display | 1 | ₹699 |
| 2 | SmartElex BME280 Atmospheric Sensor Breakout Board | Temperature, relative humidity and atmospheric pressure | 1 | ₹539 |
| 3 | CJMCU TEMT6000 Ambient Light Sensor Module | Ambient light intensity measurement | 1 | ₹89 |
| 4 | TXS0108E 8-Channel Logic Level Converter | Logic-level interfacing, where required | 1 | ₹59 |
| 5 | DS3231 RTC Module (without battery) | Real-time clock and timestamps | 1 | ₹219 |
| 6 | MicroSD Card Reader Module | Local data storage | 1 | ₹39 |
| **Total** | | | **6** | **₹1,644** |

---

## Available components

The following components are already available and not included in the cost above:

- Arduino Uno R3
- microSD card
- Breadboard
- Jumper wires

---

## Not yet included

- Rain gauge — to be selected and added later.

---

## Notes

- Prices are from Robu.in and may vary by region, supplier, and over time.
- Clone and third-party module variants can differ significantly. Always verify the specific board received.
- Do not substitute components without checking compatibility and updating the documentation.
- No purchases have been made yet.

---

## Status legend

| Status | Meaning |
|--------|---------|
| Proposed | Considered, but not selected or acquired |
| Selected | Chosen for the build, but not yet acquired |
| Acquired | Physically obtained |
| Tested | Verified working in the current design |

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