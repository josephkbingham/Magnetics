# THE MAGNETIC–MECHANICAL ANALOGY
*Inductance, Reluctance, Permeability, Air Gaps, and Saturation — Mapped to Springs and Masses*
Engineering Reference Document
July 2026  ·  Rev A
## 1.  Purpose and Scope
This document consolidates the complete mapping between magnetic-circuit variables and their mechanical (spring–mass) equivalents. The analogy is a working tool for inductor and transformer design: it explains, in one consistent mechanical picture, why inductors resist changes in current, why low-permeability material stores more energy per unit volume than high-permeability material, why an air gap lowers inductance yet raises energy-storage capability, and what actually happens at saturation. The mapping is developed at three levels, from the circuit terminals down to the material itself, and closes with the design loop used for gap and turns selection (the same loop a magnetics design tool such as a PyOpenMagnetics-based application must solve).
## 2.  The Analogy Has Three Levels
A single spring analogy applied loosely produces contradictions (an inductor appears to be both a mass and a spring). The contradictions disappear once the analogy is organized into three distinct levels, connected by the coil acting as a gyrator. Each level maps a different pair of variables:
| Level | Magnetic / electrical view | Mechanical view | What it governs |
| --- | --- | --- | --- |
| 1 — Circuit terminals | L, C, R, v, i | mass, spring, damper, force, velocity | dynamics the converter sees (resonance, di/dt) |
| 2 — Magnetic circuit | MMF, Φ, reluctance ℛ | force, displacement, stiffness | energy storage, gap design, saturation current |
| 3 — Material | B, H, permeability μ | strain, stress, material softness | energy density, saturation flux density |


## 3.  Level 1 — Circuit Elements: the Inductor Is a Mass, Not a Spring
At the circuit level, the inductor is inertia for current. It does not oppose current; it opposes change in current, exactly as a mass opposes change in velocity, not velocity itself. A spring stores energy in displacement (½kx²) — the electrical element that does that is the capacitor, which stores energy in voltage (½Cv²). This is why an LC tank rings at ω₀ = 1/√(LC) with precisely the mathematics of a mass–spring oscillator at ω₀ = √(k/m): energy sloshes between the “kinetic” form (inductor current) and the “potential” form (capacitor voltage).
| Electrical quantity | Defining relation | Mechanical equivalent | Defining relation |
| --- | --- | --- | --- |
| Inductance L  (H) | v = L · di/dt | Mass m  (inertia) | F = m · dv/dt |
| Current i  (A) | — | Velocity v  (m/s) | — |
| Voltage v  (V) | — | Force F  (N) | — |
| Capacitance C  (F) | i = C · dv/dt | Spring compliance  1/k | F = k · x |
| Resistance R  (Ω) | v = iR | Damper (friction) b | F = b · v |
| Inductor energy | ½ Li2 | Kinetic energy | ½ mv2 |
| Capacitor energy | ½ Cv2 | Spring potential energy | ½ kx2 |
| LC resonance | ω₀ = 1/√(LC) | Mass–spring resonance | ω₀ = √(k/m) |


Figure 1 — Circuit-level duality. The LC tank and the mass–spring oscillator obey identical equations; L plays the role of mass, C the role of spring compliance.
A practical consequence of this row of the map: an LC output filter that rings (for example, a resonance near 2.3 kHz excited by a clipped load-current waveform) is a mass–spring system oscillating undamped; the damping resistor is the friction element added to bleed off the sloshing energy.
## 4.  Level 2 — The Magnetic Circuit Is a Spring (Hopkinson ↔ Hooke)
Inside the inductor, the magnetic circuit obeys Hopkinson’s law, MMF = ℛΦ, which is Hooke’s law F = kx with different symbols. Ampere-turns are the force, flux is the displacement, and reluctance is the spring constant.
| Magnetic quantity | Relation / units | Mechanical equivalent | Relation / units |
| --- | --- | --- | --- |
| MMF  (= Ni) | A·t | Force F | N |
| Flux Φ | Wb | Displacement x | m |
| Reluctance ℛ | ℛ = l / (μA)   [A·t/Wb] | Spring constant k | N/m |
| Permeance 𝒫 = 1/ℛ | Wb/A·t | Compliance  1/k | m/N |
| Hopkinson’s law | MMF = ℛ · Φ | Hooke’s law | F = k · x |
| Stored energy | ½ ℛ Φ2 | Spring energy | ½ k x2 |
| Reluctances in series (same Φ, MMFs add) | ℛtot = ℛcore + ℛgap | Springs in parallel (same x, forces add) | ktot = k1 + k2 |


