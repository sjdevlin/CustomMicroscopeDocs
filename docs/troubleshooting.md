# Troubleshooting

Use this page as the first pass before changing hardware settings or editing scripts.

## Common problems

| Symptom | Likely cause | Checks | Action |
|---|---|---|---|
| No image in fluorescent mode | Wrong fluorescence position or filter path | Check fluorescence position and active LED channel | Set the validated filter position and correct epi channel |
| No live video window on startup | Camera not connected or transmission disabled | Confirm camera connection and open `Camera Control` | Reconnect camera, enable transmission, restart `temika` if needed |
| Stage or focus will not move | Axis disabled in `Movement` tab | Check `Enable` checkbox for the axis | Re-enable axis, then retry GUI or software control |
| Condenser hits sample holder path | Condenser zeroed with plate in place or moved unsafely | Inspect physical clearance before motion | Remove obstruction, re-home carefully, reset zero if needed |
| Autofocus fails to lock | Optical path mismatch, bad sample interface, or autofocus left disabled | Check autofocus enable, offset, and signal graph | Disable autofocus, refocus manually, restore optical path, then retry lock |
| Image too dark | LED channel disabled, low intensity, or short exposure | Check illumination enable, intensity, and camera exposure | Enable correct LED, increase intensity or exposure |
| Script runs but images are missing | Save basename incorrect, recording off, or trigger misconfigured | Check main window save settings, `<record>`, and trigger mode | Fix output path and camera trigger configuration |
| Long run completed but data is gone | Data left on RAID0 workspace only | Check whether data was copied after acquisition | Copy datasets to reliable storage immediately after runs |
| Temperature does not stabilize | Wrong sensor or feedback channel, feedback not enabled | Check `Environment` tab channel mapping and setpoint path | Validate wiring and feedback target before retrying |
| Software control receives no useful reply | Socket dropped, stale buffer, or timeout | Inspect logs from the TCP client | Reconnect, clear stale data, and wait for explicit reply tokens |

## What to capture when reporting a problem

- Screenshot of the relevant Temika window
- Terminal output from the `temika` launch session
- Current save basename and output directory
- Camera name and trigger mode
- Active illumination channel and fluorescence position
- XML or Python command fragment if the run was automated
