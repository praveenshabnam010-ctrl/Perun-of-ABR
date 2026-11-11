# Wiring

**Status: planning.** No wiring has been performed or tested. The pin assignments are proposals and must be verified before anything is connected.

## Buses

### I2C

The BME280, BH1750 and DS3231 share the I2C bus. Pull-up resistors may be present on the modules, and multiple modules can load the bus. Check the modules and the bus requirements before connecting them together.

### SPI

The microSD module and the ILI9341 display share the SPI bus. Each device requires its own chip-select line. Confirm the voltage and control-pin requirements of the display module.

### Rain gauge

The tipping bucket is intended to connect to an interrupt-capable GPIO pin. The required pull-up, debounce and protection depend on the gauge. Verify the output type before connecting it.

## Power

- The Arduino Uno R3 provides 5 V and 3.3 V rails, but the 3.3 V rail has limited current capacity. Check the board datasheet.
- Many modules are designed for 3.3 V logic. Do not connect 5 V logic signals directly without checking the module requirements.
- The final power supply has not been selected. It must be able to supply the station reliably for the intended deployment.
- Consider protection against reverse polarity, overcurrent and environmental conditions.

## Connection notes

| Device | Bus | Notes |
| --- | --- | --- |
| BME280 | I2C | Address depends on the module |
| BH1750 | I2C | Address depends on the module |
| DS3231 | I2C | Battery backup supports timekeeping when power is removed |
| MicroSD module | SPI | Confirm 3.3 V logic and level shifting |
| ILI9341 TFT | SPI | Control pins depend on the module; verify |
| Rain gauge | GPIO interrupt | Verify debounce and pull-up requirements |

See the [pin map](../hardware/pinmap.md) for the proposed assignments.

## Before wiring

- [ ] Collect the datasheet for every module.
- [ ] Confirm the logic levels.
- [ ] Review the pin map.
- [ ] Check the I2C addresses for conflicts.
- [ ] Check the power supply and current budget.
- [ ] Prepare a wiring diagram.
- [ ] Confirm that no hardware is connected until the checks are complete.

## Diagram

A wiring diagram and photographs will be added after the hardware has been acquired and verified. No diagram is included yet because the connections have not been tested.