| Reluctance is not a resistance. The resistance analogy (ℛ = l/μA mirrors R = l/σA) is useful for computing flux, but it is misleading about energy: resistance dissipates power, whereas reluctance dissipates nothing. Reluctance stores energy and returns it — the defining behavior of a spring. Note also the series/parallel inversion: reluctances in series (one flux path through core and gap) correspond to springs in parallel — both springs clamped to the same displacement Φ, with their forces (MMF drops) adding. |
| --- |


## 5.  The Gyrator — Why the Inductor Is a Spring Inside but a Mass Outside
The two levels are reconciled by the coil’s defining equations:  v = N dΦ/dt   and   MMF = Ni.  Note the cross-coupling: the electrical effort (voltage) ties to the magnetic flow (rate of change of flux), while the magnetic effort (MMF) ties to the electrical flow (current). An element that swaps effort and flow across its port is a gyrator — and gyrators flip element types. A spring viewed through a gyrator presents as a mass. The compliance of the internal reluctance-spring, reflected through the N-turn gyrator, is exactly the inertia felt at the electrical terminals:
L = N2 / ℛ = N2 · 𝒫
This is the gyrator–capacitor model of magnetic circuits. It explains the apparent contradiction directly: stiffen the internal spring (raise ℛ, e.g. by adding a gap) and the mass felt at the terminals (L) gets lighter. Both effects come from the same physical change, seen from the two ports of the gyrator.

Figure 2 — Gyrator–spring model of a gapped inductor. The N-turn coil is a gyrator between the electrical domain (which feels a mass, L) and the magnetic domain (a soft core spring and a stiff gap spring in parallel, sharing displacement Φ, with a hard bind wall at Φmax = Bsat·Ae).
## 6.  Level 3 — Material Level: Permeability Is Softness
Zooming from lumped springs into the material itself, the field quantities map onto stress and strain in a solid. Permeability plays the role of mechanical compliance (softness): high-μ ferrite is soft rubber, air is stiff steel.
| Magnetic (field) quantity | Relation / units | Mechanical equivalent | Relation / units |
| --- | --- | --- | --- |
| Flux density B | T | Strain ε | — |
| Field intensity H | A/m | Stress σ | Pa |
| Permeability μ = B/H | H/m | Compliance  1/E  (softness) | 1/Pa   (E = Young’s modulus) |
| High-μ ferrite (μᵣ ≈ 2000–5000) | — | Soft rubber | — |
| Air, μ0 | — | Stiff steel | — |
| Energy density | w = ½BH = B2/(2μ) | Strain energy density | w = ½σε = ½Eε2 |


### What strain actually means (and why it maps to B)
Strain is fractional deformation — how much a material has stretched or compressed relative to its original size:  ε = ΔL / L0.  Pull a 100 mm rod until it is 100.1 mm long and the strain is 0.1/100 = 0.001 (0.1%, or 1000 microstrain). No force appears in the definition — strain is pure geometry.
It is dimensionless by design: meters divided by meters, which removes the size of the part from the picture. Under the same stress, a 1 m rod and a 10 m rod of the same steel stretch by different total millimeters but experience the same strain — the material at any point inside both is in the identical physical condition. Strain describes what the material experiences locally; total displacement describes what the part does. It is also the response, not the cause: stress σ is what is applied, strain is how the material answers, and the material’s stiffness connects them (σ = Eε). At the atomic level, strain is the lattice bonds pulled slightly off their equilibrium spacing; each stretched bond stores energy like a microscopic spring — which is why strain energy density is ½σε = ½Eε2, and why the material springs back when released (below yield).
This is exactly the role B plays on the magnetic side. Φ is the total displacement of the whole magnetic circuit; B = Φ/Ae is that displacement with the geometry divided out — the local, per-unit-volume condition of the material itself. That is why saturation is specified by Bsat (a material condition, exactly like a yield strain) rather than by any absolute flux: the wall belongs to the material, regardless of how large the core is.
Why large μ means small energy density.  Compare rubber and steel stretched to the same strain (the same B). The rubber reaches that strain under almost zero stress, so its stored energy ½σε is nearly nothing; the steel requires enormous stress to reach the same strain and therefore stores far more. Energy is force × displacement, and the soft (high-μ) material is missing the force. At equal B, air stores μᵣ times more energy per unit volume than the core material. This is the field-level reason the air gap — a geometrically tiny volume — holds nearly all of a gapped inductor’s stored energy.
## 7.  The Air Gap — A Stiff Spring in Parallel
In the flux path, the gap is a short segment of “steel” inserted into a long piece of “rubber.” Because core and gap carry the same flux (series reluctances), their spring equivalents sit in parallel: two springs clamped to the same displacement Φ, forces adding. With μᵣ of the core in the thousands, even a fraction-of-a-millimeter gap contributes most of the total stiffness ℛ. At any given Φ, each spring holds energy ½kᵢΦ² in proportion to its stiffness — so the stiff gap spring carries nearly all the MMF and nearly all the energy. The soft core spring’s entire job is to be mechanically invisible: it guides the displacement (routes the flux) where it is wanted while contributing almost no force. In one sentence: the core carries flux; the gap stores energy.
An important subtlety at fixed current:  adding a gap at the same current lowers Φ, lowers L, and lowers stored energy together (E = ½(Ni)²/ℛ falls as ℛ rises). Nothing paradoxical happens at fixed current. The benefit of the gap appears only against the real design constraint — saturation — covered next.
## 8.  Saturation — Coil Bind
Real coil springs have a failure mode called coil bind: compressed far enough, the coils stack solid and the incremental stiffness jumps by orders of magnitude. Saturation is coil bind. Below Bsat the core is soft, normal travel; beyond it, the incremental permeability collapses toward μ0 — the rubber suddenly behaves like steel.
| Magnetic phenomenon | Expression | Mechanical equivalent |
| --- | --- | --- |
| Saturation flux limit | Φmax = Bsat · Ae | Bind displacement xmax — a hard wall |
| Below saturation | μ ≈ μrμ0 | Soft spring, normal travel |
| Beyond saturation | incremental μ → μ0 | Coils stacked solid; incremental stiffness → steel |
| Saturation current Isat | MMF to reach Φmax:   NIsat = ℛ Φmax | Force required to reach the bind wall |
| Maximum storable energy | Emax = ½ ℛ Φmax2 | Energy at the wall — scales with total stiffness |


Two facts make the whole gap story fall into place. First, the wall belongs to the core alone: Φmax = BsatAe is fixed by material and cross-section, and adding the stiff gap spring in parallel does not move it a millimeter — it only raises the force (ampere-turns) needed to reach it. That is the saturation current going up. Second, because the wall is a fixed displacement, the energy that can be stored before hitting it, Emax = ½ℛΦmax2, scales directly with total stiffness ℛ. A stiffer (gapped) assembly crams in more energy before bind — even though its terminal inductance L = N²/ℛ went down.

