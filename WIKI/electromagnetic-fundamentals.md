# Electromagnetic Fundamentals

## Definitions

Magnetic flux $\Phi$ is the surface integral of flux density $\mathbf{B}$, and for uniform flux density over cross-sectional area $A_c$ the relation reduces to $\Phi = B A_c$. [source: Erickson & Maksimovic Ch. 10 eq. 10.3-10.4]

Faraday's law for a single turn is

$$
v(t) = \frac{d\Phi(t)}{dt}
$$

and, for uniform flux density through area $A_c$,

$$
v(t) = A_c \frac{dB(t)}{dt}
$$

[source: Erickson & Maksimovic Ch. 10 eq. 10.5-10.6]

Ampere's law relates winding current to magnetic field by

$$
\oint H \cdot d\ell = \text{total current enclosed}
$$

and for a uniform field along magnetic path length $\ell_m$ this becomes

$$
\mathcal{F} = H\ell_m = i
$$

for the one-turn example shown in the source text. [source: Erickson & Maksimovic Ch. 10 eq. 10.7-10.8]

## Field-Solution Methods

`[UNVERIFIED]` The Biot-Savart law is the point-by-point field construction method for steady current distributions. It gives the incremental magnetic-flux-density contribution produced at a field point by an elemental current segment:

$$
d\mathbf{B} = \frac{\mu_0}{4\pi} \frac{I \, d\mathbf{l} \times \hat{\mathbf{r}}}{r^2}
$$

`[UNVERIFIED]` This form is general for arbitrary current geometry, but practical use requires integrating contributions from the entire conductor path, which makes it algebraically heavy except for simple geometries.

Ampere's law is the symmetry-based alternative used throughout converter magnetics. In integral form,

$$
\oint H \cdot d\ell = NI
$$

and for uniform field along a known magnetic path length this reduces to

$$
H \approx \frac{NI}{\ell_m}
$$

This simplification is valid when geometry makes the field approximately uniform over the chosen path, which is the usual approximation for toroids, long solenoids, and closed magnetic cores analyzed with an effective path length. [source: Erickson & Maksimovic Ch. 10 eq. 10.7-10.8] [source: TI SLUP132 eq. 1]

## What $B$ Is And What $H$ Is

Magnetic field intensity $H$ is the winding-imposed magnetizing force. Ampere's law makes $H$ the quantity set directly by enclosed current, turns, and magnetic-path length rather than by the core material itself. For a uniform path, increasing ampere-turns increases $H$, while increasing path length reduces $H$ for the same current drive. [source: Erickson & Maksimovic Ch. 10 eq. 10.7-10.8]

Flux density $B$ is the magnetic response that appears in the material and in the magnetic cross-section. It is the quantity that determines total flux through area $A_c$ via $\Phi = BA_c$. In the linear material model, $B$ is related to $H$ by permeability:

$$
B = \mu H = \mu_r \mu_0 H
$$

[source: Erickson & Maksimovic Ch. 10 eq. 10.3-10.4] [source: Erickson & Maksimovic Ch. 10 eq. 10.10]

The basic causal chain in a winding-driven magnetic element is therefore

$$
i \rightarrow H \rightarrow B \rightarrow \Phi
$$

and, when the flux changes with time,

$$
\frac{d\Phi}{dt} \rightarrow v
$$

via Faraday's law. [source: Erickson & Maksimovic Ch. 10 eq. 10.5-10.8]

For converter magnetics driven from a low-impedance switched voltage source, Faraday's law often provides the most direct design view because applied volts-per-turn set the flux-density slope:

$$
v(t) = A_c \frac{dB(t)}{dt}
$$

This means the applied voltage fixes the required flux swing over time, while the current adjusts to whatever value is necessary to produce the corresponding $H$ implied by the material's $B$-$H$ characteristic. [source: Erickson & Maksimovic Ch. 10 eq. 10.5-10.6]

## Core Material Model

With hysteresis and saturation neglected, the core-material model is linear:

$$
B = \mu H = \mu_r \mu_0 H
$$

[source: Erickson & Maksimovic Ch. 10 eq. 10.10]

The source text states typical saturation-flux-density ranges of 1 to 2 T for iron laminations and silicon steel, 0.5 to 1 T for powdered iron and molypermalloy materials, and 0.25 to 0.5 T for ferrites. [source: Erickson & Maksimovic Ch. 10 discussion following Fig. 10.6]

## Relevance To Converter Inductors

The buck-inductor equations in this wiki reuse these relationships in two places: Faraday's law governs the relation between applied volt-seconds and flux swing, while Ampere's law and the magnetic-circuit model govern current, gap MMF, and saturation. [source: Erickson & Maksimovic Ch. 10 eq. 10.5-10.7] [source: Erickson & Maksimovic Ch. 10 eq. 10.26-10.33]

## Related Pages

- [Air Gap And Saturation](./air-gap-and-saturation.md)
- [Magnetic-Mechanical Analogy](./magnetic-mechanical-analogy.md)
- [Buck Output Filter Inductor Design](./buck-output-filter-inductor-design.md)
- [Core Materials And Losses](./core-materials-and-losses.md)
- [Index](./index.md)