# Master Design Guide

This is the practical starting point. Begin here after the converter electrical design has defined the magnetic component's job. Use the strict equations to keep the design physically valid; use the rules of thumb only to choose first-pass assumptions before checking the equations.

For deeper derivations, use [Magnetic Theory](./magnetic-theory.md), [Core, Gap, And Thermal Design](./core-gap-and-thermal-design.md), [High-Frequency And Winding Effects](./high-frequency-and-winding-effects.md), and [Equation Reference](./equation-reference.md).

---

## Inductor One-Pager

Use this path for buck/boost/PFC/filter inductors, DC chokes, resonant inductors, and flyback magnetics. A flyback "transformer" is an energy-storage coupled inductor, so it starts here, not in the true-transformer flow. [source: TI SLUP132 §2 Core Limitations in SMPS Applications] [source: TI SLUP132 §5 Inductor and Flyback Transformer Design]

### 0. Start Here

Start from the converter waveform, not from a core catalog.

Required inputs:

| Input | Typical first-pass value or assumption |
| --- | --- |
| Topology and magnetic role | Buck output inductor, boost/PFC inductor, flyback coupled inductor, EMI choke, etc. |
| Inductance or ripple target | CCM buck ripple often starts at 20-40% of full-load current; use 10-20% for low ripple/noise, 40-80% when size is more important. |
| Current set | Use DC, RMS, ripple, peak, overload, and short-circuit/current-limit current. Saturation checks use the worst credible peak current. |
| Frequency and volt-second interval | Use the worst case that maximizes ripple or flux swing. |
| Thermal limit | 20-40 deg C rise is a normal first pass; 10-15 deg C for hot ambient or enclosed designs. |
| Core material | MnZn ferrite for low high-frequency loss; powder/metal composite for soft saturation and distributed gap. |
| Flux-density limit | Gapped ferrite inductor first pass: 0.20-0.30 T hot. Powder cores require the manufacturer's DC-bias curve. |
| Window fill factor | 0.25-0.40 for bobbin/litz/insulated windings; 0.50-0.70 for simple foil or low-insulation inductor builds; use 0.40 if unsure. |
| Current density | 3-6 A/mm^2 for natural convection first pass; lower for high ambient or poor cooling. |

### 1. Set The Electrical Target

**Strict equations**

For any interval:

$$
\Delta I = \frac{V_L \Delta t}{L}
$$

For a CCM buck output inductor:

$$
D \approx \frac{V_o}{V_{in}}, \qquad \Delta I_L = \frac{(V_{in}-V_o)D}{f_s L}
$$

Peak current:

$$
I_{pk} = I_{dc} + \frac{\Delta I_{pp}}{2}
$$

Triangular ripple RMS:

$$
I_{rms} \approx \sqrt{I_{dc}^2 + \frac{\Delta I_{pp}^2}{12}}
$$

**Rule of thumb**

Choose ripple before choosing the core. A smaller ripple target increases inductance, stored energy, turns, size, and cost. A larger ripple target increases capacitor ripple current, switch current stress, and core-loss swing.

### 2. Choose Material And Starting Flux Density

**Strict equations**

Flux and saturation are checked with:

$$
B_{pk} = \frac{L I_{pk}}{N A_e}
$$

For a core plus gap:

$$
B = \frac{\mu_0 N I}{\ell_g + \ell_c/\mu_r}
$$

**Rule of thumb**

Use the hot saturation value, not the 25 deg C headline number. For ferrite inductors, start around 0.20-0.30 T peak. For high-ripple or high-frequency operation, reduce the flux target because core loss rises strongly with flux swing.

### 3. Pick A First Core Size

**Strict equations**

Stored energy:

$$
E = \frac{1}{2} L I_{pk}^2
$$

Gap-dominated core geometry constant:

$$
K_g = \frac{A_e^2 W_a}{MLT} \ge \frac{\rho L^2 I_{pk}^2}{B_{max}^2 R K_u}
$$

Thermal area-product estimate:

$$
A_p = \left[\frac{\sqrt{1+\gamma}K_i L I_{pk}^2}{B_{max}K_t\sqrt{k_u\Delta T}}\right]^{8/7}
$$

