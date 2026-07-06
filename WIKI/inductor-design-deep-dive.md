# Inductor Design Deep Dive

This page merges the former inductor input checklist, buck-inductor procedure, sensitivity notes, coupled-filter-inductor notes, and the ETD49 worked example into one cohesive reference. Use [Master Design Guide](./master-design-guide.md) for the short workflow, then return here for assumptions and tradeoffs.

## Design-Ready Input Contract

An inductor design is ready to start only when the converter has defined the magnetic waveform and the failure limits. Required inputs are:

| Group | Inputs |
| --- | --- |
| Converter identity | Topology, isolation role, magnetic role, operating mode, number of outputs, and whether the part is a filter inductor, boost/PFC inductor, buck-boost/flyback inductor, coupled output inductor, EMI choke, or DC choke. [source: TI SLUP132 §5 Inductor and Flyback Transformer Design] |
| Voltage waveform | Voltage across the inductor during each switching interval, duty-cycle limits, timing, and the worst case that maximizes ripple or flux swing. [source: TI SLUP132 §5 Design Strategy] |
| Current set | Average current, RMS current, ripple current, peak current, overload current, and short-circuit/current-limit current. [source: TI SLUP132 §5 Design Strategy] |
| Loss and thermal limits | Ambient, cooling method, maximum temperature rise, allowed copper loss, allowed core loss, and hot-spot limit. [source: Hurley & Wolfle Ch. 3 §3.2] |
| Magnetic limits | Candidate material, hot $B_{sat}$, design $B_{max}$, allowed $\Delta B$, gap strategy, and saturation margin. [source: Erickson & Maksimovic Ch. 11 §11.1] |
| Geometry candidates | Core family, $A_e$, $W_a$, $MLT$, $l_e$, $V_e$, gap or effective-permeability options, and manufacturer $A_L$ data. [source: Hurley & Wolfle Ch. 3 §3.2] |
| Winding constraints | Window utilization $k_u$, conductor type, current-density target, insulation, layer count, termination method, and maximum DCR/ACR. [source: Erickson & Maksimovic Ch. 11 eq. 11.10-11.13] |

For topology mapping before this input list, see [Converter Topology Inventory](./converter-topologies.md).

## Strict Design Equations

### Ripple, Peak Current, And RMS Current

The inductor voltage law is:

$$
V_L = L\frac{di}{dt}, \qquad \Delta I = \frac{V_L\Delta t}{L}
$$

For a CCM buck output filter:

$$
D \approx \frac{V_o}{V_{in}}, \qquad \Delta I_L = \frac{(V_{in}-V_o)D}{f_sL}
$$

Peak current is:

$$
I_{pk}=I_{dc}+\frac{\Delta I_{pp}}{2}
$$

For triangular ripple:

$$
I_{rms}\approx\sqrt{I_{dc}^2+\frac{\Delta I_{pp}^2}{12}}
$$

### Gap-Dominated Magnetic Circuit

Core and gap reluctances are:

$$
\mathcal{R}_c=\frac{\ell_c}{\mu A_e}, \qquad \mathcal{R}_g=\frac{\ell_g}{\mu_0 A_e}
$$

The magnetic-circuit relation is:

$$
NI=\Phi(\mathcal{R}_c+\mathcal{R}_g)
$$

Inductance is:

$$
L=\frac{N^2}{\mathcal{R}_c+\mathcal{R}_g}
$$

For a gap-dominated inductor:

$$
B = \frac{\mu_0NI}{\ell_g+\ell_c/\mu_r}, \qquad L \approx \frac{\mu_0A_eN^2}{\ell_g}
$$

The design consequence is important: the gap lowers inductance but raises the current required to reach saturation. The core flux limit remains $B_{sat}A_e$; the gap raises the ampere-turns needed to reach it. [source: Erickson & Maksimovic Ch. 10 eq. 10.27-10.33]

### First-Pass Core Sizing

Allowed copper loss sets winding resistance:

$$
R_{max}=\frac{P_{cu,max}}{I_{rms}^2}
$$

Winding fit:

$$
k_u W_a \ge N A_{cu}
$$

Winding resistance:

$$
R=\rho\frac{N(MLT)}{A_{cu}}
$$

The gap-dominated geometry constant condition is:

$$
K_g=\frac{A_e^2W_a}{MLT}\ge\frac{\rho L^2I_{pk}^2}{B_{max}^2RK_u}
$$

The thermal area-product estimate is:

$$
A_p=\left[\frac{\sqrt{1+\gamma}K_iLI_{pk}^2}{B_{max}K_t\sqrt{k_u\Delta T}}\right]^{8/7}
$$

where $\gamma=P_{fe}/P_{cu}$. If core loss is expected to be small, start with $\gamma=0$ and verify later. [source: Erickson & Maksimovic Ch. 11 eq. 11.14-11.15] [source: Hurley & Wolfle Ch. 3 eq. 3.35]

### Turns, Gap, And Manufacturer Data

Minimum turns from peak flux:

$$
N\ge\frac{LI_{pk}}{B_{max}A_e}
$$

Turns from manufacturer $A_L$:

$$
N=\sqrt{\frac{L}{A_L}}
$$

Approximate discrete gap:

$$
\ell_g\approx\frac{\mu_0A_eN^2}{L}-\frac{\ell_c}{\mu_r}
$$

The ideal gap calculation neglects fringing, manufacturing tolerance, and finite permeability. In a real design, final turns should be checked against the manufacturer's gapped-core $A_L$ value. [source: Hurley & Wolfle Ch. 3 eq. 3.36]

### Loss And Temperature

Temperature-corrected copper resistivity:

$$
\rho_w=\rho_{20}[1+\alpha_{20}(T_{max}-20^\circ\text{C})]
$$

DC winding resistance:

$$
R_{dc}=\rho_w\frac{N(MLT)}{A_{cu}}
$$

Copper loss:

$$
P_{cu}=I_{rms}^2R
$$

Core-loss density must come from the material data or a fitted Steinmetz model:

$$
P_{fe}=K_cf^\alpha B_{ac}^\beta V_e
$$

Temperature rise:

$$
\Delta T=R_\theta(P_{cu}+P_{fe})
$$

An empirical natural-convection approximation is:

$$
R_\theta=\frac{0.06}{\sqrt{V_c}}
$$

with $R_\theta$ in deg C/W for $V_c$ in m^3. [source: Hurley & Wolfle Ch. 3 eq. 3.14-3.16]

## Rules Of Thumb And Starting Assumptions

| Design choice | Practical starting point |
| --- | --- |
| Ripple ratio | Buck CCM: 20-40% of full-load current. Use lower for low ripple/noise; higher for size reduction. |
| Ferrite $B_{max}$ | 0.20-0.30 T peak for gapped ferrite inductors, checked at hot $B_{sat}$. |
| Powder/metal-composite cores | Use manufacturer DC-bias curves; saturation is gradual and tied to selected effective permeability. |
| Window utilization | 0.25-0.40 for bobbin/litz/insulated windings; up to 0.70 for simple foil or low-insulation builds. |
| Current density | 3-6 A/mm^2 natural convection; lower for hot ambient, many layers, or poor airflow. |
| Temperature rise | 20-40 deg C normal first pass; 10-15 deg C for hot ambient or high reliability. |
| Core-loss assumption | Small in low-ripple DC-biased buck inductors; not small in PFC, DCM, resonant, or large-ripple designs. |

## Sensitivity And Iteration Logic

| Variable changed | Primary effect | Tradeoff |
| --- | --- | --- |
| Increase turns $N$ | Lowers $B_{pk}$ for fixed $L$ | Raises copper length and usually copper loss; required gap grows as $N^2$. |
| Increase gap $\ell_g$ | Raises saturation current | Lowers inductance unless turns are increased; fringing becomes worse for large discrete gaps. |
| Increase core size | Lowers flux density and improves heat removal | Raises volume, mass, and cost. |
| Increase wire area | Lowers DCR and copper loss | Consumes window and may worsen proximity effect if it adds layers. |
| Increase switching frequency | Can reduce required inductance for the same ripple | Raises switching loss and can raise AC winding/core losses depending on flux swing. |

The important beginner lesson is that the gap is not a magic way to increase inductance. It increases energy capability by allowing more current before saturation. To keep the same inductance after increasing gap, turns or core size must change. [source: Magnetic-Mechanical Analogy Ref. §9]

## Coupled Filter Inductors

Coupled output inductors are used when multiple outputs share a transformer and the designer wants ripple steering or improved cross regulation. The coupled-inductor turns ratio should match the transformer secondary ratio so the common flux component cancels correctly. [source: TI SLUP132 R5-1 to R5-3]

