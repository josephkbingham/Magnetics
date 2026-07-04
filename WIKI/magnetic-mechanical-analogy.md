# Magnetic-Mechanical Analogy

## Scope

This page maps magnetic-circuit variables onto a mechanical spring-mass system at three distinct levels, connected by the coil acting as a gyrator. The analogy explains why an inductor behaves as inertia at its electrical terminals while its internal magnetic circuit behaves as a spring, why low-permeability material stores more energy per unit volume than high-permeability material, why an air gap lowers inductance yet raises energy-storage capability, and what happens physically at saturation. [source: Magnetic-Mechanical Analogy Ref. §1]

## GIC

### Geometry

A gapped magnetic core: core segment of length $\ell_c$, permeability $\mu = \mu_r\mu_0$, cross-section $A_e$, in series with an air gap of length $\ell_g$, wound with $N$ turns. [source: Magnetic-Mechanical Analogy Ref. §7] [source: Magnetic-Mechanical Analogy Ref. §10.3]

### Input

Winding current $i$ or applied volt-seconds, producing MMF $Ni$ and, via the coil's gyrator action ($v = N\,d\Phi/dt$, $\text{MMF} = Ni$), an inductance $L = N^2/\mathcal{R}$ seen at the electrical terminals. [source: Magnetic-Mechanical Analogy Ref. §5]

### Constraint

Flux density must stay below the material's saturation limit, $\Phi_{max} = B_{sat}A_e$, at the peak operating current. This wall is fixed by the core material and cross-section alone; it does not move when a gap is added. [source: Magnetic-Mechanical Analogy Ref. §8] [source: Magnetic-Mechanical Analogy Ref. §10.3]

## The Analogy Has Three Levels

A single spring analogy applied loosely produces a contradiction — an inductor appears to be both a mass and a spring. The contradiction is resolved by separating the analogy into three levels, connected by the coil acting as a gyrator:

| Level | Magnetic / electrical view | Mechanical view | What it governs |
| --- | --- | --- | --- |
| 1 — Circuit terminals | $L, C, R, v, i$ | mass, spring, damper, force, velocity | dynamics the converter sees (resonance, $di/dt$) |
| 2 — Magnetic circuit | MMF, $\Phi$, reluctance $\mathcal{R}$ | force, displacement, stiffness | energy storage, gap design, saturation current |
| 3 — Material | $B$, $H$, permeability $\mu$ | strain, stress, material softness | energy density, saturation flux density |

[source: Magnetic-Mechanical Analogy Ref. §2]

## Level 1 — Circuit Elements: the Inductor Is a Mass, Not a Spring

At the circuit terminals, the inductor is inertia for current: it opposes change in current, not current itself, exactly as a mass opposes change in velocity rather than velocity itself. The capacitor is the electrical element that behaves as a spring, storing energy in voltage ($\tfrac12 Cv^2$) as a spring stores energy in displacement ($\tfrac12 kx^2$). [source: Magnetic-Mechanical Analogy Ref. §3]

| Electrical quantity | Defining relation | Mechanical equivalent | Defining relation |
| --- | --- | --- | --- |
| Inductance $L$ (H) | $v = L\,di/dt$ | Mass $m$ (inertia) | $F = m\,dv/dt$ |
| Current $i$ (A) | — | Velocity $v$ (m/s) | — |
| Voltage $v$ (V) | — | Force $F$ (N) | — |
| Capacitance $C$ (F) | $i = C\,dv/dt$ | Spring compliance $1/k$ | $F = kx$ |
| Resistance $R$ ($\Omega$) | $v = iR$ | Damper (friction) $b$ | $F = bv$ |
| Inductor energy | $\tfrac12 Li^2$ | Kinetic energy | $\tfrac12 mv^2$ |
| Capacitor energy | $\tfrac12 Cv^2$ | Spring potential energy | $\tfrac12 kx^2$ |
| LC resonance | $\omega_0 = 1/\sqrt{LC}$ | Mass-spring resonance | $\omega_0 = \sqrt{k/m}$ |

[source: Magnetic-Mechanical Analogy Ref. §3]

