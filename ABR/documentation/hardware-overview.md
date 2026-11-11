# Hardware Overview

## Purpose

ABR is intended to monitor temperature, relative humidity, atmospheric pressure, light intensity and rainfall. The design prioritises affordability, modularity, reproducibility, reliability and simplicity.

## Status

ABR is in the planning stage. No physical station has been built. No components have been acquired or tested. All components and connections described here are proposals and are subject to change as the project develops.

---

## Proposed architecture

```text
                    +----------------------+
                    |   Arduino Uno R3     |
                    |   (main controller)  |
                    |   5 V logic          |
                    +----------+-----------+
                               |
        +----------------------+----------------------+
        |                      |                      |
   I²C bus (A4/A5)        SPI bus (D11–D13)      GPIO interrupt
        |                      |                      |
 BME280 (temp,          MicroSD module (CS: D4)   Tipping-bucket
 humidity, pressure)    ILI9341 TFT (CS: D10)     rain gauge (D2)
 BH1750 (light)
 DS3231 (real-time clock)
```

The MicroSD module and the ILI9341 display share the SPI bus and each require a dedicated chip-select line. I²C devices share the same two wires and are distinguished by their addresses. The exact requirements depend on the specific module variants used.

---

## Proposed components

### Core components

| Component | Role | Interface | Power rail | Status | Verification needed |
|-----------|------|-----------|------------|--------|---------------------|
| Arduino Uno R3 | Main microcontroller | — | External 5 V | Proposed, not acquired | Confirm board variant and logic level |
| BME280 | Temperature, relative humidity and atmospheric pressure | I²C | 3.3 V | Proposed, not acquired | Confirm module regulator, 5 V tolerance and I²C address |
| BH1750 | Light intensity | I²C | 3.3 V | Proposed, not acquired | Confirm module variant, 5 V tolerance and I²C address |
| DS3231 | Real-time clock | I²C | 5 V | Proposed, not acquired | Confirm module variant, battery type and I²C address |
| MicroSD module | Local data storage | SPI | 3.3 V logic | Proposed, not acquired | Confirm logic voltage, level shifting and CS pin |
| 2.4-inch ILI9341 TFT | Local display | SPI | 3.3 V logic | Proposed, not acquired | Confirm module voltage, level shifting and control pin layout |
| Tipping-bucket rain gauge | Rainfall measurement | GPIO interrupt | — | Proposed, not acquired | Confirm resolution, output type and debounce requirements |

### Supporting components

| Component | Purpose | Status |
|-----------|---------|--------|
| Breadboard or perfboard | Prototyping and assembly | Proposed, not acquired |
| Jumper wires | Connections | Proposed, not acquired |
| Logic-level shifter | 5 V to 3.3 V conversion, where required | Proposed, not acquired |
| Voltage regulator | Supplementary 3.3 V supply, if needed | Proposed, not acquired |
| Regulated 5 V power supply | Station power | Proposed, not acquired |
| Weather-resistant enclosure | Outdoor protection | Proposed, not acquired |
| Cable glands, connectors and mounting hardware | Assembly and weatherproofing | Proposed, not acquired |

---

## Power and logic levels

The Arduino Uno R3 operates at **5 V logic**. Several proposed modules — including the BME280, BH1750, ILI9341 TFT and MicroSD module — are commonly designed for **3.3 V logic**.

**Do not assume that a 3.3 V module is 5 V tolerant.** Connecting a 5 V logic signal to a 3.3 V module input without verification risks damaging the module.

| Device | Typical logic voltage | 5 V tolerant? |
|--------|-----------------------|---------------|
| BME280 | 3.3 V | Not assumed — verify the specific module |
| BH1750 | 3.3 V | Not assumed — verify the specific module |
| DS3231 | 3.3 V–5 V | Many modules include a regulator; verify |
| ILI9341 TFT | 3.3 V (some modules include level shifting) | Not assumed — verify the specific module |
| MicroSD module | 3.3 V (most modules include a regulator and level shifter) | Not assumed — verify the specific module |

Where a module is not 5 V tolerant and does not include level shifting, a separate logic-level shifter is required. Check each datasheet before making any connections.

The Uno's onboard 3.3 V rail has a limited current capacity. If multiple 3.3 V modules draw more current than the rail can supply, an external 3.3 V regulator will be needed. Verify before connecting.

---

## Open questions

- Which exact module variants will be used?
- What is the rain gauge resolution and output type?
- How will the station be powered in deployment?
- What enclosure is suitable for the local environment?
- What measurement intervals and accuracy are appropriate?
- What level of weatherproofing is needed for the enclosure and cable entry points?

---

## What this document does not claim

No compatibility, accuracy, power consumption, reliability or test results are claimed. All hardware is proposed and unverified. These details must be established using the physical hardware and the relevant datasheets.
