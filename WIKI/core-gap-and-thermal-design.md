# Core, Gap, And Thermal Design

This page consolidates the former air-gap, saturation, distributed-gap, fringing, core-material, and thermal core-selection notes. Use it when a one-page workflow says "choose core", "choose gap", or "check temperature."

## Core Material Selection

| Material family | Useful traits | Common limits |
| --- | --- | --- |
| MnZn ferrite | Low eddy-current loss, common for roughly 10 kHz to 1 MHz power magnetics. | Low saturation flux density, strong temperature dependence, brittle, may need a discrete gap for inductors. |
| NiZn ferrite | Higher resistivity and useful at higher frequency. | Lower permeability and often not the first choice for high-power energy storage. |
| Powdered iron / metal composite | Distributed gap, soft saturation, good DC-bias tolerance, lower local fringing. | Higher core loss than ferrite in many high-frequency cases; material grade strongly affects performance. |
| Silicon steel / laminated iron | High saturation flux density, useful at line frequency and lower-frequency filters. | High high-frequency loss unless laminated very thin. |
| Amorphous / nanocrystalline | High saturation with good loss performance in selected applications. | Cost, availability, mechanical handling, and core-form limits. |

Ferrite saturation can fall substantially with temperature; a room-temperature headline value is not enough for design. Compare materials using hot $B_{sat}$, core-loss curves, frequency range, thermal behavior, core shape availability, and gap options. [source: Erickson & Maksimovic Ch. 10 §10.3.1] [source: Hurley & Wolfle Ch. 1 §1.3]

## Discrete Gap Versus Distributed Gap

For energy-storage inductors, the practical question is usually not "gap or no gap"; it is "discrete gap or distributed gap." [source: TI SLUP132 §2 Core Limitations in SMPS Applications]

### Discrete-Gapped Ferrite

Benefits:

- Low high-frequency core loss.
- Many E, ETD, PQ, RM, and similar catalog shapes.
- Manufacturer-gapped sets with specified $A_L$ values.

Costs:

- Local fringing at the gap.
- Possible nearby copper heating and EMI.
- Sharp inductance drop when ferrite saturates.
- Gap tolerance matters.

### Distributed-Gap Powder Or Composite Core

Benefits:

- Gap is spread through the material.
- Softer saturation and better DC-bias roll-off.
- Less local fringing and often lower gap-field copper heating.

Costs:

- Effective permeability grade is a primary design choice.
- Core loss may be higher than ferrite.
- Shape and size availability can be narrower.

## Gap-Dominated Inductor Model

For a core and gap in series:

$$
\mathcal{R}_c=\frac{\ell_c}{\mu A_e}, \qquad
\mathcal{R}_g=\frac{\ell_g}{\mu_0 A_e}
$$

Total reluctance:

$$
\mathcal{R}_{tot}=\mathcal{R}_c+\mathcal{R}_g
$$

Inductance:

$$
L=\frac{N^2}{\mathcal{R}_{tot}}
$$

Peak flux density:

$$
B=\frac{\mu_0NI}{\ell_g+\ell_c/\mu_r}
$$

If $\ell_g \gg \ell_c/\mu_r$, the gap dominates. Example: with $\ell_c=9.2\text{ cm}$ and $\mu_r=2000$, the core term is only 0.046 mm. A 1 mm air gap dominates the magnetic length. In that regime, raw material permeability is less important than hot saturation, loss data, and gap manufacturability. [source: Erickson & Maksimovic Ch. 10 discussion following eq. 10.31]

## Saturation Current

At saturation:

$$
\Phi_{sat}=B_{sat}A_e
$$

$$
I_{sat}=\frac{B_{sat}A_e}{N}(\mathcal{R}_c+\mathcal{R}_g)
$$

Increasing the gap increases saturation current but decreases inductance unless turns are increased. This is the core tradeoff of power-inductor design.

## Fringing Around A Discrete Gap

The no-fringing approximation underestimates inductance because flux bulges around the gap. Fringing also increases loss in nearby conductors. [source: Hurley & Wolfle Ch. 2 §2.5]

For a rectangular gap cross-section $a\times b$ and gap $g$:

$$
L'=L\frac{(a+g)(b+g)}{ab}
$$

For $g \ll a$ or $b$:

$$
L'\approx L\left(1+\frac{a+b}{ab}g\right)
$$

For a square cross-section, the factor reduces to:

$$
1+\frac{2g}{a}
$$

Rules of thumb:

- Keep winding copper away from strong discrete-gap fields when possible.
- Large gaps relative to pole dimensions need fringing correction or measurement.
- Distributed-gap cores reduce local fringing but bring material-loss tradeoffs.

## Thermal Model

Total magnetic loss is:

$$
P_{tot}=P_{cu}+P_{fe}
$$

Temperature rise:

$$
\Delta T=R_\theta P_{tot}
$$

Convection form:

$$
\Delta T=\frac{Q}{h_cA_t}
$$

Empirical volume approximation:

$$
R_\theta=\frac{0.06}{\sqrt{V_c}}
$$

with $R_\theta$ in deg C/W for $V_c$ in m^3. Natural-convection power-magnetic estimates often start around $h_c=10\text{ W/m}^2\text{K}$; forced airflow may move into roughly 10-30 W/m^2K depending geometry and flow. [source: Hurley & Wolfle Ch. 3 eq. 3.14-3.16]

## Window Utilization And Current Density

Window utilization:

$$
k_u=\frac{W_c}{W_a}
$$

Practical starting values:

| Build type | Starting $k_u$ |
| --- | --- |
| Isolated transformer with margins/tape | 0.25-0.40 |
| Bobbin-wound inductor | 0.30-0.45 |
| Simple foil or low-insulation inductor | 0.50-0.70 |
| Very conservative unknown layout | 0.30-0.40 |

Current-density starting values:

| Cooling/layout | Starting current density |
| --- | --- |
| Natural convection, moderate temperature | 3-6 A/mm^2 |
| Hot ambient or enclosed product | 2-4 A/mm^2 |
| Forced cooling or short duty | Higher may be acceptable after thermal test |

These are rules of thumb, not pass/fail equations. Final current density is whatever satisfies copper loss, AC loss, temperature rise, window fill, and manufacturability.

## Area Product For Core Selection

For an inductor:

$$
A_p=\left[\frac{\sqrt{1+\gamma}K_iLI_{pk}^2}{B_{max}K_t\sqrt{k_u\Delta T}}\right]^{8/7}
$$

For a transformer:

$$
\sum VA=K_vfB_{max}Jk_fk_uA_p
$$

Area product is a first-pass sizing tool. It does not replace final checks for turns, actual $A_L$, winding build, insulation, leakage, core loss, fringing, and temperature. [source: Hurley & Wolfle Ch. 3 eq. 3.35] [source: Hurley & Wolfle Ch. 4 eq. 4.73]

## Optimum Effective Permeability

For a gapped inductor, Hurley and Wolfle give:

$$
\mu_{opt}=\frac{B_{sat}l_cK_i}{\mu_0\sqrt{\frac{P_{cu,max}k_uW_a}{\rho_wMLT}}}
$$

For a discrete gap, this target maps to a gap length. For a distributed-gap core, it maps to an effective-permeability grade. [source: Hurley & Wolfle Ch. 3 eq. 3.20]

## Practical Core/Gapping Checklist

1. Choose material family from frequency, DC bias, loss, saturation, and cost.
2. Pick a conservative hot $B_{max}$.
3. Use $K_g$ or $A_p$ to choose a first core size.
4. Use turns and gap equations, then replace ideal values with catalog $A_L$ data when available.
5. Check window fill with real insulation and terminations.
6. Estimate copper and core losses at hot resistance and real flux swing.
7. Check temperature rise and fringing.
8. Iterate core size, turns, gap/effective permeability, and conductor.

## Related Pages

- [Master Design Guide](./master-design-guide.md)
- [Magnetic Theory](./magnetic-theory.md)
- [Inductor Design Deep Dive](./inductor-design-deep-dive.md)
- [Transformer Design Deep Dive](./transformer-design-deep-dive.md)
- [High-Frequency And Winding Effects](./high-frequency-and-winding-effects.md)
- [Equation Reference](./equation-reference.md)
