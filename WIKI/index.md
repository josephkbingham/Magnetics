# Magnetics Wiki

Start with [Master Design Guide](./master-design-guide.md). It contains one practical inductor workflow and one practical transformer workflow, with strict equations separated from rules of thumb.

## Practical Guides

- [Master Design Guide](./master-design-guide.md): start here for the end-to-end design checklist.
- [Inductor Design Deep Dive](./inductor-design-deep-dive.md): inductor inputs, buck design equations, sensitivity, coupled filter inductors, and the ETD49 worked buck example.
- [Transformer Design Deep Dive](./transformer-design-deep-dive.md): true-transformer design, practical model, area-product sizing, insulation, leakage, and fractional turns.

## Theory And Reference

- [Magnetic Theory](./magnetic-theory.md): Faraday's law, Ampere's law, $B$, $H$, reluctance, stored energy, saturation, and analogies.
- [Core, Gap, And Thermal Design](./core-gap-and-thermal-design.md): material selection, discrete and distributed gaps, fringing, saturation current, area product, and thermal sizing.
- [High-Frequency And Winding Effects](./high-frequency-and-winding-effects.md): skin depth, proximity effect, conductor selection, core loss, and frequency tradeoffs.
- [Equation Reference](./equation-reference.md): compact formula sheet.

## System Context And Validation

- [Converter Topology Inventory](./converter-topologies.md): maps converter families to magnetic roles and input hooks.
- [Verification And Measurement](./verification-and-measurement.md): measurement procedures for inductance under bias, incremental inductance, B-H loops, core loss, and thermal checks.
- [Changelog](./changelog.md): documentation change history.

## How To Navigate

1. Use [Converter Topology Inventory](./converter-topologies.md) to classify the magnetic component.
2. Use [Master Design Guide](./master-design-guide.md) for the short design workflow.
3. Use [Inductor Design Deep Dive](./inductor-design-deep-dive.md) or [Transformer Design Deep Dive](./transformer-design-deep-dive.md) when a step needs more context.
4. Use [Magnetic Theory](./magnetic-theory.md), [Core, Gap, And Thermal Design](./core-gap-and-thermal-design.md), and [High-Frequency And Winding Effects](./high-frequency-and-winding-effects.md) for physics, materials, thermal, and winding details.
5. Use [Equation Reference](./equation-reference.md) as the quick lookup sheet.
6. Use [Verification And Measurement](./verification-and-measurement.md) to plan bench checks after a first-pass design.

## Source Set

The current wiki is built from the raw/source-note set in `Raw/` and `SOURCE_NOTES/`, especially Erickson and Maksimovic, Hurley and Wolfle, TI/Dixon magnetics material, and the magnetic-mechanical analogy reference.
