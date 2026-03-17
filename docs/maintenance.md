# Maintenance

This section covers routine instrument care and operational maintenance. It is intentionally conservative: if a step could affect alignment or optics, document it and validate the microscope afterward.

## Routine checks

| Task | Frequency | Notes |
|---|---|---|
| Clean external surfaces and stage inserts | As needed | Avoid contaminating samples and motion surfaces |
| Inspect camera, trigger, USB-C, RS485, afocus, and heater connections | Before long unattended runs | Loose connectors cause intermittent failures |
| Verify condenser and focus zero references | After transport, servicing, or collisions | Use the same physical reference each time |
| Confirm fluorescence position and illumination channels | Before fluorescent experiments | Wrong optical path is a common failure mode |
| Copy data off the RAID0 acquisition partition | After every experiment | RAID0 is fast but not fault-tolerant |

## Optical and mechanical care

- Keep the field diaphragm and aperture diaphragm in known positions for standard operating modes.
- Do not adjust condenser centering screws unless you are intentionally re-aligning the optical path.
- Use the supplied locking screw and appropriate tools when centering the condenser.
- Remove plates or inserts before moving the condenser to its lowest reference point.
- Protect the C-mount camera port from dust when the camera is removed.

## Electrical and controller checks

From `microscope.odt`, the main external connections include:

- illumination CH0-CH3
- illumination CH4-CH7
- trigger 0
- USB
- heater
- afocus
- RS485
- enclosure
- 24 V microscope power supply

If any control subsystem behaves intermittently, inspect the full connector chain before changing software.

## After maintenance

After any work that affects optics, motion, or cables:

1. Launch `temika`.
2. Confirm video is live.
3. Confirm `X`, `Y`, `Z`, and condenser motion.
4. Confirm autofocus can be enabled and locked.
5. Confirm at least one brightfield and one epi channel produce expected images.
6. Confirm data saves correctly to the intended output directory.
