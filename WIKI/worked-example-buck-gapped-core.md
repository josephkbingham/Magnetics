# Worked Example: Buck Gapped Core

## Source Case

This page condenses Hurley and Wolfle Example 3.1 into a wiki-format reference because it is the first full buck-inductor worked example present in the current raw-source set. The page expands on the source by making every formula explicit, checking the consequences of rounding decisions, and mapping the design to bench-measurement procedures from [Verification And Measurement](./verification-and-measurement.md). [source: Hurley & Wolfle Ch. 3 Example 3.1]

## GIC

### Geometry

Selected core: ETD49 ferrite core with $A_c = 2.09\ \text{cm}^2$, $l_c = 11.4\ \text{cm}$, $W_a = 2.69\ \text{cm}^2$, $A_p = 5.62\ \text{cm}^4$, $V_c = 23.8\ \text{cm}^3$, and $MLT = 8.6\ \text{cm}$. The discrete gap selected is 2 mm with a manufacturer-specified $A_L = 188\ \text{nH}$. Winding is a single-layer foil conductor, 8 mm $\times$ 2 mm cross-section. [source: Hurley & Wolfle Ch. 3 Table 3.3 and Example 3.1 gap section]

### Input

Buck-converter specification: $V_{in} = 12\ \text{V}$, $V_{out} = 6\ \text{V}$, $L = 34\ \mu\text{H}$, DC current 20 A, switching frequency $f_{sw} = 80\ \text{kHz}$, ambient $T_a = 70\ ^\circ\text{C}$, temperature rise limit $\Delta T = 15\ ^\circ\text{C}$, and $k_u = 0.8$. [source: Hurley & Wolfle Ch. 3 Table 3.1]

### Constraint

Material: EPCOS N87 MnZn ferrite with $B_{sat} = 0.4\ \text{T}$. Operating flux density selected at $B_{max} = 0.25\ \text{T}$ (62.5 % of saturation). Total temperature rise is limited to 15 $^\circ\text{C}$ on top of 70 $^\circ\text{C}$ ambient, giving a maximum winding temperature of 85 $^\circ\text{C}$. Core loss is treated as secondary to copper loss because the ripple is small. [source: Hurley & Wolfle Ch. 3 Table 3.2 and Example 3.1 discussion]

---

## Design Sequence

### Step 1 — Ripple And Peak Current

Duty ratio for the ideal lossless buck is

$$
D = \frac{V_{out}}{V_{in}} = \frac{6}{12} = 0.5
$$

The peak-to-peak ripple current at $D = 0.5$ is

$$
\Delta I_L = \frac{(V_{in} - V_{out})\,D}{f_{sw}\,L} = \frac{6 \times 0.5}{80\,000 \times 34 \times 10^{-6}} = 1.10\ \text{A}
$$

The peak current that the inductor must support without saturating is

$$
\hat{I} = I_{dc} + \frac{\Delta I_L}{2} = 20 + 0.55 = 20.55\ \text{A}
$$

[source: Hurley & Wolfle Ch. 3 Example 3.1]

### Step 2 — Area Product And Core Selection

The Hurley and Wolfle energy-based area-product formula for an inductor is

$$
A_p = \left[\frac{\sqrt{1+\gamma}\;K_i\;L\;\hat{I}^2}{B_{max}\;K_t\;\sqrt{k_u\;\Delta T}}\right]^{8/7}
$$

where $\gamma = P_{fe}/P_{cu}$ (taken as zero because core loss is small relative to copper loss), $K_i$ is a waveform factor equal to 1 for a DC-bias-dominated inductor, and $K_t$ is a thermal-geometry constant evaluated for the selected core family. [source: Hurley & Wolfle Ch. 3 eq. 3.35]

The stored-energy term evaluates to

$$
L\hat{I}^2 = 34 \times 10^{-6} \times 20.55^2 = 0.0144\ \text{J}
$$

Substituting into the area-product formula with the source-tabulated constants for the ETD-family core gives

$$
A_p = 4.12\ \text{cm}^4
$$

The ETD49 has $A_p = 5.62\ \text{cm}^4$, which exceeds the requirement. It is the smallest standard ETD-family core that satisfies the area-product lower bound and is therefore selected. [source: Hurley & Wolfle Ch. 3 Example 3.1] [source: Hurley & Wolfle Ch. 3 Table 3.3]

### Step 3 — Thermal Dissipation Budget

The manufacturer-quoted thermal resistance for the ETD49 in natural convection is $R_\theta = 11\ ^\circ\text{C/W}$. With the 15 $^\circ\text{C}$ temperature-rise budget, the maximum allowable total dissipation is

$$
P_{D,max} = \frac{\Delta T}{R_\theta} = \frac{15}{11} = 1.36\ \text{W}
$$

All subsequent loss calculations must stay below this limit. [source: Hurley & Wolfle Ch. 3 Example 3.1]

### Step 4 — Optimum Effective Permeability And Gap

The source gives the optimum effective permeability as

$$
\mu_{opt} = \frac{B_{sat}\;l_c\;K_i}{\mu_0\;\sqrt{\dfrac{P_{cu,max}\;k_u\;W_a}{\rho_w\;MLT}}}
$$

[source: Hurley & Wolfle Ch. 3 eq. 3.20]

Substituting $B_{sat} = 0.4\ \text{T}$, $l_c = 11.4 \times 10^{-2}\ \text{m}$, $K_i = 1$, $\mu_0 = 4\pi \times 10^{-7}$, $P_{cu,max} = 1.36\ \text{W}$, $k_u = 0.8$, $W_a = 2.69 \times 10^{-4}\ \text{m}^2$, $\rho_w$ at 85 $^\circ$C, and $MLT = 8.6 \times 10^{-2}\ \text{m}$ gives

$$
\mu_{opt} = 51
$$

The corresponding gap length is obtained from the relationship between effective permeability and gap. For a gap much shorter than the magnetic path length, the gap-dominated approximation gives

$$
\ell_{g,max} = \frac{\mu_0\;A_c\;N^2}{L} \approx \frac{l_c}{\mu_{opt}} = \frac{11.4\ \text{cm}}{51} = 2.24\ \text{mm}
$$

A standard 2 mm gapped ETD49 core set is then selected from the manufacturer offering. [source: Hurley & Wolfle Ch. 3 Example 3.1]

### Step 5 — Turns From Manufacturer $A_L$

The gapped core set carries a manufacturer-specified inductance factor $A_L = 188\ \text{nH}$ (inductance per turn squared). The required turns count is

$$
N = \sqrt{\frac{L}{A_L}} = \sqrt{\frac{34 \times 10^{-6}}{188 \times 10^{-9}}} = \sqrt{180.9} = 13.45
$$

The source rounds down to $N = 13$ turns. [source: Hurley & Wolfle Ch. 3 eq. 3.36 and Example 3.1]

### Step 6 — Inductance Check After Turn Rounding

With $N = 13$ turns and the manufacturer $A_L$, the realized inductance is

$$
L_{actual} = N^2 \times A_L = 13^2 \times 188\ \text{nH} = 169 \times 188\ \text{nH} = 31.8\ \mu\text{H}
$$

This is 6.5 % below the specified 34 $\mu$H. The consequence in the converter is a proportionally larger ripple current:

$$
\Delta I_{L,actual} = \frac{(V_{in} - V_{out})\,D}{f_{sw}\,L_{actual}} = \frac{6 \times 0.5}{80\,000 \times 31.8 \times 10^{-6}} = 1.18\ \text{A}
$$

and a revised peak current

$$
\hat{I}_{actual} = 20 + 0.59 = 20.59\ \text{A}
$$

The peak-current increase is less than 0.2 %, which has negligible effect on saturation margin and copper loss. The inductance shortfall is accepted here; rounding up to $N = 14$ would give $L = 14^2 \times 188 = 36.8\ \mu\text{H}$ (8 % over-inductance) and a somewhat larger window-fill requirement. [source: Hurley & Wolfle Ch. 3 Example 3.1]

### Step 7 — Wire Sizing

The maximum conductor area that fits in the window at the chosen fill factor is

$$
A_{W,max} = \frac{k_u\;W_a}{N} = \frac{0.8 \times 2.69\ \text{cm}^2}{13} = 0.166\ \text{cm}^2
$$

The source selects a foil conductor with cross-section 8 mm $\times$ 2 mm = $0.16\ \text{cm}^2 \le 0.166\ \text{cm}^2$, which satisfies the window constraint. [source: Hurley & Wolfle Ch. 3 Example 3.1]

### Step 8 — Loss Verification

Copper resistivity at the maximum winding temperature $T_{max} = 85\ ^\circ\text{C}$ is

$$
\rho_w(85) = \rho_{20}\left[1 + \alpha_{20}(85 - 20)\right] = 1.724 \times 10^{-8} \times 1.256 = 2.165 \times 10^{-8}\ \Omega\text{m}
$$

[source: Hurley & Wolfle Ch. 3 eq. 3.37]

DC winding resistance is

$$
R_{dc} = \rho_w(85) \times \frac{N \times MLT}{A_W} = 2.165 \times 10^{-8} \times \frac{13 \times 0.086}{1.6 \times 10^{-5}} = 1.51\ \text{m}\Omega
$$

Copper loss at 20 A DC is

$$
P_{cu} = I_{dc}^2 \times R_{dc} = 400 \times 1.51 \times 10^{-3} = 0.604\ \text{W}
$$

[source: Hurley & Wolfle Ch. 3 Example 3.1]

The flux-density ripple corresponding to the realized ripple current is

$$
\Delta B = \frac{\mu_0\;N\;\Delta I_L}{2\;\ell_g} = \frac{4\pi \times 10^{-7} \times 13 \times 1.18}{2 \times 2 \times 10^{-3}} = 0.014\ \text{T}
$$

At $f_{sw} = 80\ \text{kHz}$ and $\Delta B = 0.014\ \text{T}$, the N87 Steinmetz parameters yield

$$
P_{fe} = 0.005\ \text{W}
$$

Total dissipation is $P_{total} = 0.604 + 0.005 = 0.609\ \text{W}$, which is comfortably below the 1.36 W thermal budget. The resulting temperature rise is

$$
\Delta T_{actual} = R_\theta \times P_{total} = 11 \times 0.609 = 6.7\ ^\circ\text{C}
$$

well within the 15 $^\circ\text{C}$ limit. [source: Hurley & Wolfle Ch. 3 Example 3.1]

---

## Tradeoffs

### ETD49 Versus A Smaller Core

The area-product calculation required $A_p \ge 4.12\ \text{cm}^4$. The next smaller standard ETD core (ETD44, $A_p \approx 3.4\ \text{cm}^4$) falls below the threshold. Choosing ETD44 would require either increasing $B_{max}$ beyond 0.25 T (reducing saturation margin), reducing $k_u$ and accepting lower fill factor and more turns, or accepting a temperature rise above 15 $^\circ$C. All three directions are constrained by the GIC inputs, so ETD44 is not viable without changing the specification. [source: Hurley & Wolfle Ch. 3 Table 3.3 and Example 3.1]

### $B_{max} = 0.25\ \text{T}$ Versus The Saturation Limit

The source chooses $B_{max} = 0.25\ \text{T}$ against $B_{sat} = 0.4\ \text{T}$, a 37.5 % derating margin. The implied saturation current (at constant gap and turns) is

$$
\hat{I}_{sat} = \hat{I}_{actual} \times \frac{B_{sat}}{B_{max}} = 20.59 \times \frac{0.4}{0.25} = 33.0\ \text{A}
$$

This provides 60 % headroom above the 20.59 A peak. The derating is deliberate: N87 permeability begins to decline noticeably well before the hard saturation knee, so operating at $B_{max} = 0.25\ \text{T}$ keeps the inductance well within the linear region over the full current range. A larger derating also makes the inductor tolerant of transient overcurrent. The penalty is a core larger than the minimum possible at $B_{sat}$. [source: Hurley & Wolfle Ch. 3 Table 3.2 and Example 3.1]

### 2 mm Standard Gap Versus The Computed 2.24 mm Optimum

The optimum gap calculation gives 2.24 mm, but 2 mm is the nearest available standard gapped core set. A shorter gap increases $\mu_e$ above $\mu_{opt}$, which slightly tightens the tradeoff between flux density and copper loss: at the same turns count, a shorter gap raises $A_L$, which would increase inductance (reducing ripple) but also increases $B_{max}$ at a given current. Because $\mu_e$ is approximately $l_c/\ell_g = 11.4/0.2 = 57$ at 2 mm versus 51 at 2.24 mm, the actual $B_{max}$ at peak current rises slightly. The source accepts this modest deviation and uses the manufacturer $A_L$ to recalculate turns rather than grinding a custom gap. [source: Hurley & Wolfle Ch. 3 Example 3.1]

