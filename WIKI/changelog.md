# Changelog

## 2026-07-03 (magnetic-mechanical analogy)

- Ingested `Raw/Magnetic_Mechanical_Analogy_Reference.docx` (extracted to `Raw/Magnetic_Mechanical_Analogy_Reference.md`) and added `SOURCE_NOTES/magnetic-mechanical-analogy-reference.md` mapping its coverage. [source: /magnetics-wiki-schema.md §1]
- Added `magnetic-mechanical-analogy.md` as a new wiki page presenting the three-level spring-mass analogy (circuit terminals as mass, magnetic circuit as spring via Hopkinson's law, material permeability as compliance), the coil-as-gyrator reconciliation, the resolved gap paradox, the four working equations for $B$, and the gap-lowers-$B$ effective-magnetic-length derivation, each with a GIC framing and a dedicated Tradeoffs section. [source: Magnetic-Mechanical Analogy Ref. §1-§13]
- Cross-linked the new page from `electromagnetic-fundamentals.md`, `air-gap-and-saturation.md`, and `equation-reference.md`, and added the gap-dominated effective-magnetic-length form of $B$ to `equation-reference.md`. [source: /magnetics-wiki-schema.md §2]
- Updated `index.md`, `README.md`, and `SOURCE_NOTES/README.md` to surface the new source and page. [source: /magnetics-wiki-schema.md §2]

## 2026-07-03

- Added `converter-topologies.md` as a topology inventory for DC/DC, AC/DC, and DC/AC converters, mapping each family to the magnetic components and initial design-input fields needed for future topology-specific pages. [source: /magnetics-wiki-schema.md §3] [source: TI SLUP132 §2 Core Limitations in SMPS Applications] [source: TI SLUP132 §4 Power Transformer Design] [source: TI SLUP132 §5 Inductor and Flyback Transformer Design]
- Updated `README.md` and `index.md` navigation so the new topology inventory is visible from the repository landing page and wiki index. [source: /magnetics-wiki-schema.md §2]
- Added `inductor-design-inputs.md` as a reusable checklist for converter-derived inductor designs, covering required waveform, current, thermal, core, winding, and verification inputs before core/gap/turns calculations begin. [source: TI SLUP132 §5 Design Strategy] [source: Hurley & Wolfle Ch. 3 §3.2]
- Added `equation-reference.md` as a dedicated formula sheet covering electromagnetic fundamentals, gap and saturation equations, inductor first-pass sizing, thermal/core selection, transformer models, transformer sizing, and high-frequency effects. [source: Erickson & Maksimovic Ch. 10-11] [source: Hurley & Wolfle Ch. 1-5]

## 2026-04-20

- Created the initial linked wiki structure under `WIKI` from the repository schema and the available Erickson and Maksimovic raw source. [source: /magnetics-wiki-schema.md §1] [source: Erickson & Maksimovic Ch. 10 intro] [source: Erickson & Maksimovic Ch. 11 intro]
- Added source-backed pages for electromagnetic fundamentals, air-gap behavior, core materials and losses, and CCM buck output filter inductor design. [source: Erickson & Maksimovic Ch. 10 eq. 10.5-10.7] [source: Erickson & Maksimovic Ch. 10 eq. 10.26-10.33] [source: Erickson & Maksimovic Ch. 10 §10.3.1] [source: Erickson & Maksimovic Ch. 11 §11.1-§11.2]
- Added a verification page that separates source-backed validation statements from schema-required but currently unverified measurement topics. [source: Erickson & Maksimovic Ch. 11 §11.2] [source: /magnetics-wiki-schema.md §3]
- Ingested the Hurley and Wolfle raw source and expanded the wiki with pages on distributed-gap cores, fringing, thermal/core-selection methodology, and a worked buck-converter inductor example. [source: Hurley & Wolfle Ch. 2 §2.3.2, §2.5] [source: Hurley & Wolfle Ch. 3 §3.1-§3.2] [source: Hurley & Wolfle Ch. 3 Example 3.1]
- Replaced several `[UNVERIFIED]` measurement placeholders with source-backed procedures for step-voltage inductance measurement, incremental impedance, $B$-$H$ loop measurement, and high-frequency core-loss testing. [source: Hurley & Wolfle Ch. 8 §8.1-§8.3.3]
- Added repository landing-page and ingestion scaffolding via `README.md` and `SOURCE_NOTES/` so new raw sources can be mapped before wiki integration. [source: /magnetics-wiki-schema.md §1]
- Expanded the wiki into transformer-specific coverage: practical transformer model, transformer design methodology, transformer insulation, and high-frequency effects. [source: Hurley & Wolfle Ch. 1 §1.4] [source: Hurley & Wolfle Ch. 4 §4.2-§4.3] [source: Hurley & Wolfle Ch. 5 §5.1-§5.4]
- Reviewed the newly added TI Dixon magnetics handbook source and extracted two distinct SMPS-specific topics not yet covered elsewhere in the wiki: coupled filter inductors and fractional-turn transformers. [source: TI SLUP132 R5-1] [source: TI SLUP132 R6-1]

## 2026-04-20 (worked example expansion)

- Rewrote `worked-example-buck-gapped-core.md` into an eight-step numbered design sequence with all formulas shown inline at each step; added Step 6 to check the inductance shortfall from turn rounding (31.8 µH vs 34 µH target, 6.5 % under). [source: Hurley & Wolfle Ch. 3 Example 3.1]
- Added a Tradeoffs section with six explicit discussions: core size choice, B_max derating vs. saturation margin, standard gap vs. computed optimum, turn-rounding direction, foil vs. Litz at 80 kHz (with AC resistance and AC loss calculation), and the conditions under which the core-loss-negligible assumption breaks. [source: Hurley & Wolfle Ch. 3 Example 3.1] [source: Hurley & Wolfle Ch. 1 §1.4.1]
- Added a Validation: Bench Measurements section with five tests (DC resistance cold/hot, step-voltage inductance vs. bias, incremental AC inductance, temperature rise, core loss spot check), each with expected values and deviation interpretation. [source: Hurley & Wolfle Ch. 8 §8.1-§8.3.3]
- Updated index.md description of the worked-example page to reflect expanded coverage.

## 2026-04-20 (schema compliance review)

- Added GIC sections to `coupled-filter-inductors.md` and `fractional-turn-transformers.md` to satisfy §4.2: both pages apply equations without previously declaring Geometry, Input, and Constraint context. [source: /magnetics-wiki-schema.md §4.2]
- Renamed `## Design Implication` to `## Tradeoffs` in `high-frequency-effects.md` to satisfy §4.4: comparative/evaluative language must appear only in sections titled `## Tradeoffs` or `## Design Decision`. [source: /magnetics-wiki-schema.md §4.4]
- Rephrased vague "can be beneficial here" in `coupled-filter-inductors.md` Limits section to a clinical statement about $L_\ell$ limiting mismatch-driven circulating current. [source: /magnetics-wiki-schema.md §4.4]
- Extended the `index.md` navigation section to explicitly include the two TI-sourced pages. [source: /magnetics-wiki-schema.md §2]

## 2026-04-20 ($B$ vs. $H$ clarification)

- Expanded `electromagnetic-fundamentals.md` with an explicit cause-and-effect explanation of magnetic field intensity $H$, flux density $B$, flux $\Phi$, and induced voltage so the page now states what is directly imposed by current drive versus what is the material response. [source: Erickson & Maksimovic Ch. 10 eq. 10.3-10.10]
- Added a short comparison between the general Biot-Savart field-construction method and the symmetry-based use of Ampere's law; Biot-Savart content is explicitly marked `[UNVERIFIED]` because it is not yet backed by an ingested source in this repo. [source: /magnetics-wiki-schema.md §4.1] [source: Erickson & Maksimovic Ch. 10 eq. 10.7-10.8] [source: TI SLUP132 eq. 1]

## Related Pages

- [Index](./index.md)
- [Verification And Measurement](./verification-and-measurement.md)
