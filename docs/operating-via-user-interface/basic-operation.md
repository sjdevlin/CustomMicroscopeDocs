# Basic Operation

This section covers the normal GUI workflow for launching Temika, opening the required windows, moving the microscope, setting illumination, and taking an image.

## Start the GUI

1. Open a terminal on the Temika control workstation.
2. Run `temika`.
3. Watch the terminal for status messages.
4. Confirm that the `Temika` main window opens.
5. If a working camera is connected, confirm that a `Temika Video` window opens automatically.

The manuals indicate that `temika` running by itself is enough to expose microscope control to external software and XML scripts. The GUI windows are needed for interactive operation and most settings changes.

## Main window

![Temika main window](../assets/images/temika-manual/main-window.png)

The main window provides:

- `File`, `View`, and `Help` menus
- `Record Camera` shortcut
- `Advanced` shortcut
- save settings for output naming and annotation

### Save settings

| Control | Purpose | Notes |
|---|---|---|
| Comment field | Free-text annotation saved into recorded files | Use for experiment notes |
| `Basename` | Base output path and filename stem | Should point to the data directory |
| `Append` | Filename suffix policy | `Nothing`, `Date`, or `Two Numbers` |
| `First Number` / `Second Number` | Manual numbering fields | Used when `Append = Two Numbers` |

The manual notes that the data partition is RAID0: high performance but not fault-tolerant. Copy data to reliable storage after experiments.

## Open the working windows

From `View`, open the windows needed for the current task:

- `Video 0`
- `Display Settings`
- `Camera Control`
- `Microscopeone`
- `Script` when running XML scripts

For routine interactive imaging, `Video 0`, `Camera Control`, and `Microscopeone` are the usual minimum set.

## Video window

![Temika video window](../assets/images/temika-manual/video-window.png)

The video window displays the live camera stream.

- A purple border at the top and right marks the full camera field of view.
- Resize the window or change scale to see the full sensor area.
- Pixel information is shown for the cursor position.
- Display adjustments are visualization-only and are not recorded into the image data.

## Camera control

![Camera control window](../assets/images/temika-manual/camera-control.png)

Use `Camera Control` to:

- select the active camera
- rename the displayed camera name if needed
- enable or disable video transmission
- access camera-specific GenICam features
- send a software trigger
- start recording the camera video stream

The exact camera features depend on the camera model and vendor feature set.

## Move the microscope

Open `Microscopeone` and use the `Movement` tab.

![Microscopeone movement tab](../assets/images/temika-manual/microscopeone-movement.png)

### Stepper controls

The `Stepper` section contains rows for:

- `X` and `Y`: stage motion
- `Z`: focus
- `Condenser`: condenser height

Each row provides:

- arrow buttons for manual motion
- a speed slider
- direct numeric position entry
- a live position label
- `Reset` to zero the coordinate
- `Enable` to allow or block motion

At slider value `5`, the observed nominal speeds are:

| Axis | Speed at slider 5 |
|---|---|
| X/Y | 100 um/s |
| Z | 5 um/s |
| Condenser | 500 um/s |

### Position referencing

Start from a known reference whenever possible.

1. Lower `Z` to the lowest safe position and zero it.
2. Lower the condenser to the lowest safe position with no plate or sample holder in the way.
3. Zero the condenser position.

This makes it easier to set condenser and focus to matching values for a repeatable optical path.

### Axis enable

`Enable` disables an axis completely. This prevents accidental motion, but it also affects programmatic control. If an axis refuses to move from software, check whether it has been disabled in the GUI.

## Control illumination

Open `Microscopeone -> Illumination`.

![Microscopeone illumination tab](../assets/images/temika-manual/microscopeone-illumination.png)

Use this tab to:

- set LED intensity per channel
- enable or disable each LED channel
- select trigger synchronization mode
- define multi-step illumination sequences
- monitor photodiode readouts

For basic operation:

1. Select the required brightfield or epi channel.
2. Set the intensity.
3. Enable only the channel you want to use.
4. Use `Trigger 0` or `Trigger 1` when synchronizing illumination to the camera.
5. Use `None` only when unsynchronized continuous illumination is intended.

## Take an image

For a single interactive acquisition:

1. Set the save basename in the main window.
2. Confirm the required camera is selected in `Camera Control`.
3. Set illumination in `Microscopeone -> Illumination`.
4. Move to the desired position in `Microscopeone -> Movement`.
5. Focus using `Z`, or use autofocus if required.
6. Use software trigger or record control from `Camera Control`.

For streamed recording, the `Record Camera` shortcut on the main window can be used once the save settings are configured.
