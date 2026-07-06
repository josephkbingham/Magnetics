# High-Frequency And Winding Effects

This page consolidates winding AC loss, core loss, skin effect, proximity effect, and practical conductor-choice notes.

## Skin Depth

Skin effect reduces the effective conduction area as frequency rises. Skin depth is:

$$
\delta=\frac{1}{\sqrt{\pi f\mu\sigma}}
$$

For round wire, a first approximation for AC resistance is:

$$
R_{ac}=R_{dc}\left[1+\frac{(r_o/\delta)^4}{48+0.8(r_o/\delta)^4}\right]
$$

[source: Hurley & Wolfle Ch. 1 eq. 1.21-1.22] [source: Hurley & Wolfle Ch. 4 eq. 4.36]

Rules of thumb:

- If conductor thickness or radius is much less than skin depth, skin effect is small.
- If it is several skin depths thick, AC resistance can be much larger than DCR.
- Apply AC resistance to the AC current component, not blindly to the whole DC current. A DC-biased inductor with tiny ripple can tolerate a conductor that would be poor for a transformer winding.

## Proximity Effect

Proximity effect is loss caused by the magnetic field of nearby conductors forcing current crowding. It can dominate skin effect in multilayer windings.

Practical mitigations:

- Use fewer layers where possible.
- Interleave transformer windings when leakage must be low.
- Use litz wire for high-ripple or high-frequency windings when strand diameter is chosen for the operating frequency.
- Use foil carefully: it can be excellent for high-current, low-turn, low-ripple windings, but poor when the AC field cuts through its thickness.
- Keep winding copper away from discrete air gaps when fringing field is strong.

[source: Hurley & Wolfle Ch. 1 §1.4.1]

## Core Loss

Core-loss mechanisms include hysteresis and eddy currents. Hysteresis loss is tied to the area of the $B$-$H$ loop. Eddy-current loss is induced current loss inside conductive magnetic material. Ferrites reduce eddy-current loss through high resistivity; laminated steels reduce it by breaking up current paths. [source: Erickson & Maksimovic Ch. 10 §10.3.1] [source: Hurley & Wolfle Ch. 1 §1.4.3]

The Steinmetz form is:

$$
P_{fe}=K_cf^\alpha B_{max}^\beta
$$

For converter waveforms, use the manufacturer's recommended loss method when available. The simple Steinmetz equation is a first-pass approximation and can be inaccurate for nonsinusoidal excitation or large DC bias.

## Frequency Tradeoff

Higher switching frequency can reduce required inductance, turns, and core size, but it increases:

- Semiconductor switching loss.
- Transformer AC winding loss.
- Proximity effect.
- Core loss if flux swing is not reduced enough.
- EMI difficulty.

For an inductor held at fixed inductance and fixed voltage, increasing frequency reduces ripple and can reduce AC flux swing. In a real converter, designers usually spend that margin by reducing inductance or core size, so losses must be recalculated after every frequency change.

## Conductor Selection

| Conductor | Useful when | Watchouts |
| --- | --- | --- |
| Solid round wire | Low frequency, small currents, simple windings. | Skin/proximity loss above modest frequencies, poor packing for high current. |
| Parallel round wires | Moderate current and easier termination than litz. | Current sharing and proximity loss depend on layout. |
| Litz wire | High AC current, transformer windings, PFC/large-ripple inductors. | Expensive, termination-sensitive, not useful if strand size is wrong. |
| Foil | Low-turn high-current windings, strong DC component, planar-like layouts. | Edge effects, proximity loss, insulation between layers, poor performance if thick compared with skin depth and AC current is large. |
| PCB/planar copper | Repeatable low-profile transformers and inductors. | Limited copper thickness, thermal spreading, high capacitance, via/termination loss. |

## Example: Why Thick Foil Worked In The Buck Inductor

In the ETD49 buck-inductor example, the foil is 2 mm thick while copper skin depth at 80 kHz is about 0.26 mm. The AC-to-DC resistance ratio is therefore poor. However, ripple current is only 1.18 A peak-to-peak on a 20 A DC current, so ripple RMS is:

$$
I_{ripple,rms}=\frac{\Delta I}{2\sqrt{3}}\approx0.34\text{ A}
$$

The AC copper loss is tiny compared with the DC copper loss. That same foil choice would be much less attractive in a transformer winding or a high-ripple PFC inductor.

## Practical Checklist

1. Split current into DC, RMS, and AC components.
2. Calculate DCR at hot copper temperature.
3. Estimate skin depth at the relevant ripple or winding frequency.
4. Check layer count and proximity-effect risk.
5. Choose conductor type.
6. Calculate copper loss using the appropriate resistance for each current component.
7. Check fringing-field exposure near discrete gaps.
8. Verify temperature rise with a real build.

## Related Pages

- [Master Design Guide](./master-design-guide.md)
- [Core, Gap, And Thermal Design](./core-gap-and-thermal-design.md)
- [Inductor Design Deep Dive](./inductor-design-deep-dive.md)
- [Transformer Design Deep Dive](./transformer-design-deep-dive.md)
- [Equation Reference](./equation-reference.md)
- [Verification And Measurement](./verification-and-measurement.md)
