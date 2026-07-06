# Self And Mutual Inductance Analogy

## Scope

This page explains self-inductance, mutual inductance, coupling coefficient, leakage flux, and coupled-coil energy using a water-wheel analogy. It is a conceptual companion to the [Magnetic-Mechanical Analogy](./magnetic-mechanical-analogy.md) and the transformer equations in [Practical Transformer Model](./practical-transformer-model.md). [source: User note 2026-07-05]

## The Analogy: Water Wheels In A Shared Stream

Self-inductance is like the flywheel effect of a heavy water wheel. Push water through a pipe that spins a massive wheel: the wheel resists changes in flow. It does not oppose steady flow at all; once spinning, water passes freely. But try to speed the flow up and the wheel pushes back. Try to stop the flow suddenly and the wheel keeps shoving water forward; that is the inductive kick. Current is the water flow, voltage is the pressure required to change it, and inductance $L$ is the heaviness of the wheel. [source: User note 2026-07-05]

Mutual inductance is what happens when a second wheel sits in the same stream, linked to the first by a belt. Whenever the flow on side 1 changes, the belt drags wheel 2 and generates pressure, or voltage, in circuit 2 even though no water crosses between the two pipes. That is a transformer: energy is coupled through the shared belt, representing magnetic flux in the core, not through an electrical connection. [source: User note 2026-07-05]

The belt can slip. A tight belt is a high coupling coefficient, $k \to 1$, like a good transformer on an ungapped core. A loose belt is weak coupling, $k \ll 1$, like two coils far apart in air. The slippage is leakage flux: flux from one coil that never links the other. [source: User note 2026-07-05]

## Self-Inductance

Self-inductance relates a coil's own flux linkage to its own current:

$$
\lambda = N\Phi = Li
$$

so

$$
L = \frac{N\Phi}{i} = \frac{N^2}{\mathcal{R}} = A_L N^2
$$

where $\mathcal{R}$ is the magnetic-circuit reluctance. This is why gapping the core, which raises $\mathcal{R}$, lowers $L$, as shown in the [buck gapped-core worked example](./worked-example-buck-gapped-core.md). [source: User note 2026-07-05] [source: Erickson & Maksimovic Ch. 10 eq. 10.31]

The terminal voltage is

$$
v = \frac{d\lambda}{dt} = L\frac{di}{dt}
$$

for a linear inductor with constant $L$. [source: User note 2026-07-05]

## Mutual Inductance

Mutual inductance $M$ relates the flux linkage in coil 2 caused by current in coil 1, and vice versa. For a reciprocal magnetic structure,

$$
M_{12} = M_{21} = M
$$

and, for the shared flux path,

$$
M = \frac{N_2\Phi_{21}}{i_1} = \frac{N_1\Phi_{12}}{i_2} = \frac{N_1N_2}{\mathcal{R}}
$$

in the ideal fully linked case. [source: User note 2026-07-05]

The coupled-coil terminal equations show that each coil's voltage responds to both current derivatives:

$$
v_1 = L_1\frac{di_1}{dt} + M\frac{di_2}{dt}
$$

$$
v_2 = M\frac{di_1}{dt} + L_2\frac{di_2}{dt}
$$

The sign of the $M$ terms follows the dot convention: currents entering both dotted terminals make the mutual terms add. [source: User note 2026-07-05] [source: Hurley & Wolfle Ch. 4 eq. 4.39-4.40]

## Coupling Coefficient And Leakage

The coupling coefficient measures how tightly the two windings share flux:

$$
k = \frac{M}{\sqrt{L_1L_2}}, \qquad 0 \le k \le 1
$$

$k = 1$ means every line of flux links both windings, the ideal-transformer limit. The shortfall shows up as leakage inductance. In a simple symmetric split,

$$
L_{\ell 1} = L_1(1-k)
$$

which is the portion of winding 1's inductance associated with flux that does not link winding 2. [source: User note 2026-07-05] [source: Hurley & Wolfle Ch. 4 eq. 4.50-4.51]

## Stored Energy

The stored energy in the coupled pair is

$$
W = \tfrac{1}{2}L_1 i_1^2 + \tfrac{1}{2}L_2 i_2^2 + M i_1 i_2
$$

with the sign of the mutual term again set by the dot convention and current reference directions. The requirement $W \ge 0$ for all current combinations is what forces

$$
M \le \sqrt{L_1L_2}
$$

or equivalently $k \le 1$. [source: User note 2026-07-05]

## Ideal Transformer Consequence

For two windings on a shared core with perfect coupling,

$$
L_1 = \frac{N_1^2}{\mathcal{R}}
$$

and

$$
L_2 = \frac{N_2^2}{\mathcal{R}}
$$

so

$$
M = \frac{N_1N_2}{\mathcal{R}} = \sqrt{L_1L_2}
$$

The voltage ratio then collapses to

$$
\frac{v_2}{v_1} = \frac{N_2}{N_1}
$$

which is the ideal transformer equation falling directly out of the mutual-inductance formalism. [source: User note 2026-07-05]

## Related Pages

- [Magnetic-Mechanical Analogy](./magnetic-mechanical-analogy.md)
- [Practical Transformer Model](./practical-transformer-model.md)
- [Coupled Filter Inductors](./coupled-filter-inductors.md)
- [Equation Reference](./equation-reference.md)
- [Index](./index.md)
