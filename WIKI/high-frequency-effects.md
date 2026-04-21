# High-Frequency Effects

## Scope

This page collects the high-frequency effects explicitly discussed in the currently ingested sources: skin effect, proximity effect, AC winding resistance, hysteresis, eddy currents, and the Steinmetz form of core loss. [source: Hurley & Wolfle Ch. 1 §1.4.1-§1.4.4] [source: Hurley & Wolfle Ch. 4 §4.2.2]

## Winding Effects

The added source states that skin effect reduces the effective conduction area as frequency rises, with skin depth

$$
\delta = \frac{1}{\sqrt{\pi f \mu \sigma}}
$$

[source: Hurley & Wolfle Ch. 1 eq. 1.21]

For a round conductor, a first AC-resistance approximation is

$$
R_{ac} = R_{dc}\left[1 + \frac{(r_o/\delta)^4}{48 + 0.8(r_o/\delta)^4}\right]
$$

[source: Hurley & Wolfle Ch. 1 eq. 1.22] [source: Hurley & Wolfle Ch. 4 eq. 4.36]

The same source identifies proximity effect as the increase in resistance caused by the magnetic field of nearby conductors and recommends stranded transposed conductors such as litz wire, or foil for low-turn-count windings, as mitigation approaches. [source: Hurley & Wolfle Ch. 1 §1.4.1]

## Core Effects

The source describes hysteresis loss as the unrecoverable energy represented by the area enclosed by the $B$-$H$ loop over one cycle. [source: Hurley & Wolfle Ch. 1 eq. 1.27 and accompanying discussion]

It describes eddy-current loss as induced $I^2R$ loss within conductive core material and explains why lamination thickness reduces the loss strongly relative to a solid core. [source: Hurley & Wolfle Ch. 1 §1.4.3]

The time-average core-loss density is expressed with the Steinmetz equation:

$$
P_{fe} = K_c f^\alpha B_{max}^\beta
$$

[source: Hurley & Wolfle Ch. 1 eq. 1.29]

## Tradeoffs

High-frequency operation reduces magnetic size but pushes both winding and core losses upward. The transformer-design source therefore treats high-frequency optimization as a balance between copper loss and core loss, not as a simple push toward maximum frequency. [source: Hurley & Wolfle Ch. 5 intro] [source: Hurley & Wolfle Ch. 4 §4.3.5]

## Related Pages

- [Core Materials And Losses](./core-materials-and-losses.md)
- [Practical Transformer Model](./practical-transformer-model.md)
- [Transformer Design Methodology](./transformer-design-methodology.md)
- [Verification And Measurement](./verification-and-measurement.md)
- [Index](./index.md)