# Overview

The Temika microscope is a brightfield and epi-fluorescent microscope designed for automated imaging. It combines motorized XY stage motion, motorized focus (`Z`), motorized condenser height, programmable illumination, temperature control, and an optical autofocus system similar in purpose to Nikon PFS.

## Core capabilities

- Imaging modes: brightfield and epi-fluorescence
- Illumination channels: 8 total
- Motion axes: motorized `X`, `Y`, `Z`, and condenser
- Stage accessories: interchangeable inserts for cover slides, multiwell plates, and custom sample holders
- Temperature module: controllable from the GUI or through automation
- Autofocus: optical level lock with offset and PID-style control parameters

## Optical and illumination specification

### LED channels

The `Microscopeone -> Illumination` tab exposes the following channels:

| Channel | Mode | Nominal LED Wavelength | Notes |
|---|---|---|---|
| Ch0 | Brightfield | 475 nm | From GUI screenshot in `temika_manual.odt` |
| Ch1 | Brightfield | 528 nm | From GUI screenshot in `temika_manual.odt` |
| Ch2 | Brightfield | 625 nm | From GUI screenshot in `temika_manual.odt` |
| Ch3 | Brightfield | 655 nm | From GUI screenshot in `temika_manual.odt` |
| Ch4 | Epi | 385 nm | From GUI screenshot in `temika_manual.odt` |
| Ch5 | Epi | 475 nm | From GUI screenshot in `temika_manual.odt` |
| Ch6 | Epi | 528 nm | From GUI screenshot in `temika_manual.odt` |
| Ch7 | Epi | 625 nm | From GUI screenshot in `temika_manual.odt` |

### Fluorescence filters

The microscope exposes fluorescence position selection in software, but the attached manuals do not provide the full excitation/dichroic/emission specification. Fill these values once the filter set is confirmed from hardware labels or supplier records.

| Position | Intended Use | Excitation Filter | Dichroic | Emission Filter | Notes |
|---|---|---|---|---|---|
| 0 | TODO | TODO | TODO | TODO | Placeholder |
| 1 | Default operating position | TODO | TODO | TODO | Current workflows use this as the standard position |
| 2 | TODO | TODO | TODO | TODO | Placeholder |

## Motion and sample handling

| Subsystem | Description | Notes |
|---|---|---|
| XY stage | Motorized stage for sample positioning | Used for manual movement and scripted scans |
| Focus (`Z`) | Motorized objective/sample focus axis | Works with autofocus system |
| Condenser | Motorized condenser height | Can be zeroed relative to focus for repeatable setup |
| Inserts | Cover slide, multiwell plate, and other holders | Confirm insert list and part numbers when available |

## Temperature control

The microscope includes a temperature control module with monitored sensors and controllable power channels. The GUI exposes temperature plots, readback values, and feedback enable controls. Programmatic control is also available through `microscopeone` XML commands such as `<pwr number="0"><feedback>...</feedback></pwr>`.

## Autofocus

Temika provides an optical autofocus subsystem (`afocus`) that behaves like a hardware lock rather than a software image-sharpness search. The control layer exposes:

- enable/disable
- offset
- lock wait
- peak start/stop/setpoint
- threshold and fit points
- PID terms (`kp`, `ti`, `td`)

## Hardware photos

### Front view

![Front view of the Temika microscope](assets/images/microscope/front-view.jpg)

### Rear view

![Rear view of the Temika microscope](assets/images/microscope/rear-view.jpg)

### Electronics connections

![Microscope controller back panel](assets/images/microscope/back-panel.jpg)

![Microscope controller front panel](assets/images/microscope/front-panel.jpg)

## Important physical features from `microscope.odt`

- Field diaphragm and aperture diaphragm should normally be opened fully for standard setup unless a specific imaging mode requires adjustment.
- The condenser has centering screws and a locking screw.
- The phase annulus and Bertrand lens are present for specialized optical modes.
- The epi-fluorescence block accepts a liquid guide and has a field diaphragm.
- Camera mounting is via the C-mount camera port.
