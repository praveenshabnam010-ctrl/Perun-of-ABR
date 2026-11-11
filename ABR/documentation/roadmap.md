# Roadmap

Status labels: **Planned**, **In development**, **Implemented**, **Tested**. Only mark work as Implemented when it exists, and as Tested when it has been verified on the physical hardware.

## Phase 0 — Repository foundations

**Status: In development**

- Add contribution guidance and ignore rules.
- Keep the README and project status accurate.
- Choose a licence (deferred).

## Phase 1 — Planning documentation

**Status: In development**

- Document the proposed hardware architecture.
- Document proposed pin assignments and wiring considerations.
- Record the proposed bill of materials.
- Identify open questions and verification tasks.

## Phase 2 — Firmware skeleton

**Status: Planned**

- Add configuration for pins and measurement intervals.
- Implement a non-blocking main loop.
- Add one sensor module at a time.
- Bench-test each sensor when the hardware is available.

## Phase 3 — Integration

**Status: Planned**

- Add real-time clock timestamps.
- Add CSV logging to the microSD card.
- Add local display output.
- Keep each module independent and replaceable.

## Phase 4 — Reliability

**Status: Planned**

- Handle missing or invalid readings gracefully.
- Enforce sensor measurement intervals.
- Add rain-gauge debounce.
- Record calibration notes and measurement limitations.

## Phase 5 — Prototype

**Status: Planned**

- Build the physical station.
- Record actual test results.
- Add photographs and a verified wiring diagram.
- Document known limitations.

## Phase 6 — Release

**Status: Planned**

- Tag a documented version.
- Publish setup and troubleshooting guidance.
- Review the documentation for reproducibility.

## Current blockers

- No physical hardware has been acquired yet.
- Exact module variants and logic levels are unverified.
- No firmware has been written.
- No measurements or test results exist.