An LC output filter that rings is, in this picture, an undamped mass-spring system; the damping resistor is the friction element added to bleed off the sloshing energy. [source: Magnetic-Mechanical Analogy Ref. §3]

## Level 2 — The Magnetic Circuit Is a Spring (Hopkinson &harr; Hooke)

Inside the inductor, the magnetic circuit obeys Hopkinson's law, $\text{MMF} = \mathcal{R}\Phi$, which is Hooke's law $F = kx$ with different symbols: ampere-turns are the force, flux is the displacement, and reluctance is the spring constant. [source: Magnetic-Mechanical Analogy Ref. §4]

| Magnetic quantity | Relation / units | Mechanical equivalent | Relation / units |
| --- | --- | --- | --- |
| MMF ($=Ni$) | A$\cdot$t | Force $F$ | N |
| Flux $\Phi$ | Wb | Displacement $x$ | m |
| Reluctance $\mathcal{R}$ | $\mathcal{R} = \ell/(\mu A)$ [A$\cdot$t/Wb] | Spring constant $k$ | N/m |
| Permeance $\mathcal{P} = 1/\mathcal{R}$ | Wb/A$\cdot$t | Compliance $1/k$ | m/N |
| Hopkinson's law | $\text{MMF} = \mathcal{R}\Phi$ | Hooke's law | $F = kx$ |
| Stored energy | $\tfrac12\mathcal{R}\Phi^2$ | Spring energy | $\tfrac12 kx^2$ |
| Reluctances in series (same $\Phi$, MMFs add) | $\mathcal{R}_{tot} = \mathcal{R}_{core} + \mathcal{R}_{gap}$ | Springs in parallel (same $x$, forces add) | $k_{tot} = k_1 + k_2$ |

[source: Magnetic-Mechanical Analogy Ref. §4]

Reluctance is not a resistance. $\mathcal{R} = \ell/(\mu A)$ mirrors $R = \ell/(\sigma A)$ in form, but resistance dissipates power while reluctance stores energy and returns it — the defining behavior of a spring. This is also why reluctances in series (one flux path through core and gap) correspond to springs in **parallel**: both springs are clamped to the same displacement $\Phi$, with their forces (MMF drops) adding. [source: Magnetic-Mechanical Analogy Ref. §4]

## The Gyrator — Why the Inductor Is a Spring Inside but a Mass Outside

The circuit and magnetic-circuit levels are reconciled by the coil's defining equations, $v = N\,d\Phi/dt$ and $\text{MMF} = Ni$. An element that swaps effort and flow across its port this way is a gyrator, and gyrators flip element types: a spring viewed through a gyrator presents as a mass. The compliance of the internal reluctance-spring, reflected through the $N$-turn gyrator, is exactly the inertia felt at the electrical terminals:

$$
L = N^2/\mathcal{R} = N^2\mathcal{P}
$$

This is the gyrator-capacitor model of magnetic circuits. It resolves the apparent contradiction directly: stiffening the internal spring (raising $\mathcal{R}$, e.g. by adding a gap) makes the mass felt at the terminals ($L$) lighter — both effects are the same physical change, seen from the two ports of the gyrator. [source: Magnetic-Mechanical Analogy Ref. §5]

### The Gyrator Is Not Specific to This Page

The gyrator-capacitor model is a named alternative (D.C. Hamill, 1993) to the older, more commonly taught resistance-reluctance analogy, which models Hopkinson's law ($\text{MMF}=\mathcal{R}\Phi$) directly on Ohm's law ($V=IR$) by treating reluctance as a resistor. That older analogy gets the static MMF/flux relationship right but is physically wrong about energy: a resistor dissipates power, while reluctance stores energy and returns it, so the resistance analogy cannot represent an inductor's dynamics or energy storage correctly. The gyrator-capacitor model fixes this by mapping permeance to a capacitor — which does store energy — coupled to the electrical side through a gyrator.

More generally, in electromechanical energy-domain modeling, every ideal two-port transducer between domains is one of exactly two types: a **transformer** (effort&harr;effort, flow&harr;flow — e.g. an ideal lever, a piezoelectric transducer, an ideal electrical transformer) or a **gyrator** (effort in one domain paired with flow in the other — e.g. a DC motor, a loudspeaker voice coil). A winding is a gyrator by this classification because $v=N\,d\Phi/dt$ ties electrical effort to magnetic flow-rate, while $\text{MMF}=Ni$ ties magnetic effort to electrical flow — the defining effort/flow swap of a gyrator, and the reason a spring on one side of it presents as a mass on the other.

