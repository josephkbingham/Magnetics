# Magnetics Knowledge Base Schema and Rules

This document defines the schema and rules for maintaining the Magnetics (Transformers and Inductors) Deep Dive Wiki. It governs how source material — textbooks, application notes, core manufacturer datasheets, and design calculations — is ingested, organized, and verified into a compiled knowledge base covering both transformer design (PSFB, flyback, push-pull, line-frequency) and inductor/choke design (PFC boost, output filter, EMI common-mode, DC choke).

## 1. Ingestion Workflow
When new source material (textbook chapters, application notes, core datasheets, measurement data) is provided in the `/RAW` directory, the following workflow must be followed:
1. **Read source**: Thoroughly analyze the provided raw files. Identify the specific magnetics domain covered (core materials, winding design, loss mechanisms, topology-specific guidance, etc.).
2. **Extract design-relevant content**: Synthesize the key design equations, material properties, empirical rules, and tradeoff insights. Ignore marketing content and redundant introductory material. Focus on *what governs the design* and *why*.
3. **Update/Create Wiki pages**: Integrate this knowledge into the compiled Markdown wiki in the `/WIKI` directory. Keep derived results (worked examples, equation forms, material comparisons) current; do not re-derive them on every query. Note any contradictions or enhancements compared to existing wiki knowledge.
4. **Log the change**: Record updates in a changelog or commit history to maintain traceability, including which source document motivated the change.

## 2. Linking Policy
* **No Orphans**: Every page in the `/WIKI` directory must link to at least one other page.
* **Concept Linking**: Always link core concepts (e.g., Core Loss, Skin Effect, Leakage Inductance, Ap Product, Saturation Flux Density) to their respective definition or derivation pages to build a strong knowledge graph.
* **Cross-Domain Linking**: Transformer and inductor pages must link to shared foundational pages (e.g., Faraday's Law, Ampere's Law, Core Material Comparison) rather than duplicating derivations.

