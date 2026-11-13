# Pin Map

**Status: proposed, not verified.**

The pin assignments below are based on the confirmed hardware components and have not been tested on physical hardware. They are subject to change as the project develops. Once a physical build is complete and tested, this document will be updated to reflect the confirmed assignments.

If a conflict or error is identified at any stage of development, this document should be corrected and the change noted.

---

## Arduino Uno R3

The Arduino Uno R3 operates at 5 V logic. All pin assignments below are proposals. Verify every assignment against the datasheet of the specific module you are using before making any connections.

---

## I²C bus — A4 (SDA) and A5 (SCL)

The DS3231 and AHT20+BMP280 module share the I²C bus. Each device has a different address and can coexist on the same two wires, provided there are no address conflicts.

| Device | Signal | Arduino pin | Power rail | Notes |
|--------|--------|-------------|------------|-------|
| DS3231 RTC | SDA | A4 | 5 V | Shared I²C bus |
| DS3231 RTC | SCL | A5 | 5 V | Shared I²C bus |
| DS3231 RTC | GND | GND | — | — |
| AHT20+BMP280 | SDA | A4 | 3.3 V | Shared I²C bus |
| AHT20+BMP280 | SCL | A5 | 3.3 V | Shared I²C bus |
| AHT20+BMP280 | GND | GND | — | — |

---

## SPI bus — D11 (MOSI), D12 (MISO), D13 (SCK)

The ST7789 TFT display and the MicroSD module share the SPI bus. Each device requires its own chip-select (CS) line to avoid conflicts.

### ST7789 TFT display (1.9", 170×320)

| Signal | Arduino pin | Notes |
|--------|-------------|-------|
| CS | D10 | Chip select — active low |
| DC/RS | D9 | Data/command select |
| RST | D8 | Reset line; some modules use the Arduino reset pin instead |
| MOSI | D11 | Shared SPI bus |
| MISO | D12 | Shared SPI bus |
| SCK | D13 | Shared SPI bus |

### MicroSD Card Reader Module

| Signal | Arduino pin | Notes |
|--------|-------------|-------|
| CS | D4 | Chip select — active low |
| MOSI | D11 | Shared SPI bus |
| MISO | D12 | Shared SPI bus |
| SCK | D13 | Shared SPI bus |

---

## Analog input — Light sensor

| Device | Signal | Arduino pin | Notes |
|--------|--------|-------------|-------|
| CJMCU TEMT6000 | Analog out | A0 | Ambient light intensity measurement |
| CJMCU TEMT6000 | GND | GND | — |

---

## Power rails

| Rail | Voltage | Notes |
|------|---------|-------|
| 5 V | 5 V | Arduino Uno regulated output; DS3231 |
| 3.3 V | 3.3 V | Arduino Uno regulated output; limited current capacity — check the board datasheet |
| GND | — | Common ground for all devices |

---

## SmartElex Bi-Directional Logic Level Converter

Used to shift 5 V logic signals from the Arduino Uno R3 to 3.3 V logic for modules that are not 5 V tolerant (ST7789 TFT, MicroSD module, AHT20+BMP280). Verify the specific converter's pinout before wiring — it does not use Arduino digital pins; it sits between the Uno and the modules on their signal lines.

---

## I²C addresses

| Device | Commonly reported address | Notes |
|--------|--------------------------|-------|
| DS3231 RTC | 0x68 | Fixed; verify for the specific module used |
| AHT20 | 0x38 | Typical; verify |
| BMP280 | 0x76 or 0x77 | Determined by the SDO pin; verify |

These are typical values reported for these components. They are not confirmed for the specific modules that will be used. Verify before use.

---

## Voltage compatibility

The Arduino Uno R3 operates at **5 V logic**. Several confirmed modules operate at **3.3 V logic**.

| Device | Typical operating voltage | 5 V tolerant? | Level shifter needed? |
|--------|--------------------------|---------------|----------------------|
| DS3231 RTC | 3.3 V–5 V | Many modules include a regulator | Verify |
| AHT20+BMP280 | 3.3 V | Not assumed — verify | Likely |
| ST7789 TFT | 3.3 V logic | Not assumed — verify | Likely |
| MicroSD module | 3.3 V logic | Most modules include regulator/shifter | Verify |
| CJMCU TEMT6000 | 3.3 V–5 V | Depends on module variant | Verify |

Do not connect a 5 V logic signal to a 3.3 V module input without first verifying that the module is 5 V tolerant or that it includes a level shifter. If it does not, the SmartElex Bi-Directional Logic Level Converter is required.

---

## Verification checklist

- [ ] Confirm the logic voltage of every module against its datasheet.
- [ ] Confirm whether level shifting is required for each device.
- [ ] Confirm that I²C addresses do not conflict.
- [ ] Confirm that SPI devices use separate chip-select pins.
- [ ] Confirm total current consumption against the power supply capacity.
- [ ] Check for pin conflicts with any additional modules added in future.
- [ ] Update this document after each verification step.
- [ ] Record the exact module variant used for each component.