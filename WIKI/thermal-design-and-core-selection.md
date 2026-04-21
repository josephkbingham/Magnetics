# Thermal Design And Core Selection

## Scope

The Hurley and Wolfle source extends first-pass inductor design beyond inductance, saturation, and DC copper loss by making temperature rise an explicit design constraint. The design basis is core selection from stored energy, maximum flux density, and allowable temperature rise, followed by winding design. [source: Hurley & Wolfle Ch. 3 opening paragraph]

## GIC

### Geometry

The relevant core geometry is captured by cross-sectional area $A_c$, magnetic path length $l_c$, window area $W_a$, mean length per turn $MLT$, core volume $V_c$, and area product $A_p = A_c W_a$. [source: Hurley & Wolfle Ch. 3 §3.2]

### Input

The design inputs are inductance, peak or DC current, switching frequency, allowable temperature rise, ambient temperature, waveform factor $K_i$, and window utilization factor $k_u$. [source: Hurley & Wolfle Ch. 3 §3.2 summary]

### Constraint

The design must satisfy maximum flux density, maximum dissipation, current-density limit implied by thermal performance, and the selected gap or effective permeability. [source: Hurley & Wolfle Ch. 3 eq. 3.5, 3.8, 3.24, 3.35]

## Thermal Equation

The total inductor loss is the sum of copper loss and core loss. The source models steady temperature rise by

$$
\Delta T = R_{\theta} Q = \frac{1}{h_c A_t} Q
$$

where $Q$ is total loss, $h_c$ is the convection coefficient, and $A_t$ is external surface area. [source: Hurley & Wolfle Ch. 3 eq. 3.14-3.15]

The same section gives an empirical thermal-resistance approximation based on core volume:

$$
R_{\theta} = \frac{0.06}{\sqrt{V_c}}
$$

with $R_{\theta}$ in $^\circ$C/W for $V_c$ in m$^3$. [source: Hurley & Wolfle Ch. 3 eq. 3.16]

The source also notes that a typical natural-convection design value of $h_c = 10\ \text{W/m}^2\, ^\circ\text{C}$ is often used for switch-mode cores, while forced convection may move $h_c$ into the 10 to 30 W/m$^2\, ^\circ$C range. [source: Hurley & Wolfle Ch. 3 §3.1.6]

## Current Density And Window Use

Window utilization is defined as

$$
k_u = \frac{W_c}{W_a}
$$

and the source states practical values ranging from roughly 0.2 to 0.8 depending on winding arrangement and insulation requirements. [source: Hurley & Wolfle Ch. 3 eq. 3.18 and following discussion]

The thermal-current-density result is

$$
J_o = \sqrt{\frac{1}{1 + \gamma} \frac{h_c A_t \Delta T}{\rho_w V_w k_u}}
$$

[source: Hurley & Wolfle Ch. 3 eq. 3.24]

Using dimensional analysis and the area product $A_p$, the same source reduces this to

$$
J_o = K_t \sqrt{\frac{\Delta T}{k_u(1 + \gamma)}} \frac{1}{\sqrt[8]{A_p}}
$$

with

$$
K_t = \sqrt{\frac{h_c k_a}{\rho_w k_w}}
$$

[source: Hurley & Wolfle Ch. 3 eq. 3.28-3.29]

## Area-Product Core Selection

Starting from stored energy and current-density constraints, the source derives the inductor area-product requirement:

$$
A_p = \left[ \frac{\sqrt{1 + \gamma}\, K_i L \hat{I}^2}{B_{max} K_t \sqrt{k_u \Delta T}} \right]^{8/7}
$$

[source: Hurley & Wolfle Ch. 3 eq. 3.35]

This equation selects the core family and size before turns, wire, and exact gap are finalized. The source then proceeds by manufacturer data: choose a standard core with known $A_c$, $W_a$, $MLT$, $l_c$, and core volume. [source: Hurley & Wolfle Ch. 3 §3.2]

## Optimum Effective Permeability

The source makes the effective permeability an optimization variable balancing flux-density and dissipation limits. The optimum value is given as

$$
\mu_{opt} = \frac{B_{sat} l_c K_i}{\mu_0 \sqrt{\frac{P_{cu\ max} k_u W_a}{\rho_w MLT}}}
$$

[source: Hurley & Wolfle Ch. 3 eq. 3.20]

For discrete-gap cores, this result determines the gap target. For distributed-gap cores, it determines the effective-permeability grade to select from the manufacturer. [source: Hurley & Wolfle Ch. 3 §3.2]

## Procedure

1. Specify $L$, current, $f$, $\Delta T$, ambient, and $k_u$. [source: Hurley & Wolfle Ch. 3 §3.2 summary]
2. Select a material and choose $B_{max}$ consistent with saturation and loss. [source: Hurley & Wolfle Ch. 3 §3.1.2, §3.1.5]
3. Compute required $A_p$ and choose a standard core. [source: Hurley & Wolfle Ch. 3 eq. 3.35]
4. Compute $\mu_{opt}$ and then choose either discrete gap or distributed-gap effective permeability. [source: Hurley & Wolfle Ch. 3 eq. 3.20 and §3.2]
5. Compute turns from manufacturer $A_L$ data:

$$
N = \sqrt{\frac{L}{A_L}}
$$

[source: Hurley & Wolfle Ch. 3 eq. 3.36]
6. Correct conductor resistivity for operating temperature:

$$
\rho_w = \rho_{20}[1 + \alpha_{20}(T_{max} - 20^\circ\text{C})]
$$

[source: Hurley & Wolfle Ch. 3 eq. 3.37]
7. Compute winding loss from actual wire choice and iterate if thermal or flux limits are violated. [source: Hurley & Wolfle Ch. 3 eq. 3.38]

## Related Pages

- [Buck Output Filter Inductor Design](./buck-output-filter-inductor-design.md)
- [Distributed Gap And Fringing](./distributed-gap-and-fringing.md)
- [Worked Example: Buck Gapped Core](./worked-example-buck-gapped-core.md)
- [Index](./index.md)