**Rule of thumb**

If you do not have enough data for the full thermal area-product equation, choose a core with comfortable energy margin, then verify copper loss, core loss, and temperature. Core scale is the variable that improves both saturation and temperature at the same time; turns and gap mostly trade one failure mode for another.

### 4. Calculate Turns And Gap

**Strict equations**

Minimum turns from peak flux:

$$
N \ge \frac{L I_{pk}}{B_{max} A_e}
$$

Manufacturer inductance factor:

$$
L = N^2 A_L, \qquad N = \sqrt{\frac{L}{A_L}}
$$

Approximate discrete gap:

$$
\ell_g \approx \frac{\mu_0 N^2 A_e}{L} - \frac{\ell_c}{\mu_r}
$$

Window fit:

$$
N A_{cu} \le k_u W_a
$$

**Rule of thumb**

Round turns, then recalculate everything. Rounding down lowers inductance and raises ripple; rounding up raises copper length and may exceed window fill. For discrete gaps, prefer catalog gapped sets and use the manufacturer's $A_L$ instead of trusting the ideal gap calculation alone.

### 5. Size The Conductor And Losses

**Strict equations**

Temperature-corrected copper resistivity:

$$
\rho(T) = \rho_{20}[1+\alpha_{20}(T-20^\circ\text{C})]
$$

DC winding resistance:

$$
R_{dc} = \rho(T)\frac{N \cdot MLT}{A_{cu}}
$$

Copper loss:

$$
P_{cu} = I_{rms}^2 R
$$

Core loss from the material data:

$$
P_{fe} = P_v(f, B_{ac}) V_e
$$

Temperature rise:

$$
\Delta T = R_\theta(P_{cu}+P_{fe})
$$

**Rule of thumb**

For DC-biased inductors with small ripple, DC copper loss often dominates. Foil or heavy copper can be excellent even if its AC resistance is poor, as long as ripple RMS is small. For PFC, DCM, or large-ripple inductors, AC winding loss and core loss can dominate.

### 6. Iterate And Verify

Pass conditions:

- $L$ is inside tolerance at zero bias and at operating bias.
- $B_{pk}$ stays below the hot saturation target at the worst peak current.
- Winding fits the window with insulation and termination space.
- $P_{cu}+P_{fe}$ meets the temperature-rise budget.
- Fringing from a discrete gap does not overheat nearby copper.
- Bench tests confirm DCR, inductance versus DC bias, and temperature.

Deep dive: [Inductor Design Deep Dive](./inductor-design-deep-dive.md)

---

## Transformer One-Pager

Use this path for true transformers in forward, push-pull, half-bridge, full-bridge, PSFB, LLC, gate-drive, and line-frequency applications. A true transformer transfers energy through mutual flux; it should not deliberately store the load energy in a gap. [source: TI SLUP132 §4 Power Transformer Design]

### 0. Start Here

Start from topology waveforms and isolation requirements.

Required inputs:

| Input | Typical first-pass value or assumption |
| --- | --- |
| Topology | Forward, push-pull, half bridge, full bridge, PSFB, LLC, line-frequency, etc. |
| Primary voltage waveform | Include duty range, reset method, dead time, and worst-case volt-second imbalance. |
| Output set | Each secondary voltage, current, rectifier drop, regulation target, and cross-regulation requirement. |
| Total winding VA | Sum all winding VA, including auxiliaries when they matter thermally. |
| Isolation | Working voltage, transient voltage, pollution environment, creepage, clearance, insulation class, and hipot target. |
| Flux-density limit | Ferrite transformer first pass: 0.12-0.22 T at 50-200 kHz; lower for hotter, higher-frequency, or low-loss designs. |
| Window fill factor | 0.25-0.40 for isolated transformers; use 0.30-0.35 if unsure. |
| Current density | 3-5 A/mm^2 natural convection first pass; reduce for high ambient or many layers. |
| Loss split | Start with copper and core losses in the same rough range, then optimize from measured/material data. |

### 1. Classify The Magnetic

**Strict equations**

True-transformer core mmf balance:

$$
N_p I_p - N_s I_s = \Phi_m \mathcal{R}
$$

Flyback energy storage:

$$
E = \frac{1}{2} L_m I_{pk}^2
$$

**Rule of thumb**

If the magnetizing inductance stores the transferred load energy, it is a flyback coupled inductor and needs the inductor flow. If the transformer mainly transfers power while magnetizing current is a parasitic/design constraint, use this transformer flow.

### 2. Choose Turns Ratio From Circuit Requirements

**Strict equations**

Ideal transformer ratio:

$$
\frac{V_s}{V_p} \approx \frac{N_s}{N_p}
$$

For converter designs, include duty cycle, rectifier drops, switch drops, and regulation headroom in the applied voltages before turning this into an integer turns ratio.

**Rule of thumb**

Do the electrical turns-ratio math first, then check flux and window. Do not choose turns from a catalog core first. For low-voltage, high-current secondaries, one turn may already be too many; see fractional-turn notes in the deep dive.

### 3. Set Core Flux From Volt-Seconds

**Strict equations**

General volt-second relation:

$$
\Delta B = \frac{1}{N A_e}\int v(t)\,dt
$$

General RMS form:

$$
V_{rms} = K_v f N B_{max} A_e
$$

Primary minimum turns:

$$
N_p \ge \frac{\int v_p(t)\,dt}{A_e \Delta B_{allow}}
$$

**Rule of thumb**

For high-frequency ferrite transformers, a first flux target of 0.12-0.22 T is usually more practical than designing near saturation. Core loss and hot-margin usually set the limit before the material's hard saturation knee.

### 4. Select Core Size

**Strict equations**

Transformer area-product relation:

$$
\sum VA = K_v f B_{max} J k_f k_u A_p
$$

Fixed-frequency optimized estimate:

$$
A_p = \left[\frac{\sqrt{2}\sum VA}{K_v f B_o k_f K_t\sqrt{k_u\Delta T}}\right]^{8/7}
$$

Window fit:

$$
\sum_i N_i A_{cu,i} \le k_u W_a
$$

**Rule of thumb**

Use area product to get near the right core family, then let winding layout decide the final choice. Isolation tape, creepage margins, triple-insulated wire, margins, and interleaving usually consume more window than the arithmetic first suggests.

### 5. Size Windings And Control Parasitics

**Strict equations**

Per-winding copper loss:

$$
P_{cu,i}=I_{rms,i}^2R_i
$$

Referred secondary resistance:

$$
R_s' = a^2 R_s
$$

Skin depth:

$$
\delta = \frac{1}{\sqrt{\pi f \mu \sigma}}
$$

Core loss:

$$
P_{fe}=P_v(f,B_{ac})V_e
$$

Temperature rise:

$$
\Delta T = R_\theta(P_{cu}+P_{fe})
$$

**Rule of thumb**

Interleaving lowers leakage inductance but raises interwinding capacitance and may complicate isolation. Put high-current windings close together when leakage must be low; add spacing or shields when common-mode noise and safety isolation dominate.

### 6. Check Magnetizing Current, Leakage, Insulation, And Heat

**Strict equations**

Magnetizing inductance:

$$
L_m=\frac{N_p^2}{\mathcal{R}}
$$

Magnetizing current ramp:

$$
\Delta I_m = \frac{1}{L_m}\int v_p(t)\,dt
$$

Referred leakage:

$$
X_{l,s}' = a^2 X_{l,s}
$$

**Rule of thumb**

Magnetizing current should be large enough for the converter's intended behavior only when intentionally required, such as resonant operation. Otherwise it is usually a loss and switch-stress penalty. Leakage can be parasitic, functional, or both; decide that before winding layout.

Pass conditions:

- Integer turns produce the required output voltages across line/load range.
- Flux swing stays below the selected hot $B_{max}$ under worst volt-seconds.
- Winding fill, insulation, creepage, and clearance fit physically.
- Copper plus core loss meets thermal limit.
- Leakage and magnetizing inductance meet converter requirements.
- Hipot/insulation tests and thermal tests pass.

Deep dive: [Transformer Design Deep Dive](./transformer-design-deep-dive.md)
