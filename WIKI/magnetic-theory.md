# Magnetic Theory

This page consolidates the former electromagnetic fundamentals, magnetic-mechanical analogy, and self/mutual inductance analogy pages. It is intentionally theory-heavy; use [Master Design Guide](./master-design-guide.md) for the design recipe.

## Core Field Variables

Magnetic flux through a cross-section is:

$$
\Phi = B A_e
$$

Faraday's law for one turn is:

$$
v(t)=\frac{d\Phi(t)}{dt}
$$

For uniform flux density:

$$
v(t)=A_e\frac{dB(t)}{dt}
$$

For $N$ turns:

$$
v(t)=N A_e\frac{dB(t)}{dt}
$$

Ampere's law is:

$$
\oint H\cdot d\ell = NI
$$

For an approximately uniform magnetic path:

$$
H\approx\frac{NI}{\ell_m}
$$

The linear material relation is:

$$
B=\mu H=\mu_r\mu_0H
$$

[source: Erickson & Maksimovic Ch. 10 eq. 10.3-10.10]

## What $B$ And $H$ Mean

$H$ is the magnetizing force imposed by current, turns, and magnetic path length. $B$ is the flux-density response in the material and geometry. In a winding-driven magnetic element, the causal chain is:

$$
i \rightarrow H \rightarrow B \rightarrow \Phi
$$

For voltage-driven power converters, Faraday's law is often the more useful design view: applied volt-seconds per turn set the flux swing, while current changes as needed to establish the required $H$ on the material's $B$-$H$ curve.

The practical split:

- Saturation is governed by $B$.
- Magnetizing force, gap MMF, and current are governed by $H$.
- Voltage waveforms set $dB/dt$.
- Current waveforms reveal the reluctance and saturation state.

## Reluctance And Inductance

Magnetic reluctance is:

$$
\mathcal{R}=\frac{\ell}{\mu A_e}
$$

Hopkinson's law is:

$$
\text{MMF}=NI=\mathcal{R}\Phi
$$

Inductance follows from flux linkage:

$$
L=\frac{N\Phi}{I}=\frac{N^2}{\mathcal{R}}
$$

This is the bridge between the magnetic circuit and the electrical terminal model. A larger reluctance lowers inductance for a fixed turn count, but it can raise the saturation current by requiring more ampere-turns to reach the same core flux. [source: Erickson & Maksimovic Ch. 10 eq. 10.27-10.33]

## Energy Storage

Electrical inductor energy:

$$
E=\frac{1}{2}LI^2
$$

Magnetic circuit energy:

$$
E=\frac{1}{2}\mathcal{R}\Phi^2
$$

Field energy density in a linear material:

$$
w=\frac{1}{2}BH=\frac{B^2}{2\mu}
$$

At equal $B$, low-permeability material stores more energy per unit volume than high-permeability material. That is why an air gap, despite being physically small, stores most of the energy in a gapped ferrite inductor. [source: Magnetic-Mechanical Analogy Ref. §6-§9]

## The Gap Paradox

Three statements are all true, but each holds a different variable constant:

| Statement | Held constant | Consequence |
| --- | --- | --- |
| Higher reluctance lowers inductance | Same turns and same geometry | $L=N^2/\mathcal{R}$ falls. |
| Higher reluctance lowers energy at fixed current | Same current | $E=\frac12(NI)^2/\mathcal{R}$ falls. |
| A gap raises usable energy before saturation | Same core $A_e$ and $B_{sat}$ | $I_{sat}$ rises, so the usable current range grows. |

At the saturation limit:

$$
\Phi_{max}=B_{sat}A_e
$$

and:

$$
NI_{sat}=\mathcal{R}\Phi_{max}
$$

Substitution gives:

$$
E_{max}=\frac{1}{2}LI_{sat}^2
=\frac{1}{2}\mathcal{R}\Phi_{max}^2
$$

So the gap lowers inductance per ampere but raises the ampere limit. Because energy depends on current squared, the energy ceiling rises. [source: Magnetic-Mechanical Analogy Ref. §9]

## Magnetic-Mechanical Analogy

The analogy has three useful levels:

| Level | Magnetic/electrical view | Mechanical view | Design use |
| --- | --- | --- | --- |
| Circuit terminals | $L$, $C$, $R$, voltage, current | mass, spring, damper, force, velocity | Converter dynamics and resonance. |
| Magnetic circuit | MMF, flux, reluctance | force, displacement, stiffness | Gap design, stored energy, saturation current. |
| Material | $H$, $B$, permeability | stress, strain, compliance | Saturation, energy density, material selection. |

At the electrical terminals, an inductor acts like inertia: it opposes current change. Inside the magnetic circuit, reluctance acts like spring stiffness: MMF pushes flux against reluctance. The winding connects these views because:

$$
v=N\frac{d\Phi}{dt}, \qquad \text{MMF}=NI
$$

This effort/flow swap is the reason a spring-like magnetic circuit presents as an inertial inductor at the electrical terminals. [source: Magnetic-Mechanical Analogy Ref. §2-§5]

## Self And Mutual Inductance

Self-inductance is flux linkage caused by a winding's own current:

$$
\lambda_1=L_1i_1
$$

Mutual inductance is flux linkage in one winding caused by current in another:

$$
\lambda_2=Mi_1
$$

For two coupled windings:

$$
M=k\sqrt{L_1L_2}
$$

where $0\le k\le1$. Leakage inductance is the portion of winding flux that does not couple into the other winding. A true transformer wants high useful coupling; a resonant or PSFB design may intentionally use part of the leakage inductance as a functional circuit element.

Stored magnetic energy for two coupled inductors is:

$$
W=\frac12L_1i_1^2+\frac12L_2i_2^2+Mi_1i_2
$$

with sign determined by dot convention. In an ideal transformer, equal and opposite ampere-turns cancel most core MMF under load, leaving magnetizing current as the current component that establishes mutual flux.

## Saturation

$B_{sat}$ is a measured material property, not a circuit equation. It falls with temperature, so designs should use the hot value. Typical first-pass ranges:

| Material family | Typical saturation range | Practical note |
| --- | --- | --- |
| MnZn power ferrite | About 0.25-0.5 T | Low core loss at high frequency, but hot $B_{sat}$ may be much lower than room-temperature data. |
| Powdered iron / metal composite | About 0.6-1.5 T depending material | Distributed gap and softer saturation; use DC-bias curves. |
| Silicon steel | About 1.5-2 T | Better suited to low-frequency and laminated-core applications. |
| Amorphous / nanocrystalline | About 1.2-1.6 T | High saturation with low loss in selected frequency ranges. |

When saturation occurs, incremental permeability collapses, inductance falls, and applied volt-seconds can drive a rapid current increase. That is why saturation checks use peak current and hot material data.

## B-H Loop Area

The area enclosed by a $B$-$H$ loop is energy per unit volume per cycle, not instantaneous power. Multiplying that energy by frequency gives hysteresis power density. This differs from a voltage-current plot, where $v i$ is instantaneous power. [source: Erickson & Maksimovic Ch. 10 eq. 10.55-10.56] [source: Magnetic-Mechanical Analogy Ref. §6]
