# Distributed Gap And Fringing

## Distributed Gap

Powder-iron cores are described in the added source as high-permeability magnetic alloy beads bonded with non-ferromagnetic material. The bonding material acts as a gap distributed through the whole core rather than concentrated in one discrete air gap. The resulting effective relative permeability is typically in the range 15 to 550. [source: Hurley & Wolfle Ch. 2 §2.3.2]

The source identifies several benefits of the distributed-gap approach:

- less flux fringing than a discrete gap
- reduced EMI effects
- reduced winding loss caused by fringing
- greater mechanical stability of the core assembly

[source: Hurley & Wolfle Ch. 2 §2.3.2]

The same section also states that discrete-gap ferrites are often less expensive and are available in a greater variety of shapes and sizes. [source: Hurley & Wolfle Ch. 2 §2.3.2]

## Saturation Behavior Comparison

The added source states that a gapped ferrite exhibits a comparatively sharp reduction in permeability when saturation is reached, with a correspondingly dramatic drop in inductance. A distributed-gap powder core exhibits a less severe roll-off because the intrinsic permeability of the magnetic particles is much higher than that of ferrite. The same source also states that ferrite saturation is more temperature-dependent. [source: Hurley & Wolfle Ch. 2 §2.3.2]

## Fringing Around A Discrete Gap

The no-fringing approximation for a gapped core underestimates inductance because actual flux lines bulge out around the air gap, reducing the effective air-gap reluctance. The source explicitly states that fringing both increases inductance and increases loss in neighbouring conductors. [source: Hurley & Wolfle Ch. 2 §2.5]

For a rectangular gap cross-section $a \times b$ and air-gap length $g$, the source gives the first correction as

$$
L' = L \frac{(a + g)(b + g)}{ab}
$$

[source: Hurley & Wolfle Ch. 2 eq. 2.65]

Under the assumption $g \ll a$ or $b$, this simplifies to

$$
L' \approx L \left(1 + \frac{a + b}{ab} g\right)
$$

[source: Hurley & Wolfle Ch. 2 eq. 2.66]

For a square cross-section, the source reduces the fringing factor to $(1 + 2g/a)$. [source: Hurley & Wolfle Ch. 2 §2.5]

## Design Decision

Discrete-gap ferrite is favored when core shape availability, lower cost, or manufacturer-supplied gapped sets matter more than local fringing. Distributed-gap powder cores are favored when the main constraint is DC-bias tolerance with lower fringing side effects. The forcing constraint is application-specific: current-bias tolerance, EMI sensitivity, and winding-loss sensitivity pull the design toward distributed gap, while catalog availability and ferrite material performance at switching frequency pull it toward discrete-gap ferrite. [source: Hurley & Wolfle Ch. 2 §2.3.2] [source: Hurley & Wolfle Ch. 2 §2.5]

## Industry Split

For DC-carrying energy-storage inductors, the practical rule is that the component is gapped in some form. The split is between a discrete air gap in a high-permeability core and a distributed gap built into the magnetic material. The design fork is therefore not "gapped or ungapped" for an energy-storage inductor; it is "discrete gap or selected $\mu_{eff}$." [source: TI SLUP132 §2 Core Limitations in SMPS Applications] [source: TI SLUP132 §5 Inductor and Flyback Transformer Design] [source: Hurley & Wolfle Ch. 2 §2.3.2]

Discrete-gapped ferrite is common in flyback coupled inductors, larger output chokes, and resonant inductors where low high-frequency core loss, bobbin availability, and standard E/PQ/RM-style core sets are useful. The flyback case is especially important: despite the common name "flyback transformer," the magnetic is an energy-storage coupled inductor, so it requires a gap. [source: TI SLUP132 §5 Flyback Transformer Design] [source: Hurley & Wolfle Ch. 3 §3.2]

Distributed-gap powder and metal-composite materials are common where high DC bias, soft saturation, and low local fringing are more important than the lowest ferrite core loss. This includes many PFC boost inductors, high-DC-bias chokes, powder toroids, and molded low-voltage SMD power inductors. In these parts the material effective permeability is the purchased design grade, so $\mu_{eff}$ is a primary selection parameter. [source: Hurley & Wolfle Ch. 2 §2.3.2] [source: TI SLUP132 §5 Boost Inductor] [source: User note 2026-07-05]

Ungapped high-permeability cores remain common where the magnetic is not intended to store load energy: true power transformers, gate-drive transformers, common-mode EMI chokes, and line-frequency transformers. These parts usually want high magnetizing or common-mode inductance rather than deliberate energy storage in a gap. [source: TI SLUP132 §2 Core Limitations in SMPS Applications] [source: TI SLUP132 §4 Power Transformer Design] [source: /magnetics-wiki-schema.md §3]

The manufacturing trade is not free in either direction. A discrete gap can create a strong local fringing field that raises nearby copper loss and may require a grinding or shimming step. A distributed-gap material spreads that field out, but accepts its own penalties in core loss, permeability grade availability, and material cost. [source: Hurley & Wolfle Ch. 2 §2.3.2] [source: Hurley & Wolfle Ch. 2 §2.5]

## Related Pages

- [Air Gap And Saturation](./air-gap-and-saturation.md)
- [Buck Output Filter Inductor Design](./buck-output-filter-inductor-design.md)
- [Thermal Design And Core Selection](./thermal-design-and-core-selection.md)
- [Index](./index.md)
