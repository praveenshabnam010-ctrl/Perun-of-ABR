# Hardware Overview

## Purpose

ABR is intended to monitor temperature, relative humidity, atmospheric pressure and light intensity. The design prioritises affordability, modularity, reproducibility, reliability and simplicity.

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
   I²C bus (A4/A5)        SPI bus (D11–D13)      Analog
        |                      |                      |
 AHT20+BMP280      ST7789 TFT (CS: D10)      CJMCU TEMT6000 (A0)
 (temp, humidity,   MicroSD (CS: D4)          Ambient light
 pressure)
 DS3231 RTC
```

The MicroSD module and the ST7789 TFT display share the SPI bus and each require a dedicated chip-select line. I²C devices share the same two wires and are distinguished by their addresses. The exact requirements depend on the specific module variants used.

---

## Proposed components

### Core components

| Component | Role | Interface | Power rail | Status | Verification needed |
|-----------|------|-----------|------------|--------|---------------------|
| Arduino Uno R3 | Main microcontroller | — | External 5 V | Proposed, not acquired | Confirm board variant and logic level |
| AHT20+BMP280 | Temperature, relative humidity and atmospheric pressure | I²C | 3.3 V | Proposed, not acquired | Confirm module regulator, 5 V tolerance and I²C addresses |
| CJMCU TEMT6000 | Ambient light intensity | Analog (A0) | 3.3 V | Proposed, not acquired | Confirm module variant and analog output range |
| DS3231 | Real-time clock | I²C | 5 V | Proposed, not acquired | Confirm module variant, battery type and I²C address |
| MicroSD module | Local data storage | SPI | 3.3 V logic | Proposed, not acquired | Confirm logic voltage, level shifting and CS pin |
| GoldenMorning 1.9" ST7789 TFT | Local display | SPI | 3.3 V logic | Proposed, not acquired | Confirm module voltage, level shifting and control pin layout |
| SmartElex Bi-Directional Logic Level Converter | 5 V ↔ 3.3 V level shifting | — | 5 V / 3.3 V | Proposed, not acquired | Confirm converter pinout and channel count |

### Supporting components

| Component | Purpose | Status |
|-----------|---------|--------|
| Breadboard or perfboard | Prototyping and assembly | Proposed, not acquired |
| Jumper wires | Connections | Proposed, not acquired |
| Voltage regulator | Supplementary 3.3 V supply, if needed | Proposed, not acquired |
| Regulated 5 V power supply | Station power | Proposed, not acquired |
| Weather-resistant enclosure | Outdoor protection | Proposed, not acquired |
| Cable glands, connectors and mounting hardware | Assembly and weatherproofing | Proposed, not acquired |

---

## Power and logic levels

The Arduino Uno R3 operates at **5 V logic**. Several confirmed modules — including the AHT20+BMP280, ST7789 TFT and MicroSD module — are commonly designed for **3.3 V logic**.

**Do not assume that a 3.3 V module is 5 V tolerant.** Connecting a 5 V logic signal to a 3.3 V module input without verification risks damaging the module.

| Device | Typical logic voltage | 5 V tolerant? | Level shifter needed? |
|--------|-----------------------|---------------|----------------------|
| DS3231 RTC | 3.3 V–5 V | Many modules include a regulator | Verify |
| AHT20+BMP280 | 3.3 V | Not assumed — verify | Likely |
| CJMCU TEMT6000 | 3.3 V–5 V | Depends on module variant | Verify |
| ST7789 TFT | 3.3 V | Not assumed — verify | Likely |
| MicroSD module | 3.3 V | Most modules include regulator/shifter | Verify |

Where a module is not 5 V tolerant and does not include level shifting, the SmartElex Bi-Directional Logic Level Converter is required. Check each datasheet before making any connections.

The Uno's onboard 3.3 V rail has a limited current capacity. If multiple 3.3 V modules draw more current than the rail can supply, an external 3.3 V regulator will be needed. Verify before connecting.

---

## Open questions

- Which exact module variants will be used?
- How will the station be powered in deployment?
- What enclosure is suitable for the local environment?
- What measurement intervals and accuracy are appropriate?
- What level of weatherproofing is needed for the enclosure and cable entry points?

---

## What this document does not claim

No compatibility, accuracy, power consumption, reliability or test results are claimed. All hardware is proposed and unverified. These details must be established using the physical hardware and the relevant datasheets.