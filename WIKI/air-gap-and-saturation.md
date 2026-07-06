# Air Gap And Saturation

## Gap-Dominated Magnetic Circuit

For an inductor with a core section and an air gap in series, the reluctances are

$$
\mathcal{R}_c = \frac{\ell_c}{\mu A_c}
$$

and

$$
\mathcal{R}_g = \frac{\ell_g}{\mu_0 A_c}
$$

[source: Erickson & Maksimovic Ch. 10 eq. 10.27]

The winding MMF drives total flux according to

$$
ni = \Phi (\mathcal{R}_c + \mathcal{R}_g)
$$

[source: Erickson & Maksimovic Ch. 10 eq. 10.28]

The corresponding inductance is

$$
L = \frac{n^2}{\mathcal{R}_c + \mathcal{R}_g}
$$

[source: Erickson & Maksimovic Ch. 10 eq. 10.31]

## Why The Gap Exists

The source text gives two reasons for adding an air gap to practical inductors. First, when the gap reluctance dominates the total reluctance, the inductance becomes less sensitive to variations in the core permeability $\mu$. Second, the onset-of-saturation current increases when gap reluctance is added. [source: Erickson & Maksimovic Ch. 10 discussion following eq. 10.31]

At the onset of saturation,

$$
\Phi_{sat} = B_{sat} A_c
$$

and the corresponding current is

$$
I_{sat} = \frac{B_{sat} A_c}{n}(\mathcal{R}_c + \mathcal{R}_g)
$$

[source: Erickson & Maksimovic Ch. 10 eq. 10.32-10.33]

## Permeability Versus Saturation

For a discrete-gapped ferrite inductor, the material relative permeability $\mu_r$ is usually a second-order selection property because the air-gap term dominates the effective magnetic length:

$$
\ell_{eff} = \ell_g + \frac{\ell_c}{\mu_r}
$$

At the baseline point from [Inductor Design Sensitivity](./inductor-design-sensitivity.md), $\ell_g = 1.02\ \text{mm}$, $\ell_c = 9.2\ \text{cm}$, and $\mu_r = 2000$, so the core contributes only $9.2\ \text{cm}/2000 = 0.046\ \text{mm}$ compared with the 1.02 mm gap. Increasing $\mu_r$ to 4000 reduces the core term to 0.023 mm, changing the total effective magnetic length by only about 2 %. In the same design, changing ferrite $B_{sat}$ from 0.35 T to 0.45 T, or using the hot instead of room-temperature $B_{sat}$ value, changes saturation margin by tens of percent. [source: /WIKI/inductor-design-sensitivity.md GIC and Governing Equations] [source: Hurley & Wolfle Ch. 1 §1.3]

The design consequence is that, for gapped ferrite energy-storage inductors, material comparison should emphasize hot $B_{sat}$, core-loss curves, temperature behavior, and manufacturable gap/$A_L$ values. The raw material $\mu_r$ mainly needs to be high enough that $\ell_c/\mu_r$ stays small compared with the intentional gap. [source: Erickson & Maksimovic Ch. 10 discussion following eq. 10.31] [source: Hurley & Wolfle Ch. 3 §3.2]

This statement does not apply to every magnetic component. In distributed-gap powder inductors, the purchased effective permeability grade plays the role of the gap and directly sets inductance per turn squared, flux per ampere, and DC-bias roll-off. In true transformers, high permeability is again valuable because it raises magnetizing inductance and reduces magnetizing current, although the exact value is normally a "high enough" design property rather than the primary material differentiator. [source: Hurley & Wolfle Ch. 2 §2.3.2] [source: TI SLUP132 §2 Core Limitations in SMPS Applications] [source: TI SLUP132 §4 Power Transformer Design]

## Tradeoffs

Increasing $\ell_g$ increases $\mathcal{R}_g$, which increases saturation current but decreases inductance because $L = n^2/(\mathcal{R}_c + \mathcal{R}_g)$. The forcing constraint in a CCM buck output inductor is usually simultaneous satisfaction of required inductance and allowable peak current without core saturation. [source: Erickson & Maksimovic Ch. 10 eq. 10.31-10.33] [source: Erickson & Maksimovic Ch. 11 §11.1]

## Related Pages

- [Electromagnetic Fundamentals](./electromagnetic-fundamentals.md)
- [Magnetic-Mechanical Analogy](./magnetic-mechanical-analogy.md)
- [Equation Reference](./equation-reference.md)
- [Buck Output Filter Inductor Design](./buck-output-filter-inductor-design.md)
- [Verification And Measurement](./verification-and-measurement.md)
- [Index](./index.md)
