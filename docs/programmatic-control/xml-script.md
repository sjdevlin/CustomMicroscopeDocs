# XML Script

Temika can execute XML scripts directly. This is the simplest route for unattended acquisitions such as time courses, repeated capillary imaging, or scripted plate positions.

## How the XML model works

The root element is `<temika>`. Inside that, commands are executed in sequence. XML blocks target subsystems such as:

- `<save>` for output naming
- `<camera>` for camera selection, GenICam settings, triggering, and recording
- `<microscopeone>` for illumination, motion, autofocus, temperature, digital outputs, and recording
- `<sleep>` and `<timestamp>` for timing control

The full reference file is available here: [temika.xml](../assets/templates/temika.xml)

A shortened example:

```xml
<temika>
  <save>
    <basename>test_file</basename>
    <append>TWONUMBERS</append>
  </save>

  <camera name="Genicam Point Grey Research Blackfly BFLY-U3-23S6M 01223BFA">
    <genicam>
      <float feature="ExposureTime">1918.4</float>
    </genicam>
    <record>OFF</record>
  </camera>

  <microscopeone>
    <fluorescence_position>1</fluorescence_position>
    <stepper axis="c">
      <move_absolute>-10000.00 5000.2</move_absolute>
      <wait_moving_end></wait_moving_end>
    </stepper>
  </microscopeone>
</temika>
```

## Example: capillary imaging script

The full example file is available here: [scriptfile.xml](../assets/templates/scriptfile.xml)

This is a concrete acquisition script for repeated capillary imaging at controlled temperature.

The structure is:

1. Set the temperature and wait for heating.
2. Start recording.
3. Move to a capillary position.
4. Disable autofocus for travel.
5. Move `x`, `y`, `z`, and `a` axes.
6. Wait for motion to end.
7. Re-enable autofocus and wait for lock.
8. Acquire several illumination conditions by switching `<illumination><enable>...</enable></illumination>`.
9. Stop recording.
10. Sleep, then repeat at the next timestamp.

Representative fragment:

```xml
<microscopeone>
  <afocus>
    <enable>OFF</enable>
  </afocus>
  <stepper axis="x">
    <move_absolute>17773.42 100</move_absolute>
  </stepper>
  <stepper axis="y">
    <move_absolute>-14205.12 100</move_absolute>
  </stepper>
  <stepper axis="z">
    <move_absolute>3403.05 10</move_absolute>
  </stepper>
  <stepper axis="a">
    <move_absolute>13063.01 100</move_absolute>
  </stepper>
</microscopeone>
```

The same script then toggles illumination bitmasks and triggers the camera with different exposure times for dark and fluorescent frames.

## When XML is a good fit

- fixed imaging sequences
- repeated time points
- deterministic stage positions
- simple hardware state changes with known order

## Limitations

This approach is intentionally simple, but it is rigid.

- There is no clean way to catch and branch on runtime errors.
- Logic cannot adapt based on incoming image data or sensor state during the run.
- Recovery from partial failures is manual.
- Large scripts become repetitive and hard to validate.
- If a previous command fails or is skipped, later commands may still run.

Use XML when the sequence is fixed. Move to software control when the run needs state tracking, retries, validation, or data-dependent decisions.
