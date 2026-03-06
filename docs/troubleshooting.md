# Troubleshooting

## Stop conditions

Stop operation immediately if any of the following occurs:

- Burning smell, smoke, unusual heat, or exposed conductors
- Safety interlock failure or emergency stop malfunction
- Unexpected stage motion or collision risk

## Quick triage matrix

| Symptom | Likely cause | First checks | Corrective action |
|---|---|---|---|
| No image | Illumination off, camera disconnected, wrong profile | Verify source on, camera link, exposure settings | Restore connection, load known-good profile |
| Blurry image | Defocus, sample tilt, vibration | Refocus, inspect mounting, check stage stability | Re-level sample, reduce vibration, rerun focus routine |
| Stage drift | Thermal drift, backlash, controller tuning | Run repeatability check, inspect backlash and temperature | Warm-up period, retune, service mechanics |
| Software disconnect | USB/network instability, driver crash | Check logs and cable integrity, restart device service | Reconnect with clean startup, replace cable if recurring |

## Diagnostic data to collect

- Timestamp and operator
- Active hardware/software revision
- Last known good run
- Relevant logs and screenshots
- Any recent hardware/software changes

## Incident report template

- Date/time:
- Operator:
- Symptom:
- Reproduction steps:
- What changed recently:
- Logs/screenshots:
- Root cause (if known):
- Resolution:
- Follow-up actions:
