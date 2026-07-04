# Air Gap And Saturation

## Gap-Dominated Magnetic Circuit

For an inductor with a core section and an air gap in series, the reluctances are

$$
\mathcal{R}_c = \frac{\ell_c}{\mu A_c}
$$

and

$$
\mathcal{R}_g = \frac{\ell_g}{\mu_0 A_c}
$$

[source: Erickson & Maksimovic Ch. 10 eq. 10.27]

The winding MMF drives total flux according to

$$
ni = \Phi (\mathcal{R}_c + \mathcal{R}_g)
$$

[source: Erickson & Maksimovic Ch. 10 eq. 10.28]

The corresponding inductance is

$$
L = \frac{n^2}{\mathcal{R}_c + \mathcal{R}_g}
$$

[source: Erickson & Maksimovic Ch. 10 eq. 10.31]

## Why The Gap Exists

The source text gives two reasons for adding an air gap to practical inductors. First, when the gap reluctance dominates the total reluctance, the inductance becomes less sensitive to variations in the core permeability $\mu$. Second, the onset-of-saturation current increases when gap reluctance is added. [source: Erickson & Maksimovic Ch. 10 discussion following eq. 10.31]

At the onset of saturation,

$$
\Phi_{sat} = B_{sat} A_c
$$

and the corresponding current is

$$
I_{sat} = \frac{B_{sat} A_c}{n}(\mathcal{R}_c + \mathcal{R}_g)
$$

[source: Erickson & Maksimovic Ch. 10 eq. 10.32-10.33]

## Tradeoffs

Increasing $\ell_g$ increases $\mathcal{R}_g$, which increases saturation current but decreases inductance because $L = n^2/(\mathcal{R}_c + \mathcal{R}_g)$. The forcing constraint in a CCM buck output inductor is usually simultaneous satisfaction of required inductance and allowable peak current without core saturation. [source: Erickson & Maksimovic Ch. 10 eq. 10.31-10.33] [source: Erickson & Maksimovic Ch. 11 §11.1]

## Related Pages

- [Electromagnetic Fundamentals](./electromagnetic-fundamentals.md)
- [Magnetic-Mechanical Analogy](./magnetic-mechanical-analogy.md)
- [Equation Reference](./equation-reference.md)
- [Buck Output Filter Inductor Design](./buck-output-filter-inductor-design.md)
- [Verification And Measurement](./verification-and-measurement.md)
- [Index](./index.md)
