# Equation Reference

## Scope

This page collects the main equations used by the magnetics wiki for quick lookup. Detailed assumptions, design context, and tradeoffs remain on the topic pages linked at the end of this page.

## Electromagnetic Fundamentals

Magnetic flux through a cross-section is

$$
\Phi = B A_c
$$

[source: Erickson & Maksimovic Ch. 10 eq. 10.3-10.4]

Faraday's law for one turn is

$$
v(t) = \frac{d\Phi(t)}{dt}
$$

and, for uniform flux density through area $A_c$,

$$
v(t) = A_c \frac{dB(t)}{dt}
$$

[source: Erickson & Maksimovic Ch. 10 eq. 10.5-10.6]

Ampere's law is

$$
\oint H \cdot d\ell = NI
$$

and for an approximately uniform magnetic path,

$$
H \approx \frac{NI}{\ell_m}
$$

[source: Erickson & Maksimovic Ch. 10 eq. 10.7-10.8] [source: TI SLUP132 eq. 1]

The linear material relation is

$$
B = \mu H = \mu_r \mu_0 H
$$

[source: Erickson & Maksimovic Ch. 10 eq. 10.10]

## Reluctance, Gap, And Saturation

Core and air-gap reluctance are

$$
\mathcal{R}_c = \frac{\ell_c}{\mu A_c}
$$

$$
\mathcal{R}_g = \frac{\ell_g}{\mu_0 A_c}
$$

[source: Erickson & Maksimovic Ch. 10 eq. 10.27]

The magnetic-circuit relation is

$$
ni = \Phi(\mathcal{R}_c + \mathcal{R}_g)
$$

[source: Erickson & Maksimovic Ch. 10 eq. 10.28]

Inductance is

$$
L = \frac{n^2}{\mathcal{R}_c + \mathcal{R}_g}
$$

[source: Erickson & Maksimovic Ch. 10 eq. 10.31]

At saturation,

$$
\Phi_{sat} = B_{sat} A_c
$$

and

$$
I_{sat} = \frac{B_{sat} A_c}{n}(\mathcal{R}_c + \mathcal{R}_g)
$$

[source: Erickson & Maksimovic Ch. 10 eq. 10.32-10.33]

For a gap-dominated inductor,

$$
n I_{max} = B_{max} \frac{\ell_g}{\mu_0}
$$

and

$$
L = \frac{\mu_0 A_c n^2}{\ell_g}
$$

[source: Erickson & Maksimovic Ch. 11 eq. 11.6-11.7]

Equivalently, in terms of the effective magnetic length of the series core-plus-gap path,

$$
B = \frac{\mu_0 NI}{\ell_c/\mu_r + \ell_g}
$$

which shows the gap term $\ell_g$ dominates the denominator once $\ell_c/\mu_r \ll \ell_g$, since the core contributes only its physical length divided by $\mu_r$. [source: Magnetic-Mechanical Analogy Ref. §10.3]

## Buck Inductor First-Pass Design

Allowed copper loss sets winding resistance through

$$
P_{cu} = I_{rms}^2 R
$$

[source: Erickson & Maksimovic Ch. 11 eq. 11.1]

The winding fit condition is

$$
K_u W_A \ge n A_W
$$

[source: Erickson & Maksimovic Ch. 11 eq. 11.10]

Winding resistance from mean length per turn is

$$
R = \rho \frac{n(MLT)}{A_W}
$$

[source: Erickson & Maksimovic Ch. 11 eq. 11.13]

The core-geometry constant condition is

$$
K_g = \frac{A_c^2 W_A}{MLT} \ge \frac{\rho L^2 I_{max}^2}{B_{max}^2 R K_u}
$$

[source: Erickson & Maksimovic Ch. 11 eq. 11.14-11.15]

For centimeter-based core tables,

$$
K_g \ge \frac{\rho L^2 I_{max}^2}{B_{max}^2 R K_u}10^8
$$

[source: Erickson & Maksimovic Ch. 11 eq. 11.16]

Turns and approximate gap are

$$
n = \frac{L I_{max}}{B_{max} A_c}10^4
$$

