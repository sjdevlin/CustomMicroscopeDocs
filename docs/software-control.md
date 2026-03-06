# Software & Control

## Goal

Define the software stack, startup sequence, and data handling path for reliable operation.

## Environment inventory

| Component | Version | Location | Notes |
|---|---|---|---|
| OS |  |  |  |
| Acquisition app |  |  |  |
| Motion control library |  |  |  |
| Camera SDK/driver |  |  |  |
| Controller firmware |  |  |  |

## Startup sequence

1. Power hardware in approved order.
2. Start control application.
3. Connect camera, stage, and illumination devices.
4. Run homing/reference routine.
5. Acquire and review test frames.

## Configuration management

| Config Item | File/Location | Owner | Change Process |
|---|---|---|---|
| Motion limits |  |  |  |
| Calibration constants |  |  |  |
| Imaging profiles |  |  |  |
| Device addresses/ports |  |  |  |

## Data handling

| Data Type | Path | Format | Retention | Backup |
|---|---|---|---|---|
| Raw images |  |  |  |  |
| Metadata |  |  |  |  |
| Logs |  |  |  |  |
| Calibration artifacts |  |  |  |  |

## Release checklist

- [ ] Version and tag the control software.
- [ ] Archive configuration snapshot.
- [ ] Run smoke test on camera, stage, illumination.
- [ ] Update [Maintenance & Change Log](maintenance-change-log.md).
