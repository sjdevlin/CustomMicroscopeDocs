# Software Control

## Goal

Define software environment, launch/shutdown control, configuration management, and release controls for the Temika microscope.

## Primary control application

- Application: `temika`
- Launch method: command line
- UI type: X-Windows graphical application
- Primary users: trained microscope operators

For window-by-window behavior, see [User Interface](user-interface.md).

## Environment inventory

| Component | Version | Location | Notes |
|---|---|---|---|
| OS |  |  | Linux distribution and release |
| Acquisition app | `temika` |  | Command launched from terminal |
| Motion control library |  |  |  |
| Camera SDK/driver |  |  |  |
| Controller firmware |  |  |  |

## Startup sequence

1. Power hardware in approved order (controller, camera, illumination, host PC as applicable).
2. Open terminal on the control workstation.
3. Run `temika`.
4. Confirm the X-Windows UI opens with no startup errors.
5. Connect/initialize camera, stage, and illumination devices from the UI.
6. Run homing/reference routine before loading a sample.
7. Acquire a short test capture and verify focus, exposure, and stage motion.

## Shutdown sequence

1. Stop active acquisition.
2. Save run settings and metadata.
3. Park stage at safe position.
4. Close `temika` cleanly from UI (or controlled terminal exit if required).
5. Power down illumination and hardware using approved order.

## Configuration management

| Config Item | File/Location | Owner | Change Process |
|---|---|---|---|
| Motion limits |  |  | Change-controlled; revalidate travel after edits |
| Calibration constants |  |  | Link update to calibration record |
| Imaging profiles |  |  | Version profile names and lock defaults |
| Device addresses/ports |  |  | Confirm against physical wiring labels |
| UI presets/workspaces |  |  | Export before software updates |

## Data handling

| Data Type | Path | Format | Retention | Backup |
|---|---|---|---|---|
| Raw images |  |  |  |  |
| Metadata |  |  |  |  |
| Logs |  |  |  |  |
| Calibration artifacts |  |  |  |  |

## Common software issues

| Symptom | Likely cause | First check | Corrective action |
|---|---|---|---|
| `temika` does not launch | PATH or install issue | Run `which temika` and check terminal error | Fix install/PATH, relaunch |
| UI launches but no camera | SDK/driver or cable issue | Check device detection/status panel | Restart camera service, reconnect |
| Stage controls unresponsive | Controller link not initialized | Verify controller status and COM/USB mapping | Reconnect controller and rerun homing |
| Capture saves no files | Output path/config issue | Check selected save directory and permissions | Correct path and retry with test capture |

## Release checklist

- [ ] Confirm `temika` launch and clean shutdown on target workstation.
- [ ] Version and tag the control software.
- [ ] Archive configuration snapshot.
- [ ] Run smoke test on camera, stage, illumination.
- [ ] Update [Maintenance & Change Log](maintenance-change-log.md).
