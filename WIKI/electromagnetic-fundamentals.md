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
- [Buck Output Filter Inductor Design](./buck-output-filter-inductor-design.md)
- [Core Materials And Losses](./core-materials-and-losses.md)
- [Index](./index.md)