# Wiring

**Status: planning.** No wiring has been performed or tested. The pin assignments below are proposals and must be verified against the datasheets of the specific modules used before anything is connected.

---

## Buses

### I²C — A4 (SDA), A5 (SCL)

The DS3231 RTC and the AHT20+BMP280 module share the I²C bus. Each device is addressed individually, so they can coexist on the same two wires provided there are no address conflicts.

Pull-up resistors may already be present on the modules. Multiple modules on the same bus can affect bus loading. Check the requirements of each module before combining them.

### SPI — D11 (MOSI), D12 (MISO), D13 (SCK)

The ST7789 TFT display and the MicroSD module share the SPI bus. Each device has its own chip-select line:

- ST7789 TFT — CS on **D10**
- MicroSD module — CS on **D4**

Only one SPI device is active at a time, determined by which chip-select line is pulled low.

---

## Voltage compatibility

The Arduino Uno R3 operates at **5 V logic**. Many modules in the proposed design operate at **3.3 V logic**.

**Do not connect a 5 V logic signal to a 3.3 V module without first verifying that the module is 5 V tolerant or includes a level shifter.** If it does not, a separate logic-level shifter is required.

| Device | Typical logic voltage | Notes |
|--------|-----------------------|-------|
| DS3231 RTC | 3.3 V–5 V | Many modules include a regulator; verify |
| AHT20+BMP280 | 3.3 V | Verify whether the module includes level shifting |
| CJMCU TEMT6000 | 3.3 V–5 V | Depends on module variant |
| ST7789 TFT | 3.3 V | Some modules include level shifting; verify |
| MicroSD module | 3.3 V | Most modules include a regulator and level shifter; verify |

---

## Power

- The Arduino Uno R3 provides 5 V and 3.3 V rails, but the 3.3 V rail has a limited current capacity. Check the board datasheet.
- If the combined current draw of 3.3 V modules exceeds the rail's capacity, an external regulated 3.3 V supply is required.
- The final power supply for field deployment has not been selected. It must supply sufficient current for all components reliably.
- Consider protection against reverse polarity, overcurrent and environmental conditions.

---

## Connection summary

| Device | Bus | Proposed pins | Power rail | Notes |
|--------|-----|--------------|------------|-------|
| DS3231 RTC | I²C | A4 (SDA), A5 (SCL) | 5 V | Confirm address (0x68) and module variant |
| AHT20+BMP280 | I²C | A4 (SDA), A5 (SCL) | 3.3 V | Confirm addresses and 5 V tolerance |
| CJMCU TEMT6000 | Analog | A0 | 3.3 V–5 V | Confirm analog output range |
| ST7789 TFT | SPI | D10 (CS), D8 (RESET), D7 (DC), D11, D12, D13 | 3.3 V logic | Confirm control pin layout and level shifting |
| MicroSD module | SPI | D4 (CS), D11, D12, D13 | 3.3 V logic | Confirm level shifting and FAT32 compatibility |

See the [pin map](../hardware/pinmap.md) for the full proposed assignments.

---

## Before wiring

- [ ] Collect the datasheet for every specific module to be used.
- [ ] Confirm the logic voltage of each module.
- [ ] Determine whether level shifting is required for each device.
- [ ] Review the pin map and check for conflicts.
- [ ] Check I²C addresses for conflicts.
- [ ] Calculate the total current draw and verify the power supply can meet it.
- [ ] Prepare a wiring diagram before making any connections.
- [ ] Do not connect anything until the above checks are complete.

---

## Diagram

A wiring diagram and photographs will be added after the hardware has been acquired and the connections have been verified on the physical build. No diagram is included yet.
