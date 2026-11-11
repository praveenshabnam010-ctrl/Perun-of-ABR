# Hardware Overview

## Purpose

ABR is intended to monitor temperature, relative humidity, atmospheric pressure, light intensity and rainfall. The design prioritises affordability, modularity, reproducibility, reliability and simplicity.

## Status

ABR is in the planning stage. No physical station has been built. No components have been acquired or tested. All components and connections described here are proposals.

## Proposed architecture

```text
                    +----------------------+
                    |   Arduino Uno R3     |
                    |   (main controller)  |
                    +----------+-----------+
                               |
        +----------------------+----------------------+
        |                      |                      |
   I2C bus                SPI bus                GPIO interrupt
        |                      |                      |
 BME280 (temperature,     microSD module         tipping-bucket
 humidity, pressure)      ILI9341 TFT            rain gauge
 BH1750 (light)
 DS3231 (real-time clock)
```

The microSD module and the ILI9341 display share the SPI bus and require separate chip-select lines. The exact requirements depend on the module variants.

## Proposed components

| Component | Role | Interface | Status | Verification needed |
| --- | --- | --- | --- | --- |
| Arduino Uno R3 | Main microcontroller | — | Proposed, not acquired | Confirm board variant and logic levels |
| BME280 | Temperature, relative humidity and atmospheric pressure | I2C | Proposed, not acquired | Confirm module regulator, level shifting and I2C address |
| BH1750 | Light intensity | I2C | Proposed, not acquired | Confirm module variant and I2C address |
| DS3231 | Real-time clock | I2C | Proposed, not acquired | Confirm module variant, battery and I2C address |
| MicroSD module | Local data storage | SPI | Proposed, not acquired | Confirm logic voltage and level shifting |
| 2.4-inch ILI9341 TFT | Local display | SPI | Proposed, not acquired | Confirm module voltage, control pins and level shifting |
| Tipping-bucket rain gauge | Rainfall measurement | GPIO interrupt | Proposed, not acquired | Confirm resolution, output type and debounce requirements |

## Power and logic levels

The Arduino Uno R3 operates at 5 V logic. Many sensor, storage and display modules are designed for 3.3 V logic. The actual requirements depend on the specific module variant.

Check each datasheet before connecting anything. Level shifting or a different module variant may be required. Do not assume compatibility based on the component name alone.

The Uno's 3.3 V rail has limited current capacity. Check the board datasheet and the current requirements of every module before using it to power the station.

## Open questions

- Which exact module variants will be used?
- What is the rain gauge resolution and output type?
- How will the station be powered?
- What enclosure is suitable for the local environment?
- Are there pin conflicts between the display, SD card, sensors and rain gauge?
- What measurement intervals and accuracy are appropriate?
- What level of weather protection is needed?

## What this document does not claim

No compatibility, accuracy, power consumption, reliability or test results are claimed. These must be verified with the physical hardware and the relevant datasheets.
