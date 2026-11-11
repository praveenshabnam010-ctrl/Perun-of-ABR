# Pin Map

**Status: proposed.** Verify every assignment against the datasheets and the actual modules before wiring. No pin assignment is final.

## Arduino Uno R3

| Function | Proposed pin | Notes |
| --- | --- | --- |
| I2C SDA | A4 | Shared by BME280, BH1750 and DS3231 |
| I2C SCL | A5 | Shared by BME280, BH1750 and DS3231 |
| SPI MOSI | D11 | Shared by the microSD module and ILI9341 |
| SPI MISO | D12 | Shared by the microSD module and ILI9341 |
| SPI SCK | D13 | Shared by the microSD module and ILI9341 |
| MicroSD chip select | D10 | Proposed; confirm module requirements |
| ILI9341 chip select | D9 | Proposed; confirm module requirements |
| ILI9341 data/command | D8 | Proposed; confirm module requirements |
| ILI9341 reset | D7 | Proposed; some modules use the Arduino reset line instead |
| Rain gauge | D2 | Interrupt-capable; confirm output type and debounce requirements |
| Power | 5 V, 3.3 V and GND | Depends on the modules; verify before connecting |

## I2C addresses

| Device | Commonly used address | Status |
| --- | --- | --- |
| BME280 | 0x76 or 0x77 | Module-dependent; verify |
| BH1750 | 0x23 or 0x5C | Module-dependent; verify |
| DS3231 | 0x68 | Verify for the module used |

These are typical values, not confirmed values for the modules that will be used.

## Verification checklist

- [ ] Confirm the logic voltage of every module.
- [ ] Confirm whether level shifting is required.
- [ ] Confirm that I2C addresses do not conflict.
- [ ] Confirm that SPI devices use separate chip-select pins.
- [ ] Confirm the rain gauge output type and interrupt behaviour.
- [ ] Confirm total current consumption and power supply capacity.
- [ ] Check for pin conflicts with any future modules.
- [ ] Update this file after verification.
