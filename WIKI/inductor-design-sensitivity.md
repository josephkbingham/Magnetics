# Inductor Design Sensitivity

## Scope

This page records the one-variable-at-a-time sensitivity of the two governing failure quantities of a DC-biased power inductor — peak flux density $\hat{B}$ (saturation) and temperature rise $\Delta T$ (heating) — for the design-choice variables turns $N$, air gap $\ell_g$, core scale $a$, winding current density $J$, and switching frequency $f$. All scalings are algebraic consequences of the equations collected in [Equation Reference](./equation-reference.md). Each sweep holds every other variable constant at the baseline design point defined below. [source: Hurley & Wolfle Ch. 3 §3.1-§3.2] [source: Erickson & Maksimovic Ch. 11 §11.1]

## Interactive Companion

An interactive chart version of this page, with all curves computed live from the equations below (hover tooltips, per-chart data tables, light/dark themes), is stored at [interactive/inductor-design-sensitivity.html](./interactive/inductor-design-sensitivity.html) and published at <https://claude.ai/code/artifact/1d072965-b1f8-4aed-891c-baa197b5d1e7>. The dot on every curve marks the baseline design point; dashed lines mark the constraints. [source: /WIKI/inductor-design-sensitivity.md Baseline Design Point]

## GIC

### Geometry

Gapped MnZn ferrite core with $A_c = 1.0\ \text{cm}^2$, $W_a = 1.78\ \text{cm}^2$, $\ell_c = 9.2\ \text{cm}$, $V_c = 8.0\ \text{cm}^3$, $MLT = 6.6\ \text{cm}$, $\mu_r = 2000$, discrete gap $\ell_g = 1.02\ \text{mm}$. Winding is $N = 20$ turns of solid round wire filling the window at $k_u = 0.4$, giving $A_w = 3.56\ \text{mm}^2$ per conductor. [source: Hurley & Wolfle Ch. 3 §3.2] [source: Erickson & Maksimovic Ch. 11 §11.1.2-§11.1.5]

### Input

$L = 47\ \mu\text{H}$, $I_{dc} = 10\ \text{A}$, $\Delta I_{pp} = 4\ \text{A}$ (hence $\hat{I} = 12\ \text{A}$, $I_{rms} = 10.07\ \text{A}$), $f_s = 100\ \text{kHz}$, buck-type volt-second drive, natural convection, winding resistivity $\rho_w = 2.1\times10^{-8}\ \Omega\text{m}$ (copper near 100 °C). [source: TI SLUP132 §5 Design Strategy] [source: Hurley & Wolfle Ch. 3 eq. 3.37]

### Constraint

$\hat{B} \le B_{sat} = 0.35\ \text{T}$ (baseline operates at $\hat{B} = 0.28\ \text{T}$), $\Delta T \le 40\ ^\circ\text{C}$, window fill $k_u \le 0.4$. [source: Erickson & Maksimovic Ch. 11 §11.1 opening paragraphs] [source: Hurley & Wolfle Ch. 3 eq. 3.14-3.15]

## Governing Equations

Saturation gauge:

$$
\hat{B} = \frac{L\hat{I}}{N A_c} = \frac{\mu_0 N \hat{I}}{\ell_g + \ell_c/\mu_r}
$$

[source: Erickson & Maksimovic Ch. 11 eq. 11.17] [source: Magnetic-Mechanical Analogy Ref. §10.3]

Heating gauge:

$$
\Delta T = R_\theta (P_{cu} + P_{fe}), \qquad R_\theta = \frac{0.06}{\sqrt{V_c}}
$$

[source: Hurley & Wolfle Ch. 3 eq. 3.14-3.16]

$$
P_{cu} = I_{rms}^2 R, \qquad R = \rho_w \frac{N \cdot MLT}{A_w}
$$

[source: Erickson & Maksimovic Ch. 11 eq. 11.1, 11.13]

$$
P_{fe} = K_c f^\alpha B_{ac}^\beta V_c, \qquad B_{ac} = \frac{\Delta B}{2} = \frac{L\,\Delta I_{pp}}{2 N A_c}
$$

