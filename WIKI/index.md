# Magnetics Wiki

This wiki compiles magnetics design knowledge from the source material currently present in the workspace and is organized to satisfy the repository schema for linked, traceable pages. [source: /magnetics-wiki-schema.md §1] [source: /magnetics-wiki-schema.md §2] [source: /magnetics-wiki-schema.md §4.1]

## Available Source Set

The current raw source set contains one textbook extract covering basic magnetics theory, loss mechanisms, and inductor design. [source: Erickson & Maksimovic Ch. 10 intro] [source: Erickson & Maksimovic Ch. 11 intro]

## Pages

- [Electromagnetic Fundamentals](./electromagnetic-fundamentals.md): Faraday's law, Ampere's law, and the $B$, $H$, and $\Phi$ relationships used throughout the inductor pages. [source: Erickson & Maksimovic Ch. 10 eq. 10.5-10.7]
- [Air Gap And Saturation](./air-gap-and-saturation.md): Gap-dominated inductor relations, reluctance model, and saturation-current dependence on gap. [source: Erickson & Maksimovic Ch. 10 eq. 10.26-10.33]
- [Magnetic-Mechanical Analogy](./magnetic-mechanical-analogy.md): Three-level spring-mass mapping (circuit, magnetic-circuit, material) for inductance, reluctance, permeability, air gaps, and saturation, including the gyrator reconciliation and the gap-paradox resolution. [source: Magnetic-Mechanical Analogy Ref. §1-§13]
- [Distributed Gap And Fringing](./distributed-gap-and-fringing.md): Comparison of distributed-gap powder cores with discrete-gap ferrites, plus fringing corrections and practical side effects. [source: Hurley & Wolfle Ch. 2 §2.3.2, §2.5]
- [Core Materials And Losses](./core-materials-and-losses.md): Hysteresis, eddy current loss, and the material trade space relevant to switching-converter inductors. [source: Erickson & Maksimovic Ch. 10 §10.3.1]
- [Converter Topology Inventory](./converter-topologies.md): DC/DC, AC/DC, and DC/AC topology list that maps converter families to the magnetic components and input fields needed for later design pages. [source: /magnetics-wiki-schema.md §3]
- [Inductor Design Inputs](./inductor-design-inputs.md): Topology-independent checklist of electrical, waveform, thermal, core, winding, and verification inputs needed before designing a converter inductor. [source: TI SLUP132 §5 Design Strategy]
- [Equation Reference](./equation-reference.md): Dedicated formula sheet for electromagnetic fundamentals, gaps, inductor sizing, transformer models, thermal sizing, and high-frequency effects. [source: Erickson & Maksimovic Ch. 10-11] [source: Hurley & Wolfle Ch. 1-5]
- [Buck Output Filter Inductor Design](./buck-output-filter-inductor-design.md): First-pass CCM buck-inductor sizing using the $K_g$ method. [source: Erickson & Maksimovic Ch. 11 §11.1-§11.2]
- [Thermal Design And Core Selection](./thermal-design-and-core-selection.md): Temperature-rise equations, current-density design, and $A_p$-based core selection for practical inductors. [source: Hurley & Wolfle Ch. 3 §3.1-§3.2]
- [Worked Example: Buck Gapped Core](./worked-example-buck-gapped-core.md): Eight-step design sequence from spec to finished inductor, with turn-rounding consequence check, six explicit design tradeoffs, and five mapped bench-validation tests with expected values. [source: Hurley & Wolfle Ch. 3 Example 3.1]
- [Practical Transformer Model](./practical-transformer-model.md): Magnetizing branch, winding resistance, leakage inductance, and referred equivalent-circuit relations. [source: Hurley & Wolfle Ch. 4 §4.2]
- [Transformer Design Methodology](./transformer-design-methodology.md): High-frequency transformer sizing with waveform factor, VA summation, thermal/current-density constraints, and area-product selection. [source: Hurley & Wolfle Ch. 4 §4.3, Ch. 5 §5.1-§5.2]
- [Transformer Insulation](./transformer-insulation.md): Operational insulation, reinforced insulation, creepage, clearance, and practical implementation elements. [source: Hurley & Wolfle Ch. 5 §5.4]
- [High-Frequency Effects](./high-frequency-effects.md): Skin effect, proximity effect, AC winding resistance, hysteresis, eddy-current loss, and Steinmetz modeling. [source: Hurley & Wolfle Ch. 1 §1.4] [source: Hurley & Wolfle Ch. 4 §4.2.2]
- [Coupled Filter Inductors](./coupled-filter-inductors.md): Multi-output buck-derived converter outputs coupled on a common core for ripple steering and improved dynamic cross-regulation. [source: TI SLUP132 R5-1]
- [Fractional-Turn Transformers](./fractional-turn-transformers.md): Fractional-turn secondary techniques, leakage-inductance pitfalls, and flux-balancing methods. [source: TI SLUP132 R6-1]
- [Verification And Measurement](./verification-and-measurement.md): What the current source supports for validation, plus explicitly flagged gaps in measurement coverage. [source: Erickson & Maksimovic Ch. 11 §11.2] [source: /magnetics-wiki-schema.md §3]
- [Changelog](./changelog.md): Traceability record for wiki creation and updates. [source: /magnetics-wiki-schema.md §1.4]

