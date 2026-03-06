# Electronics & Wiring

## Goal

Document power distribution, signal wiring, and safety-relevant controls.

## Power tree

| Rail | Nominal Voltage | Max Current | Source | Protected By | Loads |
|---|---:|---:|---|---|---|
|  |  |  |  |  |  |

## Wiring map

| From | To | Signal | Connector | Cable Type | Length | Notes |
|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |

## Grounding and shielding

- Chassis ground strategy:
- Signal ground strategy:
- Shield termination points:

## Bring-up checklist

1. Continuity check on all power rails.
2. Insulation/short check before first power-on.
3. Power-on with no sensitive loads connected.
4. Verify each subsystem rail and temperature rise.
5. Connect loads one subsystem at a time.

Record:

| Step | Result | Evidence |
|---|---|---|
| Continuity |  |  |
| No-load power-on |  |  |
| Motion controller online |  |  |
| Camera online |  |  |
| Thermal soak (30-60 min) |  |  |

## Safety controls

| Control | Implementation | Test Method | Last Verified |
|---|---|---|---|
| Fuse/breaker sizing |  |  |  |
| Emergency stop |  |  |  |
| Interlock behavior |  |  |  |

## References

- [Safety](safety.md)
- [Troubleshooting](troubleshooting.md)