[source: Hurley & Wolfle Ch. 1 eq. 1.29] [source: TI SLUP132 §5 Design Strategy eq. 5]

AC-resistance correction applied to the ripple-current component only:

$$
R_{ac} = R_{dc}\left[1 + \frac{(r_o/\delta)^4}{48 + 0.8(r_o/\delta)^4}\right], \qquad \delta = \frac{1}{\sqrt{\pi f \mu_0 \sigma}}
$$

[source: Hurley & Wolfle Ch. 1 eq. 1.21-1.22]

Steinmetz constants used: $K_c = 2.25$, $\alpha = 1.46$, $\beta = 2.75$ (SI units), fitted so that $P_v(100\ \text{kHz}, 0.1\ \text{T}) = 80\ \text{mW/cm}^3$, representative of MnZn power ferrite; no manufacturer loss datasheet is ingested in this repository, so the specific constant values are [UNVERIFIED].

## Baseline Design Point

Evaluating the governing equations at the GIC values above gives the operating point marked on every chart. [source: /WIKI/inductor-design-sensitivity.md Governing Equations]

| Quantity | Value |
| --- | --- |
| Gap $\ell_g = \mu_0 N^2 A_c / L - \ell_c/\mu_r$ | 1.02 mm |
| Peak flux $\hat{B}$ | 0.28 T (margin to 0.35 T) |
| AC flux amplitude $B_{ac}$ | 0.047 T |
| DC resistance $R_{dc}$ | 7.8 mΩ |
| Copper loss $P_{cu}$ (incl. ripple $R_{ac}$ term) | 0.80 W |
| Core loss $P_{fe}$ | 0.08 W |
| Thermal resistance $R_\theta$ | 21.2 °C/W |
| Temperature rise $\Delta T$ | 19 °C (limit 40 °C) |

## Sensitivity Relations

Each row states the first-order scaling of both gauges when one variable is swept and the stated quantities are held constant. The scalings follow algebraically from the Governing Equations section. [source: /WIKI/inductor-design-sensitivity.md Governing Equations]

| Swept variable | Held constant | $\hat{B}$ | $P_{cu}$ | $P_{fe}$ | $\Delta T$ |
| --- | --- | --- | --- | --- | --- |
| Turns $N$ | $L$ (gap re-cut as $\ell_g \propto N^2$), window refilled so $A_w = k_u W_a / N$ | $\propto 1/N$ | $\propto N^2$ | $\propto N^{-\beta}$ | non-monotonic; copper term dominates at high $N$ |
| Gap $\ell_g$ | $N$; $L \propto 1/(\ell_g + \ell_c/\mu_r)$ follows | $\propto 1/(\ell_g + \ell_c/\mu_r)$ | rises only through the ripple term $\Delta I^2/12$ | unchanged — $\Delta B$ is volt-second-set, $L\,\Delta I = V t_{on}$ is constant | approximately flat |
| Core scale $a$ ($A_c, W_a \propto a^2$, $V_c \propto a^3$, $MLT \propto a$) | $N$, $L$ (re-gapped), window refilled | $\propto a^{-2}$ | $\propto a^{-1}$ | $\propto a^{3-2\beta} \approx a^{-2.5}$ | $\approx \propto a^{-2.5}$ (with $R_\theta \propto a^{-1.5}$) |
| Current density $J$ (wire thinned, $A_w = I_{rms}/J$) | $N$, $L$, core, gap | unchanged | $\propto J$ | unchanged | $\approx \propto J$ above the fixed $P_{fe}$ floor |
| Frequency $f$ | $L$, $N$, gap; $\Delta I \propto 1/f$ follows | $\hat{I}$ term falls as ripple shrinks | DC term unchanged; ripple term scales with $\Delta I^2 R_{ac}(f)$ | $\propto f^{\alpha-\beta}$ ($\alpha < \beta$ for ferrite, so falling) | falls with $f$ at fixed $L$ |

Window-fit bound for the $J$ sweep: $J \ge I_{rms} N / (k_u W_a) = 2.8\ \text{A/mm}^2$ at the baseline geometry; smaller $J$ requires wire that does not fit the window. [source: Erickson & Maksimovic Ch. 11 eq. 11.10, 11.20]

