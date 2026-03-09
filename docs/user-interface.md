# User Interface

## Goal

Document how operators use the `temika` graphical interface for daily operation.

## Primary interface

- Application: `temika`
- Launch method: run `temika` from terminal
- UI type: X-Windows graphical interface
- Primary users: trained microscope operators

## Operator workflow map

Use this as the baseline flow and refine with screenshots.

1. Launch `temika` and connect hardware.
2. Home/reference axes.
3. Load or choose imaging profile.
4. Use live view for focus and exposure tuning.
5. Define acquisition region/sequence.
6. Start capture.
7. Verify output and metadata.
8. Shutdown and log run summary.

## UI screen catalog (build from screenshots)

Add one row per screenshot you share.

| Screenshot File | Window/Panel Name | Inferred Function | Controls Seen | Open Questions |
|---|---|---|---|---|
| `temika-main-window.png` | Main | Top-level control and status |  |  |
| `temika-live-view.png` | Live View | Camera preview and exposure tuning |  |  |
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