The idealized ratio constraint is:

$$
\frac{N_{L1}}{N_{L2}}=\frac{N_{s1}}{N_{s2}}
$$

Practical limits:

- Leakage or uncoupled inductance still sets residual ripple.
- Cross-regulation depends on load distribution and controlled output.
- Winding layout can trade ripple cancellation against copper loss and insulation.

## Worked Example: Buck Gapped Core

This example condenses Hurley and Wolfle Example 3.1 and keeps the reasoning visible. [source: Hurley & Wolfle Ch. 3 Example 3.1]

### Specification

| Quantity | Value |
| --- | --- |
| Converter | Buck, 12 V input to 6 V output |
| Inductor | 34 uH target |
| Current | 20 A DC |
| Switching frequency | 80 kHz |
| Ambient | 70 deg C |
| Temperature-rise limit | 15 deg C |
| Core material | N87 MnZn ferrite |
| Selected design flux | 0.25 T versus 0.4 T saturation |
| Fill factor | 0.8 |

### Main Calculations

Duty ratio:

$$
D=\frac{6}{12}=0.5
$$

Ripple:

$$
\Delta I_L=\frac{(12-6)0.5}{80000\cdot34\times10^{-6}}=1.10\text{ A}
$$

Peak current:

$$
I_{pk}=20+0.55=20.55\text{ A}
$$

The area-product calculation gives a required $A_p=4.12\text{ cm}^4$. ETD49 has $A_p=5.62\text{ cm}^4$, so it is selected. Its catalog data are $A_e=2.09\text{ cm}^2$, $l_c=11.4\text{ cm}$, $W_a=2.69\text{ cm}^2$, $V_c=23.8\text{ cm}^3$, and $MLT=8.6\text{ cm}$. [source: Hurley & Wolfle Ch. 3 Table 3.3]

With a 15 deg C rise and $R_\theta=11\text{ deg C/W}$:

$$
P_{D,max}=\frac{15}{11}=1.36\text{ W}
$$

The optimum effective permeability calculation gives $\mu_{opt}\approx51$, corresponding to a gap near 2.24 mm. A standard 2 mm gapped ETD49 set is selected, with $A_L=188\text{ nH}$. [source: Hurley & Wolfle Ch. 3 Example 3.1]

Turns:

$$
N=\sqrt{\frac{34\times10^{-6}}{188\times10^{-9}}}=13.45
$$

Round to 13 turns:

$$
L_{actual}=13^2\cdot188\text{ nH}=31.8\text{ uH}
$$

Revised ripple:

$$
\Delta I_{actual}=\frac{(12-6)0.5}{80000\cdot31.8\times10^{-6}}=1.18\text{ A}
$$

Window check:

$$
A_{cu,max}=\frac{0.8\cdot2.69\text{ cm}^2}{13}=0.166\text{ cm}^2
$$

The selected foil conductor is 8 mm by 2 mm, or $0.16\text{ cm}^2$, so it fits. [source: Hurley & Wolfle Ch. 3 Example 3.1]

Copper resistance at 85 deg C:

$$
R_{dc}=2.165\times10^{-8}\frac{13\cdot0.086}{1.6\times10^{-5}}=1.51\text{ m}\Omega
$$

Copper loss:

$$
P_{cu}=20^2\cdot1.51\text{ m}\Omega=0.604\text{ W}
$$

Core loss is about 0.005 W because the ripple flux is small. Total loss is therefore about 0.609 W, giving:

$$
\Delta T=11\cdot0.609=6.7\text{ deg C}
$$

The design passes the 15 deg C temperature-rise budget. [source: Hurley & Wolfle Ch. 3 Example 3.1]

### Example Lessons

- ETD49 is selected because the next smaller ETD core falls below the area-product requirement.
- $B_{max}=0.25\text{ T}$ gives large margin against $B_{sat}=0.4\text{ T}$ and keeps the ferrite in a more linear region.
- The standard 2 mm gap is accepted instead of a custom 2.24 mm gap because catalog $A_L$ data closes the loop.
- Rounding down to 13 turns under-inducts by 6.5%, but the resulting ripple and saturation margin remain acceptable.
- Thick foil is acceptable here because DC current dominates and ripple RMS is small; litz becomes more attractive when ripple current is large.

Verification methods are summarized in [Verification And Measurement](./verification-and-measurement.md).
