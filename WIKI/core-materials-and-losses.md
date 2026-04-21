# Core Materials And Losses

## Core-Loss Basis

For a periodic excitation, the energy lost per cycle in the core equals core volume times the area of the $B$-$H$ loop, and hysteresis power loss is that cycle loss multiplied by frequency. [source: Erickson & Maksimovic Ch. 10 eq. 10.55-10.56]

The source text states that eddy currents in conductive core materials are induced by time-varying flux and cause $i^2R$ loss inside the core material. It further states that, if core impedance were purely resistive and frequency-independent, eddy-current loss would scale as $f^2$, while practical ferrites often exhibit an even faster increase over their useful range. [source: Erickson & Maksimovic Ch. 10 §10.3.1 discussion around Fig. 10.19]

## Material Comparison

Silicon steel and related laminated ferrous materials exhibit saturation flux densities in the range 1.5 to 2 T and high core loss, which makes them suited to filter inductors and low-frequency transformers rather than high-frequency ferrite applications. [source: Erickson & Maksimovic Ch. 10 §10.3.1]

Powdered iron and molypermalloy powder cores exhibit typical saturation flux densities of 0.6 to 0.8 T, relatively low permeability due to the distributed-gap effect of the insulating binder, and find application in filter inductors for high-frequency switching converters. [source: Erickson & Maksimovic Ch. 10 §10.3.1]

Ferrite cores exhibit saturation flux densities of 0.25 to 0.5 T and much lower eddy-current loss because of their high resistivity. The source text states that MnZn ferrites are widely used from 10 kHz to 1 MHz, while NiZn ferrites can extend to higher frequencies. [source: Erickson & Maksimovic Ch. 10 §10.3.1]

The added Hurley and Wolfle source states that the saturation flux density of a MnZn ferrite can fall from approximately 450 mT at 25 $^\circ$C to about 360 mT at 100 $^\circ$C, and further notes that ferrite Curie temperature can be as low as 200 $^\circ$C. This makes hot-condition flux-density margin a design requirement rather than an optional safety factor. [source: Hurley & Wolfle Ch. 1 §1.3]

## Design Decision

Choosing higher operating flux density reduces required magnetic size, but the source text identifies a direct tradeoff with core loss. For switching-converter inductors, material choice therefore couples the allowable $B_{max}$ to the thermal and efficiency budget rather than to saturation alone. [source: Erickson & Maksimovic Ch. 10 §10.3.1] [source: Erickson & Maksimovic Ch. 11 eq. 11.14-11.16]

## Related Pages

- [Electromagnetic Fundamentals](./electromagnetic-fundamentals.md)
- [Distributed Gap And Fringing](./distributed-gap-and-fringing.md)
- [Buck Output Filter Inductor Design](./buck-output-filter-inductor-design.md)
- [Thermal Design And Core Selection](./thermal-design-and-core-selection.md)
- [Verification And Measurement](./verification-and-measurement.md)
- [Index](./index.md)