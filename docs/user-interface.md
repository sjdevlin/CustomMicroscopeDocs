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

This page now includes startup behavior, window navigation, and initial `Microscopeone` controls.

## Microscopeone window overview

Open from: `Temika` main window -> `View` -> `Microscopeone`.

Observed window title: `Temika Microscopeone`

This window has four tabs:

1. `Movement`
2. `Illumination`
3. `Environment`
4. `IO`

## Microscopeone -> Movement tab

### Stepper section

The `Stepper` section has four axis rows:

- `X`: stage axis
- `Y`: stage axis
- `Z`: focus axis
- `Condenser`: condenser axis

Each row includes:

- Arrow buttons for axis movement
- A speed slider (default shown as `5`, range `1-9`)
- Numeric position display
- `Reset` control for position zeroing
- `Enable` checkbox for axis control

At slider value `5`, observed speed scales differ by axis:

| Axis | Speed at Slider 5 |
|---|---|
| X/Y | 100 um/s |
| Z (focus) | 5 um/s |
| Condenser | 500 um/s |

### Referencing and zeroing guidance

- Position readouts can be zeroed at any point.
- Use a known reference before operation.
- Recommended practice:
  1. Lower `Z` to the lowest safe point.
  2. Zero `Z`.
  3. Lower `Condenser` to the lowest safe point (ensure no plate collision risk).
  4. Zero `Condenser`.
- With both zeroed at the low reference, condenser and focus values can be matched for consistent optical path setup.

### Axis enable behavior

- The `Enable` checkbox at the right of each axis can disable control for that axis.
- This prevents accidental movement.
- Important: disabling an axis also affects software/script control, not only manual GUI input.

### Fluorescence selector

- In the `Fluorescence` section, the operational default should be `Position 1`.

## Microscopeone -> Illumination tab (initial observations)

- Multiple LED channels are shown (for example BF 475 nm, BF 528 nm, BF 625 nm, BF 655 nm, FL 385 nm, FL 475 nm, FL 528 nm, FL 625 nm).
- Each channel has:
  - intensity slider/value
  - `Enable` checkbox
  - status indicator
- Trigger mode options are visible (`Trigger 0`, `Trigger 1`, `None`).
- Sequence section includes channel checkboxes per step.
- Photodiode and recording controls are visible.

## Microscopeone -> Environment tab (initial observations)

- Temperature plot and sensor readbacks (`TC`, `RTD`, `I2C`, enclosure, internal, IO) are shown.
- Control blocks for peltier/power/enclosure/LED/fan/buzzer are present.
- Each block appears to include setpoint/value controls and optional enable controls.
- Recording controls are visible at the bottom.

## Microscopeone -> IO tab

Pending screenshots and commentary.

## UI screen catalog (build from screenshots)

Add one row per screenshot you share.

| Screenshot File | Window/Panel Name | Inferred Function | Controls Seen | Open Questions |
|---|---|---|---|---|
| `Main_Window.png` | Temika (Main) | Startup control and save naming setup | Menus, Record Camera, Save Settings, basename/append/numbering | Confirm exact behavior of numbering controls |
| `Main_Window_View_Menu.png` | Temika View Menu | Window visibility toggles for UI modules | Video 0-3, Display Settings, Camera Control, Camera Feedback, Microscopeone, Script | Confirm whether checked state persists across relaunch |
| `Microscopeone_Movement.png` | Microscopeone -> Movement | Manual axis motion, reference zeroing, fluorescence position | X/Y/Z/Condenser steppers, speed scales, enable per axis, fluorescence selector, autofocus region | Confirm if speed mapping for values other than 5 is linear |
| `Microscopeone_Illumination.png` | Microscopeone -> Illumination | LED channel intensity and trigger/sequence setup | Channel sliders, enable toggles, trigger selection, sequence channels, photodiode | Document normal channel presets for common imaging modes |
| `Microscopeone_Environment.png` | Microscopeone -> Environment | Thermal and power subsystem monitoring/control | Temperature plot, sensor values, peltier/power/enclosure/LED/fan/buzzer controls | Define safe operating ranges and default enabled blocks |

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
