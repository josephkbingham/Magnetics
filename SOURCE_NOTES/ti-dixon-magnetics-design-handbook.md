# TI Dixon Magnetics Design Handbook

## Source

- File: `Raw/Magnetic-Design-Handboob_2D00_slup132.md`
- Bibliographic identity: Lloyd H. Dixon, Jr., *Magnetics Design Handbook*, Texas Instruments / Unitrode, SLUP132, reproduced from the 2001 Unitrode Magnetics Design Handbook.

## Distinctive Contributions

- physical-to-electrical equivalent-circuit derivation using reluctance models and magnetic-electrical duality
- SMPS-specific winding-layout guidance focused on leakage inductance, eddy-current loss, and capacitance tradeoffs
- coupled filter inductors for multi-output buck-derived converters
- transformer fractional-turn techniques and flux-balancing windings
- practical transformer-design heuristics for loss balance, window use, topology effects, and isolation penalties

## Wiki Pages Fed By This Source

- `WIKI/coupled-filter-inductors.md`
- `WIKI/fractional-turn-transformers.md`

## Candidate Follow-On Updates

- enhance `WIKI/practical-transformer-model.md` with physical-to-equivalent-circuit derivation notes
- enhance `WIKI/high-frequency-effects.md` with winding-placement tradeoffs and rectangular-drive caveats
- add a dedicated page on winding layout and hierarchy for SMPS transformers

## Notes

- This source is strong on practical SMPS magnetics behavior and winding-layout heuristics, weaker on formal thermal modeling than Hurley/Wolfle.
- Treat it as a lower-priority source than direct manufacturer datasheets or measured data when specific numeric properties conflict.
