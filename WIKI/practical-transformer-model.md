# Practical Transformer Model

## Scope

This page summarizes the non-ideal transformer model needed for power-electronics design: magnetizing current, core loss, winding resistance, leakage inductance, and the referred equivalent circuit. [source: Hurley & Wolfle Ch. 4 §4.2]

## Magnetizing Branch

The practical primary current has two components: a magnetizing component that establishes mutual flux and a load component reflected from the secondary. The source gives the reflected load current as

$$
I_2^1 = \frac{1}{a} I_2
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.35]

The net mmf in the core is

$$
N_1 I_1 - N_2 I_2 = \phi_m \mathcal{R}
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.34]

The source represents magnetization and core loss with a shunt branch across the input, consisting of magnetizing reactance $X_m$ and core-loss resistance $R_c$ in parallel. [source: Hurley & Wolfle Ch. 4 §4.2.1]

## Winding Resistance

Primary and secondary winding resistances are represented explicitly. The source also gives a first skin-effect approximation for round-wire AC resistance:

$$
R_{ac} = R_{dc} \left[1 + \frac{\left(\frac{r_o}{\delta}\right)^4}{48 + 0.8\left(\frac{r_o}{\delta}\right)^4}\right]
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.36]

This is only a first approximation; the source defers detailed skin and proximity analysis to the high-frequency winding chapter. [source: Hurley & Wolfle Ch. 4 §4.2.2]

## Leakage Inductance

The practical transformer contains leakage flux that links only one winding. The source writes the winding voltages as

$$
V_1 = [L_{l1} + L_1] \frac{di_1}{dt} + M_{12} \frac{di_2}{dt}
$$

$$
V_2 = [L_{l2} + L_2] \frac{di_2}{dt} + M_{21} \frac{di_1}{dt}
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.39-4.40]

The mutual inductance is

$$
M = \sqrt{L_1 L_2}
$$

and the coupling coefficient is

$$
k = \sqrt{k_1 k_2}
$$

with

$$
M = k \sqrt{L_{11}L_{22}}
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.45, 4.50-4.51]

## Referred Equivalent Circuit

When quantities are referred from secondary to primary, the source gives

$$
R_2^1 = a^2 R_2
$$

$$
X_{l2}^1 = a^2 X_{l2}
$$

$$
V_2^1 = a V_2
$$

$$
I_2^1 = \frac{1}{a} I_2
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.53-4.56]

The series terms combine to

$$
R_{eq} = R_1 + a^2 R_2
$$

$$
X_{eq} = X_{l1} + a^2 X_{l2}
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.57-4.58]

## Related Pages

- [Transformer Design Methodology](./transformer-design-methodology.md)
- [High-Frequency Effects](./high-frequency-effects.md)
- [Verification And Measurement](./verification-and-measurement.md)
- [Index](./index.md)