## Level 3 — Material Level: Permeability Is Softness

Zooming into the material itself, the field quantities map onto stress and strain in a solid. Permeability plays the role of mechanical compliance: high-$\mu$ ferrite is soft rubber, air is stiff steel. [source: Magnetic-Mechanical Analogy Ref. §6]

| Magnetic (field) quantity | Relation / units | Mechanical equivalent | Relation / units |
| --- | --- | --- | --- |
| Flux density $B$ | T | Strain $\varepsilon$ | — |
| Field intensity $H$ | A/m | Stress $\sigma$ | Pa |
| Permeability $\mu = B/H$ | H/m | Compliance $1/E$ (softness) | 1/Pa ($E$ = Young's modulus) |
| High-$\mu$ ferrite ($\mu_r \approx 2000$-$5000$) | — | Soft rubber | — |
| Air, $\mu_0$ | — | Stiff steel | — |
| Energy density | $w = \tfrac12 BH = B^2/(2\mu)$ | Strain energy density | $w = \tfrac12\sigma\varepsilon = \tfrac12 E\varepsilon^2$ |

[source: Magnetic-Mechanical Analogy Ref. §6]

Strain $\varepsilon = \Delta L/L_0$ is fractional deformation: dimensionless, and a description of the material's local condition rather than the whole part's total displacement. $B$ plays the identical role on the magnetic side — $\Phi$ is the total displacement of the whole magnetic circuit, while $B = \Phi/A_e$ is that displacement with geometry divided out, the local per-unit-volume condition of the material. This is why saturation is specified by $B_{sat}$, a material property analogous to yield strain, rather than by any absolute flux value. [source: Magnetic-Mechanical Analogy Ref. §6]

At equal $B$ (equal strain), a low-$\mu$ material reaches that state under much higher $H$ (stress) than a high-$\mu$ material, so it stores far more energy density $w = \tfrac12 BH$. At equal $B$, air stores $\mu_r$ times more energy per unit volume than the core material — the field-level reason a geometrically tiny air gap holds nearly all of a gapped inductor's stored energy. [source: Magnetic-Mechanical Analogy Ref. §6]

### Why Area on the B-H Plane Is Energy, Not Power

On a $V$-$I$ plane, the product $VI$ is already power: both are instantaneous quantities, so no time integration is needed to form it, and getting energy from that plane requires an extra explicit step, $E=\int P\,dt$.

The $B$-$H$ plane does not work the same way, which is easy to miss because $B$ and $H$ look like another instantaneous pair. $H$ is effort-like and set instantaneously by current ($H\ell=Ni$), but $B$ is not instantaneous the way $V$ or $I$ are — it is an accumulated quantity, like displacement or charge. By Faraday's law, $v=N\,d\Phi/dt$, so reaching a given $B$ requires volt-seconds, $\Delta\Phi=\tfrac1N\int v\,dt$: every step along a $B$-$H$ trajectory has a finite elapsed time already built into it. Area on the $B$-$H$ plane, $w=\int H\,dB$, is therefore already an energy density — there is no further time integral left to take.

This matches the force/displacement framing of this table exactly: $H$ plays stress (force), $B$ plays strain (displacement), and area under a force-displacement curve is always work, $W=\int F\,dx$, never power. The same logic applies one level up, at the $\Phi$-versus-MMF plane (Level 2): area there is $\tfrac12\,\text{MMF}\cdot\Phi$, matching spring energy $\tfrac12kx^2=\tfrac12Fx$, for the identical reason.

## The Air Gap — A Stiff Spring in Parallel

Because core and gap carry the same flux (series reluctances), their spring equivalents sit in parallel, clamped to the same displacement $\Phi$, with forces (MMF) adding. With the core's $\mu_r$ in the thousands, even a fraction-of-a-millimeter gap contributes most of the total stiffness $\mathcal{R}$. At any given $\Phi$, each spring holds energy $\tfrac12 k_i\Phi^2$ in proportion to its stiffness, so the stiff gap spring carries nearly all the MMF and nearly all the energy: the core carries flux, the gap stores energy. [source: Magnetic-Mechanical Analogy Ref. §7]

At fixed current, adding a gap lowers $\Phi$, lowers $L$, and lowers stored energy together, since $E = \tfrac12(Ni)^2/\mathcal{R}$ falls as $\mathcal{R}$ rises. Nothing paradoxical happens at fixed current — the benefit of the gap appears only against the saturation constraint (see [Resolving the Gap Paradox](#resolving-the-gap-paradox) below). [source: Magnetic-Mechanical Analogy Ref. §7]

## Saturation — Coil Bind

Real coil springs exhibit coil bind: compressed far enough, the coils stack solid and incremental stiffness jumps by orders of magnitude. Saturation is coil bind. Below $B_{sat}$ the core is a soft spring with normal travel; beyond it, incremental permeability collapses toward $\mu_0$. [source: Magnetic-Mechanical Analogy Ref. §8]

| Magnetic phenomenon | Expression | Mechanical equivalent |
| --- | --- | --- |
| Saturation flux limit | $\Phi_{max} = B_{sat}A_e$ | Bind displacement $x_{max}$ — a hard wall |
| Below saturation | $\mu \approx \mu_r\mu_0$ | Soft spring, normal travel |
| Beyond saturation | incremental $\mu \to \mu_0$ | Coils stacked solid; incremental stiffness $\to$ steel |
| Saturation current $I_{sat}$ | MMF to reach $\Phi_{max}$: $NI_{sat} = \mathcal{R}\Phi_{max}$ | Force required to reach the bind wall |
| Maximum storable energy | $E_{max} = \tfrac12\mathcal{R}\Phi_{max}^2$ | Energy at the wall — scales with total stiffness |

[source: Magnetic-Mechanical Analogy Ref. §8]

The wall $\Phi_{max} = B_{sat}A_e$ belongs to the core material and cross-section alone; adding a gap in parallel does not move it, it only raises the ampere-turns needed to reach it (the saturation current). Because the wall is a fixed displacement, the maximum storable energy $E_{max} = \tfrac12\mathcal{R}\Phi_{max}^2$ scales directly with total stiffness $\mathcal{R}$ — a stiffer, gapped assembly stores more energy before bind even though its terminal inductance $L = N^2/\mathcal{R}$ is lower. [source: Magnetic-Mechanical Analogy Ref. §8]

At the moment of saturation, permeance $\mathcal{P}$ collapses by orders of magnitude and with it the terminal mass $L = N^2\mathcal{P}$; with volt-seconds still applied, a nearly massless object under sustained force accelerates violently. This is the field-level explanation for the sharp current spike observed at the peak of each cycle when an output choke or PFC inductor saturates. [source: Magnetic-Mechanical Analogy Ref. §8]

## Resolving the Gap Paradox

Three true statements appear to collide: (1) more permeable material stores less energy; (2) raising reluctance lowers inductance and, at fixed current, lowers stored energy; (3) adding a gap — which raises reluctance and lowers $L$ — increases the energy an inductor can store. Each statement holds a different quantity constant: [source: Magnetic-Mechanical Analogy Ref. §9]

| Statement | Held constant | Governing relation |
| --- | --- | --- |
| (1) More permeable $\to$ less energy stored | comparing materials at the same $B$ | $w = B^2/(2\mu)$ — the high-$\mu$ material reaches that $B$ with almost no $H$, so $w$ is tiny |
| (2) Higher $\mathcal{R}$ $\to$ lower $L$ $\to$ less energy | same inductor, same current | $E = \tfrac12(Ni)^2/\mathcal{R}$ — gapping at fixed current stores less energy; no paradox at fixed current |
| (3) Gap $\to$ more storable energy | operating at the saturation limit, where real designs live | $E_{max} = \tfrac12\mathcal{R}\Phi_{max}^2$ — grows linearly with $\mathcal{R}$ |

[source: Magnetic-Mechanical Analogy Ref. §9]

Statements (2) and (3) are reconciled through the saturation current: $\Phi_{max} = B_{sat}A_e$ is fixed by the core alone, and the ampere-turns needed to reach it scale with stiffness, $NI_{sat} = \mathcal{R}\Phi_{max}$. Substituting into $E_{max} = \tfrac12 LI_{sat}^2$:

$$
E_{max} = \tfrac12 L I_{sat}^2 = \tfrac12 \left(\frac{N^2}{\mathcal{R}}\right)\left(\frac{\mathcal{R}\Phi_{max}}{N}\right)^2 = \tfrac12\mathcal{R}\Phi_{max}^2
$$

$L$ falls linearly with $\mathcal{R}$, but $I_{sat}^2$ rises quadratically, so the energy ceiling grows linearly with $\mathcal{R}$. [source: Magnetic-Mechanical Analogy Ref. §9]

For a $10\times$ reluctance increase:

| Quantity | Ungapped core | Gapped core ($\mathcal{R}\times 10$) |
| --- | --- | --- |
| Inductance $L = N^2/\mathcal{R}$ | $L_0$ | $L_0/10$ |
| Saturation current $I_{sat} = \mathcal{R}\Phi_{max}/N$ | $I_0$ | $10\,I_0$ |
| Energy ceiling $E_{max} = \tfrac12 L I_{sat}^2$ | $\tfrac12 L_0 I_0^2$ | $\tfrac12(L_0/10)(10I_0)^2 = 10\times$ more |

[source: Magnetic-Mechanical Analogy Ref. §9]

The gap lowers energy stored per ampere (lower $L$) but raises the amperes permitted ($I_{sat}$) by the same factor; because energy goes as current squared, the ceiling rises. Statement (1) locates where the extra energy physically resides: at $B_{sat}$ the gap volume, sitting at $\mu_0$, holds orders of magnitude more energy density than the ferrite at the same $B$, so the enlarged ceiling resides almost entirely in the gap. [source: Magnetic-Mechanical Analogy Ref. §9]

## From Current to B — Working Equations

### What $B_{sat}$ Is (and Is Not)

There is no equation for $B_{sat}$ in terms of circuit quantities — it is a measured material property, the magnetic analog of yield strain, taken from a datasheet rather than derived. Its physical origin is $B = \mu_0(H+M)$, where $M$ is the material's magnetization. Below saturation, increasing $H$ grows $M$ rapidly (the steep slope is the high $\mu$); once every magnetic domain is aligned, $M$ hits its ceiling, the saturation magnetization $M_s$, and $B_{sat} \approx \mu_0 M_s$. Beyond that point $B$ still grows with $H$, but only at slope $\mu_0$. $M_s$ is fixed by atomic physics and falls with temperature, so designs must be checked against the hot value rather than the 25 &deg;C datasheet number. [source: Magnetic-Mechanical Analogy Ref. §10.1]

| Core material | Typical $B_{sat}$ (25 &deg;C) | Note |
| --- | --- | --- |
| MnZn power ferrite (3C95, N87) | 0.4-0.5 T | $\approx$ 0.35-0.4 T at 100 &deg;C — design to the hot value |
| Powdered iron / sendust | 1.0-1.5 T | soft (gradual) saturation — distributed gap |
| Silicon steel | 1.5-2.0 T | line-frequency magnetics |
| Amorphous / nanocrystalline | 1.2-1.56 T | high $B_{sat}$ with low loss |

[source: Magnetic-Mechanical Analogy Ref. §10.1]

These ranges are consistent with, and refine, the broader material ranges already given in [Electromagnetic Fundamentals](./electromagnetic-fundamentals.md) (1-2 T iron/silicon steel, 0.5-1 T powdered iron, 0.25-0.5 T ferrite). [source: Erickson & Maksimovic Ch. 10 discussion following Fig. 10.6] [source: Magnetic-Mechanical Analogy Ref. §10.1]

### The Four Equations for $B$ in an Inductor

All four forms express the same physics through different known quantities; forms (1) and (2) are identical once $L = N^2/\mathcal{R}$ is substituted. [source: Magnetic-Mechanical Analogy Ref. §10.2]

| # | Equation | Comes from | Use when |
| --- | --- | --- | --- |
| (1) | $B = LI/(NA_e)$ | flux linkage $N\Phi = LI$; $B=\Phi/A_e$ | design check with known $L$, turns, core; use peak current ($I_{dc}+\Delta I/2$) |
| (2) | $B = NI/(\mathcal{R}A_e)$ | Hopkinson: $\Phi = \text{MMF}/\mathcal{R}$ | magnetic-circuit view — force over stiffness, per unit area |
| (3) | $B \approx \mu_0 NI/\ell_g$ | gap-dominated: $\mathcal{R}\approx \ell_g/(\mu_0 A_e)$ | quick saturation check; shows gap length is the primary knob |
| (4) | $B_{pk} = V\Delta t/(NA_e)$; sine: $B_{pk} = V_{rms}/(4.44fNA_e)$ | Faraday $v = N\,d\Phi/dt$ integrated: flux = volt-seconds per turn | AC flux swing $\Delta B$ for core loss; transformers — $B$ set by volts, not load current |

[source: Magnetic-Mechanical Analogy Ref. §10.2]

For an energy-storage inductor, check form (1) or (3) against peak current for saturation, and use form (4) for the swing $\Delta B$ that feeds a Steinmetz core-loss calculation. For a transformer, form (4) against the applied volt-seconds sets $B$, and it is the magnetizing current — not the load current — that saturates it. [source: Magnetic-Mechanical Analogy Ref. §10.2]

### How the Gap Lowers B — the Mechanism

The gap does not raise $B_{sat}$; the wall is a material property and never moves. What the gap does is lower the $B$ obtained per ampere, so more amperes fit before $B$ reaches the same unchanged wall. From Ampere's law around the flux path, total ampere-turns divide between core and gap:

$$
NI = H_{core}\ell_c + H_{gap}\ell_g
$$

Flux is continuous through the series path, so $B$ is identical in core and gap, but the $H$ required to sustain that $B$ differs enormously ($H = B/\mu$ is tiny in the core, large in the gap). Substituting and solving for $B$:

$$
B = \frac{\mu_0 NI}{\ell_c/\mu_r + \ell_g}
$$

[source: Magnetic-Mechanical Analogy Ref. §10.3]

The denominator is the effective magnetic length of the path: the core contributes only its physical length divided by $\mu_r$. A 100 mm ferrite path at $\mu_r=2500$ contributes just 0.04 mm; adding a 1 mm physical gap takes the denominator to 1.04 mm, a 26x increase — equivalently, a 1 mm air gap is magnetically equivalent to inserting 2.5 m of extra ferrite into the path. [source: Magnetic-Mechanical Analogy Ref. §10.3]

| Quantity (fixed $NI=100$ A$\cdot$t; $\ell_c=100$ mm, $\mu_r=2500$) | Ungapped core | 1 mm gap |
| --- | --- | --- |
| Effective magnetic length $\ell_c/\mu_r + \ell_g$ | 0.04 mm | 1.04 mm (26x longer) |
| Flux density $B = \mu_0 NI/(\ell_c/\mu_r+\ell_g)$ | 3.1 T — saturates hard | 0.12 T — comfortable |
| $NI$ allowed before $B=0.4$ T | $\approx 13$ A$\cdot$t | $\approx 330$ A$\cdot$t |

[source: Magnetic-Mechanical Analogy Ref. §10.3]

At any operating $B$, the gap consumes almost all the ampere-turns; the core sits near the bottom of its $B$-$H$ curve while the gap does the work. A practical consequence: when the gap owns roughly 96% of total reluctance, a $\pm25\%$ swing in the core's $\mu_r$ (tolerance, temperature) moves $L$ by only about 1% — gapped designs are stable against core-material variation even when energy storage is not the driver. [source: Magnetic-Mechanical Analogy Ref. §10.3]

## Tradeoffs

Gapping trades terminal inductance for saturation-current headroom: $L$ falls linearly with $\mathcal{R}$ while $I_{sat}$ rises linearly with $\mathcal{R}$, so the energy ceiling $E_{max}=\tfrac12\mathcal{R}\Phi_{max}^2$ rises linearly with $\mathcal{R}$ (∂$E_{max}$/∂$\mathcal{R}$ > 0) — see the [10x-reluctance worked comparison](#resolving-the-gap-paradox) above. The constraint that forces this tradeoff is the fixed saturation wall $\Phi_{max}=B_{sat}A_e$, set by core material and cross-section alone. [source: Magnetic-Mechanical Analogy Ref. §9]

Inductor design is therefore a two-knob loop, and the two knobs are nearly orthogonal, which is what makes the loop converge: the gap sets saturation headroom ($\mathcal{R}$ up $\to$ $I_{sat}$ up, since $NI_{sat}=\mathcal{R}\Phi_{max}$), and the turns restore the inductance target ($L=N^2/\mathcal{R}$, so an increase in $\mathcal{R}$ is compensated by $N^2$). The closing checks are the same physical limits found in the [Inductor Design Inputs](./inductor-design-inputs.md) checklist: flux density $B=LI/(NA_e) < B_{sat}$ at peak current, window fill and copper loss for the added turns, and core loss for the resulting flux swing. [source: Magnetic-Mechanical Analogy Ref. §11]

## Master Variable Map

Consolidated reference — every variable across the three levels:

| Magnetic / electrical | Symbol $\cdot$ units | Mechanical equivalent | Symbol $\cdot$ units | Notes |
| --- | --- | --- | --- | --- |
| Inductance | $L \cdot$ H | Mass (inertia) | $m \cdot$ kg | inertia for current; $L=N^2/\mathcal{R}$ |
| Current | $i \cdot$ A | Velocity | $v \cdot$ m/s | circuit-level flow |
| Voltage | $v \cdot$ V | Force | $F \cdot$ N | circuit-level effort |
| Capacitance | $C \cdot$ F | Spring compliance | $1/k$ | the true circuit-level spring |
| Resistance | $R \cdot \Omega$ | Damper (friction) | $b$ | dissipates; $\mathcal{R}$ does not |
| Magnetomotive force | $\text{MMF}=Ni \cdot$ A$\cdot$t | Force | $F \cdot$ N | magnetic-level effort |
| Flux | $\Phi \cdot$ Wb | Displacement | $x \cdot$ m | magnetic-level position |
| Flux linkage | $N\Phi \cdot$ Wb$\cdot$t | — | — | defines $L=N\Phi/i$ |
| Reluctance | $\mathcal{R}=\ell/(\mu A) \cdot$ A$\cdot$t/Wb | Spring constant | $k \cdot$ N/m | stores energy — not a resistance |
| Permeance | $\mathcal{P}=1/\mathcal{R}$ | Compliance | $1/k$ | $L=N^2\mathcal{P}$ |
| Turns | $N$ | Gyrator ratio | — | flips spring $\leftrightarrow$ mass across domains |
| Flux density | $B \cdot$ T | Strain | $\varepsilon$ | material-level displacement |
| Field intensity | $H \cdot$ A/m | Stress | $\sigma \cdot$ Pa | material-level force |
| Permeability | $\mu=B/H \cdot$ H/m | Softness (compliance) | $1/E$ | high $\mu$ = rubber; air = steel |
| Saturation limit | $\Phi_{max}=B_{sat}A_e$ | Coil-bind wall | $x_{max}$ | property of core alone; gap can't move it |
| Stored energy | $\tfrac12 LI^2=\tfrac12\mathcal{R}\Phi^2$ | $\tfrac12 mv^2=\tfrac12 kx^2$ | — | same number, two viewpoints |
| Energy density | $B^2/(2\mu)$ | $\tfrac12\sigma\varepsilon=\tfrac12 E\varepsilon^2$ | — | low $\mu$ (air) stores more at equal $B$ |

[source: Magnetic-Mechanical Analogy Ref. §12]

## Related Pages

- [Electromagnetic Fundamentals](./electromagnetic-fundamentals.md)
- [Air Gap And Saturation](./air-gap-and-saturation.md)
- [Core Materials And Losses](./core-materials-and-losses.md)
- [Equation Reference](./equation-reference.md)
- [Inductor Design Inputs](./inductor-design-inputs.md)
- [Index](./index.md)