Figure 3 — Force–displacement (MMF–Φ) view of saturation. Both springs bind at the same wall Φmax; the stiffer gapped spring needs far more force (Ni) to reach it, and the shaded area — stored energy — is correspondingly larger.
What the electrical port feels at bind.  At saturation the inner spring stiffens by orders of magnitude, so permeance 𝒫 collapses and with it the terminal mass L = N²𝒫. With volt-seconds still applied, a nearly massless object under sustained force accelerates violently: di/dt runs away. This is the familiar sharp current spike at the peak of each cycle when an output choke or PFC inductor saturates — the current is not misbehaving; the flywheel vanished mid-push.
## 9.  Resolving the Gap Paradox — Three True Statements, Three Different Questions
Three true statements appear to collide:  (1) the more permeable a material, the less energy it stores;  (2) raising reluctance lowers inductance, and at a given current, lowers stored energy;  (3) adding an air gap — which raises reluctance and lowers L — increases the energy an inductor can store. The collision is only apparent. Each statement answers a different question, distinguished by what is silently held constant:
| Statement | True when… (what is held constant) | Governing relation |
| --- | --- | --- |
| (1)  “More permeable → less energy stored” | comparing materials at the same B | w = B2/(2μ) — the high-μ material reached that B with almost no H (no force), so ½BH is tiny |
| (2)  “Higher ℛ → lower L → less energy” | same inductor, same current | E = ½(Ni)2/ℛ — gapping at fixed current stores less energy, not more; no paradox exists at fixed current |
| (3)  “Gap → more storable energy” | operating at the saturation limit — where real designs live | Emax = ½ ℛ Φmax2 — grows linearly with ℛ |


Statements (2) and (3) are reconciled through the saturation current. The wall Φmax = BsatAe is fixed by the core alone; the ampere-turns needed to reach it scale with stiffness, NIsat = ℛ Φmax. Gapping therefore trades inductance for current headroom:
Emax = ½ L Isat2  =  ½ (N2/ℛ) · (ℛ Φmax/N)2  =  ½ ℛ Φmax2
L falls linearly with ℛ, but Isat2 rises quadratically — the square wins, so the energy ceiling grows linearly with ℛ. A worked comparison for a 10× reluctance increase:
| Quantity | Ungapped core | Gapped core (ℛ × 10) |
| --- | --- | --- |
| Inductance   L = N2/ℛ | L0 | L0 / 10 |
| Saturation current   Isat = ℛΦmax/N | I0 | 10 · I0 |
| Energy ceiling   Emax = ½L·Isat2 | ½ L0I02 | ½ (L0/10)(10I0)2  =  10× more |


In one sentence:  the gap lowers the energy stored per ampere (lower L) but raises the number of amperes permitted (higher Isat) by the same factor — and because energy goes as current squared, the ceiling rises. In the spring picture: the stiffer spring stores less energy per unit of force, but allows far more force before hitting the same bind wall, and force² wins. Statement (1) then locates the winnings: at Bsat the gap volume, at μ0, holds thousands of times the energy density of the ferrite at the same B, so the enlarged ceiling physically resides almost entirely in the gap.
## 10.  From Current to B — The Working Equations
This section captures the full computational chain — current → MMF → flux → flux density → check against Bsat — with every equation needed to follow it later.
### 10.1  What Bsat is (and is not)
There is no equation for Bsat in terms of circuit quantities.  It is a measured material property — the analog of yield strain — taken from the material datasheet, not derived. Its physical origin: flux density in a magnetic material is
B = μ0 (H + M)
where M is the material’s magnetization — the alignment of its internal magnetic domains. Below saturation, increasing H flips and rotates domains, so M grows rapidly and B climbs steeply (that steep slope is the high μ). Once every domain is aligned, M hits its ceiling — the saturation magnetization Ms — and there is nothing left to align:
Bsat  ≈  μ0 Ms
Beyond that point B still grows with H, but only at the slope μ0 — the coils-stacked-solid regime. Ms is set by atomic physics (magnetic moment per atom × atoms per unit volume), which is why it is fixed by material chemistry. It falls with temperature (thermal scrambling of domains) and vanishes at the Curie temperature — so designs are checked against the hot value, not the 25 °C datasheet number.
| Core material | Typical Bsat (25 °C) | Note |
| --- | --- | --- |
| MnZn power ferrite (3C95, N87) | 0.4–0.5 T | ≈ 0.35–0.4 T at 100 °C — design to the hot value |
| Powdered iron / sendust | 1.0–1.5 T | soft (gradual) saturation — distributed gap |
| Silicon steel | 1.5–2.0 T | line-frequency magnetics |
| Amorphous / nanocrystalline | 1.2–1.56 T | high Bsat with low loss |


