# Advanced Controls

This section covers the higher-control features exposed through the Temika GUI once the basic workflow is understood.

## Autofocus

The `Movement` tab includes an `Afocus` section with:

- autofocus enable
- autofocus offset
- live error, velocity, and position status
- sensor graph

The attached reference XML (`temika.xml`) shows that the autofocus subsystem also supports:

- lock wait: `<wait_lock>value timeout</wait_lock>`
- sensor period
- LED drive
- peak start, stop, threshold, fit points, and setpoint
- PID tuning values

Use autofocus when:

- the sample is compatible with the optical lock signal
- long runs need drift compensation
- scripted imaging returns repeatedly to the same optical plane

Disable autofocus before large manual `Z` moves or scripted repositioning, then re-enable it and wait for lock once motion has finished.

## Fluorescence position

The `Movement` tab includes fluorescence position selection. Existing operating practice is to keep the microscope in `Position 1` unless a specific validated workflow requires a different setting.

If there is no fluorescent image:

1. Confirm the selected LED channel is enabled.
2. Confirm the fluorescence position is correct.
3. Confirm the filter set installed at that position matches the fluorophore.

The full filter specifications still need to be added to [Overview](../overview.md).

## Display settings

The manual describes a `Display Settings` window for video display only. These controls affect visualization, not recorded data.

Use it to adjust:

- which video window is being configured
- which camera stream is shown
- image scaling
- interpolation
- pixel display and colour mapping
- pixel range mapping, including automatic range and locked range

This is useful when the live image is difficult to inspect because of dynamic range or sensor size.

Screenshot placeholder:
`TODO: add confirmed Display Settings window screenshot from the Temika manual or a fresh screen capture.`

## Camera-specific settings

The manual notes that `Camera Control` exposes camera-specific GenICam features defined by the manufacturer. These are the place to set items such as:

- exposure time
- trigger mode
- acquisition mode
- transmission state

When recording a validated imaging workflow, note both the GUI values and the corresponding XML or GenICam feature names used by automation.

Screenshot placeholder:
`TODO: add confirmed Camera Feedback or advanced camera-feature screenshot if these windows will be documented in detail.`

## Illumination sequences and trigger modes

The `Illumination` tab can build synchronized multi-colour sequences.

- `Number`: total number of sequencer steps
- `Index`: currently displayed step
- `Enable`: turns the sequencer on
- step checkboxes: select the LED active in each step

This is the GUI equivalent of the XML commands:

```xml
<illumination>
  <sequencer_enable>ON</sequencer_enable>
  <sequencer_step number="2">0x22</sequencer_step>
  <sequencer_number>5</sequencer_number>
  <sequencer_index>3</sequencer_index>
</illumination>
```

## Environment and temperature control

Open `Microscopeone -> Environment`.

![Microscopeone environment tab](../assets/images/temika-manual/microscopeone-environment.png)

This tab exposes:

- temperature plots
- sensor readouts (`TC`, `RTD`, `I2C`, enclosure, internal, IO)
- peltier and power channels
- enclosure control
- LED and fan duty-cycle controls
- buzzer control

The GUI allows both open-loop and feedback-controlled operation depending on the selected channel.

Use the temperature controls carefully:

- confirm which power channel is connected to the actual heater or peltier
- confirm the active sensor type
- enable feedback only when the sensor mapping is known
- record setpoints in experiment notes for long runs

## Script window

![Temika script window](../assets/images/temika-manual/script-window.png)

The `Script` window shows script interpreter output and running script status.

- Multiple scripts can run in parallel.
- `Terminate` stops the selected script.
- `Clear` clears the output display.

Use this window whenever XML automation is launched from within Temika so that execution progress and failures remain visible.
