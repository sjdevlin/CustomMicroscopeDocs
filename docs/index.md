# Temika Microscope Documentation

This site documents the Temika microscope as an instrument and as a control platform.

## Start here

1. Read [Overview](overview.md) for microscope capabilities, channel layout, inserts, autofocus, and hardware photos.
2. Use [Basic Operation](operating-via-user-interface/basic-operation.md) to launch `temika`, move the microscope, control illumination, and acquire images.
3. Use [Advanced Controls](operating-via-user-interface/advanced-controls.md) for autofocus, temperature control, filter position, and deeper GUI features.
4. Use [Programmatic Control](programmatic-control/xml-script.md) when building scripted runs or long unattended acquisitions.
5. Check [Troubleshooting](troubleshooting.md) before modifying hardware or scripts.

## Source material used for this version

- `microscope.odt`
- `temika_manual.odt`
- `temika.xml`
- `scriptfile.xml`
- `temika_jurij.py`
- `temika_comms.py`
- `stage_controller.py`
- `illumination_controller.py`
- `focus_controller.py`
- `camera_controller.py`

## Code-as-docs principle

The documentation lives in Git alongside example XML scripts, Python control code, and extracted screenshots. Changes to operation or automation should be documented in the same revision that changes the underlying files.