## Tradeoffs

- **Turns $N$ set the position between the two failure modes.** Reducing $N$ raises $\hat{B}$ toward $B_{sat}$ ($\hat{B} \propto 1/N$); raising $N$ increases $P_{cu} \propto N^2$ toward the $\Delta T$ limit. At the baseline the feasible window is approximately $N = 17$–$31$: below 17 turns $\hat{B} > 0.35\ \text{T}$, above 31 turns $\Delta T > 40\ ^\circ\text{C}$. The required gap grows as $N^2$ (4.3 mm at $N = 40$), where the no-fringing assumption fails — see [Distributed Gap And Fringing](./distributed-gap-and-fringing.md). Forcing constraints: $B_{sat}$ and $\Delta T$ limits from the GIC list.
- **The gap trades inductance for saturation margin at near-zero thermal cost.** Opening $\ell_g$ from 0.2 mm to 3 mm drops $\hat{B}$ from 1.07 T to 0.13 T while $\Delta T$ moves only 18→20 °C, because $\Delta B$ is volt-second-set and only the ripple RMS term grows. The cost is exported to the converter: $L$ falls $\propto 1/\ell_g$ and $\Delta I_{pp}$ rises accordingly, loading the output capacitor and switches. Forcing constraint: $\hat{B} \le B_{sat}$ traded against the converter ripple budget in [Inductor Design Inputs](./inductor-design-inputs.md).
- **Core scale is the only variable that improves both gauges simultaneously** ($\hat{B} \propto a^{-2}$, $\Delta T \approx a^{-2.5}$), which is the structural reason a single area-product number $A_p = A_c W_a \propto a^4$ suffices for first-pass core selection in [Thermal Design And Core Selection](./thermal-design-and-core-selection.md). The traded quantities are volume, mass, and cost, all $\propto a^3$. Forcing constraint: packaging/mechanical limits from the GIC list.
- **Wire size is a pure heating variable.** $P_{cu} \propto J$ while $\hat{B}$ is exactly unchanged, so wire gauge buys temperature margin only; the largest wire that fits the window ($J = 2.8\ \text{A/mm}^2$ here) minimizes $\Delta T$, and the baseline design uses it. Forcing constraint: $k_u \le 0.4$ window fill.
- **At fixed $L$, higher $f$ relaxes this inductor** — ripple, $\hat{B}$, and $P_{fe} \propto f^{\alpha-\beta}$ all fall — and the practical use of that margin is reducing $L \propto 1/f$ to shrink the core, at the cost of switching loss in the semiconductors and rising AC winding resistance ($\delta \propto 1/\sqrt{f}$, dominant in transformers per [High-Frequency Effects](./high-frequency-effects.md)). Forcing constraint: converter-level efficiency budget, decided upstream of the magnetic design.

## Limits

The curves use the first-order design model only: uniform flux, no fringing correction (large-gap $\hat{B}$ values read high and $L$ values read low relative to a fringing-corrected model), the empirical natural-convection $R_\theta = 0.06/\sqrt{V_c}$, solid round wire with the low-order $R_{ac}$ approximation applied to ripple current only, and sinusoidal-equivalent Steinmetz core loss. Accuracy is the same class as a first-pass hand design; bench validation methods are on [Verification And Measurement](./verification-and-measurement.md). [source: Hurley & Wolfle Ch. 2 §2.5] [source: Hurley & Wolfle Ch. 3 eq. 3.16] [source: Hurley & Wolfle Ch. 1 eq. 1.22, 1.29]

## Related Pages

- [Equation Reference](./equation-reference.md)
- [Inductor Design Inputs](./inductor-design-inputs.md)
- [Thermal Design And Core Selection](./thermal-design-and-core-selection.md)
- [Worked Example: Buck Gapped Core](./worked-example-buck-gapped-core.md)
- [Air Gap And Saturation](./air-gap-and-saturation.md)
- [Distributed Gap And Fringing](./distributed-gap-and-fringing.md)
- [High-Frequency Effects](./high-frequency-effects.md)
- [Verification And Measurement](./verification-and-measurement.md)
- [Index](./index.md)