### $N = 13$ Versus $N = 14$ (Turn Rounding)

Rounding down from 13.45 to 13 turns under-inducts the design by 6.5 % ($L_{actual} = 31.8\ \mu\text{H}$ versus $L_{spec} = 34\ \mu\text{H}$). This increases ripple current by the same factor. Rounding up to 14 turns over-inducts by 8 % ($L = 36.8\ \mu\text{H}$) and requires a larger conductor area ($A_W = 0.154\ \text{cm}^2$ for 14 turns, which still fits). The down-round is acceptable here because the ripple increase is small (1.10 A → 1.18 A), saturation margin remains large, and the temperature rise is well within budget. In applications where ripple is tightly constrained or where converter control bandwidth is sensitive to inductor value, the up-round is safer. [source: Hurley & Wolfle Ch. 3 Example 3.1]

### Foil Conductor Versus Litz Wire At 80 kHz

For copper at 85 $^\circ$C, the skin depth at 80 kHz is

$$
\delta = \frac{1}{\sqrt{\pi f_{sw}\;\mu_0\;\sigma_{85}}} = \frac{1}{\sqrt{\pi \times 80\,000 \times 4\pi \times 10^{-7} \times 4.62 \times 10^7}} \approx 0.26\ \text{mm}
$$

The 2 mm foil thickness is approximately 7.7 skin depths. The AC-to-DC resistance ratio at 80 kHz is therefore approximately

$$
\frac{R_{ac}}{R_{dc}} \approx \frac{t}{2\delta} = \frac{2}{2 \times 0.26} \approx 3.8
$$

Despite this large ratio, the AC copper loss remains negligible because the ripple current rms value is very small. For a triangular ripple of 1.18 A peak-to-peak, the rms ripple is $\Delta I_{rms} = \Delta I/(2\sqrt{3}) = 0.34\ \text{A}$, giving

$$
P_{ac} = \Delta I_{rms}^2 \times R_{ac} = 0.34^2 \times (1.51 \times 3.8)\ \text{m}\Omega = 0.66\ \text{mW}
$$

which is 0.1 % of total loss. The foil is therefore an effective choice precisely because the inductor is a DC-dominated component with small ripple. The foil's low DC resistance (large cross-section) dominates, and its poor AC behavior is irrelevant. Litz wire would be the correct choice if the ripple fraction were large (for example, discontinuous-conduction-mode operation or PFC boost inductors), where AC loss drives the winding design. [source: Hurley & Wolfle Ch. 3 Example 3.1] [source: Hurley & Wolfle Ch. 1 §1.4.1]

### Core Loss Is Negligible: When This Assumption Breaks

The example assumes $\gamma = P_{fe}/P_{cu} \approx 0$. This holds because $\Delta B = 0.014\ \text{T}$ is very small relative to $B_{max} = 0.25\ \text{T}$. The same core and material at a higher ripple fraction — for example, a discontinuous-conduction-mode inductor or a PFC boost inductor where $\Delta I/I_{dc} \sim 0.3$ to 1 — would have a proportionally larger $\Delta B$, and core loss would become non-negligible. In that regime the area-product formula must be iterated with $\gamma \ne 0$ and $B_{max}$ solved jointly for minimum total loss. [source: Hurley & Wolfle Ch. 3 §3.1.5 and Example 3.1]

---

## Validation: Bench Measurements

The following tests, using procedures from [Verification And Measurement](./verification-and-measurement.md), should be applied to a built unit of this design. The expected results for a correct build are given so that a deviation from expectation identifies the failure mode.

### Test 1 — DC Winding Resistance (Cold And Hot)

**Method:** Four-wire Kelvin resistance measurement at the winding terminals.

**Expected values:**
- At 20 $^\circ$C: $R_{dc,20} = R_{dc,85} / [1 + 0.00393 \times (85 - 20)] = 1.51\ \text{m}\Omega / 1.256 = 1.20\ \text{m}\Omega$
- At 85 $^\circ$C: $R_{dc,85} = 1.51\ \text{m}\Omega$

**Deviation interpretation:** High cold resistance indicates undersized conductor cross-section or insufficient turns length estimate ($MLT$ underestimated). Low cold resistance may indicate a shorted turn.

### Test 2 — Inductance Vs. DC Bias (Step-Voltage Method)

