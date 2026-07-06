# Magnetics Wiki

This repository organizes notes on power-electronics magnetics, inductor design, transformer design, core materials, winding effects, and validation. The user-facing documentation now starts with a practical one-page design guide and keeps deeper theory in consolidated reference pages.

Start here:

- [Master Design Guide](WIKI/master-design-guide.md): one practical checklist for inductors and one for transformers.
- [Wiki Index](WIKI/index.md): short map of all consolidated pages.
- [Equation Reference](WIKI/equation-reference.md): formula lookup.

## Repository Structure

```text
Raw/           Source extracts and PDFs kept for provenance.
SOURCE_NOTES/  Per-source ingestion notes and coverage notes.
WIKI/          Consolidated design guide, deep dives, equations, and validation notes.
```

## WIKI Structure

| Page | Purpose |
| --- | --- |
| [master-design-guide.md](WIKI/master-design-guide.md) | Beginner-oriented design recipe for one inductor flow and one transformer flow. |
| [inductor-design-deep-dive.md](WIKI/inductor-design-deep-dive.md) | Consolidated inductor inputs, equations, sensitivity logic, coupled inductor notes, and worked buck example. |
| [transformer-design-deep-dive.md](WIKI/transformer-design-deep-dive.md) | Consolidated transformer model, area-product method, insulation notes, and fractional-turn notes. |
| [magnetic-theory.md](WIKI/magnetic-theory.md) | B/H/Phi fundamentals, reluctance, energy storage, saturation, and magnetic analogies. |
| [core-gap-and-thermal-design.md](WIKI/core-gap-and-thermal-design.md) | Core materials, gap strategy, fringing, area product, and thermal sizing. |
| [high-frequency-and-winding-effects.md](WIKI/high-frequency-and-winding-effects.md) | Skin effect, proximity effect, core loss, conductor choices, and frequency tradeoffs. |
| [converter-topologies.md](WIKI/converter-topologies.md) | Topology-to-magnetic-role routing table. |
| [verification-and-measurement.md](WIKI/verification-and-measurement.md) | Source-backed measurement methods and validation checks. |
| [equation-reference.md](WIKI/equation-reference.md) | Compact equation sheet. |

## Current Coverage

The consolidated wiki currently covers:

- Electromagnetic fundamentals: Faraday's law, Ampere's law, reluctance, flux density, and saturation.
- Power-inductor workflow: input definition, ripple, peak current, core selection, gap/effective permeability, winding design, losses, temperature rise, and validation.
- Transformer workflow: true-transformer classification, volt-second turns, area product, practical equivalent circuit, insulation, leakage, and fractional turns.
- Core and gap selection: ferrite, powder/composite, distributed gap, discrete gap, fringing, and thermal tradeoffs.
- High-frequency effects: skin depth, proximity effect, AC resistance, Steinmetz-style core loss, and conductor selection.
- Bench verification: inductance under bias, incremental inductance, B-H loop measurement, transformer core-loss testing, and thermal checks.

Some topology-specific areas remain placeholders until source-backed notes are added, including LLC-specific magnetics, inverter output filters, interleaved PFC magnetics, and detailed safety-standard tables.

## Content Rules

- Keep the [Master Design Guide](WIKI/master-design-guide.md) practical and short; move derivations and caveats into the deep dives.
- Mark strict equations separately from rules of thumb when adding beginner-facing guidance.
- Preserve source traceability with `[source: ...]` notes where source material is used.
- Keep raw extracts in `Raw/` and source coverage notes in `SOURCE_NOTES/`.
- Record major documentation reorganizations in [WIKI/changelog.md](WIKI/changelog.md).
