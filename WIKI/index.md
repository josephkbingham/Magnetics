# Magnetics Wiki

This wiki compiles magnetics design knowledge from the source material currently present in the workspace and is organized to satisfy the repository schema for linked, traceable pages. [source: /magnetics-wiki-schema.md §1] [source: /magnetics-wiki-schema.md §2] [source: /magnetics-wiki-schema.md §4.1]

## Available Source Set

The current raw source set contains one textbook extract covering basic magnetics theory, loss mechanisms, and inductor design. [source: Erickson & Maksimovic Ch. 10 intro] [source: Erickson & Maksimovic Ch. 11 intro]

## Pages

- [Electromagnetic Fundamentals](./electromagnetic-fundamentals.md): Faraday's law, Ampere's law, and the $B$, $H$, and $\Phi$ relationships used throughout the inductor pages. [source: Erickson & Maksimovic Ch. 10 eq. 10.5-10.7]
- [Air Gap And Saturation](./air-gap-and-saturation.md): Gap-dominated inductor relations, reluctance model, and saturation-current dependence on gap. [source: Erickson & Maksimovic Ch. 10 eq. 10.26-10.33]
- [Distributed Gap And Fringing](./distributed-gap-and-fringing.md): Comparison of distributed-gap powder cores with discrete-gap ferrites, plus fringing corrections and practical side effects. [source: Hurley & Wolfle Ch. 2 §2.3.2, §2.5]
- [Core Materials And Losses](./core-materials-and-losses.md): Hysteresis, eddy current loss, and the material trade space relevant to switching-converter inductors. [source: Erickson & Maksimovic Ch. 10 §10.3.1]
- [Buck Output Filter Inductor Design](./buck-output-filter-inductor-design.md): First-pass CCM buck-inductor sizing using the $K_g$ method. [source: Erickson & Maksimovic Ch. 11 §11.1-§11.2]
- [Thermal Design And Core Selection](./thermal-design-and-core-selection.md): Temperature-rise equations, current-density design, and $A_p$-based core selection for practical inductors. [source: Hurley & Wolfle Ch. 3 §3.1-§3.2]
- [Worked Example: Buck Gapped Core](./worked-example-buck-gapped-core.md): Fully worked buck-inductor example including ripple, core selection, gap, turns, copper loss, and core loss. [source: Hurley & Wolfle Ch. 3 Example 3.1]
- [Verification And Measurement](./verification-and-measurement.md): What the current source supports for validation, plus explicitly flagged gaps in measurement coverage. [source: Erickson & Maksimovic Ch. 11 §11.2] [source: /magnetics-wiki-schema.md §3]
- [Changelog](./changelog.md): Traceability record for wiki creation and updates. [source: /magnetics-wiki-schema.md §1.4]

## Navigation

The buck-inductor design page depends on the definitions in [Electromagnetic Fundamentals](./electromagnetic-fundamentals.md), the gap model in [Air Gap And Saturation](./air-gap-and-saturation.md), the fringing and distributed-gap discussion in [Distributed Gap And Fringing](./distributed-gap-and-fringing.md), and the material tradeoffs in [Core Materials And Losses](./core-materials-and-losses.md). [source: Erickson & Maksimovic Ch. 10 eq. 10.5-10.7] [source: Erickson & Maksimovic Ch. 10 eq. 10.31-10.33] [source: Hurley & Wolfle Ch. 2 §2.3.2, §2.5] [source: Erickson & Maksimovic Ch. 10 §10.3.1] [source: Erickson & Maksimovic Ch. 11 §11.1-§11.2]