## 3. Entity Mapping
Magnetics content is mapped into the following structural entities:
* **Core Materials and Geometry**: Ferrite (MnZn, NiZn), powdered iron, amorphous, nanocrystalline, silicon steel; core shapes (E, ETD, PQ, RM, toroid, pot); gap strategies (center-leg, distributed, stepped); Ap product, Kg product, window area, effective parameters (Ae, le, Ve).
* **Electromagnetic Fundamentals**: Faraday's Law, Ampere's Law, Lenz's Law, permeability (μr, μe, μΔ), flux density (B, Bsat, Bpk, ΔB), magnetic field intensity (H), BH loop behavior, initial vs. incremental vs. amplitude permeability.
* **Winding Design**: Turns calculations (Vsec/NAe formula), wire selection (AWG, Litz, foil), current density (J, A/mm²), fill factor (Ku), skin depth (δ), proximity effect, interleaving strategies, creepage/clearance, insulation systems.
* **Loss Mechanisms**: Core losses (hysteresis, eddy, residual) via Steinmetz equation, iGSE, or manufacturer loss charts; copper losses (DC I²R, AC Rac/Rdc ratio, Dowell's equation); gap fringing losses; total loss and thermal rise.
* **Topology-Specific Design**: PSFB transformer (duty cycle limits, ZVS requirements, leakage L for ZVS energy), flyback (primary-referenced flux, gapped core, RCD snubber sizing), push-pull and half/full-bridge (flux walking, volt-second balance), PFC boost inductor (ripple current, saturation margin), output filter (LC corner, DCR), EMI CM choke (impedance vs. frequency, common-mode saturation).
* **Thermal and Mechanical**: Temperature rise models (empirical Rth, surface area methods), ambient derating, hotspot vs. surface, varnish/potting, mounting and vibration (naval/MIL applications).
* **Measurement and Verification**: Inductance at operating current (saturation curve), AC resistance vs. frequency, impedance analyzer sweeps, core loss measurement (two-winding method), thermal imaging, B-H loop capture.

## 4. Verification Protocol
All wiki content must satisfy the following constraints:

### 4.1 Source Traceability
Every factual claim, equation, and material property value must include a citation to a specific source. Format:
* Textbook: `[source: McLyman Ch. 7 p.7-12 eq 7.21]`
* App note: `[source: TI SLUA144A §3.2]`
* Datasheet: `[source: Ferroxcube 3C95 datasheet p.4 fig.2]`
* Calculation/derivation: `[source: /WIKI/derivations/ap-product.md]`

Claims without citations are considered unverified and must be flagged with `[UNVERIFIED]`. Empirical rules of thumb (e.g., "ΔB ≈ 0.1 T for ferrite at 100 kHz to keep core loss < 500 mW/cm³") must cite the source that establishes the rule, not just assert it.

### 4.2 GIC (Geometry-Input-Constraint) Modeling
All magnetic components and design procedures must be described using the GIC framework:
* **Geometry**: The chosen core and winding structure (e.g., ETD-49 core with Ae = 211 mm², le = 114 mm, 3C95 material; primary 22 turns of 2× 0.4 mm Litz, secondary 5 turns of 0.1 mm × 12 mm foil).
* **Input**: The electrical operating conditions and environmental constraints (e.g., Vin = 400 V nominal, fsw = 100 kHz, Ipk = 18 A, Ta = 55 °C, 2× overcurrent for 50 ms).
* **Constraint**: The design limits that must be satisfied (e.g., Bpk ≤ 0.25 T to stay below saturation knee, ΔT ≤ 40 °C, window fill Ku ≤ 0.4, creepage ≥ 8 mm for reinforced insulation per IEC 62368-1).

Every wiki description of a worked design, equation application, or material selection must explicitly identify its Geometry, Input, and Constraint. Design tradeoff discussions (§4.4) are permitted and encouraged — but must still reference the GIC entries they trade against.

### 4.3 Conflict Resolution: Source Hierarchy
When sources contradict, resolve in this priority order:
1. **Measured data from the specific core/sample at hand** — authoritative when available.
2. **Core manufacturer datasheet for the specific part number and temperature** — authoritative for material properties (Bsat, μi, Pv curves).
3. **Peer-reviewed textbooks** (McLyman, Erickson & Maksimović, Kazimierczuk) — authoritative for derivations and general methodology.
4. **Application notes from silicon/controller vendors** (TI, ADI, Infineon, ON Semi) — authoritative for topology-specific guidance but may oversimplify.
5. **Generic rules of thumb from web sources or forums** — lowest priority; only cite if nothing better exists.

When a conflict arises, the wiki must:
1. State the higher-priority source's claim as the primary assertion.
2. Note the contradiction in a `> **Conflict Note:**` blockquote, citing both sources and explaining the likely cause (e.g., different test frequency, different core geometry assumed, approximation in the app note).
3. Never silently adopt the lower-priority source.

### 4.4 Language Standard
All wiki prose must be clinical and precise, with a carve-out for explicit design tradeoff discussion:

**General rules (apply to factual claims):**
* No hedging language ("might", "possibly", "seems to") when stating an equation, material property, or measurement result.
* No marketing phrasing ("excellent", "superior", "optimal") without quantified comparison.
* Use quantified thresholds, equation symbols, and material grade names instead of vague descriptors.
* Example — write: `Pv(3C95, 100 kHz, 100 mT, 100 °C) = 280 mW/cm³ [source: Ferroxcube 3C95 datasheet p.6]` not "3C95 has low core loss."

**Design tradeoff carve-out:**
Design decisions inherently involve tradeoffs (core size vs. loss, fill factor vs. leakage, gap vs. fringing). Sections explicitly titled `## Tradeoffs` or `## Design Decision` may use comparative and evaluative language, provided they:
* Identify the specific variables being traded (e.g., "increasing turns reduces Bpk but increases Rdc and leakage L").
* Quantify the tradeoff with numbers or a sensitivity direction (∂y/∂x sign at minimum).
* Name the constraint that ultimately forces the decision (from §4.2 Constraint list).

Tradeoff discussion outside a designated tradeoff section is not permitted — factual sections must remain clinical.
