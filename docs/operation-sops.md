# Operating Procedures

## Scope

Standard operating procedure for routine imaging runs.

## Preconditions

- Operator is trained for this system revision.
- Safety checks in [Safety](safety.md) are complete.
- Calibration is current per [Calibration & Validation](calibration-validation.md).

## Pre-run checklist

- [ ] Optics and sample area are clean.
- [ ] Stage and cables are unobstructed through full travel.
- [ ] Interlocks and emergency stop are verified.
- [ ] Correct objective/filter/profile selected.
- [ ] Storage location and metadata template confirmed.

## Standard imaging workflow

1. Start system using approved power and software sequence.
2. Load sample and set reference position.
3. Acquire test frame and verify focus, exposure, and contrast.
4. Run small pilot capture and review quality metrics.
5. Acquire full dataset.
6. Save raw data, metadata, and run log.

## In-run quality gates

| Checkpoint | Criteria | Action if Failed |
|---|---|---|
| Focus stability |  |  |
| Illumination consistency |  |  |
| Stage repeatability |  |  |
| Metadata completeness |  |  |

## Shutdown

1. Park stage.
2. Turn off illumination.
3. Close acquisition software cleanly.
4. Save logs and transfer data.
5. Follow power-down sequence.

## Run record

- Date/time:
- Operator:
- Sample ID:
- Imaging profile:
- Notable issues:
- Data location:
