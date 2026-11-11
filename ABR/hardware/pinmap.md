# Pin Map

**Status: proposed, not verified.**

The pin assignments below are based on the proposed hardware design and have not been tested on physical hardware. They are subject to change as the project develops. Once a physical build is complete and tested, this document will be updated to reflect the confirmed assignments.

If a conflict or error is identified at any stage of development, this document should be corrected and the change noted.

---

## Arduino Uno R3

The Arduino Uno R3 operates at 5 V logic. All pin assignments below are proposals. Verify every assignment against the datasheet of the specific module you are using before making any connections.

---

## I²C bus — A4 (SDA) and A5 (SCL)

The BME280, BH1750 and DS3231 share the I²C bus. Each device has a different address and can coexist on the same two wires, provided there are no address conflicts.

| Device | Signal | Arduino pin | Power rail | Notes |
|--------|--------|-------------|------------|-------|
| BME280 | SDA | A4 | 3.3 V | Shared I²C bus |
| BME280 | SCL | A5 | 3.3 V | Shared I²C bus |
| BME280 | GND | GND | — | — |
| BH1750 | SDA | A4 | 3.3 V | Shared I²C bus |
| BH1750 | SCL | A5 | 3.3 V | Shared I²C bus |
| BH1750 | GND | GND | — | — |
| DS3231 | SDA | A4 | 5 V | Shared I²C bus |
| DS3231 | SCL | A5 | 5 V | Shared I²C bus |
| DS3231 | GND | GND | — | — |

---

## SPI bus — D11 (MOSI), D12 (MISO), D13 (SCK)

The ILI9341 TFT display and the MicroSD module share the SPI bus. Each device requires its own chip-select (CS) line to avoid conflicts.

### ILI9341 TFT display

| Signal | Arduino pin | Notes |
|--------|-------------|-------|
| CS | D10 | Chip select — active low |
| RESET | D8 | Reset line; some modules use the Arduino reset pin instead |
| DC | D7 | Data/command select |
| MOSI | D11 | Shared SPI bus |
| MISO | D12 | Shared SPI bus |
| SCK | D13 | Shared SPI bus |

### MicroSD module

| Signal | Arduino pin | Notes |
|--------|-------------|-------|
| CS | D4 | Chip select — active low |
| MOSI | D11 | Shared SPI bus |
| MISO | D12 | Shared SPI bus |
| SCK | D13 | Shared SPI bus |

---

## GPIO — Rain gauge

| Device | Signal | Arduino pin | Notes |
|--------|--------|-------------|-------|
| Tipping-bucket rain gauge | Signal | D2 | Interrupt-capable pin; pull-up and debounce requirements depend on the gauge module |
| Tipping-bucket rain gauge | GND | GND | — |

D2 supports hardware interrupts on the Arduino Uno R3 (interrupt 0). D3 is the other interrupt-capable pin and is available as a fallback.

---

## Power rails

| Rail | Voltage | Notes |
|------|---------|-------|
| 5 V | 5 V | Arduino Uno regulated output; DS3231 |
| 3.3 V | 3.3 V | Arduino Uno regulated output; limited current capacity — check the board datasheet |
| GND | — | Common ground for all devices |

---

## I²C addresses

| Device | Commonly reported address | Notes |
|--------|--------------------------|-------|
| BME280 | 0x76 or 0x77 | Determined by the SDO pin on the module; verify |
| BH1750 | 0x23 or 0x5C | Determined by the ADDR pin on the module; verify |
| DS3231 | 0x68 | Fixed; verify for the specific module used |

These are typical values reported for these components. They are not confirmed for the specific modules that will be used. Verify before use.

---

## Voltage compatibility

The Arduino Uno R3 operates at **5 V logic**. Many sensor and peripheral modules operate at **3.3 V logic**.

| Device | Typical operating voltage | 5 V tolerant? |
|--------|--------------------------|---------------|
| BME280 | 3.3 V | Not assumed — verify the specific module |
| BH1750 | 3.3 V | Not assumed — verify the specific module |
| DS3231 | 3.3 V–5 V | Many modules include a regulator; verify |
| ILI9341 TFT | 3.3 V logic (some modules include level shifting) | Not assumed — verify the specific module |
| MicroSD module | 3.3 V logic (most modules include a regulator and level shifter) | Not assumed — verify the specific module |

Do not connect a 5 V logic signal to a 3.3 V module input without first verifying that the module is 5 V tolerant or that it includes a level shifter. If it does not, a separate logic-level shifter is required.

---

## Verification checklist

- [ ] Confirm the logic voltage of every module against its datasheet.
- [ ] Confirm whether level shifting is required for each device.
- [ ] Confirm that I²C addresses do not conflict.
- [ ] Confirm that SPI devices use separate chip-select pins.
- [ ] Confirm the rain gauge output type, pull-up requirements and interrupt behaviour.
- [ ] Confirm total current consumption against the power supply capacity.
- [ ] Check for pin conflicts with any additional modules added in future.
- [ ] Update this document after each verification step.
- [ ] Record the exact module variant used for each component.