### 10.2  The four equations for B in an inductor
All are the same physics through different known quantities. Forms (1) and (2) are literally identical — substitute L = N2/ℛ into one and the other falls out.
| # | Equation | Comes from | Use when |
| --- | --- | --- | --- |
| (1) | B = LI / (NAe) | flux linkage NΦ = LI;  B = Φ/Ae | the design check: known L, turns, core; use peak current (Idc + ΔI/2) |
| (2) | B = NI / (ℛ Ae) | Hopkinson: Φ = MMF/ℛ | magnetic-circuit view — force over stiffness, per unit area |
| (3) | B ≈ μ0NI / lg | gap-dominated: ℛ ≈ lg/(μ0Ae) | quick saturation check; shows gap length is the primary knob |
| (4) | Bpk = V·Δt/(NAe);   sine: Bpk = Vrms/(4.44 fNAe) | Faraday v = N dΦ/dt, integrated: flux = volt·seconds per turn | AC flux swing ΔB (core loss); transformers — B set by volts, not load current |


| Which one, when:  for an energy-storage inductor, check form (1) or (3) against peak current for saturation, and use form (4) for the swing ΔB that feeds the core-loss (Steinmetz) calculation. For a transformer, form (4) against the applied volt-seconds sets B, and it is the magnetizing current — not the load current — that saturates it. |
| --- |


### 10.3  How the gap lowers B — the mechanism
Framing first: the gap does not raise Bsat.  The wall is a material property and never moves. What the gap does is lower the B obtained per ampere, so more amperes fit before B reaches the same unchanged wall. The mechanism comes from Ampère’s law around the flux path — the total ampere-turns divide between driving the core and driving the gap:
NI = Hcore lc  +  Hgap lg
Flux is continuous through the series path (same Φ, same Ae), so B is the same in the core and in the gap — the gap does not shield the core. But the H required to sustain that B differs enormously: H = B/μ is tiny in the core (huge μ) and enormous in the gap (μ0). Substituting H = B/μ for each segment and solving for B:
B = μ0 NI  /  ( lc/μr  +  lg )
The denominator is the effective magnetic length of the path, and it is the whole story: the core contributes its physical length divided by μr. A 100 mm ferrite path at μr = 2500 contributes only 0.04 mm. Adding a 1 mm physical gap takes the denominator from 0.04 mm to 1.04 mm — a 26× increase. Equivalently, a 1 mm air gap is magnetically equivalent to inserting 2.5 meters of extra ferrite into the path: the same ampere-turns now push flux through a path that is magnetically 26× longer. (The denominator is ℛ·μ0Ae, so the 26× is exactly the reluctance ratio.)
| Quantity   (fixed NI = 100 A·t;  lc = 100 mm, μr = 2500) | Ungapped core | 1 mm gap |
| --- | --- | --- |
| Effective magnetic length   lc/μr + lg | 0.04 mm | 1.04 mm   (26× longer) |
| Flux density   B = μ0NI/(lc/μr + lg) | 3.1 T — saturates hard | 0.12 T — comfortable |
| NI allowed before B = 0.4 T | ≈ 13 A·t | ≈ 330 A·t |


