# Verification And Measurement

## Source-Backed Measurement Methods

The added Hurley and Wolfle source provides explicit measurement procedures for inductance under bias, incremental inductance, $B$-$H$ loops, and core-loss testing.

### Step-Voltage Method For Inductance Under DC Excitation

The inductor is modeled as a series $R$-$L$ element driven by a constant-voltage step from a charged capacitor. The source gives the discrete flux-linkage update

$$
\lambda(k) = V\Delta t - Ri(k)\Delta t + \lambda(k-1)
$$

and then computes inductance point-by-point as

$$
L(i_k) = \frac{\lambda(k)}{i(k)}
$$

[source: Hurley & Wolfle Ch. 8 eq. 8.1-8.3 and §8.1.1]

This directly yields inductance as a function of current and exposes the onset of saturation when $L(i)$ collapses. [source: Hurley & Wolfle Ch. 8 Example 8.1]

### Incremental Impedance Method For AC Inductance Under DC Bias

The source describes a decoupled DC-plus-AC setup where the DC current is established independently, a small AC stimulus is injected, and the AC impedance is measured. The impedance and incremental inductance are computed as

$$
Z = \frac{v_{ac}}{i_{ac}}
$$

$$
L_{ac} = \frac{1}{\omega}\sqrt{\frac{v_{ac}^2}{i_{ac}^2} - R^2}
$$

[source: Hurley & Wolfle Ch. 8 eq. 8.4-8.6 and §8.1.2]

This provides the AC inductance-versus-DC-bias characteristic needed to verify incremental behavior near saturation. [source: Hurley & Wolfle Ch. 8 Example 8.2]

### B-H Loop Measurement

For a toroidal sample, the magnetic field intensity is obtained from current

$$
H_c = \frac{N}{l_c} i
$$

and flux density is obtained by integrating the coil voltage

$$
B = \frac{1}{N A_c} \int v\,dt
$$

[source: Hurley & Wolfle Ch. 8 eq. 8.7-8.8]

For sinusoidal excitation the source also gives

$$
B_{max} = \frac{V_{peak}}{2\pi f N A_c}
$$

[source: Hurley & Wolfle Ch. 8 eq. 8.9]

The source explicitly notes that hysteresis-loss density can be obtained from the enclosed loop area. [source: Hurley & Wolfle Ch. 8 §8.2]

### Open-Circuit Test For Transformer Core Loss

With rated voltage applied and the secondary open, the input power is approximately equal to core loss. The source gives

$$
R_c = \frac{V_{oc}^2}{P_{oc}}
$$

and

$$
X_c = \frac{1}{\sqrt{\frac{1}{Z_\phi^2} - \frac{1}{R_c^2}}}
$$

[source: Hurley & Wolfle Ch. 8 eq. 8.15-8.18 and §8.3.2]

### High-Frequency Core-Loss Test

At switching frequencies, the source replaces the wattmeter with a gain-phase meter and holds flux constant across frequency by keeping $E_{rms}/f$ constant using

$$
E_{rms} = 4.44 f N B_{max} A_c
$$

[source: Hurley & Wolfle Ch. 8 eq. 8.19 and §8.3.3]

The measured core loss is then

$$
P_{fe} = a v_2 \frac{v_{ref}}{R_{ref}} \cos\theta
$$

[source: Hurley & Wolfle Ch. 8 eq. 8.20]

The source also states that temperature control is important during this test because the core heats during measurement. [source: Hurley & Wolfle Ch. 8 §8.3.3]

## Remaining Gaps Relative To Schema

The schema also mentions AC resistance versus frequency, impedance-analyzer sweeps, and thermal imaging. The current raw source set still does not provide a dedicated primary-source procedure for those specific workflows, so they remain unverified in this wiki. [source: /magnetics-wiki-schema.md §3 Measurement and Verification]

- [UNVERIFIED] AC-resistance-versus-frequency measurement method. [source: /magnetics-wiki-schema.md §3 Measurement and Verification]
- [UNVERIFIED] Dedicated impedance-analyzer sweep workflow for magnetic components. [source: /magnetics-wiki-schema.md §3 Measurement and Verification]
- [UNVERIFIED] Thermal-imaging validation method. [source: /magnetics-wiki-schema.md §3 Measurement and Verification]

## Next Source Needed

To complete this page without unverified placeholders, add manufacturer app notes, measurement notes, or lab procedures that explicitly describe bias-inductance measurement, AC resistance measurement, and core-loss test setups. [source: /magnetics-wiki-schema.md §1] [source: /magnetics-wiki-schema.md §4.1]

## Related Pages

- [Buck Output Filter Inductor Design](./buck-output-filter-inductor-design.md)
- [Worked Example: Buck Gapped Core](./worked-example-buck-gapped-core.md)
- [Core Materials And Losses](./core-materials-and-losses.md)
- [Air Gap And Saturation](./air-gap-and-saturation.md)
- [Thermal Design And Core Selection](./thermal-design-and-core-selection.md)
- [Index](./index.md)