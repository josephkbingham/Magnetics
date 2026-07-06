# Transformer Design Deep Dive

This page merges the former transformer methodology, practical transformer model, insulation, and fractional-turn notes. Use [Master Design Guide](./master-design-guide.md) for the short workflow.

## True Transformer Versus Flyback Coupled Inductor

A true transformer transfers energy through mutual flux while ideally storing no load energy. Practical energy appears in magnetizing inductance and leakage inductance, but those are design constraints or parasitics. A flyback "transformer" stores the transferred energy in magnetizing inductance, so it is a gapped coupled inductor and should be designed with [Inductor Design Deep Dive](./inductor-design-deep-dive.md). [source: TI SLUP132 §2 Core Limitations in SMPS Applications] [source: TI SLUP132 §5 Flyback Transformer Design]

## Input Contract

| Group | Inputs |
| --- | --- |
| Electrical specification | Input voltage range, output voltages/currents, power, rectifier drops, duty-cycle range, and regulation method. [source: Hurley & Wolfle Ch. 5 §5.2] |
| Waveform | Primary voltage waveform, reset method, volt-second balance, switching frequency, and waveform factor $K_v$. [source: Hurley & Wolfle Ch. 4 eq. 4.62] |
| Winding set | Turns ratio targets, RMS and AC current in each winding, auxiliary winding requirements, and total winding VA. [source: Hurley & Wolfle Ch. 4 §4.3.2] |
| Magnetic constraints | Candidate material, $A_e$, $W_a$, $MLT$, $V_e$, design $B_{max}$, core-loss data, magnetizing-current target, and leakage target. |
| Thermal constraints | Ambient, cooling method, allowed temperature rise, loss budget, and hot-spot limit. [source: Hurley & Wolfle Ch. 5 §5.2] |
| Insulation constraints | Working voltage, peak voltage, transient voltage, creepage, clearance, insulation class, bobbin/tape/wire insulation, and hipot target. [source: Hurley & Wolfle Ch. 5 §5.4] |

## Strict Design Equations

### Voltage, Flux, And Turns

The general transformer voltage equation is:

$$
V_{rms}=K_v f N B_{max} A_e
$$

Equivalently, volt-seconds set flux swing:

$$
\Delta B=\frac{1}{NA_e}\int v(t)\,dt
$$

The first primary-turn check is:

$$
N_p\ge\frac{\int v_p(t)\,dt}{A_e\Delta B_{allow}}
$$

The ideal turns-ratio relation is:

$$
\frac{V_s}{V_p}\approx\frac{N_s}{N_p}
$$

In converter transformers, the voltages in this ratio must include duty cycle, rectifier drops, switch drops, and regulation headroom.

### Area Product And Thermal Optimization

Summing all winding VA gives:

$$
\sum VA=K_v f B_{max} J k_f k_u A_p
$$

The winding loss model is:

$$
P_{cu}=\rho_w V_w k_u J^2
$$

The core-loss model is:

$$
P_{fe}=K_c f^\alpha B_{max}^\beta V_e
$$

At fixed frequency, the optimized loss relation is:

$$
P_{cu}=\frac{\beta}{2}P_{fe}
$$

The fixed-frequency area-product estimate is:

$$
A_p=\left[\frac{\sqrt{2}\sum VA}{K_vfB_ok_fK_t\sqrt{k_u\Delta T}}\right]^{8/7}
$$

If saturation limits operation, use the saturation-limited initial estimate:

$$
A_{p1}=\left[\frac{\sqrt{2}\sum VA}{K_vfB_{sat}k_fK_t\sqrt{k_u\Delta T}}\right]^{8/7}
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.73-4.83] [source: Hurley & Wolfle Ch. 5 eq. 5.4-5.15]

### Practical Transformer Model

The magnetizing balance is:

$$
N_1I_1-N_2I_2=\Phi_m\mathcal{R}
$$

Reflected secondary current:

$$
I_2'=\frac{1}{a}I_2
$$

Reflected secondary impedance:

$$
R_2'=a^2R_2, \qquad X_{l2}'=a^2X_{l2}
$$

Equivalent series terms:

$$
R_{eq}=R_1+a^2R_2
$$

$$
X_{eq}=X_{l1}+a^2X_{l2}
$$

Mutual inductance with non-ideal coupling:

$$
M=k\sqrt{L_{11}L_{22}}
$$

[source: Hurley & Wolfle Ch. 4 eq. 4.34-4.58]

## Rules Of Thumb And Starting Assumptions

| Design choice | Practical starting point |
| --- | --- |
| Ferrite $B_{max}$ | 0.12-0.22 T for many 50-200 kHz power transformers; reduce at higher frequency or high ambient. |
| Window fill | 0.25-0.40 for isolated transformers; use 0.30-0.35 early unless layout data say otherwise. |
| Current density | 3-5 A/mm^2 natural convection; lower for high ambient, high AC loss, or many layers. |
| Loss split | Start with core and copper losses in the same range, then optimize using material and winding data. |
| Magnetizing current | Usually a penalty in PWM transformers; intentionally large only when required by resonant operation or control. |
| Leakage inductance | A parasitic maximum in most PWM supplies, but may be a functional energy element in PSFB/LLC designs. |

## Insulation And Safety

The current source set distinguishes dielectric insulation, creepage along an insulating surface, and clearance through air. Insulation strength depends on dielectric material, surface condition, pollution level, humidity, pressure, and temperature. [source: Hurley & Wolfle Ch. 5 §5.4]

Voltage definitions to collect:

- RMS working voltage.
- Peak working voltage.
- Abnormal or transient voltages.

Operational insulation is not the same as safety isolation. Hazardous-to-user-accessible barriers may require double or reinforced insulation. Practical transformer insulation elements include bobbin isolation, wire enamel, tape between winding layers, sleeving, and spacers for creepage. The source notes that transformer window utilization is often near 40% because insulation consumes window area. [source: Hurley & Wolfle Ch. 5 §5.4.1-§5.4.2]

Design rule: never treat creepage/clearance as a rule-of-thumb substitution for the applicable safety standard. Use the one-page guide only to remember that insulation must be part of the geometry from the start.

## Fractional-Turn Transformers

Fractional turns are useful when high frequency and low secondary voltage make the optimum secondary turn count less than one full turn, or when small integer turns create unacceptable ratio error. Dixon gives:

$$
N_{optimum}=(V_N\Delta t/A_e\Delta B)\cdot10^4
$$

with $A_e$ in cm^2. [source: TI SLUP132 R6-1]

An E-E core with equal outer legs can create an electrical half turn by winding around one outer leg, because that conductor links half of the total flux. More generally, if a winding links fraction $F$ of the outer-leg permeance:

$$
F=\frac{P_3}{P_2+P_3}=\frac{A_3}{A_2+A_3}
$$

then the no-load voltage relation is:

$$
\frac{V_{out}}{V_{in}}=\frac{N_s+F}{N_p}
$$

The major penalty is leakage:

$$
L=F(1-F)P
$$

The worst case is one-half turn. Practical implementations therefore need flux balancing, such as parallel half-turns on equal outer legs, cross-connected foil half-cylinders, or a separate flux-balancing winding. [source: TI SLUP132 R6-2 to R6-6]

## Design Procedure

1. Confirm this is a true transformer, not a flyback coupled inductor.
2. Define input/output voltages, currents, power, frequency, ambient, temperature rise, and insulation requirements.
3. Compute turns ratio from the circuit, including duty cycle and voltage drops.
4. Select material and starting $B_{max}$ from loss and hot saturation.
5. Use volt-seconds to calculate primary turns.
6. Use the turns ratio to calculate secondaries and auxiliaries, then round to manufacturable integers.
7. Use area product and window fill to choose a core.
8. Lay out windings for current density, skin depth, proximity loss, leakage, capacitance, and insulation.
9. Calculate copper loss, core loss, magnetizing current, leakage, temperature rise, and voltage regulation.
10. Iterate core size, turns, material, winding arrangement, and frequency until all checks pass.

## Verification Targets

- Turns ratio and output voltages across line/load range.
- Magnetizing inductance and magnetizing current.
- Leakage inductance and clamp/resonant behavior.
- DCR and AC resistance per winding.
- Core loss and total temperature rise.
- Creepage, clearance, insulation resistance, and hipot where applicable.
- Converter-level waveform checks for flux walking, reset, and switch stress.

Measurement methods are summarized in [Verification And Measurement](./verification-and-measurement.md).
