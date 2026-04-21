# Coupled Filter Inductors

## Scope

This page covers coupled filter inductors in multiple-output buck-derived regulators such as forward, full-bridge, and half-bridge converters. The current source set now includes a dedicated Lloyd Dixon treatment focused on performance benefits and implementation constraints. [source: TI SLUP132 R5-1]

## GIC

### Geometry

A common-core E-E or similar multi-leg ferrite structure wound with one winding per regulated output. Turns on each winding are set to match the corresponding transformer secondary turns ratio. The core gap, if any, is set to support the required common-mode inductance $L_m$. [source: TI SLUP132 R5-2 to R5-3] [source: TI SLUP132 R5-5 to R5-6]

### Input

A multiple-output buck-derived converter (forward, full-bridge, or half-bridge) operating from a shared primary PWM duty cycle. One output is directly regulated; remaining outputs are cross-regulated through the coupled winding. [source: TI SLUP132 R5-1]

### Constraint

Turns ratio on each coupled winding must match the corresponding transformer secondary turns ratio exactly. The uncoupled (leakage) inductance between windings must be minimized (typically < 10% of mutual inductance, and as low as 2% with interleaving) to avoid spurious resonances and loop instability. [source: TI SLUP132 R5-3] [source: TI SLUP132 R5-6]

## Why Couple The Output Inductors

The source states that independent output inductors in a multiple-output buck family converter decouple the outputs from each other and create several performance problems. Winding the output inductors on a common core largely eliminates these issues. [source: TI SLUP132 R5-1 introduction]

The stated benefits are:

- much better dynamic cross-regulation
- reduced large-signal over/undershoot during load changes
- reduced severity of minimum-load problems
- simplified current limiting because primary-side current limit can prevent inductor saturation regardless of which output is overloaded
- elimination of loop-gain irregularities caused by multiple uncoupled output filters
- lower cost and volume than separate inductors

[source: TI SLUP132 R5-3]

The same source also states that ripple-current steering can dramatically reduce required filter capacitance and can reduce or eliminate dummy-load requirements on some outputs. [source: TI SLUP132 R5-1 introduction] [source: TI SLUP132 R5-3 to R5-4]

## Constraint: Matching Turns Ratio

The source gives a critical implementation rule: the coupled inductor windings must have exactly the same turns ratio as the corresponding transformer secondary windings. Otherwise, the voltage waveforms across the coupled windings conflict and large circulating ripple current flows between outputs. [source: TI SLUP132 R5-2 to R5-3]

The source states this as a hard requirement for proper operation in the coupled-inductor approach. [source: TI SLUP132 R5-3]

## Ripple Steering Model

After normalization to a common voltage level, the source combines the mutual part of the coupled inductor into a common inductance $L_m$ and represents the non-common part as small uncoupled inductances $L_{\ell 1}$ and $L_{\ell 2}'$. The total ripple current is then set mainly by $L_m$, while the distribution of ripple current among outputs is controlled by the uncoupled inductances. [source: TI SLUP132 R5-5 to R5-6]

This means ripple current can be steered intentionally toward the output where ripple filtering is cheapest or least harmful. The source specifically recommends steering most ripple to the highest-voltage output, because capacitor size and ESR requirements scale much more favorably there. [source: TI SLUP132 R5-4 to R5-6]

## Design Decision

The source recommends keeping uncoupled inductance as small as practical, because large uncoupled inductance values create spurious resonances and degrade loop behavior. In a ferrite E-E coupled inductor, leakage is typically less than 10% of mutual inductance and may be as low as 2% with interleaving. [source: TI SLUP132 R5-3] [source: TI SLUP132 R5-6]

To steer most ripple current to the high-voltage winding, the source recommends placing the high-voltage winding closest to the center leg and the low-voltage winding on top of it. [source: TI SLUP132 R5-6]

## Limits And Penalties

The source lists several constraints and penalties:

- rectifier mismatch within one output increases ripple if coupling is very tight; a non-zero uncoupled inductance $L_\ell$ limits the resulting mismatch-driven circulating current, so eliminating all leakage is not the design target
- timing of all corresponding winding waveforms must be identical, which rules out independent secondary-side PWM techniques such as magnetic-amplifier style post regulation
- downstream LC sections can create resonant problems and must be adequately damped for stable closed-loop behavior

[source: TI SLUP132 R5-3] [source: TI SLUP132 R5-8 to R5-9]

## Related Pages

- [Buck Output Filter Inductor Design](./buck-output-filter-inductor-design.md)
- [Distributed Gap And Fringing](./distributed-gap-and-fringing.md)
- [Practical Transformer Model](./practical-transformer-model.md)
- [High-Frequency Effects](./high-frequency-effects.md)
- [Index](./index.md)