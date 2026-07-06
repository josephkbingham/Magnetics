# Equation Reference

This is a compact formula sheet. Use [Master Design Guide](./master-design-guide.md) for the beginner workflow and the deep-dive pages for assumptions.

## Constants And Symbols

| Symbol | Meaning |
| --- | --- |
| $A_e$ or $A_c$ | Effective core cross-sectional area |
| $W_a$ | Core window area |
| $A_p=A_eW_a$ | Area product |
| $MLT$ | Mean length per turn |
| $V_e$ or $V_c$ | Core volume |
| $k_u$ or $K_u$ | Window utilization/fill factor |
| $\mu_0$ | Permeability of free space |
| $\mu_r$ | Relative permeability |
| $\rho_w$ | Winding resistivity |

## Electromagnetic Fundamentals

Flux:

$$
\Phi=BA_e
$$

Faraday's law:

$$
v(t)=N\frac{d\Phi}{dt}=NA_e\frac{dB}{dt}
$$

Ampere's law:

$$
\oint H\cdot d\ell=NI
$$

Uniform path approximation:

$$
H\approx\frac{NI}{\ell_m}
$$

Linear material relation:

$$
B=\mu H=\mu_r\mu_0H
$$

[source: Erickson & Maksimovic Ch. 10 eq. 10.3-10.10]

## Reluctance, Gap, And Saturation

Reluctance:

$$
\mathcal{R}=\frac{\ell}{\mu A_e}
$$

Core and gap:

$$
\mathcal{R}_c=\frac{\ell_c}{\mu A_e}, \qquad
\mathcal{R}_g=\frac{\ell_g}{\mu_0A_e}
$$

Magnetic circuit:

$$
NI=\Phi(\mathcal{R}_c+\mathcal{R}_g)
$$

Inductance:

$$
L=\frac{N^2}{\mathcal{R}_c+\mathcal{R}_g}
$$

Gap-dominated flux density:

$$
B=\frac{\mu_0NI}{\ell_g+\ell_c/\mu_r}
$$

Gap-dominated inductance:

$$
L\approx\frac{\mu_0A_eN^2}{\ell_g}
$$

Saturation flux and current:

$$
\Phi_{sat}=B_{sat}A_e
$$

$$
I_{sat}=\frac{B_{sat}A_e}{N}(\mathcal{R}_c+\mathcal{R}_g)
$$

[source: Erickson & Maksimovic Ch. 10 eq. 10.27-10.33]

## Inductor Design

Inductor ripple:

$$
\Delta I=\frac{V_L\Delta t}{L}
$$

CCM buck ripple:

$$
D\approx\frac{V_o}{V_{in}}, \qquad
\Delta I_L=\frac{(V_{in}-V_o)D}{f_sL}
$$

Peak current:

$$
I_{pk}=I_{dc}+\frac{\Delta I_{pp}}{2}
$$

Triangular ripple RMS:

$$
I_{rms}\approx\sqrt{I_{dc}^2+\frac{\Delta I_{pp}^2}{12}}
$$

Stored energy:

$$
E=\frac{1}{2}LI_{pk}^2
$$

Flux check:

$$
B_{pk}=\frac{LI_{pk}}{NA_e}
$$

Minimum turns:

$$
N\ge\frac{LI_{pk}}{B_{max}A_e}
$$

Turns from $A_L$:

$$
N=\sqrt{\frac{L}{A_L}}
$$

Approximate gap:

$$
\ell_g\approx\frac{\mu_0A_eN^2}{L}-\frac{\ell_c}{\mu_r}
$$

Window fit:

$$
NA_{cu}\le k_uW_a
$$

Allowed resistance from copper loss:

$$
R_{max}=\frac{P_{cu,max}}{I_{rms}^2}
$$

Winding resistance:

$$
R=\rho_w\frac{N(MLT)}{A_{cu}}
$$

Geometry constant:

$$
K_g=\frac{A_e^2W_a}{MLT}\ge\frac{\rho_wL^2I_{pk}^2}{B_{max}^2RK_u}
$$

Inductor area product:

$$
A_p=\left[\frac{\sqrt{1+\gamma}K_iLI_{pk}^2}{B_{max}K_t\sqrt{k_u\Delta T}}\right]^{8/7}
$$

Optimum effective permeability:

$$
\mu_{opt}=\frac{B_{sat}l_cK_i}{\mu_0\sqrt{\frac{P_{cu,max}k_uW_a}{\rho_wMLT}}}
$$

[source: Erickson & Maksimovic Ch. 11 eq. 11.1-11.20] [source: Hurley & Wolfle Ch. 3 eq. 3.20, 3.35-3.38]

## Transformer Design

Ideal ratio:

$$
\frac{V_s}{V_p}\approx\frac{N_s}{N_p}
$$

Volt-second flux swing:

$$
\Delta B=\frac{1}{NA_e}\int v(t)\,dt
$$

General RMS voltage equation:

$$
V_{rms}=K_vfNB_{max}A_e
$$

VA area-product relation:

$$
\sum VA=K_vfB_{max}Jk_fk_uA_p
$$

Fixed-frequency area product:

$$
A_p=\left[\frac{\sqrt{2}\sum VA}{K_vfB_ok_fK_t\sqrt{k_u\Delta T}}\right]^{8/7}
$$

Saturation-limited starting estimate:

$$
A_{p1}=\left[\frac{\sqrt{2}\sum VA}{K_vfB_{sat}k_fK_t\sqrt{k_u\Delta T}}\right]^{8/7}
$$

Minimum-loss relation at fixed frequency:

$$
P_{cu}=\frac{\beta}{2}P_{fe}
$$

Magnetizing inductance:

$$
L_m=\frac{N_p^2}{\mathcal{R}}
$$

Magnetizing current ramp:

$$
\Delta I_m=\frac{1}{L_m}\int v_p(t)\,dt
$$

Reflected secondary terms:

$$
I_s'=\frac{1}{a}I_s, \qquad
R_s'=a^2R_s, \qquad
X_{ls}'=a^2X_{ls}
$$

Equivalent series terms:

$$
R_{eq}=R_p+a^2R_s, \qquad
X_{eq}=X_{lp}+a^2X_{ls}
$$

Mutual inductance:

$$
M=k\sqrt{L_1L_2}
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.34-4.83] [source: Hurley & Wolfle Ch. 5 eq. 5.4-5.15]

## Core, Thermal, And Winding Loss

Temperature-corrected copper resistivity:

$$
\rho_w=\rho_{20}[1+\alpha_{20}(T_{max}-20^\circ\text{C})]
$$

Copper loss:

$$
P_{cu}=I_{rms}^2R
$$

Core-loss density:

$$
P_{fe}=K_cf^\alpha B_{max}^\beta
$$

Total temperature rise:

$$
\Delta T=R_\theta(P_{cu}+P_{fe})
$$

Convection form:

$$
\Delta T=\frac{Q}{h_cA_t}
$$

Empirical thermal resistance:

$$
R_\theta=\frac{0.06}{\sqrt{V_c}}
$$

Skin depth:

$$
\delta=\frac{1}{\sqrt{\pi f\mu\sigma}}
$$

Round-wire AC-resistance approximation:

$$
R_{ac}=R_{dc}\left[1+\frac{(r_o/\delta)^4}{48+0.8(r_o/\delta)^4}\right]
$$

[source: Hurley & Wolfle Ch. 1 eq. 1.21-1.29] [source: Hurley & Wolfle Ch. 3 eq. 3.14-3.16, 3.37] [source: Hurley & Wolfle Ch. 4 eq. 4.36]

## Fringing

For a rectangular discrete gap:

$$
L'=L\frac{(a+g)(b+g)}{ab}
$$

For $g\ll a$ or $b$:

$$
L'\approx L\left(1+\frac{a+b}{ab}g\right)
$$

For a square cross-section:

$$
1+\frac{2g}{a}
$$

[source: Hurley & Wolfle Ch. 2 eq. 2.65-2.66]

## Related Pages

- [Master Design Guide](./master-design-guide.md)
- [Inductor Design Deep Dive](./inductor-design-deep-dive.md)
- [Transformer Design Deep Dive](./transformer-design-deep-dive.md)
- [Magnetic Theory](./magnetic-theory.md)
- [Core, Gap, And Thermal Design](./core-gap-and-thermal-design.md)
- [High-Frequency And Winding Effects](./high-frequency-and-winding-effects.md)
- [Verification And Measurement](./verification-and-measurement.md)
- [Index](./index.md)