$$
\ell_g = \frac{\mu_0 A_c n^2}{L}10^{-4}
$$

with $A_c$ in cm$^2$. [source: Erickson & Maksimovic Ch. 11 eq. 11.17-11.18]

The usable wire-area check is

$$
A_W \le \frac{K_u W_A}{n}
$$

[source: Erickson & Maksimovic Ch. 11 eq. 11.20]

## Fringing

For a rectangular gap cross-section $a \times b$ and gap length $g$,

$$
L' = L \frac{(a + g)(b + g)}{ab}
$$

[source: Hurley & Wolfle Ch. 2 eq. 2.65]

For $g \ll a$ or $b$,

$$
L' \approx L \left(1 + \frac{a + b}{ab} g\right)
$$

[source: Hurley & Wolfle Ch. 2 eq. 2.66]

For a square cross-section, the fringing factor reduces to

$$
1 + \frac{2g}{a}
$$

[source: Hurley & Wolfle Ch. 2 §2.5]

## Thermal And Core Selection

Temperature rise is modeled as

$$
\Delta T = R_{\theta} Q = \frac{1}{h_c A_t}Q
$$

[source: Hurley & Wolfle Ch. 3 eq. 3.14-3.15]

An empirical thermal-resistance approximation is

$$
R_{\theta} = \frac{0.06}{\sqrt{V_c}}
$$

with $R_{\theta}$ in $^\circ$C/W for $V_c$ in m$^3$. [source: Hurley & Wolfle Ch. 3 eq. 3.16]

Window utilization is

$$
k_u = \frac{W_c}{W_a}
$$

[source: Hurley & Wolfle Ch. 3 eq. 3.18]

The thermal-current-density result is

$$
J_o = \sqrt{\frac{1}{1 + \gamma} \frac{h_c A_t \Delta T}{\rho_w V_w k_u}}
$$

[source: Hurley & Wolfle Ch. 3 eq. 3.24]

Using dimensional analysis,

$$
J_o = K_t \sqrt{\frac{\Delta T}{k_u(1 + \gamma)}} \frac{1}{\sqrt[8]{A_p}}
$$

with

$$
K_t = \sqrt{\frac{h_c k_a}{\rho_w k_w}}
$$

[source: Hurley & Wolfle Ch. 3 eq. 3.28-3.29]

The inductor area-product requirement is

$$
A_p = \left[ \frac{\sqrt{1 + \gamma}\, K_i L \hat{I}^2}{B_{max} K_t \sqrt{k_u \Delta T}} \right]^{8/7}
$$

[source: Hurley & Wolfle Ch. 3 eq. 3.35]

Optimum effective permeability is

$$
\mu_{opt} = \frac{B_{sat} l_c K_i}{\mu_0 \sqrt{\frac{P_{cu\ max} k_u W_a}{\rho_w MLT}}}
$$

[source: Hurley & Wolfle Ch. 3 eq. 3.20]

Turns from manufacturer $A_L$ data are

$$
N = \sqrt{\frac{L}{A_L}}
$$

[source: Hurley & Wolfle Ch. 3 eq. 3.36]

Temperature-corrected winding resistivity is

$$
\rho_w = \rho_{20}[1 + \alpha_{20}(T_{max} - 20^\circ\text{C})]
$$

[source: Hurley & Wolfle Ch. 3 eq. 3.37]

## Transformer Model

The reflected secondary current is

$$
I_2^1 = \frac{1}{a}I_2
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.35]

Core mmf balance is

$$
N_1 I_1 - N_2 I_2 = \phi_m \mathcal{R}
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.34]

The leakage-inclusive winding voltage equations are

$$
V_1 = [L_{l1} + L_1]\frac{di_1}{dt} + M_{12}\frac{di_2}{dt}
$$

$$
V_2 = [L_{l2} + L_2]\frac{di_2}{dt} + M_{21}\frac{di_1}{dt}
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.39-4.40]

Mutual inductance and coupling are

$$
M = \sqrt{L_1 L_2}
$$

$$
k = \sqrt{k_1 k_2}
$$

$$
M = k\sqrt{L_{11}L_{22}}
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.45, 4.50-4.51]

Referred secondary quantities are

