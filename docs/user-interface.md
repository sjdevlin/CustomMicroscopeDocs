# User Interface

## Goal

Document how operators use the `temika` graphical interface for daily operation.

## Launch behavior

- Application: `temika`
- Launch method: run `temika` from terminal
- UI type: X-Windows graphical interface
- Primary users: trained microscope operators

Launching `temika` opens two windows:

- `Temika` (main control window)
- `Temika Video` (video display window)

At this stage, the control software is running and the microscope can be controlled by external software or by sending an XML script.

For most direct GUI control and settings changes, additional windows must be opened from the main window.

## Main window overview (`Temika`)

Observed from the initial screenshot:

- Menu bar: `File`, `View`, `Help`
- Top controls include `Record Camera` and `Advanced`
- `Save Settings` area includes:
  - Free-text comment field
  - `Basename` path field and `Browse` button
  - `Append` dropdown (shown as `Date`)
  - Numbering controls (`First Number`, `Second Number`)

## View menu: opening additional windows

Additional control windows are available from `View` in the main window.

Options observed in `Main_Window_View_Menu.png`:

| View Menu Item | Purpose (inferred) | Default State in Screenshot |
|---|---|---|
| Video 0 | Primary video window toggle | Enabled |
| Video 1 | Additional video window toggle | Disabled |
| Video 2 | Additional video window toggle | Disabled |
| Video 3 | Additional video window toggle | Disabled |
| Display Settings | Display/render settings window | Disabled |
| Camera Control | Camera parameter control window | Disabled |
| Camera Feedback | Camera status/feedback window | Disabled |
| Microscopeone | Microscope hardware control window | Disabled |
| Script | Script editor/execution window | Disabled |

## Operator workflow map

1. Launch `temika` and connect hardware.
2. Home/reference axes.
3. Load or choose imaging profile.
4. Use live view for focus and exposure tuning.
5. Define acquisition region/sequence.
6. Start capture.
7. Verify output and metadata.
8. Shutdown and log run summary.

## Current documentation scope

This introduction captures startup behavior and window navigation.

Next section to build: `Microscopeone` window (controls, parameters, and operating sequence).

## UI screen catalog (build from screenshots)

Add one row per screenshot you share.

| Screenshot File | Window/Panel Name | Inferred Function | Controls Seen | Open Questions |
|---|---|---|---|---|
| `Main_Window.png` | Temika (Main) | Startup control and save naming setup | Menus, Record Camera, Save Settings, basename/append/numbering | Confirm exact behavior of numbering controls |
| `Main_Window_View_Menu.png` | Temika View Menu | Window visibility toggles for UI modules | Video 0-3, Display Settings, Camera Control, Camera Feedback, Microscopeone, Script | Confirm whether checked state persists across relaunch |
| `temika-stage-control.png` | Stage Control | Motion and homing controls |  |  |
| `temika-acquisition.png` | Acquisition | Sequence setup and capture start |  |  |
| `temika-settings.png` | Settings | Device and profile configuration |  |  |

## Screenshot capture protocol

When capturing UI images, include:

- Full window, not cropped controls only
- One screenshot per major panel/dialog
- A short filename that identifies function
- A note of what action was performed just before capture

Recommended naming: `YYYY-MM-DD_temika_<panel-name>_<operator>.png`

## References

- [Software Control](software-control.md)
- [Operating Procedures](operation-sops.md)
