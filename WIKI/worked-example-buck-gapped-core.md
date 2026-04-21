# Worked Example: Buck Gapped Core

## Source Case

This page condenses Hurley and Wolfle Example 3.1 into a wiki-format reference because it is the first full buck-inductor worked example present in the current raw-source set. [source: Hurley & Wolfle Ch. 3 Example 3.1]

## GIC

### Geometry

Selected core: ETD49 ferrite core with $A_c = 2.09\ \text{cm}^2$, $l_c = 11.4\ \text{cm}$, $W_a = 2.69\ \text{cm}^2$, $A_p = 5.62\ \text{cm}^4$, $V_c = 23.8\ \text{cm}^3$, and $MLT = 8.6\ \text{cm}$. The manufacturer-supplied discrete gap selected in the example is 2 mm with $A_L = 188\ \text{nH}$. [source: Hurley & Wolfle Ch. 3 Table 3.3 and Example 3.1 gap section]

### Input

Buck-converter specification: $V_{in} = 12\ \text{V}$, $V_{out} = 6\ \text{V}$, $L = 34\ \mu\text{H}$, DC current 20 A, switching frequency 80 kHz, ambient 70 $^\circ$C, temperature rise 15 $^\circ$C, and $k_u = 0.8$. [source: Hurley & Wolfle Ch. 3 Table 3.1]

### Constraint

Material: EPCOS N87 MnZn ferrite with $B_{sat} = 0.4\ \text{T}$. The example chooses $B_{max} = 0.25\ \text{T}$, limits total temperature rise to 15 $^\circ$C, and treats core loss as negligible relative to winding loss because the ripple is small. [source: Hurley & Wolfle Ch. 3 Table 3.2 and Example 3.1 discussion]

## Calculation Summary

### Ripple And Peak Current

With duty ratio $D = V_o/V_s = 0.5$, the ripple-current amplitude is

$$
\Delta I_L = \frac{(V_s - V_o)DT}{L} = 1.1\ \text{A}
$$

and the peak current is

$$
\hat{I} = I_{dc} + \frac{\Delta I}{2} = 20.55\ \text{A}
$$

[source: Hurley & Wolfle Ch. 3 Example 3.1]

### Core Selection

The energy term is

$$
L\hat{I}^2 = 0.0144\ \text{J}
$$

and the resulting area-product estimate is

$$
A_p = 4.12\ \text{cm}^4
$$

so the ETD49 is selected. [source: Hurley & Wolfle Ch. 3 Example 3.1]

The manufacturer thermal resistance is 11 $^\circ$C/W, which implies a maximum allowable dissipation of

$$
P_D = \frac{15}{11} = 1.36\ \text{W}
$$

[source: Hurley & Wolfle Ch. 3 Example 3.1]

### Optimum Effective Permeability And Gap

The example computes

$$
\mu_{opt} = 51
$$

and from this derives a maximum gap target of 2.24 mm. A standard 2 mm gapped core set is then chosen from the manufacturer offering. [source: Hurley & Wolfle Ch. 3 Example 3.1]

### Turns And Wire

From the manufacturer $A_L$ value,

$$
N = \sqrt{\frac{L}{A_L}} = 13.5
$$

and the example chooses 13 turns. The required conductor area is 0.119 cm$^2$, and the example selects an 8 mm by 2 mm conductor. [source: Hurley & Wolfle Ch. 3 Example 3.1]

### Losses

At $T_{max} = 85\ ^\circ$C, the example computes

$$
R_{dc} = 1.51\ \text{m}\Omega
$$

and copper loss

$$
P_{cu} = 0.604\ \text{W}
$$

[source: Hurley & Wolfle Ch. 3 Example 3.1]

The flux-density ripple is

$$
\Delta B = 0.014\ \text{T}
$$

and the corresponding core loss is only

$$
P_{fe} = 0.005\ \text{W}
$$

for total loss of 0.609 W. [source: Hurley & Wolfle Ch. 3 Example 3.1]

## Design Decision

This example is valuable because it shows a low-ripple buck inductor where copper loss dominates strongly over core loss. That confirms the design choice to size primarily for current, temperature rise, and window use while using ferrite plus a discrete gap to control inductance and saturation. [source: Hurley & Wolfle Ch. 3 Example 3.1]

## Related Pages

- [Buck Output Filter Inductor Design](./buck-output-filter-inductor-design.md)
- [Thermal Design And Core Selection](./thermal-design-and-core-selection.md)
- [Distributed Gap And Fringing](./distributed-gap-and-fringing.md)
- [Verification And Measurement](./verification-and-measurement.md)
- [Index](./index.md)