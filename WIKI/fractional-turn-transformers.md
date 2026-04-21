# Fractional-Turn Transformers

## Scope

This page summarizes the fractional-turn transformer techniques described by Lloyd Dixon for high-frequency switching power supplies. The topic is useful when optimum turns counts become very small and integer-turn implementations force excessive core and winding size. [source: TI SLUP132 R6-1]

## GIC

### Geometry

An E-E ferrite core in which at least one secondary winding is implemented as a fractional turn around one or more outer legs rather than the full center leg. A flux-balancing structure (parallel outer-leg turns, cross-connected foil half-cylinders, or a dedicated flux-balancing winding) is required to suppress leakage inductance. [source: TI SLUP132 R6-1 to R6-6]

### Input

A high-frequency switching power supply operating above approximately 50 kHz where the optimum secondary turns calculated from

$$
N_{optimum} = (V_N \Delta t / A_e \Delta B) \cdot 10^4
$$

fall below one full turn, or where a required turns ratio between multiple outputs cannot be achieved accurately with small integer turns. [source: TI SLUP132 R6-1]

### Constraint

The fractional winding's series leakage inductance $L = F(1-F) \cdot P$ must be suppressed to an acceptable level for the converter's secondary regulation and voltage stress requirements. Flux balancing must hold the outer-leg flux division to within the design ratio across the full load range. [source: TI SLUP132 R6-2 to R6-3]

## Why Fractional Turns Matter

The source gives the optimum-turns expression as

$$
N_{optimum} = (V_N \Delta t / A_e \Delta B) \cdot 10^4
$$

with $A_e$ in cm$^2$ and $\Delta B$ in Tesla. [source: TI SLUP132 R6-1]

It then states two conditions where fractional turns become attractive above roughly 50 kHz:

- the optimum low-voltage secondary requires less than one full turn
- the required ratio between multiple outputs cannot be achieved accurately with small integer turns, which forces all windings to use more turns than optimum

[source: TI SLUP132 R6-1]

The source explicitly claims this integer-turn penalty can multiply transformer size and cost several-fold, which is the main motivation for fractional-turn techniques. [source: TI SLUP132 R6-1]

## Basic Principle

A fractional turn encloses only a fraction of the total center-leg flux. In an E-E core with two equal outer legs, one turn around a single outer leg links half the total flux and therefore behaves as one-half turn. [source: TI SLUP132 R6-1 to R6-2]

For the general multi-leg representation in the source, if a fractional-turn winding encloses a fraction

$$
F = \frac{P_3}{P_2 + P_3} = \frac{A_3}{A_2 + A_3}
$$

of the outer-leg permeance or area, then it links the same fraction of total flux and behaves electrically as $F$ turns. [source: TI SLUP132 R6-2]

The no-load voltage relationship is given as

$$
V_{out}/V_{in} = (N_s + F)/N_p
$$

[source: TI SLUP132 R6-2]

## The Leakage-Inductance Problem

The source states that the raw fractional turn has inherently high leakage inductance, so its induced voltage collapses badly under load unless the flux in the outer legs is forced to remain in the correct ratio. [source: TI SLUP132 R6-2 to R6-3]

The leakage inductance of the fractional turn is given as

$$
L = F(1-F) \cdot P = F(1-F) \cdot \mu A/\ell \cdot 10^{-2}\ \text{H}
$$

[source: TI SLUP132 R6-3]

The source identifies the worst case at one-half turn. [source: TI SLUP132 R6-3]

## Flux-Balancing Solutions

The source presents several ways to force the outer-leg fluxes to remain in the required ratio and thereby suppress the huge leakage inductance.

### Parallel Half-Turns On Equal Outer Legs

Putting one turn around each equal outer leg and connecting them in parallel forces equal induced voltage, which in turn forces equal flux division. This makes the pair behave as a low-leakage half-turn. [source: TI SLUP132 R6-3 to R6-4]

### Cross-Connected Foil Half Cylinders

The source gives an improved implementation using two half cylinders of copper foil placed directly over the primary, cross-connected at one or both ends. This improves coupling to the primary and reduces the series inductance of the half-turn structure. [source: TI SLUP132 R6-4]

### Separate Flux-Balancing Winding

The source also shows a separate flux-balancing winding across the two outer legs. This is especially useful when fractional turns are used on more than one secondary or with center-tapped secondaries. [source: TI SLUP132 R6-5]

### Unequal Flux Division For Other Fractions

By choosing unequal turns in the flux-balancing winding, the source states that fractions other than one-half can be obtained on a standard E-E core, such as one-quarter or three-quarters turn. [source: TI SLUP132 R6-6]

## Design Decision

Fractional turns are compelling when optimum turns are otherwise so low that integer-turn constraints inflate transformer size dramatically. The forcing constraint is leakage inductance: the fractional-turn technique is only practical if flux balancing is implemented well enough to keep the added series inductance acceptably small. [source: TI SLUP132 R6-1 to R6-6]

## Related Pages

- [Transformer Design Methodology](./transformer-design-methodology.md)
- [Practical Transformer Model](./practical-transformer-model.md)
- [High-Frequency Effects](./high-frequency-effects.md)
- [Transformer Insulation](./transformer-insulation.md)
- [Index](./index.md)