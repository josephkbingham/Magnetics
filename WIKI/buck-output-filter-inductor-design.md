# Buck Output Filter Inductor Design

## Scope

This page summarizes the first-pass design procedure for a CCM buck-converter filter inductor using the $K_g$ method. The source text states that the inductor value is usually chosen so the ripple peak magnitude is a small fraction of the full-load dc current component, and that an air gap is used to prevent saturation at the peak current. [source: Erickson & Maksimovic Ch. 11 §11.1 opening paragraph]

## GIC

### Geometry

The assumed geometry is a single-winding inductor on a gapped magnetic core characterized by core cross-sectional area $A_c$, window area $W_A$, mean length per turn $MLT$, core path length, and gap length $\ell_g$. [source: Erickson & Maksimovic Ch. 11 §11.1.2-§11.1.5]

### Input

The first-pass design inputs are wire resistivity $\rho$, peak winding current $I_{max}$, inductance $L$, winding resistance $R$, fill factor $K_u$, and maximum operating flux density $B_{max}$. [source: Erickson & Maksimovic Ch. 11 §11.2 summary table]

### Constraint

The design must simultaneously satisfy required inductance, avoid saturation at $I_{max}$, fit the winding inside the usable window area, and keep winding resistance low enough to meet the copper-loss budget. [source: Erickson & Maksimovic Ch. 11 §11.1 opening paragraphs] [source: Erickson & Maksimovic Ch. 11 eq. 11.1, 11.6, 11.7, 11.10, 11.13]

## Constraint Equations

### Maximum Flux Density

With the air gap dominating the inductor properties,

$$
n I_{max} = B_{max} \frac{\ell_g}{\mu_0}
$$

[source: Erickson & Maksimovic Ch. 11 eq. 11.6]

### Inductance

The required inductance is

$$
L = \frac{\mu_0 A_c n^2}{\ell_g}
$$

[source: Erickson & Maksimovic Ch. 11 eq. 11.7]

### Winding Area

The copper area must fit within the usable window area:

$$
K_u W_A \ge n A_W
$$

[source: Erickson & Maksimovic Ch. 11 eq. 11.10]

### Winding Resistance

Using mean length per turn,

$$
R = \rho \frac{n(MLT)}{A_W}
$$

[source: Erickson & Maksimovic Ch. 11 eq. 11.13]

### Core Geometry Constant

Eliminating the unknowns leads to the required core-selection inequality

$$
K_g = \frac{A_c^2 W_A}{MLT} \ge \frac{\rho L^2 I_{max}^2}{B_{max}^2 R K_u}
$$

[source: Erickson & Maksimovic Ch. 11 eq. 11.14-11.15]

## First-Pass Procedure

1. Determine a target winding resistance from the allowed copper loss using $P_{cu} = I_{rms}^2 R$. [source: Erickson & Maksimovic Ch. 11 eq. 11.1]
2. Choose a core whose $K_g$ satisfies the required lower bound. In centimeter-based core tables, the source gives

$$
K_g \ge \frac{\rho L^2 I_{max}^2}{B_{max}^2 R K_u}10^8
$$

[source: Erickson & Maksimovic Ch. 11 eq. 11.16]
3. Determine number of turns from

$$
n = \frac{L I_{max}}{B_{max} A_c}10^4
$$

with $A_c$ in cm$^2$. [source: Erickson & Maksimovic Ch. 11 eq. 11.17]
4. Determine the approximate air gap from

$$
\ell_g = \frac{\mu_0 A_c n^2}{L}10^{-4}
$$

with $A_c$ in cm$^2$. The source explicitly notes that this is approximate and neglects fringing, so the final gap generally needs correction. [source: Erickson & Maksimovic Ch. 11 eq. 11.18 and following discussion]
5. Check wire area against the window-fit condition

$$
A_W \le \frac{K_u W_A}{n}
$$

[source: Erickson & Maksimovic Ch. 11 eq. 11.20]

## Tradeoffs

Increasing $L$ or $I_{max}$ increases the required $K_g$ and therefore pushes the design toward a larger core. Increasing $B_{max}$ reduces the required core size, but this choice is constrained by saturation margin and material loss. Allowing larger winding resistance reduces required core size at the cost of higher copper loss and temperature rise. [source: Erickson & Maksimovic Ch. 11 discussion following eq. 11.14-11.15]

## Limits Of This Procedure

The source text states that this procedure is first-pass only and neglects detailed insulation requirements, conductor eddy-current losses, temperature rise, and turn-count roundoff. Designs therefore require iteration after geometry is chosen. [source: Erickson & Maksimovic Ch. 11 §11.2 opening paragraph]

The added Hurley and Wolfle source extends this first-pass design by explicitly introducing temperature rise, current density, area-product core selection, and manufacturer $A_L$ data for finalizing turns and gap. That material is summarized in [Thermal Design And Core Selection](./thermal-design-and-core-selection.md) and instantiated in [Worked Example: Buck Gapped Core](./worked-example-buck-gapped-core.md). [source: Hurley & Wolfle Ch. 3 §3.1-§3.2] [source: Hurley & Wolfle Ch. 3 Example 3.1]

## Related Pages

- [Electromagnetic Fundamentals](./electromagnetic-fundamentals.md)
- [Air Gap And Saturation](./air-gap-and-saturation.md)
- [Distributed Gap And Fringing](./distributed-gap-and-fringing.md)
- [Core Materials And Losses](./core-materials-and-losses.md)
- [Thermal Design And Core Selection](./thermal-design-and-core-selection.md)
- [Worked Example: Buck Gapped Core](./worked-example-buck-gapped-core.md)
- [Verification And Measurement](./verification-and-measurement.md)
- [Index](./index.md)