$$
R_2^1 = a^2 R_2
$$

$$
X_{l2}^1 = a^2 X_{l2}
$$

$$
V_2^1 = aV_2
$$

$$
I_2^1 = \frac{1}{a}I_2
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.53-4.56]

The referred series terms are

$$
R_{eq} = R_1 + a^2R_2
$$

$$
X_{eq} = X_{l1} + a^2X_{l2}
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.57-4.58]

## Transformer Design

The general transformer voltage equation is

$$
V_{rms} = K_v f N B_{max} A_m
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.62]

The winding VA sum is

$$
\sum VA = K_v f B_{max} J_o k_f k_u A_p
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.73]

Transformer winding loss is

$$
P_{cu} = \rho_w V_w k_u J_o^2
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.76]

The optimized loss model is

$$
P = \frac{a}{f^2 B_{max}^2} + b f^\alpha B_{max}^\beta
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.79]

For fixed frequency, minimum loss occurs when

$$
P_{cu} = \frac{\beta}{2}P_{fe}
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.83]

For fixed-frequency transformer design,

$$
J_o = K_t \sqrt{\frac{\Delta T}{2k_u}} \frac{1}{\sqrt[8]{A_p}}
$$

[source: Hurley & Wolfle Ch. 5 eq. 5.4]

When optimum flux density is not saturation-limited,

$$
A_p = \left[ \frac{\sqrt{2}\sum VA}{K_v f B_o k_f K_t \sqrt{k_u \Delta T}} \right]^{8/7}
$$

[source: Hurley & Wolfle Ch. 5 eq. 5.5]

The corresponding optimum flux density is

$$
B_o = \frac{[h_c k_a \Delta T]^{2/3}}{2^{2/3}[\rho_w k_w k_u]^{1/12}[k_c K_c f^\alpha]^{7/12}}\left[\frac{K_v f k_f k_u}{\sum VA}\right]^{1/6}
$$

[source: Hurley & Wolfle Ch. 5 eq. 5.8]

When saturation limits the design, the initial area-product estimate is

$$
A_{p1} = \left[ \frac{\sqrt{2}\sum VA}{K_v f B_{sat} k_f K_t \sqrt{k_u \Delta T}} \right]^{8/7}
$$

[source: Hurley & Wolfle Ch. 5 eq. 5.9]

Transformer turns are

$$
N = \frac{V_{rms}}{K_v f B_{max} A_m}
$$

[source: Hurley & Wolfle Ch. 5 eq. 5.15]

## High-Frequency Effects And Core Loss

Skin depth is

$$
\delta = \frac{1}{\sqrt{\pi f \mu \sigma}}
$$

[source: Hurley & Wolfle Ch. 1 eq. 1.21]

A first approximation for round-wire AC resistance is

$$
R_{ac} = R_{dc}\left[1 + \frac{(r_o/\delta)^4}{48 + 0.8(r_o/\delta)^4}\right]
$$

[source: Hurley & Wolfle Ch. 1 eq. 1.22] [source: Hurley & Wolfle Ch. 4 eq. 4.36]

Steinmetz core-loss density is

$$
P_{fe} = K_c f^\alpha B_{max}^\beta
$$

[source: Hurley & Wolfle Ch. 1 eq. 1.29] [source: Hurley & Wolfle Ch. 4 §4.3.4]

## Related Pages

- [Electromagnetic Fundamentals](./electromagnetic-fundamentals.md)
- [Air Gap And Saturation](./air-gap-and-saturation.md)
- [Magnetic-Mechanical Analogy](./magnetic-mechanical-analogy.md)
- [Distributed Gap And Fringing](./distributed-gap-and-fringing.md)
- [Buck Output Filter Inductor Design](./buck-output-filter-inductor-design.md)
- [Inductor Design Sensitivity](./inductor-design-sensitivity.md)
- [Thermal Design And Core Selection](./thermal-design-and-core-selection.md)
- [Practical Transformer Model](./practical-transformer-model.md)
- [Transformer Design Methodology](./transformer-design-methodology.md)
- [High-Frequency Effects](./high-frequency-effects.md)
- [Index](./index.md)