**Method:** Apply a constant-voltage step and compute inductance point-by-point using

$$
\lambda(k) = V\Delta t - R\,i(k)\Delta t + \lambda(k-1), \qquad L(i_k) = \lambda(k)/i(k)
$$

[source: Hurley & Wolfle Ch. 8 eq. 8.1-8.3 and §8.1.1]

**Expected values:**
- $L(0\ \text{A}) \approx 31.8\ \mu\text{H}$ (from $N^2 A_L = 169 \times 188\ \text{nH}$)
- $L$ remains within 10 % of its zero-bias value up to approximately 20.6 A
- $L$ begins to collapse significantly near 33 A (estimated saturation onset at $\hat{I}_{sat} = 33\ \text{A}$)

**Deviation interpretation:** $L(0)$ more than 10 % below 31.8 $\mu$H indicates gap longer than nominal (check gap spacer). Saturation onset well below 33 A indicates the $A_L$ value is higher than specified (gap shorter than nominal) or the material batch has lower $B_{sat}$.

### Test 3 — Incremental AC Inductance Under DC Bias

**Method:** Superpose a small AC stimulus on a DC operating current and measure the AC impedance:

$$
L_{ac} = \frac{1}{\omega}\sqrt{\frac{v_{ac}^2}{i_{ac}^2} - R^2}
$$

[source: Hurley & Wolfle Ch. 8 eq. 8.4-8.6 and §8.1.2]

**Expected values:** At $I_{dc} = 20\ \text{A}$ and $f_{ac} = 1\ \text{kHz}$, $L_{ac}$ should be close to $L(0)$ because the design sits comfortably on the linear portion of the $B$-$H$ curve at $B_{max} = 0.25\ \text{T}$.

**Deviation interpretation:** Significant roll-off of $L_{ac}$ at 20 A indicates proximity to the knee of the $B$-$H$ curve and insufficient saturation margin.

### Test 4 — Temperature Rise Under Load

**Method:** Apply $I_{dc} = 20\ \text{A}$ in an ambient of 70 $^\circ$C. Allow thermal steady state ($\ge 30\ \text{min}$ typical). Measure surface temperature with thermocouple or thermistor bonded to the core.

**Expected values:**
- Total dissipation: $P_{total} = 0.609\ \text{W}$
- Temperature rise: $\Delta T = 11 \times 0.609 = 6.7\ ^\circ$C
- Surface temperature: $T_{surface} \approx 76.7\ ^\circ\text{C}$

**Deviation interpretation:** Temperature rise more than 50 % above prediction (i.e., $> 10\ ^\circ$C) suggests higher-than-expected $R_{dc}$ (verify Test 1 result), a gap fringing field heating the bobbin or nearby conductors, or inadequate convection airflow around the core.

> **Note:** Thermal imaging is listed as [UNVERIFIED] in this wiki because no primary-source imaging procedure has been ingested. Thermocouple surface measurement is the procedure supported by the current source set. [source: /magnetics-wiki-schema.md §3 Measurement and Verification]

### Test 5 — Core Loss Spot Check (Optional)

**Method:** At switching frequency, the high-frequency core-loss test from [Verification And Measurement](./verification-and-measurement.md) holds $E_{rms}/f$ constant to maintain constant $\Delta B$ while sweeping frequency, then measures

$$
P_{fe} = a\,v_2\,\frac{v_{ref}}{R_{ref}}\cos\theta
$$

[source: Hurley & Wolfle Ch. 8 eq. 8.19-8.20]

**Expected values:** At 80 kHz and $\Delta B = 0.014\ \text{T}$, N87 core loss is expected to be $\approx 5\ \text{mW}$. This test is worth performing only if the thermal measurement (Test 4) reveals unexpectedly high losses, since at these conditions the core loss is a negligible fraction of total loss.

---

## Related Pages

- [Buck Output Filter Inductor Design](./buck-output-filter-inductor-design.md)
- [Thermal Design And Core Selection](./thermal-design-and-core-selection.md)
- [Air Gap And Saturation](./air-gap-and-saturation.md)
- [Distributed Gap And Fringing](./distributed-gap-and-fringing.md)
- [High-Frequency Effects](./high-frequency-effects.md)
- [Verification And Measurement](./verification-and-measurement.md)
- [Index](./index.md)