Where the MMF goes.  At any operating B, the gap consumes almost all the ampere-turns (Hgaplg ≫ Hcorelc). The core barely feels any H — it sits near the bottom of its B–H curve while the gap does all the work. High force and high displacement coexisting in one place is energy density: the field-level restatement of “the gap stores the energy.” A practical bonus falls out of the same arithmetic: when the gap owns ~96% of the reluctance, a ±25% swing in the core’s μr (tolerance, temperature) moves L by only ~1% — gapped designs are stable against core-material variation even when energy storage is not the driver.
## 11.  Design Implications — The Two-Knob Loop
Stated entirely in mechanical language, inductor design is: choose a steel spring (gap) stiff enough that the maximum operating force (N·I at Imax) never reaches the rubber’s bind point, then set the gyrator ratio (turns) to present the required mass (L) at the terminals.
The two knobs are nearly orthogonal, which is what makes the loop converge: the gap sets the saturation headroom (ℛ up → Isat up, since NIsat = ℛΦmax), and the turns restore the inductance target (L = N²/ℛ, so an increase in ℛ is compensated by N²). The closing checks are the usual physical limits: flux density B = LI/(NAe) < Bsat at peak current, window fill and copper loss for the added turns, and core loss for the resulting flux swing. This is precisely the constraint loop a magnetics design application must solve when it accepts electrical constraints (L target, Imax, ripple, frequency) and mechanical constraints (core geometry, window area) and returns a complete design.
## 12.  Master Variable Map
Consolidated reference — every variable from the three levels in one table.
| Magnetic / electrical | Symbol · units | Mechanical equivalent | Symbol · units | Notes |
| --- | --- | --- | --- | --- |
| Inductance | L  ·  H | Mass (inertia) | m  ·  kg | inertia for current;  L = N2/ℛ |
| Current | i  ·  A | Velocity | v  ·  m/s | circuit-level flow |
| Voltage | v  ·  V | Force | F  ·  N | circuit-level effort |
| Capacitance | C  ·  F | Spring compliance | 1/k | the true circuit-level spring |
| Resistance | R  ·  Ω | Damper (friction) | b | dissipates; ℛ does not |
| Magnetomotive force | MMF = Ni  ·  A·t | Force | F  ·  N | magnetic-level effort |
| Flux | Φ  ·  Wb | Displacement | x  ·  m | magnetic-level position |
| Flux linkage | NΦ  ·  Wb·t | — | — | defines L = NΦ/i |
| Reluctance | ℛ = l/(μA)  ·  A·t/Wb | Spring constant | k  ·  N/m | stores energy — not a resistance |
| Permeance | 𝒫 = 1/ℛ | Compliance | 1/k | L = N2𝒫 |
| Turns | N | Gyrator ratio | — | flips spring ↔ mass across domains |
| Flux density | B  ·  T | Strain | ε | material-level displacement |
| Field intensity | H  ·  A/m | Stress | σ  ·  Pa | material-level force |
| Permeability | μ = B/H  ·  H/m | Softness (compliance) | 1/E | high μ = rubber; air = steel |
| Saturation limit | Φmax = BsatAe | Coil-bind wall | xmax | property of core alone; gap can’t move it |
| Stored energy | ½LI2 = ½ℛΦ2 | ½mv2 = ½kx2 | — | same number, two viewpoints |
| Energy density | B2/(2μ) | ½σε = ½Eε2 | — | low μ (air) stores more at equal B |


## 13.  Key Equations, Side by Side
| Relationship | Electrical / magnetic form | Mechanical form |
| --- | --- | --- |
| Inertia law | v = L di/dt | F = m dv/dt |
| Spring law | MMF = ℛΦ    (Hopkinson) | F = kx    (Hooke) |
| Stiffness from geometry | ℛ = l/(μA) | k = EA/l   (axial rod) |
| Gyrator reflection | L = N2/ℛ = N2𝒫 | spring behind gyrator → mass |
| Stored energy | ½LI2  =  ½ℛΦ2 | ½mv2  =  ½kx2 |
| Energy density | w = ½BH = B2/(2μ) | w = ½σε = ½Eε2 |
| Flux density (gapped path) | B = μ0NI / (lc/μr + lg) | strain from force over total stiffness |
| Saturation origin | Bsat ≈ μ0Ms   (measured property) | yield strain — a material limit, never derived |
| Saturation current | NIsat = ℛ Φmax = ℛ BsatAe | force to reach the bind wall |
| Energy ceiling | Emax = ½ ℛ Φmax2 | energy at bind ∝ stiffness |
| Resonance | ω₀ = 1/√(LC) | ω₀ = √(k/m) |


Summary in one line:  current → flux via the geometry (L, ℛ, μ) → energy in the field (½LI²) — an inertia at the terminals, a spring inside, a soft material that binds at Bsat.
