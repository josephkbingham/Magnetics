# Transformer Design Methodology

## Scope

This page summarizes the design framework in Hurley and Wolfle for high-frequency transformers in power electronics. The source treats transformer design as a coupled electrical, magnetic, and thermal optimization problem rather than a turns-ratio-only exercise. [source: Hurley & Wolfle Ch. 5 intro]

## GIC

### Geometry

The design uses effective magnetic area $A_m$ or $A_c$, window area $W_a$, mean length per turn $MLT$, core volume, and area product $A_p = A_c W_a$. [source: Hurley & Wolfle Ch. 4 §4.3.1 and Ch. 5 §5.2]

### Input

The source lists the main specifications as input/output voltage and current or power, operating frequency, maximum core temperature or temperature rise, and ambient temperature. Circuit parameters include waveform factor and power factor. [source: Hurley & Wolfle Ch. 5 §5.2]

### Constraint

The design is constrained by temperature rise, maximum operating flux density, winding current density, and total VA handled by all windings. [source: Hurley & Wolfle Ch. 4 eq. 4.73, 4.79-4.85] [source: Hurley & Wolfle Ch. 5 eq. 5.2-5.15]

## Voltage Equation

For general periodic excitation, the source gives

$$
V_{rms} = K_v f N B_{max} A_m
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.62]

with waveform factor $K_v$ defined from waveform form factor and the flux-rise interval. The source gives $K_v = 4.0$ for square-wave excitation and $K_v = 1/\sqrt{D(1-D)}$ for the forward-converter primary waveform. [source: Hurley & Wolfle Ch. 4 Example 4.1-4.2]

## Power Equation And Area Product

Summing the VA ratings of all windings yields

$$
\sum VA = K_v f B_{max} J_o k_f k_u A_p
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.73]

This relation makes $A_p$ the main core-sizing metric for transformer design in the same way it is used for inductors. [source: Hurley & Wolfle Ch. 4 §4.3.2]

## Loss And Optimization Model

The winding loss is

$$
P_{cu} = \rho_w V_w k_u J_o^2
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.76]

The core loss per unit volume follows the Steinmetz form

$$
P_{fe} = K_c f^\alpha B_{max}^\beta
$$

[source: Hurley & Wolfle Ch. 4 §4.3.4]

The total loss is modeled as

$$
P = \frac{a}{f^2 B_{max}^2} + b f^\alpha B_{max}^\beta
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.79]

For a fixed frequency, the source shows that minimum loss occurs when

$$
P_{cu} = \frac{\beta}{2} P_{fe}
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.83]

## Transformer-Specific Design Equations

For the fixed-frequency optimized case, the source gives current density as

$$
J_o = K_t \sqrt{\frac{\Delta T}{2k_u}} \frac{1}{\sqrt[8]{A_p}}
$$

[source: Hurley & Wolfle Ch. 5 eq. 5.4]

When optimum flux density is not limited by saturation, the area-product equation is

$$
A_p = \left[ \frac{\sqrt{2}\sum VA}{K_v f B_o k_f K_t \sqrt{k_u \Delta T}} \right]^{8/7}
$$

[source: Hurley & Wolfle Ch. 5 eq. 5.5]

The corresponding optimum flux density is

$$
B_o = \frac{[h_c k_a \Delta T]^{2/3}}{2^{2/3}[\rho_w k_w k_u]^{1/12}[k_c K_c f^\alpha]^{7/12}}\left[\frac{K_v f k_f k_u}{\sum VA}\right]^{1/6}
$$

[source: Hurley & Wolfle Ch. 5 eq. 5.8]

When saturation limits the design, the source uses an initial estimate

$$
A_{p1} = \left[ \frac{\sqrt{2}\sum VA}{K_v f B_{sat} k_f K_t \sqrt{k_u \Delta T}} \right]^{8/7}
$$

then refines it with a numerical solution of the nonlinear $A_p$ equation. [source: Hurley & Wolfle Ch. 5 eq. 5.9-5.13]

## Procedure

1. Define voltages, currents, power, frequency, ambient, and temperature-rise limit. [source: Hurley & Wolfle Ch. 5 §5.2]
2. Compute waveform factor and total winding VA. [source: Hurley & Wolfle Ch. 4 §4.3.1-§4.3.2]
3. Select material and determine whether operation is saturation-limited or optimum-flux-limited. [source: Hurley & Wolfle Ch. 4 §4.3.5] [source: Hurley & Wolfle Ch. 5 §5.1.2-§5.1.3]
4. Compute $A_p$ and choose a standard core. [source: Hurley & Wolfle Ch. 5 eq. 5.5 or 5.9-5.13]
5. Compute turns from

$$
N = \frac{V_{rms}}{K_v f B_{max} A_m}
$$

[source: Hurley & Wolfle Ch. 5 eq. 5.15]
6. Size wires from current density and then evaluate copper and core losses. [source: Hurley & Wolfle Ch. 5 §5.2]
7. Re-check temperature rise, efficiency, and high-frequency winding effects. [source: Hurley & Wolfle Ch. 5 intro and §5.2]

## Related Pages

- [Practical Transformer Model](./practical-transformer-model.md)
- [Transformer Insulation](./transformer-insulation.md)
- [High-Frequency Effects](./high-frequency-effects.md)
- [Verification And Measurement](./verification-and-measurement.md)
- [Index](./index.md)