## Navigation

The [Converter Topology Inventory](./converter-topologies.md) is the routing page for topology-specific magnetic design inputs. [Inductor Design Inputs](./inductor-design-inputs.md) defines the common input checklist before a topology-specific inductor design starts. [Equation Reference](./equation-reference.md) is the quick formula lookup page. The buck-inductor design page depends on the definitions in [Electromagnetic Fundamentals](./electromagnetic-fundamentals.md), the gap model in [Air Gap And Saturation](./air-gap-and-saturation.md), the fringing and distributed-gap discussion in [Distributed Gap And Fringing](./distributed-gap-and-fringing.md), and the material tradeoffs in [Core Materials And Losses](./core-materials-and-losses.md). [source: /magnetics-wiki-schema.md §3] [source: TI SLUP132 §5 Design Strategy] [source: Erickson & Maksimovic Ch. 10 eq. 10.5-10.7] [source: Erickson & Maksimovic Ch. 10 eq. 10.31-10.33] [source: Hurley & Wolfle Ch. 2 §2.3.2, §2.5] [source: Erickson & Maksimovic Ch. 10 §10.3.1] [source: Erickson & Maksimovic Ch. 11 §11.1-§11.2]

[Magnetic-Mechanical Analogy](./magnetic-mechanical-analogy.md) sits alongside [Electromagnetic Fundamentals](./electromagnetic-fundamentals.md) and [Air Gap And Saturation](./air-gap-and-saturation.md) as a conceptual companion: it reframes the same reluctance, gap, and saturation relations mechanically (spring-mass) rather than replacing them, and cross-links back into [Equation Reference](./equation-reference.md) and [Inductor Design Inputs](./inductor-design-inputs.md). [source: Magnetic-Mechanical Analogy Ref. §1-§13]

Transformer-related pages are now anchored by [Practical Transformer Model](./practical-transformer-model.md), [Transformer Design Methodology](./transformer-design-methodology.md), [Transformer Insulation](./transformer-insulation.md), and [High-Frequency Effects](./high-frequency-effects.md). [source: Hurley & Wolfle Ch. 4 §4.2-§4.3] [source: Hurley & Wolfle Ch. 5 §5.1-§5.4] [source: Hurley & Wolfle Ch. 1 §1.4]

Two additional SMPS-specific topics extend the transformer and inductor sections using the TI Dixon magnetics handbook source: [Coupled Filter Inductors](./coupled-filter-inductors.md) covers ripple steering and cross-regulation in multiple-output buck-derived converters, and [Fractional-Turn Transformers](./fractional-turn-transformers.md) covers low-turns-count techniques and the flux-balancing requirements they impose. [source: TI SLUP132 R5-1] [source: TI SLUP132 R6-1]
