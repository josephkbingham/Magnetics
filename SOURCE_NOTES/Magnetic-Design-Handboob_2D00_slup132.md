![Power Supply Design Seminar graphic](page_1_image_2_v2.jpg)

**Power Supply Design Seminar**

# Magnetics Design Handbook

*by Lloyd H. Dixon, Jr.*

Topic Categories:
**Basic Magnetic Technology**
**Magnetic Component Design**

Reproduced from
2001 Unitrode Magnetics Design Handbook

© 2001, 2011 Texas Instruments Incorporated

**Power Seminar topics and online power-**
**training modules are available at:**
**power.ti.com/seminars**

![Texas Instruments logo](page_1_image_1_v2.jpg)

# Table of Contents

## Magnetics Design Section

Introduction and Basic Magnetics 1-1
Magnetic Core Characteristics 2-1
Windings 3-1
Power Transformer Design 4-1
Inductor and Flyback Transformer Design 5-1

## Reference Design Section

Magnetic Core Properties R1-1
Eddy Current Losses in Transformer Windings and Circuit Wiring R2-1
Deriving the Equivalent Electrical Circuit from the Magnetic Device Physical Properties R3-1
The Effect of Leakage Inductance on Switching Power Supply Performance R4-1
Coupled Filter Inductors in Multiple Output Buck Regulators Provide Dramatic Performance Improvement R5-1
How to Design a Transformer with Fractional Turns R6-1
Winding Data R7-1

Texas Instruments
ii
SLUP132

# Introduction

*Texas Instruments Presents*

## **The Magnetics Design Handbook for Switching Power Supplies**

*By Lloyd H. Dixon*

The success or failure of a SwitchMode Power Supply design depends heavily on the magnetic components. Circuit optimization and magnetic device optimization are closely interrelated. This manual provides a comprehensive approach to magnetics design especially relevant to high frequency SMPS applications. Circuit designers will benefit from the ability to design, or participate in the design of the magnetic components.

Sections 1, 2, and 3 provide an overview of basic magnetic theory and discuss practical design aspects, including core material characteristics, how to predict and minimize high frequency winding losses, and how to minimize parasitic inductance and capacitance.

Sections 4 and 5 apply these principles to practical examples of transformer, filter inductor and flyback transformer design, utilizing an approach which optimizes utilization of the magnetic core, thereby minimizing size and cost. Cookbook examples of a variety of magnetic devices are presented to illustrate the design techniques used. This material was presented at Unitrode Power Supply Design Seminars between 1997 and 2000. An on-line audio and slide version of this material is available free of charge on the Texas Instruments web site at: **power.ti.com**.

### **About the Author**

Lloyd was a cofounder of a Unitrode predecessor company in 1958. Presently retired, Lloyd continues as one of the contributors and presenters at TI-Unitrode Seminars. Almost his entire career has been in the semiconductor industry in an applications engineering role. Lloyd has made significant contributions in power factor correction and control loop design. His unorthodox approach to teaching magnetics design for switching power supplies is always well received.

![Unitrode Products from Texas Instruments](page_3_image_1_v2.jpg)

Texas Instruments
iii
SLUP132

# Magnetics Design for Switching Power Supplies
Lloyd H. Dixon

# Section 1 Introduction and Basic Magnetics

## Introduction
Experienced SwitchMode Power Supply designers know that SMPS success or failure depends heavily on the proper design and implementation of the magnetic components. Parasitic elements inherent in high frequency transformers or inductors cause a variety of circuit problems including: high losses, high voltage spikes necessitating snubbers or clamps, poor cross regulation between multiple outputs, noise coupling to input or output, restricted duty cycle range, etc. Figure 1 represents a simplified equivalent circuit of a two-output forward converter power transformer, showing leakage inductances, core characteristics including mutual inductance, dc hysteresis and saturation, core eddy current loss resistance, and winding distributed capacitance, all of which affect SMPS performance.

With rare exception, schools of engineering provide very little instruction in practical magnetics relevant to switching power supply applications. As a result, magnetic component design is usually delegated to a self-taught expert in this "black art". There are many aspects in the design of practical, manufacturable, low cost magnetic devices that unquestionably benefit from years of experience in this field. However, the magnetics expert is unlikely to be sufficiently aware of the SMPS circuit problems caused by the various parasitic elements and the impact of the specific circuit locations of these elements. This often results in poor decisions in the magnetic component design.

This collection of topics on magnetics is intended to give the SMPS designer the confidence and the ability to: (1) Develop a reasonably accurate electrical circuit model of any magnetic device, to enable prediction of circuit performance, (2) Relate the electrical circuit model to the magnetic device structure, thus providing the insight needed to achieve an  optimized design, (3) Collaborate effectively with experts in magnetics design, and possibly (4) Become a "magnetics expert" in his own right.

![Transformer Equivalent Circuit diagram showing primary winding P with capacitance Cw, resistance RE, and inductance LP-S1, and secondary windings S1 and S2 with leakage inductance L1-2, all coupled through an ideal transformer and core.](page_4_image_1_v2.jpg)
Figure 1-1 Transformer Equivalent Circuit

## Obstacles to learning magnetics design
In addition to the lack of instruction in practical magnetics mentioned above, there are several other problems that make it difficult for the SMPS designer to feel "at home" in the magnetics realm:

*   *Archaic concepts and practices.* Our great-grandparents probably had a better understanding of practical magnetics than we do today. Unfortunately, in an era when computation was difficult, our ancestors developed concepts intended to minimize computation (such as "circular mils") and other shortcuts, still in use, which make the subject of magnetics more complex and confusing to us today. Ancient design equations intended for sinusoidal waveforms (and not clearly defined as such) are often incorrectly applied to rectangular SMPS waveforms.
*   *The CGS system of units.* Magnetics design relationships expressed in the modern SI system of units (rationalized MKS) are much simpler than in the archaic CGS system. SI equations are much easier to understand and remember. Unfortunately, in the U.S., core and magnet wire data is

Texas Instruments
1-1
SLUP132

usually published in the old-fashioned CGS system, with dimensions often in inches, requiring data conversion to apply to the SI system.

*   *Energy/time vs. power.* Circuit designers are comfortable in the electrical realm of Volts and Amperes. On a Volt/Ampere plot, area represents power. Time is not directly involved.

But on a plot of magnetic flux density, B, vs. field intensity, H, area represents energy. Time is always required to change flux density, because an energy change must take place. A change in flux density, $\Delta B$, within a winding equates to the integral volt-seconds per turn across the winding (Faraday's Law). Time is definitely involved. This concept takes some getting used to.

**An appeal to suppliers of core materials and wire:** Old-time magnetics designers in the U.S. are acclimated to the CGS system, and may prefer magnetics data expressed in Gauss and Oersteds. But newcomers to magnetics design, as well as experienced designers outside the U.S. prefer the internationally accepted SI system - Tesla and Ampere-Turns. Also, cores and wire dimensional data should *definitely* be provided in metric units.

Core losses are usually characterized as a function of frequency using sinusoidal current-driven waveforms. This is erroneous and misleading for high frequency SMPS applications. High frequency core losses are primarily caused by eddy currents, which depend on rate of flux change, not on frequency per se. (At a fixed switching frequency, higher $V_{IN}$ with short duty cycle results in higher loss.) It would be most helpful if materials intended primarily for SMPS applications were characterized using rectangular voltage-driven waveforms, with examples shown of core loss and minor hysteresis loops under these conditions.

## Magnetic Field Relationships

Understanding the rules that govern the magnetic field is extremely valuable in many aspects of switching power supply design, especially in minimizing parasitics in circuit wiring, as well as in magnetic device design.

Figure 1-2 shows the field surrounding two parallel conductors, each carrying the same current but

![Diagram showing the magnetic field lines (solid) and equipotential surfaces (dashed) around a pair of parallel conductors carrying current in opposite directions.](page_5_image_1_v2.jpg)

Figure. 1-2 Field Around Conductor Pair

in opposite directions, i.e. a pair of wires connecting an electrical source to a load.

The solid lines represent magnetic *flux*, while the dash lines represent an edge view of the *magnetic field equipotential surfaces*. Each wire has an individual field, symmetrical and radial, with field intensity diminishing in inverse proportion to the distance from the conductor. These two fields are of equal magnitude but opposite in polarity because the currents that generate the fields are in opposite directions. As shown in Fig. 1-2, the two fields, by superposition, reinforce each other in the region between the two wires, but elsewhere they tend to cancel, especially at a distance from the wires where the opposing field intensities become nearly equal.

Figure 1-3 shows the field associated with a simple air cored winding. The individual fields from each wire combine to produce a highly concentrated and fairly linear field within the winding. Outside the winding, the field diverges and weakens. Although the stored energy density is high within the winding, considerable energy is stored in the weaker field outside the winding because the volume extends to infinity.

A magnetic field cannot be blocked by "insulating" it from its surroundings - magnetic "insulation" does not exist. However, the magnetic field *can* be short-circuited - by placing the coil of Fig 1-3 inside

Texas Instruments
1-2
SLUP132

![Diagram of an air-core solenoid showing magnetic flux lines and current direction in the coils.](page_6_image_1_v2.jpg)

Figure. 1-3 Air-Core Solenoid

a box of high permeability magnetic material, which provides an easy path for the return flux, shielding the coil from the environment external to the box

*   Flux lines are always normal to the magnetic field equipotential surfaces.

*   At any location, flux density is always proportional to field intensity: $B = \mu H$

**Conservation of energy:** At any moment of time, the magnetic field and the current flow distribute themselves so as to minimize the energy taken from the source. If alternative current paths exist, current will initially flow in the path(s) resulting in minimum stored energy, but in the long term, the current flow redistributes so as to minimize $I^2R$ loss. Reference (R2) has more on this subject.

## Transformation of Axes

SMPS circuit designers are obviously interested in the electrical characteristics of the magnetic device as seen at the device terminals.

## Important Magnetic Field Principles

*   The total magnetic field integrated around any closed path equals the total ampere-turns enclosed by that path (Ampere's Law)

*   Magnetic field equipotentials are *surfaces*, not lines. (Alternatively, field intensity can be represented as a vector normal to the surface.)

*   Magnetic field equipotential surfaces are *bounded and terminated by the current* which generates the field. They are not closed surfaces, as with electric field equipotentials.

*   Flux is in the form of *lines*, not surfaces. (Flux can also be represented as a vector.)

*   Flux lines are *always closed loops* – they never begin or end. In any arbitrary volume, the number of flux lines entering must equal the number leaving, regardless of the contents of that volume.


<table>
  <thead>
    <tr>
        <th>Axis</th>
        <th>Labels</th>
    </tr>
  </thead>
  <tbody>
    <tr>
        <td>Vertical</td>
        <td>B<br/>$\phi = B \cdot A$<br/>$\int Edt = N\phi$</td>
    </tr>
    <tr>
        <td>Horizontal</td>
        <td>H<br/>$F = H \cdot l$<br/>$I = \frac{F}{N}$</td>
    </tr>
  </tbody>
</table>

Figure. 1-4 Transformation of Axes

Figure 1-4 shows how the horizontal and vertical axes scale factors can be altered so that the *B-H* characteristic (defining a *core material*) is translated into a $\phi$ vs. $\mathcal{F}$ (mmf) characteristic (defining a *specific core* with magnetic area $A_e$ and path length $l_e$). Transforming the axes once again using Faraday's Law and Ampere's Law, the same curve now represents the equivalent electrical characteristics of that core when wound with N turns, $\int Edt$ vs. $I$.

Note that the slope of the *B-H* characteristic is permeability, the slope of the $\phi$ vs. $\mathcal{F}$ characteristic is

Texas Instruments
1-3
SLUP132

permeance, while the slope of the $\int Edt$ vs. $I$ characteristic is inductance.

## Systems of Units

The internationally accepted SI system of units (Système International d'Unités) is a rationalized system, in which permeability, $\mu = \mu_0 \cdot \mu_r$ ($\mu_0$ is the absolute permeability of free space or nonmagnetic material $= 4\pi \cdot 10^{-7}$; $\mu_r$ is the relative permeability of a magnetic material). In the unrationalized CGS system, $\mu_0 = 1$, therefore $\mu_0$ is omitted from CGS equations so that $\mu = \mu_r$. But the rationalization constant $\mu_0$ doesn't just disappear in the CGS system — instead, portions of this constant show up in all the CGS equations, complicating them and making them more difficult to intuitively grasp. In the SI system, all of the "garbage" is gathered into $\mu_0$, thereby simplifying the SI equations.

The equations below are given in both systems — SI and CGS. It is suggested that beginners in magnetics design stick to the SI equations and ignore the CGS system until completely comfortable with the principles involved. Then, it may be helpful to use the CGS system when working with magnetics data expressed in CGS units, rather than convert the units.

### Table I
### Magnetic Parameters and Conversion Factors

<table>
  <thead>
    <tr>
        <th> </th>
        <th> </th>
        <th>SI</th>
        <th>CGS</th>
        <th>CGS to SI</th>
    </tr>
  </thead>
  <tbody>
    <tr>
        <td>FLUX DENSITY</td>
        <td>B</td>
        <td>Tesla</td>
        <td>Gauss</td>
        <td>10⁻⁴</td>
    </tr>
    <tr>
        <td>FIELD INTENSITY</td>
        <td>H</td>
        <td>A-T/m</td>
        <td>Oersted</td>
        <td>1000/4π</td>
    </tr>
    <tr>
        <td>PERMEABILITY (space)</td>
        <td>μ₀</td>
        <td>4π·10⁻⁷</td>
        <td>1</td>
        <td>4π·10⁻⁷</td>
    </tr>
    <tr>
        <td>PERMEABILITY (relative)</td>
        <td>μᵣ</td>
        <td> </td>
        <td> </td>
        <td>1</td>
    </tr>
    <tr>
        <td>AREA (Core Window)</td>
        <td>Aₑ, A_w</td>
        <td>m²</td>
        <td>cm²</td>
        <td>10⁻⁴</td>
    </tr>
    <tr>
        <td>LENGTH (Core, Gap)</td>
        <td>lₑ, l_g</td>
        <td>m</td>
        <td>cm</td>
        <td>10⁻²</td>
    </tr>
    <tr>
        <td>TOTAL FLUX = ∫BdA</td>
        <td>φ</td>
        <td>Weber</td>
        <td>Maxwell</td>
        <td>10⁻⁸</td>
    </tr>
    <tr>
        <td>TOTAL FIELD = ∮Hdl</td>
        <td>F, mmf</td>
        <td>A-T</td>
        <td>Gilbert</td>
        <td>10/4π</td>
    </tr>
    <tr>
        <td>RELUCTANCE = F/φ</td>
        <td>R</td>
        <td>A-T/Wb</td>
        <td>Gb/Mx</td>
        <td>10⁹/4π</td>
    </tr>
    <tr>
        <td>PERMEANCE = 1/R</td>
        <td>P</td>
        <td> </td>
        <td> </td>
        <td>4π·10⁻⁹</td>
    </tr>
    <tr>
        <td>INDUCTANCE = P·N²</td>
        <td>L</td>
        <td>Henry</td>
        <td>(Henry)</td>
        <td>1</td>
    </tr>
    <tr>
        <td>(SI) ENERGY</td>
        <td>W</td>
        <td>Joule</td>
        <td>Erg</td>
        <td>10⁻⁷</td>
    </tr>
  </tbody>
</table>

Ampere's Law and Faraday's Law jointly govern the important relationship between the magnetic elements and the equivalent electrical circuit as seen across the windings.

## Ampere's Law

**SI:**

$$F = \oint Hdl = NI \approx Hl \quad \text{A-T}$$
$$H \approx NI / l \quad \text{A-T/m (1)}$$

**CGS:**

$$F = \oint Hdl = .4\pi NI \approx Hl \quad \text{Gilberts}$$
$$H \approx .4\pi NI / l \quad \text{Oersteds (1a)}$$

Amperes Law states that the total magnetic force, $F$, along a closed path is proportional to the ampere-turns in a winding or windings linked to that path, i.e., that the path passes through. In the SI system, the units of magnetic force are expressed in ampere-turns. When the field intensity $H$ varies along the path, $H$ must be integrated along the path length. Fortunately, the simplified form shown in Eq. 1 and 1a can be used in most situations.

## Faraday's Law

**SI:**

$$\frac{d\phi}{dt} = \frac{E}{N} ; \quad \Delta\phi = \frac{1}{N} \int Edt \quad \text{Weber (2)}$$

**CGS:**

$$\frac{d\phi}{dt} = \frac{E}{N} \times 10^8 ; \quad \Delta\phi = \frac{10^8}{N} \int Edt \quad \text{Maxwell (2a)}$$

Faraday's Law equates the flux rate of change through a winding to the volts/turn applied to the winding. Thus, the flux change is proportional to the integral volt-seconds per turn (directly equal in the SI system). Faraday's Law operates bilaterally — that is, if 2.5 volts/turn is applied to winding A, the flux through A will change by 2.5 Webers/second. If a second winding, B, is linked to all of the flux produced by winding A, then 2.5 Volts/turn will be induced in B.

Faraday's Law makes it clear that flux cannot change instantaneously. Any flux change requires time and usually a change in energy. Time is required to move along the $\phi$ or $B$ axis, which is more obvious

Texas Instruments
1-4
SLUP132

considering the electrical equivalent scale dimensions are Volt-seconds.

Note that all flux lines follow a closed loop path. Flux lines have no beginning or end.

## Energy

**SI:**

$$ W / m^3 = \int HdB \approx \frac{1}{2} BH $$

$$ W = \int Vol \cdot HdB = \int I \cdot Edt \quad \text{Joules} \quad (3) $$

**CGS:**

$$ W = \int Vol \cdot HdB = \int I \cdot Edt \cdot 10^{-7} \quad \text{Ergs} \quad (3a) $$

Energy put into and removed from the magnetic system can be determined by integrating the area between the characteristic and the vertical axis ($B$, $\phi$, $\int Edt$) on the energy plane. Energy must be integrated over time, which is a factor on the vertical axis, not the horizontal.

It is much easier to understand this process by using the electrical equivalent axes, Volt-seconds and Amperes. Referring to Fig. 1-5, from point A to B, energy from the external circuit is put into the magnetic system, as shown by the shaded area between A-B and the vertical axis. From B to C, magnetically stored energy is returned to the electrical circuit. The difference between the energy put in and taken out is hysteresis loss, the area between the two curves. At C, the magnetically stored energy is zero.

From C to D, energy is put into the system. From D back to A energy is returned to the electrical circuit. The area between the curves is loss. At A, the remaining stored energy is zero.

A positive energy sign indicates energy put in; a negative sign indicates energy returning to the external circuit. From A to B, voltage and current are both positive, so the energy sign is positive. Although the integrated Volt-seconds are negative at A, *upward movement indicates positive voltage*. From B to C, current is positive but voltage is negative (downward movement). Therefore the energy sign is negative. From C to D, current and voltage are both negative, hence positive energy. From D to A, negative current with positive voltage indicates returning energy.

## Permeability

**SI:**
$$ \mu = \mu_0 \mu_r = B / H \quad \text{Tesla/A-T/m} $$

**CGS:**
$$ \mu = \mu_r = B / H \quad \text{Gauss/Oersted} $$

Permeability is a measure of a magnetic material — the amount of flux which a magnetic field can push through a unit volume of the material. Permeability is roughly analogous to conductivity in the electrical realm.


![Hysteresis loop on the energy plane showing the relationship between integrated voltage (∫Edt) and current (I), with points A, B, C, and D labeled across four quadrants.](page_8_layout_ocr_mvxf_50_424_241_265.png)

Figure 1-5 Energy Plane

Texas Instruments
1-5
SLUP132

![Energy Plane plots for different devices under sinusoidal voltage drive, showing relationships between integral of voltage (∫Edt) and current (I) for (a) air core inductor, (b) capacitor, (c) resistor, and (d) inductor with hysteresis.](page_9_image_1_v2.jpg)

Figure 1-6 - Energy Plane, Sinusoidal Voltage Drive Examples

## Permeance, Reluctance

**SI:**

$$ \mathcal{P} = 1/\mathcal{R} = \phi/\mathcal{F} = BA/H\ell $$

Webers/A-T

$$ \mathcal{P} = 1/\mathcal{R} = \mu_0\mu_r A/\ell $$

**CGS:**

$$ \mathcal{P} = 1/\mathcal{R} = \phi/\mathcal{F} = BA/H\ell $$

Maxwells/Gilbert

$$ \mathcal{P} = 1/\mathcal{R} = \mu \cdot A/\ell $$

When the material characteristic, permeability, is applied to a magnetic element of specific area and length, the result is *permeance*. In the SI system, permeance is equal to the inductance of a single turn.

Reluctance, the reciprocal of permeance, is analogous to resistance in an electrical circuit. (Don't push this analogy too far - reluctance is an energy storage element, whereas resistance is a dissipative element.) Reluctance and permeance can be defined for the entire magnetic device as seen from the electrical terminals, but it is most useful to define the reluctance of specific elements/regions within the device. This enables the construction of a reluctance model - a magnetic circuit diagram - which sheds considerable light on the performance of the device and how to improve it. From the reluctance model, using a duality process, a magnetic device can be translated into its equivalent electrical circuit, in-

cluding parasitic inductances, such as shown in Fig. 1-1.

This will be discussed in a later section.

## Inductance

**SI:**

$$ L = N^2\mathcal{P} = \mu_0\mu_r N^2 \cdot A/\ell \quad \text{Henrys (4)} $$

**CGS:**

$$ L = 4\pi\mu_r N^2 \cdot A/\ell \cdot 10^{-9} \quad \text{Henrys (4a)} $$

Inductance has the same value in the SI and CGS systems. In the SI system, inductance is simply the permeance times the number of turns squared.

## At Home on the Energy Plane

It is, of course, possible to plot any type of electrical device on the energy plane $\int Edt$ vs. $I$. Figure 1-6 shows several different devices - inductors, capacitors, resistors - driven by a sinusoidal voltage waveform. Before looking at Figure 1-7 which shows the waveforms involved, try to identify the devices represented in Fig. 1-6.

The answers:

**Fig. 1-6 (a)** is an air core inductor, ideal and lossless. Current lags the applied voltage, but as shown in Fig. 1-7, the inductor current is in phase with $\int Edt$ plotted on the vertical axis of the energy

Texas Instruments
1-6
SLUP132

plane. As the waveform traverses from B to C, voltage and current are both positive – energy is put into the inductor. from C to D, current is positive but voltage is negative – the same energy previously stored is given back to the circuit.

**Fig.1-4 (b)** is an ideal, lossless capacitor. Current leads the applied voltage and is therefore 180° out of phase with $\int Edt$. From A to B, voltage and current are both positive – energy is put into the capacitor. From B to C, the same energy previously stored is returned to the circuit.

**Fig.1-6 (c)** is a resistor. Current is in phase with applied voltage, therefore current leads $\int Edt$ by 90°. Since voltage and current are in phase, their signs are always the same. The energy sign is always positive – energy is always put into the resistor, never returned to the circuit. The entire area within the ellipse represents loss.

Of course, Faraday's Law does not apply to a resistor or capacitor. Therefore the vertical $\int Edt$ scale for these devices cannot be translated into flux.

**Fig.1-6 (d)** is an inductor with idealized metal alloy core with low frequency hysteresis, driven into saturation. A tape-wound Permalloy core driven at low frequency (no eddy currents) approaches this characteristic. The area within the characteristic is hysteresis loss. The only energy returned to the circuit is the area of the thin wedges above and below the characteristic. Only when the core saturates, taking on the characteristic of an air core, is any energy stored and returned.

The dashed characteristic shows a minor hysteresis loop occurring with reduced drive, which does not take the core into saturation.









<table>
  <thead>
    <tr>
        <th>Point</th>
        <th>E, IR</th>
        <th>∫Edt</th>
        <th>IL</th>
        <th>IC</th>
        <th>ICORE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
        <td>A</td>
        <td>0</td>
        <td>-1</td>
        <td>-1</td>
        <td>0</td>
        <td>0</td>
    </tr>
    <tr>
        <td>B</td>
        <td>1</td>
        <td>0</td>
        <td>0</td>
        <td>1</td>
        <td>0.5</td>
    </tr>
    <tr>
        <td>C</td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
    </tr>
    <tr>
        <td>D</td>
        <td>-1</td>
        <td>0</td>
        <td>0</td>
        <td>-1</td>
        <td>-0.5</td>
    </tr>
    <tr>
        <td>A</td>
        <td>0</td>
        <td>-1</td>
        <td>-1</td>
        <td>0</td>
        <td>0</td>
    </tr>
  </tbody>
</table>

Figure 1-7 Sinusoidal Voltage Drive

Texas Instruments
1-7
SLUP132

![Three plots on the energy plane (∫Edt vs. I) for (a) a lossless air-core inductor, (b) a resistor, and (c) an idealized metal-cored inductor, all under rectangular voltage drive.](page_11_image_1_v2.jpg)

Figure 1-8 - Rectangular Voltage Drive Examples

## Rectangular Voltage Drive Waveform

Sinusoidal waveshapes are not relevant in most SMPS applications. Figure 1-8 shows the same devices driven by a symmetrical rectangular voltage waveform (not including the capacitor, which would require an infinite current at the instantaneous voltage transitions). Figure 1-9 shows the corresponding waveforms.

**Fig.1-8 (a)** is the same lossless air-core inductor as in 1-6 (a). Although the characteristic looks the same as with sinusoidal drive, Fig. 1-9 waveforms reveal that the characteristic dwells at its extremes during times of zero applied voltage.

**Fig.1-8 (b)** The same resistor as in 1-6 (c) plots as a rectangle rather than an ellipse. The rectangular voltage and current waveforms exist at three distinct levels. From B to C, the voltage and current are both at a constant positive level, while $\int Edt$ slowly rises. Thus, the current is constant while $\int Edt$ changes. From C to D, current suddenly collapses to zero, where it dwells until time E, because $\int Edt$ does not change while the voltage is zero. At time F, the current suddenly changes to its constant negative level, where it remains while $\int Edt$ slowly drops toward G.

**Fig.1-8 (c)** The same idealized metal-cored inductor as Fig.1-6 (d) exhibits the same shape on the energy plane although the driving waveshape is quite different.

In fact, with any practical inductor with magnetic core, the low-frequency hysteresis loop (excluding eddy currents) does not change shape radically when frequency or voltage or the waveshape are changed. But with a resistor, unlike the inductor, the energy plane plot expands in all directions as a function of voltage, the plot changes vertically inversely with frequency, and changes shape as a function of the driving waveshape, as seen in the difference between Fig.1-8 (b) and 1-6 (c).

And no matter how many Volt-seconds are applied to the resistor, it will never saturate like the inductor in Fig.1-8 (c).

Noting the striking similarity between the resistor characteristic of Fig. 1-8 (b) and the dash line unsaturated square-loop inductor characteristic of Fig. 1-8 (c), raises an interesting question: If inductance is defined as the slope on the plot of $\int Edt$ vs. I, then the resistor in (b) is an inductor - it has infinite inductance along B to C and F to G, just like the unsaturated inductor in 1-8 (c).

But if a resistor is defined as a device that does not store energy, only dissipates energy, then the inductor of Fig.1-8 (c) is a resistor!!

## Notes on the SMPS Environment

**Transformer Definition:** A true transformer is a magnetic device with multiple windings whose purpose is *not* to store energy, but to transfer energy instantaneously from input to output(s). In addition, the windings are often electrically insulated to provide high voltage dc isolation between input and output. The turns ratio can be adjusted to obtain optimum relationship between input and output voltages.

Texas Instruments
1-8
SLUP132

![Waveforms showing rectangular voltage drive, integral of voltage, inductor current, and core current.](page_12_layout_ocr_laxc_50_36_251_480.png)

Fig. 1-9 Rectangular Voltage Drive

A practical transformer does store some energy in mutual (magnetizing) inductance and leakage inductances, which degrade circuit performance in several important respects. These inductances are normally considered undesirable parasitics, whose minimization is one of the important goals of transformer design.

**Inductor Definition:** An inductor is a device whose purpose is to store and release energy. A filter inductor uses this capability to smooth the current through it. A flyback transformer is actually an inductor with multiple windings. It stores energy taken

from the input in its mutual inductance during one portion of the switching period, then delivers energy to the output during a subsequent interval.

Since the magnetic core material itself is incapable of storing significant energy, energy storage is accomplished in a non-magnetic gap(s) in series with the core.

Although mutual inductance is an essential element in a flyback transformer, leakage inductances remain undesired parasitic elements.

**Core Material Limitations:** In dc applications, inductors are thought of as current operated devices. Even the smallest dc voltage will ultimately saturate the magnetic core, unless offset by the IR drop in the winding.

In high frequency SMPS applications, the major core material limitations are saturation and core losses, both of which depend upon flux swing. In these applications, transformer and inductor windings are usually driven with rectangular voltage waveforms derived from low impedance sources. Since the voltage, pulse width, and number of turns are quite accurately known, it is easy to apply Faraday's Law to determine the flux swing and appropriately limit it. In a ferrite core transformer, magnetizing current is difficult to determine accurately. It depends entirely on the core material characteristic which varies widely with temperature and with the flatness of the mating surfaces of the core halves. Fortunately, the magnetizing current in a transformer is small enough to be of less concern than the flux swing.

In an inductor or flyback transformer, the magnetizing current is vitally important, because it represents the energy storage required by the application. In this case, the magnetizing current can be calculated quite accurately using Ampere's Law, because it depends on the very predicable characteristics of the gap in series with the core, and the uncertain core contribution to energy storage is negligible.

**Points to Remember:**

*   Magnetic field equipotentials are surfaces, bounded by the current generating the field.

*   All flux lines form complete loops that never begin or end, normal to field equipotentials.

*   Flux change cannot occur instantaneously – time is required – an energy change occurs.

Texas Instruments
1-9
SLUP132

*   Energy added and removed is quantified by integrating the area between the characteristic and the vertical axis.

*   On the energy plane, upward movement in Quadrants I and IV or downward movement in QII and QIII *add* energy to the device. Moving downward in QI and QIV, or upward in QII and QIII returns energy to the circuit.

*   The purpose of an inductor is to store energy. In a transformer, energy storage represents an undesired parasitic element.

## References

*"R-numbered" references are reprinted in the Reference Section at the back of this Manual.*

(1) T.G. Wilson, Sr., "Fundamentals of Magnetic Materials," APEC Tutorial Seminar, 1987

(R2) "Eddy Current Losses in Transformer Windings and Circuit Wiring," Unitrode Seminar Manual SEM400, 1985

Texas Instruments
1-10
SLUP132

# Section 2 Magnetic Core Characteristics

Familiarity with the mechanisms underlying magnetic core behavior is essential to (a) optimize the magnetic device design, and (b) properly model its behavior in the circuit application.

## The Purpose of the Magnetic Core

The fundamental purpose of any magnetic core is to provide an easy path for flux in order to facilitate flux linkage, or coupling, between two or more magnetic elements. It serves as a "magnetic bus bar" to connect a magnetic source to a magnetic "load".

In a true transformer application, the magnetic source is the primary winding – ampere-turns and volts/turn. The magnetic "load" is the secondary winding (or windings). The flux through the core links the windings to each other. It also enables electrical isolation between windings, and enables adaptation to different voltage levels by adjusting the turns ratio. Energy storage in a transformer core is an undesired parasitic element. With a high permeability core material, energy storage is minimal.

In an inductor, the core provides the flux linkage path between the circuit winding and a non-magnetic gap, physically in series with the core. Virtually all of the energy is stored in the gap. High permeability ferrites, or magnetic metal alloys such as Permalloy, are incapable of storing significant energy. (The integrated area between the nearly vertical high permeability *B-H* characteristic and the vertical axis, representing energy, is minuscule.)

A flyback transformer is actually an inductor with primary and secondary windings and a gap which stores the required energy. Like a simple inductor, the core provides the flux linkage path between the primary and the gap. The core also provides the linkage between the gap and the secondary winding(s) to subsequently deliver the energy to the secondary circuit. Like a transformer, the separate windings also enable electrical isolation between windings, and turns ratio adaptation to different circuit voltages.

## Magnetic Core Materials

This paper builds upon Reference (R1), titled "Magnetic Core Properties", taken from an earlier Unitrode seminar and reprinted in the Reference Section at the back of this handbook. It discusses magnetic basics and the process of magnetization in ferromagnetic materials. This topic should be read before proceeding further.

## Metal Alloy Tape-Wound Cores

Reference (R1) focuses primarily upon the low-frequency characteristics of metal alloy tape-wound cores. Using alloys such as Permalloy, these cores approach the ideal magnetic material characteristic – square-loop with extremely high permeability (60,000), high saturation flux density (0.9 Tesla = 9000 Gauss) and insignificant energy storage. Unfortunately, resistivity of these metal alloys is quite low. To minimize losses due to induced eddy currents, these cores are built up with very thin tape-wound laminations.

Tape-wound cores are used primarily at 50, 60, and 400 Hz line frequencies. Disappointingly, they are generally unsuitable for transformer applications in SwitchMode Power Supplies. At today's SMPS frequencies (100kHz and up), eddy current losses are too great even with extremely thin 12.5µm (.0005") tape thickness. However, in SMPS filter inductor applications, gapped tape-wound cores are sometimes used when the percent ripple current and associated flux swing is small enough to keep losses at an acceptable level.

Tape-wound cores using the newer, lower loss amorphous metal alloys are used in SMPS applications up to 100-200kHz, especially as magnetic amplifiers.

## Powdered Metal Cores

Composite powdered-metal cores, such as powdered iron, Kool Mµ®, and Permalloy powder cores *do* store considerable energy, and are therefore used in inductor and flyback transformer applications. However, energy is *not* stored in the very high permeability magnetic metal portions of the composite,

Texas Instruments
2-1
SLUP132

but in the *non-magnetic* regions between the magnetic particles – in the binder that holds the cores together. Essentially, these composite cores store their energy in a non-magnetic gap that is distributed throughout the entire core. These cores are manufactured and categorized by their effective permeability (the permeability of a hypothetical homogeneous core material with the same characteristic as the actual composite). Different effective permeabilities in the range of $\approx 15$ to $\approx 200$ (relative) are achieved by varying particle size and the amount of magnetically inert material in the composite mix.

Composite powdered metal cores are not normally used in true transformer applications because their relatively low permeability results in high magnetizing current and energy storage – undesired in a transformer.

At SMPS frequencies, powdered metal cores are quite lossy. Powdered iron is worst, Kool M$\mu$ is better, Permalloy is best. But in filter inductor or continuous mode flyback applications (where the inductive energy is stored in the non-magnetic regions within the composite core), if the percent $\Delta I$ and flux swing are small enough, the losses may be low enough to permit the use of these composite materials.

Rounding of the *B-H* characteristic (which will be discussed later) causes incremental inductance to decrease substantially as the DC operating point is raised. Typically, the inductance may be halved at an operating flux density of 0.4Tesla (4000 Gauss), only half way to saturation.

The much greater saturation flux density $B_{SAT}$ of the powdered metal cores compared to ferrite (0.8T vs. 0.3T) would permit a much smaller inductor as a gapped ferrite for the same application, but at 100 kHz and above, this promise is seldom fulfilled because of the restrictions imposed by losses and rounding.

# Ferrite Cores

Ferrites are the most popular core materials used in SMPS applications.

Ferrites are ceramic materials made by sintering a mixture of iron oxide with oxides or carbonates of either manganese and zinc or nickel and zinc. MnZn ferrites are used in applications up to 1 or 2 MHz and

include the power ferrite materials used in switching power supplies. NiZn ferrites have lower permeability and much higher resistivity, hence lower losses. They are used from 1 MHz to several hundred MHz.

The permeability of power ferrite materials is in the range of 1500 to 3000 (relative). As shown in the low frequency characteristic of Fig. 2-1, a ferrite core will store a small amount of energy, as shown by the areas between the hysteresis loop and the vertical axis. This undesired magnetizing energy must be subsequently dealt with in a snubber or clamp. Sometimes it can be put to good use in Zero Voltage Transition circuitry. The permeability is high enough to keep the magnetizing current at a generally acceptable level in transformer applications.

![Hysteresis loop diagram for a ferrite core showing the relationship between magnetic flux density and current, with shaded areas representing stored energy.](page_15_layout_ocr_hqcy_316_264_241_265.png)

Figure. 2-1 Ferrite Core Characteristic

For inductor and flyback transformer applications, a gap is added in series with the core. This skews the characteristic, and provides the required energy storage capability without the rounding observed in the powdered metal cores.

The reasons for ferrite's popularity in SMPS applications are: lower cost and lower loss than the materials previously discussed. Ferrites are available in a wide variety of core shapes including low-profile and "planar" cores, to facilitate various needs. Two-

Texas Instruments
2-2
SLUP132

piece core sets allow the windings to be fabricated separately and subsequently assembled with the core.

The main disadvantage of ferrite is that being a ceramic, the core is less robust than other materials, and may be unacceptable in a high shock military environment.

Saturation flux density in ferrite is much less than with the tape-wound or powdered metal cores: $\approx$0.3T (3000Gauss) vs. $\approx$0.8T. This might seem to be a disadvantage, but saturation is not a real limitation at 100kHz or above. In a transformer application, the maximum flux swing is restricted by losses to much less than $B_{SAT}$. In inductor applications with a small percentage ripple resulting in low core losses, $B_{SAT}$ might become a limiting factor, but the lossier tape-wound or powdered metal cores are usually still at a disadvantage.

# Rounding of the B-H Characteristic

Ideal magnetic materials have a square loop characteristic with very high permeability and insignificant stored energy until finally driven into saturation. This is called a "sharp saturation" characteristic. A rounded, or "soft saturation" characteristic exhibits a gradual reduction of incremental permeability until finally the core is completely saturated. Reference (R1) mentions that magnetic "hard spots" and inside corners will cause rounding of the B-H characteristic.

Rounding effects in metal-alloy cores are generally quite trivial. However, in composite powdered metal cores, non-magnetic "gaps" exist between the discrete magnetic particles. Similar non-magnetic inclusions occur among the sintered particles in ferrite cores. These distributed non-magnetic regions cause significant rounding of the B-H characteristic. They also result in storing energy within the core. The particulate structure has two main effects:

First, the distributed reluctance of these tiny "gaps" causes the flux and the flux change to be distributed across the entire core, rather than as a discrete flux change boundary moving from inside to outside as depicted in (R1) for ungapped idealized metal alloy cores.

Second, at low flux densities, flux tends to concentrate in the "easiest" paths (lowest reluctance) where the magnetic particles are in close proximity. As the flux density increases, these easy path areas are the first to saturate. Those portions of the magnetic particles that saturate first become non-magnetic, making these paths less "easy". Incremental flux increase shifts to adjacent paths where the magnetic material has not yet saturated and where the gap is somewhat wider. This process continues, effectively widening the incremental distributed gap as the flux increases. The incremental permeability (and inductance) is progressively reduced, as observed in the rounding of the B-H characteristic.

![Diagram showing irregular magnetic particles with flux paths between them](page_16_image_1_v2.jpg)

Figure. 2-2 -- Easy Flux Path Between Particles

In powdered metal cores, this non-linear inductance characteristic is unavoidable, except by restricting the maximum flux density to a small fraction of $B_{SAT}$. In some filter inductor applications, the rounding effect, akin to a "swinging choke", might actually be desirable.

In a ferrite core, the rounding effect is, if anything, beneficial. In a transformer application, normal operation with flux density limited by core losses, the rounding is not encountered, and even if it is, the result is a small increase in magnetizing current. In a situation where the flux "walks" toward saturation due to a volt-second imbalance on the transformer primary, the soft saturation characteristic provides a gradual magnetizing current increase to facilitate control of this problem.

When a discrete gap is added to the ferrite core for energy storage in a filter inductor application, the rounding of the ferrite characteristic disappears - swamped by the linear high reluctance of the gap.

Texas Instruments
2-3
SLUP132

until saturation is reached. If a non-linear inductance characteristic is desired, it can be accomplished with a tapered or stepped gap.

# Core Limitations in SMPS Applications

In high frequency SwitchMode power supplies, magnetic core characteristics usually impose different limitations in transformer, filter inductor, and flyback transformer applications.

A **true transformer** is commonly used in buck-derived circuits such as the forward converter, full bridge, half bridge, etc. Ideally, a transformer stores no energy, but transfers energy immediately from input to output. In a practical transformer, undesired stored energy does occur in parasitic leakage inductances (outside the core), and magnetizing inductance (within the core). Magnetizing inductance is minimized by using a gapless, high permeability core material.

At low frequencies, core saturation is usually the most important limitation. But at SMPS frequencies, usually 100kHz or greater, *core loss* becomes the most important limitation in transformer applications. Powdered metal cores are effectively ruled out because of high losses and because of low permeability.

Tape-wound metal alloy cores have considerably higher core losses than ferrite cores. Tape-wound cores have higher $B_{SAT}$ than ferrite, but this is irrelevant because core loss severely restricts the flux swing. Tape-wound cores are considered for SMPS transformer applications only if their greater ruggedness is needed.

A **filter inductor** must store energy during one portion of each switching period and return this energy to the circuit during another portion of the period, thus smoothing the current flow. The required energy must be stored in a non-magnetic gap — distributed in the case of a powdered metal core, and a discrete gap in series with a ferrite core or tape-wound metal alloy core.

If the switching frequency and the percentage of current ripple (which determines the flux swing) are both low enough, core losses will be low, and the inductor core may be limited by saturation. In this situation, powdered metal cores or gapped tape-wound cores may not only be feasible, they *may* outperform gapped ferrite cores because of their higher  $B_{SAT}$. But with higher frequency and/or larger percent ripple current, core losses will dominate, and ferrite cores will outperform the others.

In situations where powdered metal cores may be advantageous, bear in mind that the inductance may diminish an unacceptable amount at higher current levels due to the rounding effect discussed earlier.

**Flyback transformers** are really inductors with multiple windings. There are some unique problems associated with the windings, but the core does not care how many windings exist — the core is aware only of the total ampere-turns and the volts/turn. When operated in the continuous current mode, with small $\Delta I$ and at low enough frequency, the same considerations apply as for the simple inductor. In the discontinuous mode, the current swing (and flux swing) become very large, the core loss limitation applies, and gapped ferrite cores provide the best performance.

Transformer and inductor design is covered in detail in other sections of this manual.

## Core Saturation

At SMPS switching frequencies, core saturation is almost never a limitation in transformer applications, although it often is in filter inductors or continuous mode flyback transformers.

**Flux Walking:** Transformers operated in push-pull circuits *do* have a potential problem with core saturation.

A positive pulse applied to a winding causes a positive flux change proportional to the pulse volt-seconds. In order to maintain a stable operating point on the B-H characteristic, the core must be "reset" by subsequently applying the exact same number of negative volt-seconds.

In a single-ended application, such as a forward converter, the core "resets itself" by an inductive voltage reversal which self-terminates when the magnetizing current returns to zero. In a push-pull application, the core is reset by the circuit, which applies sequential positive and negative pulses to the windings. With the slightest asymmetry — inequality of either voltage or time — the positive and negative volt-seconds do not completely cancel. As a result, the flux never quite returns to its starting point, and over a period of many cycles at the switching frequency,

Texas Instruments
2-4
SLUP132

the flux density "walks" into saturation. This problem is not a core limitation — any core would eventually reach saturation. This is a circuit problem, to which there are several circuit solutions which are beyond the scope of this paper.

## Core Loss

Core loss is the most important core limitation in most SMPS applications. For acceptable losses, flux density swing $\Delta B$ must be restricted to much less than $B_{SAT}$. This prevents the core from being utilized to its full capability.

At low frequencies, core loss is almost entirely hysteresis loss. For today's power ferrites, eddy current loss overtakes hysteresis loss at 200-300kHz. In metal alloy cores, eddy current loss dominates above a few hundred Hertz.

Core manufacturers usually provide curves such as Fig. 2-3 showing core loss as a function of flux swing and frequency, combining hysteresis and eddy current losses. Core loss is usually expressed in mW/cm<sup>3</sup>, sometimes in kW/m<sup>3</sup> (actually equal: 1 mW/cm<sup>3</sup> = 1 kW/m<sup>3</sup>), sometimes in Watts/pound (horrors!!)

In these Core Loss vs. Flux Density curves, the horizontal axis labeled "Flux Density" usually represents *peak* flux density, with symmetrical sinusoidal excitation. In SMPS applications, peak-to-peak flux swing, $\Delta B$, is calculated from Faraday's Law, where $\int Edt$ = applied Volt-seconds, N = turns, and $A_e$ = core cross-section area:

$$\Delta B = \frac{1}{NA_e} \int Edt$$

The total flux swing, $\Delta B$, is twice the peak flux swing referred to in the core loss curves as "Flux Density". Therefore, use $\Delta B/2$ to enter the core loss curves.

## Hysteresis Loss

The hysteresis loops shown in the core material data sheets represent the core overdriven by a sinusoidal waveform from + to - saturation. In an SMPS application, the core is usually driven by a much smaller rectangular waveform with $\Delta B$ limited by core losses to a minor hysteresis loop as shown in Fig. 2-4.

![Log-log plot of Core Loss (mW/cm³) vs. Flux Density (Gauss) for P Material at 80°C, showing multiple frequency lines from 25kHz to 1000kHz.](page_18_image_1_v2.jpg)

Figure. 2-3 Core Loss -- "P" Material


![Diagram showing a major hysteresis loop and a smaller minor hysteresis loop on a graph of ∫Edt vs I.](page_18_layout_ocr_nxdo_317_437_241_257.png)

Figure. 2-4 - Minor Hysteresis Loop

Texas Instruments
2-5
SLUP132

The hysteresis loop area represents energy loss. Power loss depends on how many times per second the hysteresis loop is traversed. Thus, hysteresis loss varies directly with frequency.

Hysteresis loss varies with flux density swing ($\Delta B$) to some power, depending on how much the minor hysteresis loop expands horizontally ($\Delta H$) as well as vertically ($\Delta B$). For most ferrites, hysteresis loss varies with $\Delta B^n$, with $n \approx 2.5 - 3.0$.

![Waveform comparison showing a 5V square wave and a 10V pulsed waveform](page_19_image_2_v2.jpg)

Figure. 2-5 Waveform Comparison

The hysteresis loop changes shape somewhat with waveshape, current or voltage drive, and temperature. This variability, together with the steep slope of the high inductance characteristic makes it impossible to predict the magnetizing current with any degree of accuracy (and eddy currents make the problem worse).

**What causes eddy currents:** Virtually all of the flux induced by the primary winding is contained within the core. The core itself is a single turn secondary linked to all of the windings. A voltage is induced around the core periphery equal to the volts/turn applied to the windings. The core material has a finite resistivity, which translates into a resistance value around the core periphery. The voltage induced around the core forces a current — the eddy current — to flow through this resistance. The result is $I^2R$ loss. The eddy current is reflected into the primary according to the ratio of the primary turns to the single turn "core secondary". In the primary, it is considered part of the magnetizing current, although it is pure loss, and in fact absorbs some of the stored energy in the core.

Fortunately, the only important concern about the hysteresis loop in SMPS applications is the core loss it represents. The shape does not matter — the core loss curves provide the necessary information. In transformer applications, all we really need to know is that the magnetizing current is acceptably low (unless $I_m$ is depended upon for some circuit function, which is risky). In filter inductor and flyback transformer applications, the hysteresis loop of the core material is totally swamped by the lossless and predictable high reluctance of the series gap, making $I_m$ easily predictable.

## Eddy Current Loss

At the high frequencies usually involved in SMPS applications, it is incorrect to think of eddy current losses in the core as being frequency dependent. Core eddy current loss is a function of the volts per turn applied to the windings, and the duty cycle. It can be modeled by placing a resistor across one of the windings.

For example, a square wave of 5 Volts/turn, as shown in Fig. 2-5, applied to the primary, will result in the same eddy current loss *regardless of frequency*. On the other hand, if the waveform is changed to 10 Volts peak at 50% duty cycle (same average value), the peak loss quadruples (proportional to $V_p^2$) while the average loss doubles (the duty cycle is halved), whether the frequency is constant or not. The resistor model demonstrates this behavior.

![Diagram of a ferrite core showing flux lines and circular eddy current flow](page_19_image_1_v2.jpg)

Fig. 2-6 Eddy Current in a Ferrite Core

Texas Instruments
2-6
SLUP132

The effective eddy current resistance can be calculated from the core resistivity and dimensions, and projected as an equivalent resistor across the primary winding according to the turns ratio squared. Hence the validity of the resistor model mentioned earlier. Placing the equivalent eddy current resistance across the primary, it is obvious that if the applied voltage changes, the eddy current instantaneously changes proportionally. When the voltage pulse ends and the voltage drops to zero, the eddy current becomes zero. The magnetizing current then reverts to the low frequency hysteresis loop value.

Resistivity of power **ferrite** materials intended for SMPS applications ranges from 200 to 2000 $\Omega$-cm. The resulting eddy currents and associated losses are barely noticeable compared to hysteresis effects at 100 kHz, but become dominant in the range of 250-600 kHz, depending on the specific material.

Resistivity of tape-wound metal alloy cores is only 50 to 150 *micro*-$\Omega$-cm. If the core was solid metal, it would be a shorted turn. High current would circulate on the core surface, and the magnetic field could not penetrate the core.

The solution to this problem is to break the core up into electrically insulated laminations. Figure 2-7 shows the detail of one such lamination. If a metal alloy core 1.2 cm thick is divided into 1000 laminations, each .0012 cm thick, then each lamination contains only 1/1000 of the total flux. Therefore the voltage induced around the periphery of each lamination is 1/1000 of the volts/turn in the windings. The

resistance around the periphery of the lamination (the eddy current path) is $\approx$500 times the resistance of the path around the entire core if it were solid. (R=$\rho\ell$/A ; path length $\ell$ around the lamination is $\approx$ ½ the path length around the entire core periphery; area A is $\approx$ 1/1000 of the effective area around the periphery of the solid core).

Thus the effective eddy current resistance is roughly equivalent to a solid core with resistivity 500,000 times greater. This is beginning to approach a solid ferrite core.

## Skin Effect

The example of the solid metal alloy core discussed earlier raises the concern that the magnetic field may not be able to penetrate the core sufficiently, confining the flux to the core surface. A calculation of the penetration depth resolves this issue.

Penetration depth (skin depth) is defined as the distance from the surface to where the current density is 1/e times the surface current density:

$$ D_{PEN} = \sqrt{\frac{\rho}{\pi\mu_0\mu_r f}} \text{ meters} $$

In a Permalloy tape-wound core, resistivity, $\rho = 55 \cdot 10^{-4} \Omega\text{-m}$, and $\mu_r = 30,000$:

$$ D_{PEN} = 0.22 / \sqrt{f} \text{ cm} $$

At 100kHz in Permalloy, $D_{PEN} = .0007 \text{ cm}$. Thus, even with .0005" (.00125cm, or 12.5$\mu$m) tape thickness, there is some concentration of current at the tape surfaces, slightly worsening the eddy current losses.

In power **ferrite** (Magnetics type K), with $\rho = 20 \Omega\text{-m}$ and $\mu_r = 1500$:

$$ D_{PEN} = 5800 / \sqrt{f} \text{ cm (ferrite)} $$

At 100kHz, in ferrite Type K, $D_{PEN} = 18\text{cm}$. Penetration depth in ferrite is thus much greater than core thickness, and skin effect can be ignored.

![Diagram showing a lamination with eddy current paths and magnetic flux arrows.](page_20_image_1_v2.jpg)

Figure. 2-7 Lamination Detail

Texas Instruments
2-7
SLUP132

# Modeling the Magnetic Core

The subject of modeling the complete magnetic device is discussed in Reference R3. The computer model might include:

* An ideal transformer with appropriate turns ratios for the windings
* leakage inductances properly located and quantified
* parasitic capacitances
* A model of the magnetic core, reflected into the primary winding or a dedicated winding.

In this Section, where the core is under discussion, it is appropriate to consider some aspects of modeling the core.

Based on the preceding discussion of the mechanisms underlying magnetic core behavior, there are several distinct elements that might be included in the core model:

* Inductance, magnetizing current, linear region, rounding, saturation – ungapped and gapped.
* Hysteresis loop centered on the inductance characteristic
* Eddy current loss – proportional to dB/dt

## Physical or Empirical ???

Should the core model be based on physical mechanisms or on empirical data? Core eddy current can easily be modeled based on the physical process, simply by placing a resistor across the primary, or across a normalized one-turn winding dedicated to hold the core model.

But for the other core characteristics, discussed earlier in this paper, the underlying physical processes are much too complex to serve as the basis for the core model. An empirical model is the only reasonable choice. However, familiarity with the physical processes *is* helpful in developing an empirical model.

There are many types of evaluations used to understand, improve, or validate various aspects of SMPS operation. Rather than use the same complex "one size fits all" model for all purposes, it is far better to use simpler models tailored to the needs of each specific situation. The evaluations will be faster, and the results are easier to understand. Include only the characteristics that are necessary, and for these, use the simplest approximation that will serve the purpose. Only when a really accurate representation is required, use a mathematical expression, curve fitted to the data sheet representation.

Core characteristics that are most important in SMPS applications are (1) losses; (2) saturation. Sometimes, in a transformer, a crude representation of magnetizing current is necessary. Replicating the curvature of the characteristic is not important except in filter inductor applications using powdered metal cores operated close to saturation, which results in increased ripple current at full load. Other than that situation, it will usually suffice to have two straight lines, one representing normal inductance, intersecting at B<sub>SAT</sub> with a second straight line representing saturated inductance. If it is certain that the core will not be driven into saturation in the evaluation being performed, the saturated inductance line may be omitted.

An adequate model for different core materials in each of the following applications might include:

* **Filter inductor with gapped ferrite core:** Until the core saturates, the gap is the only important element determining the inductance value – the effect of the ferrite core is negligible. For example: With a 0.3 cm gap and a 10 cm path length in the ferrite ($\mu_r = 3000$), the core reduces inductance by 1%. Since current limiting prevents the inductor from being driven into saturation, a simple, linear inductor model, representing the gap, is generally adequate. In computer circuit modeling, the standard L model can be used, with current specified as initial condition.
* **Filter inductor with gapped, laminated metal-alloy core:** The same considerations as the gapped ferrite core will apply. A shunt resistor to model core eddy-current losses may be desirable with this lossier material.
* **Filter inductor with powdered metal core – MPP, Powdered iron, Kool M$\mu$®:** If flux density is limited by core loss to below the region of curvature, the simple linear inductance model may suffice. If operated at higher flux densities where inductance non-linearity becomes an important consideration, a customized computer model should be used, curve-fitted to the actual inductance characteristic.

Texas Instruments
2-8
SLUP132

*   **Saturable reactor (magamp) core:** Mag-amps require high permeability square-loop core materials – metal alloy laminated cores or square-loop ferrites. It is essential to include the hysteresis characteristic in a magamp core model. In metal alloy cores, hysteresis loss is negligible compared to eddy current loss at SMPS frequencies. Nevertheless, if the square loop hysteresis characteristic is not included in the model, the flux will be unable to maintain its position on the vertical axis after reset is accomplished and before the next power pulse, and will drift toward zero.

A magamp core model requires hysteresis, eddy current, and saturation.

*   **Transformer with ungapped metal alloy core:** A straight line representing the very high unsaturated inductance is probably acceptable. An intersecting straight line representing the saturated inductance could be included if necessary for the intended evaluation. Eddy current loss resistance is very significant. Hysteresis can be omitted.

*   **Transformer with ungapped ferrite core:** As above, straight line approximations can be used to simulate inductance and saturation. Losses are primarily hysteretic at 100-200 kHz. Eddy current losses become significant at higher frequencies.

Figure 2-8 shows how the elements representing the core can be applied to a transformer model. Eddy current resistance is modeled by resistor R<sub>E</sub>. All of the other core characteristics are included in the symbol labeled "CORE" – inductance, rounding, saturation, and hysteresis effects, but only to the degree and accuracy relevant to the intended circuit evaluation.

![Circuit diagram of a transformer model showing primary and secondary windings, core elements including capacitance Cw, eddy current resistance RE, leakage inductance LP-S1, and an ideal transformer symbol.](page_22_image_1_v2.jpg)

Fig. 2-8 Transformer Model

# Points to Remember

*   Hysteresis loss is directly proportional to frequency, and to the n<sup>th</sup> power of the flux density swing. n is in the range of 2.5 to 3.0 for most power ferrites.

*   Eddy current in the core is proportional to dφ/dt (equal to volts/turn) not frequency per se. Eddy current loss (I<sup>2</sup>R) is proportional to volts/turn squared. When the voltage transitions to zero at the end of each pulse, the eddy current becomes zero.

*   At DC and low frequency, magnetic devices are current-controlled. At the SMPS switching frequency, they are voltage driven.

*   Core limitations – saturation and losses – put restrictions on flux and flux swing, which translate into volt-second limitations on the applied voltage waveforms.

# References

"R-numbered" references are reprinted in the Reference Section at the back of this Manual.

(R1) "Magnetic Core Properties," originally titled "*An Electrical Circuit Model for Magnetic Cores*," Unitrode Seminar Manual SEM1000, 1995

(R3) "Deriving the Equivalent Electrical Circuit from the Magnetic Device Physical Properties", Unitrode Seminar Manual SEM1000, 1995 and SEM1100, 1996

Texas Instruments
2-9
SLUP132

Texas Instruments 2-10 SLUP132

# Section 3 Windings

Understanding the rules governing magnetic field behavior is fundamentally important in designing and optimizing magnetic devices used in high frequency switching power supply applications. Paralleled windings can easily fail in their intended purpose, eddy current losses and leakage inductances can easily be excessive. These are some of the problems that are addressed in this Section.

Even if you never participate in transformer or inductor design, these magnetic principles apply in optimizing circuit layout and wiring practices, and minimizing EMI..

Reference paper (R2): "Eddy Current Losses in Transformer Windings and Circuit Wiring," included in this Manual, is a useful supplement.

## Conservation of Energy

Like water running downhill, electrical current always takes the easiest path available. The path taken at dc and low frequencies can be quite different from the path taken by the high frequency current components.

The basic rule governing the current path: *Current flows in the path(s) that result in the lowest expenditure of energy.* At low frequency, this is accomplished by minimizing I²R losses. At high frequency, current flows in the path(s) that minimize inductive energy — energy transfer to and from the magnetic field generated by the current flow. Energy conservation causes high frequency current to flow near the surface of a thick conductor, and only certain surfaces, even though this may results in much higher I²R losses. If there are several available paths, HF current will take the path(s) that minimize inductance. This may have undesirable side effects as shown in one of the examples below.

Examples are given later which demonstrate how to manipulate the field and current path to advantage.

## Skin Effect

The circuit of Figure 3-1 shows an inductor in series with an L-R transmission line. What happens when a dc current is put through this circuit? What

![Circuit diagram showing a skin effect model with inductors Lx and Li, and resistors Ri. Point A is at the surface and point B is at the center.](page_24_image_1_v2.jpg)

Figure 3-1 Skin Effect Model

happens when a high frequency ac current is put through?

Figure 3-1 happens to be a high-frequency model of a single wire. A represents the surface of the wire, B is the center. Lx represents the inductance per unit length *external* to the wire (what would be the measured inductance of the wire). Li is inductance distributed within the wire, from the surface to the center. (Copper is non-magnetic, just like air, and stores magnetic energy in the same way.) Ri is the distributed longitudinal resistance from the surface to the center. Collectively, Ri is the dc resistance of the wire. All of the above values are per unit length of wire.

At dc or low frequency ac, energy transfer to inductance Li, over time, is trivial compared to energy dissipated in the resistance. The current distributes itself uniformly through the wire from the surface to the center, to minimize the I²R·t loss. But at high frequency, over the short time spans involved, I²R·t loss is less than the energy transfer to and from Li. Current flow then concentrates near the surface, even though the net resistance is much greater, in order to minimize energy transfer to Li. If we look at this strictly from a circuit point of view, at high frequency, the impedance of Li near the surface blocks the current from flowing in the center of the wire.

Penetration depth (or skin depth), *Dpen*, is defined as the distance from the conductor surface to where the current density (and the field, which termi-

Texas Instruments
3-1
SLUP132

nates on the current flow) is 1/e times the surface current density:

$$ D_{PEN} = \sqrt{\frac{\rho}{\pi \mu_0 \mu_r f}} \text{ meters} $$

In copper at 100°C, resistivity, $\rho = 2.3 \cdot 10^{-8} \ \Omega\text{-m}$, and $\mu_r = 1$:

$$ D_{PEN} = 7.6 / \sqrt{f} \text{ cm (copper)} $$

At 100 kHz in copper, $D_{PEN} = .024 \text{ cm}$.

## Proximity Effect

When two conductors, thicker than $D_{PEN}$, are in proximity and carry opposing currents, the high frequency current components spread across the surfaces facing each other in order to minimize magnetic field energy transfer (minimizing inductance) This high frequency conduction pattern is shown in reference (R2) Figs 5, 6, and 7. (R2) Fig. 5 is reproduced below as Fig. 3-2.)

![Diagram showing the proximity effect between two conductors with current flowing in opposite directions. The top conductor has '+' symbols indicating current into the page, and the bottom conductor has dots indicating current out of the page. Dimensions 'l' and 'W' are labeled.](page_25_layout_ocr_fkdz_51_350_241_170.png)

Fig. 3-2 Proximity Effect

In all three configurations, current does not flow on any other surfaces because that would increase the volume of the magnetic field and require greater energy transfer. Inductance is thus minimized, but ac resistance is made higher, especially in (R2) Figs 6 and 7. Note how in Fig. 3-2, the preferred configuration, the current distributes itself fairly uniformly across the two opposing surfaces. This results in significantly less stored energy than R2 Fig. 6, even though the length and volume of the field in Fig. 3-2 is 5 times greater. This is because spreading the current over 5 times longer distance reduces the field

intensity, H, by 5 times. Energy density, proportional to $H^2$, is 25 times weaker.

$$ (W/cm^3 = \frac{1}{2} BH = \frac{1}{2} \mu H^2) $$

Therefore, total energy (volume times energy) and inductance, are 5 times less in Fig. 3-2 above than with the more concentrated field in (R2) Fig. 6.

An important principle is demonstrated here: If the field (and the current that produces it) is given the opportunity to spread out, it will do so in order to minimize energy transfer. The stored energy (and inductance) between the conductors varies inversely with the length of the field.

Visualize the magnetic field equipotential surfaces stretched across the space between the two conductors, terminating on the current flow at each surface. Visualize the flux lines, all passing horizontally between the two conductors, normal to the equipotential surfaces. The flux return paths encircle the conductors in wide loops spread out over a distance — the field here is very weak.

## Examples

In the examples of winding structures given below:

*   Each + represents 1 Ampere into the page

*   Each • represents 1 Ampere out of the page

*   Fine lines connecting + and • represent edge view of the field equipotential surfaces.

*   Conductor size is much greater than penetration (skin) depth.

### Simple Transformer Windings:

If the two flat conductors of Fig. 3-2 are placed within a transformer core, the only change in the field pattern is that the fringing field at the conductor ends is reduced. The conductors are now called "windings", and the inductance representing the energy stored between the conductors is called "leakage inductance". In Figure 3-3, one of the flat strips is replaced by 4 wires. This could be a 4-turn winding carrying 3A, opposed by a single turn secondary carrying 12A. Or, the four primary wires could be in parallel, giving a 1-turn primary carrying 12A. In either case, the field pattern spreads itself across the entire window, and the same minimized energy is

Texas Instruments
3-2
SLUP132

![Diagram showing magnetic field distribution in single layer windings with primary (P) and secondary (S) conductors.](page_26_image_1_v2.jpg)

Figure 3-3 Single Layer Windings

stored between the windings. The conductors are thicker than D<sub>PEN</sub>, so the high frequency currents flow near the surfaces in closest proximity, thus terminating the field.

![Diagram showing magnetic field distribution in two-layer series windings with primary (P) and secondary (S) conductors.](page_26_image_2_v2.jpg)

Figure 3-4 Two Layer Windings -- Series

**Multiple Layer Windings:**

In Figure 3-4, an 8-turn primary carrying 1A is opposed by a 2-turn secondary carrying 4A. The 8 turns of wire, sized for the required rms current, cannot fit into the window breadth, so it is configured in two layers. As expected, there is an 8 Ampere-turn field stretched across the entire window. But since the conductor thickness is much greater than the skin

depth, the field cannot penetrate the conductor, and current flow is confined to near the conductor surface.

A strange thing happens -- since the field cannot penetrate the conductor, the entire 8 Ampere field terminates at this inner surface of the inner layer. This requires a total of 8 Ampere-turns at this surface -- 2A per wire -- since the field can be terminated only by current flow. Inside the outer layer, there is a 4A field, from the 4 A-t flowing in the outer layer. This field must terminate on the outside of the inner layer, because it cannot penetrate. This requires 4 A-t in the opposite direction of the current in the wire!!

Thus the inner layer has 8 A-t on its inner surface, and 4 A-t in the opposite direction on its outer surface. Each inner wire has 2A on its inner surface and 1A in opposite direction on its outer surface. The net current remains 1A in all series wires in both layers. But since loss is proportional to I<sup>2</sup>, the loss in the inner layer is 1<sup>2</sup> + 2<sup>2</sup> = 5 times larger than the loss in the outer layer, where only the net 1A flows on its inner surface!!

Not only is the I<sup>2</sup>R loss larger because the current is confined to the surface, it also increases *exponentially* as the number of layers increases. This is because the field intensity increases progressively toward the inside of the winding. Since the field cannot penetrate the conductors, surface currents must also increase progressively in the inner layers. For example, if there were 6 wire layers, all wires in series carrying 1A, then each wire in the inner layer will have 6A flowing on its inner surface (facing the secondary winding) and 5A in the opposite direction on its outer surface. The loss in the inner layer is 6<sup>2</sup> + 5<sup>2</sup> = 61 times larger than in the outer layer which has only the net 1A flowing on its inner surface!!

If the wire diameter is reduced, approaching the penetration depth, the + and - currents on the inner and outer surfaces of each wire start to merge, partially canceling. The field partially penetrates through the conductor. When the wire diameter is much less than the penetration depth, the field penetrates completely, the opposing currents at the surfaces completely merge and cancel, and the 1A current flow is distributed throughout each wire.

Texas Instruments
3-3
SLUP132

Calculation of the $I^2R$ loss when the conductor size (layer thickness) is similar to the penetration depth is very complex. A method of calculating the ac resistance was published by Dowell<sup>(1)</sup>, and is discussed extensively in Reference (R2). Figure 3-5 (from R2, Fig. 15), based on Dowell's work, shows the ratio of $R_{AC}/R_{DC}$ vs. layer thickness/$D_{PEN}$ and the number of layers in each winding section. Read (R2) for a detailed discussion.


<table>
  <thead>
    <tr>
        <th>Q = Layer Thickness/Dpen</th>
        <th>10</th>
        <th>6 Layers</th>
        <th>4</th>
        <th>3</th>
        <th>2.5</th>
        <th>2</th>
        <th>1.5</th>
        <th>1 Layer</th>
        <th>0.5</th>
    </tr>
  </thead>
  <tbody>
    <tr>
        <td>0.25</td>
        <td>1</td>
        <td>1</td>
        <td>1</td>
        <td>1</td>
        <td>1</td>
        <td>1</td>
        <td>1</td>
        <td>1</td>
        <td>1</td>
    </tr>
    <tr>
        <td>0.5</td>
        <td>2.5</td>
        <td>2</td>
        <td>1.5</td>
        <td>1.2</td>
        <td>1.1</td>
        <td>1.05</td>
        <td>1.02</td>
        <td>1.01</td>
        <td>1</td>
    </tr>
    <tr>
        <td>1</td>
        <td>20</td>
        <td>12</td>
        <td>7</td>
        <td>5</td>
        <td>4</td>
        <td>3</td>
        <td>2</td>
        <td>1.2</td>
        <td>1.05</td>
    </tr>
    <tr>
        <td>2</td>
        <td>100</td>
        <td>60</td>
        <td>35</td>
        <td>25</td>
        <td>20</td>
        <td>15</td>
        <td>10</td>
        <td>4</td>
        <td>1.5</td>
    </tr>
    <tr>
        <td>4</td>
        <td> </td>
        <td>100</td>
        <td>100</td>
        <td>85</td>
        <td>70</td>
        <td>55</td>
        <td>40</td>
        <td>18</td>
        <td>5</td>
    </tr>
    <tr>
        <td>10</td>
        <td> </td>
        <td> </td>
        <td> </td>
        <td> </td>
        <td> </td>
        <td> </td>
        <td> </td>
        <td>100</td>
        <td>30</td>
    </tr>
  </tbody>
</table>

Figure. 3-5 Eddy Current Losses -- $R_{AC}/R_{DC}$

The curves of Fig. 3-5 graphically show the high ac resistance that results when the layer thickness equals or exceeds the penetration depth, especially with multiple layers. With the large ac currents in a transformer, $R_{AC}/R_{DC}$ of 1.5 is generally considered optimum. A lower $R_{AC}/R_{DC}$ ratio requires finer wire, and the wire insulation and voids between wires reduce the amount of copper, resulting in higher dc losses. In a filter inductor with small ac ripple current component, a much larger $R_{AC}/R_{DC}$ can be tolerated.

Although the curves of Fig. 3-5 are quite useful, keep in mind that an accurate solution requires harmonic (Fourier) analysis of the current waveform. Loss must then be calculated independently for each harmonic, since $D_{PEN}$ differs for each harmonic frequency, and these losses added to obtain the total loss.

Alternative methods of calculating eddy current losses include:

1. Calculate based on the fundamental only, ignore the harmonics and add 50% to the calculated loss.

2. Carsten<sup>[2]</sup> has applied Dowell's sine wave solution to a variety of non-sinusoidal waveforms encountered in SMPS applications, providing curves that include harmonic effects.

3. Computerize Dowell's work, in order to apply it to any non-sinusoidal waveshape. O'Meara<sup>[3]</sup> can be helpful.

4. A computer program "PROXY" (proximity effect analysis) is available from KO Systems<sup>[4]</sup>.

## Paralleled Layers:

The transformer of Fig. 3-6 is the same as Fig. 3-4 with the winding layers reconfigured in parallel, resulting in a 4-turn, 2 Amp primary, and a 1-turn, 8A secondary. The intention is to have 1A in each primary wire and 4A in each secondary strip, with the same field pattern as in Fig. 3-4, but it doesn't happen that way.

![Diagram of paralleled two-layer windings showing primary (P) and secondary (S) sections with current distribution.](page_27_image_1_v2.jpg)

Figure 3-6 Paralleled Two-Layer Windings

Whenever windings are paralleled, alternative current paths are provided. In Fig. 3-6, resistance in each of the paralleled windings causes the current to divide nearly equally at dc and low frequencies. But at high frequency, stored energy becomes more important than $I^2R \cdot t$. All of the high frequency current components will flow on the inside surfaces of the inner layers directly facing each other. The high frequency current in the outer layers is zero. Any current in the outer layers contributes to an additional field, between inner and outer layers, requiring additional energy. With series-connected layers the current has

Texas Instruments
3-4
SLUP132

no alternative – it *must* flow in all layers, resulting in additional energy stored between layers as shown in Fig. 3-4. When there is an alternative, as with paralleled layers, the high frequency current will flow so as to minimize the stored energy.

The leakage inductance between the windings in Fig 3-6 is slightly smaller than it would have been if the current divided equally – a small benefit. But only a tiny fraction of the available copper is utilized, making I<sup>2</sup>R loss prohibitively large.

Another example: A low voltage, high current secondary might use a single turn of copper strap, but the thickness required to carry the rms current is 5 times the skin depth. It might seem logical to parallel 5 thin strips, each one skin depth in thickness. Result: All the HF current will flow in the one strip closest to the primary. If ac current were to flow in the other strips further from the primary, I<sup>2</sup>R loss would be less, but more stored energy is required because the field is bigger (increased separation).

**Rule: If you provide alternative current paths, be sure you know what the rules are.**

## Window Shape–Maximize Breadth

The shape of the winding window has a great impact on the eddy current problem. Modern cores intended for high frequency SMPS applications have a window shape with a winding breadth (width) several times greater than its height. For the same number of turns, the number of layers required is thereby minimized. As shown in Figure 3-7, the window has twice the breadth as the core in Fig. 3-4, so that only one layer is required. This results in a very significant reduction in eddy current losses, as can be seen from Fig 3-5.

Another major benefit of the wider window is that the stored energy (leakage inductance) is minimized. With the 8 turns at 1A of Fig 3-4 fit into a single layer, (and the opposing 2-turn strap also in a single layer), the total magnetic force, $\iota$, remains 8 Ampere-turns. However, the field intensity $H$, stretched over twice the distance, is half as much. Flux density $B$ is also halved ($B = \mu H$), therefore energy density $\frac{1}{2}BH$ is one-fourth as much. However, the volume of the field is increased, perhaps doubling, therefore total energy–and leakage inductance—is halved.

![Diagram showing a wide window breadth transformer core with a single layer of windings.](page_28_image_1_v2.jpg)

Figure. 3-7 Wide Window Breadth

The penalty for stretching out the winding is increased capacitance between windings.

## Interleaving:

If the stretched out winding of Fig. 3-7 were folded in half, it could then fit into the original window, as shown in Figure 3-8. This "interleaved" winding has the same low eddy current loss, low field intensity, and low inductance as the winding of Fig. 3-7.

![Diagram showing interleaved windings (P S S P) within a transformer core window.](page_28_image_2_v2.jpg)

Figure. 3-8 Interleaved Windings

Texas Instruments
3-5
SLUP132

# Winding Sections:

Although there are two primary winding layers and two secondary layers in Fig. 3-8, the interleaved windings actually divide into two winding sections, indicated by the dashed line between the secondary layers. The boundary between winding sections is defined as the point where the total magnetic field goes through zero. Within each winding section of Fig. 3-8, there is a 4 Ampere-turn field introduced by the primary layer and canceled by the opposing secondary layer. At the dashed line between the two secondary layers, the total field is zero. Thus, in Fig. 3-8, there is one primary layer and one secondary layer in each of two winding sections. Further detail, including the concept of half layers seen in Fig. 3-6, is given in (R2).

First level interleaving (2 winding sections) is very beneficial in terms of eddy current loss and leakage inductance. EMI is minimized because the fields in each winding section are oppose each other externally. The penalty for interleaving is increased primary to secondary capacitance.

With further levels of interleaving, gains become marginal and the interwinding capacitance penalty gets worse.

A 3 winding section structure (P-S-P-S) is often executed incorrectly. For proper balance, the fields should be equal in each of the 3 winding sections. This requires the two interior winding portions have twice the Ampere-turns of the two outside winding portions: (P-SS-PP-S).

# When does Paralleling Succeed:

Paralleling succeeds when the equal division of high frequency current among the parallel paths results in the least stored energy. Paralleling fails when unequal division of current results in the least stored energy. High frequency current will always take the path that results in the least stored energy.

In the previous discussion of Fig. 3-8, the primary and secondary layers were in series. But the two primary layers and/or the two secondary layers could be paralleled, and the high frequency current would divide equally between the paralleled windings. The field must divide equally between the two winding portions in order to minimize the stored energy = ½ $BH^2$volume. If the current and the field were to concentrate in one winding section, then in that one section $H$ would double, and energy density would quadruple. Volume is halved, but net energy would double. Therefore current and field will balance nicely in both portions, for minimum energy and (coincidentally) minimum $I^2R$ losses.

To achieve acceptable eddy current losses, it is often necessary to subdivide a wire whose diameter is greater than the penetration depth into many paralleled fine wires. Simply bundling these paralleled fine wires together won't do. Twisting the bundle won't help much. Paralleled conductors within one winding section must all rotate through all levels of the winding, so that each conductor has the same induced voltage integrated along its length. A special technique to ensure the proper division of current among the paralleled wires is used in the manufacture of **Litz Wire**, discussed in reference (R2).

Bear in mind that when a wire is subdivided into many fine wires to make the layer thickness smaller than $D_{PEN}$, the number of layers is correspondingly increased. For example, a single layer of solid wire replaced by a 10x10 array of 100 parallel fine wires becomes 10 layers when entering Fig. 3-5.

# Passive losses

High ac losses can occur in windings that are carrying little or no current, if they are located in the region of high ac magnetic field intensity between primary and secondary. Situations of this nature include: Faraday shields, lightly loaded or unloaded secondaries, and the half of a center-tapped winding that is not conducting at the moment.

If the "passive winding" conductor thickness is not substantially less than $D_{PEN}$, the magnetic field cannot fully penetrate. Equal and opposite currents must then flow on opposite surfaces of the conductors in each layer of the passive winding to terminate or partially terminate the field on one side of each conductor and re-create it on the other side. Although the net current is zero, the surface currents can be quite high, causing significant additional winding loss.

Passive winding losses can be reduced or eliminated by:

* Relocating the winding out of the region of high ac field intensity.

Texas Instruments
3-6
SLUP132

*   Reducing field intensity by interleaving and by using a core with wide window breadth.
*   Making conductor thickness substantially less than D<sub>PEN</sub>.

Faraday shields prevent electrostatic coupling between primary and secondary (more later). Of necessity they are situated where the field intensity is highest. Since they carry very little current, conductor thickness can and should be very much less than D<sub>PEN</sub>.

![Diagram showing interleaved winding hierarchy with primary (P) and secondary (S1, S2) windings in a core window.](page_30_image_1_v2.jpg)

Figure 3-9 Interleaved Winding Hierarchy

With multiple secondaries, windings should be sequenced so the highest power secondary is closest to the primary. This keeps the lower-powered secondaries out of the highest field region, and has the added benefit of minimizing the adverse effect of leakage inductance on cross-regulation. This winding hierarchy is more difficult to achieve if the primary is interleaved outside of the secondaries. One way of accomplishing this, shown in Fig. 3-9, is to interleave the highest power secondary, S1, outside the lower power secondary(s), S2. The S1 sections (and/or the primary sections) can be either in series or parallel, whichever best suits the number of turns required.

shapes encountered in switching power supplies. For each half of a Center-Tap winding, which conducts only on alternate switching periods, substitute D/2 in place of D.

Center-tap windings should be avoided. In center-tap windings, one side is inactive (passive) while the other side is conducting. Not only does this result in poor utilization of the available window area (compared with the single winding of the bridge configuration), the inactive side usually sits in the high field between the active side and the opposing windings, thereby incurring passive losses.

$$I^2 = I_{DC}^2 + I_{AC}^2 ; \quad D = t/T$$

It is usually not difficult to avoid center-tap windings on the primary side, by choosing a forward converter, bridge, or half-bridge topology. But with low voltage secondaries, the importance of minimizing rectifier drops usually dictates the use of a center-tapped secondary winding.

# Calculating rms Current

The relationships between peak current, I<sub>P</sub>, total rms current, I, and its dc and ac components, I<sub>DC</sub> and I<sub>AC</sub>, are given below for several of the current wave-


<table>
  <tbody>
    <tr>
        <td>I_DC</td>
        <td>I_P D / 2</td>
    </tr>
    <tr>
        <td>I_AC</td>
        <td>I_P (D/3 - D^2/4)^1/2</td>
    </tr>
    <tr>
        <td>I</td>
        <td>I_P (D/3)^1/2</td>
    </tr>
  </tbody>
</table>

Fig 3-10a Discontinuous Mode Waveform

Texas Instruments
3-7
SLUP132

![Line chart showing inductor current waveform in continuous mode with peak current Ip, DC current IDC, and ripple current ΔI.](page_31_layout_ocr_imbc_49_41_241_242.png)

$$I \approx I_{DC} = I_P - \Delta I/2$$
$$I_{AC} = \Delta I/(12)^{1/2}$$

Figure. 3-10b Continuous Mode -- Filter Inductor

![Line chart showing transformer current waveform in continuous mode with peak current Ip, ripple current ΔI, AC current IAC, and DC current IDC over period T and duty cycle t.](page_31_image_1_v2.jpg)

$$I_{DC} = (I_P - \Delta I/2)D$$
$$I_{AC} = (I_P - \Delta I/2)[D(1-D)]^{1/2}$$
$$I = (I_P - \Delta I/2)D^{1/2}$$

Figure. 3-10c Continuous Mode -- Transformer

and/or temperature rise. A traditional rule-of-thumb for larger 60Hz transformers is to operate copper windings at a current density of 450 A/cm² (2900 A/in²). However, smaller high frequency transformers can operate at much higher current densities because there is much more heat dissipating surface area in proportion to the heat generating volume.

How much of the window area is actually useful copper area? In a small transformer with a bobbin and with high voltage isolation requirements, perhaps only 25% or 30% of the window area is copper.

Isolation safety requirements dictated by specs such as IEC 65 and VDE 0860 impose 3 layers of insulation between windings with minimum creepage distances of 6 to 8mm from primary to secondaries around the ends of the insulation layers at both ends of the winding. Nearly 1 cm of window breadth is lost to this requirement, severely impacting window utilization, especially with small cores in low power transformers. The increased separation also results in higher leakage inductance between primary and secondary.

Recent revisions to these specifications permit the use of triple-insulated wire (more about this later), which can reduce the penalty imposed by isolation requirements. This is an area where expert advice can be very worthwhile.

A bobbin, if used, significantly reduces the available window area, again impacting smaller, low power applications much more heavily.

Voids between round wires waste 21% of the winding cross-section area. Wire insulation further reduces the useful area, especially with the smaller diameter wires used to minimize high frequency losses, because insulation is a larger percentage of small wire diameter.

In Litz wire, with multiple levels of twisting very fine insulated wires, the amount of copper may be less than 30% of the total cross-section. There is no benefit in pushing to an R<sub>AC</sub>/R<sub>DC</sub> of 1.5, if R<sub>DC</sub> is increased two or three times because of the reduced copper area of the many fine wires involved.

## Window Utilization

How large a window is necessary to contain the ampere-turns of all the windings?. Ultimately, this is determined by maximum allowable power dissipation

**Topology considerations:** Bridge and half-bridge buck-derived topologies have the best primary winding utilization because the entire winding conducts most of the time. Forward converter winding utiliza-

Texas Instruments
3-8
SLUP132

tion is less efficient, because the windings usually conduct less than 50% of the time. Higher peak primary current is required for the same power output. Center-tapped windings utilize window area inefficiently because half of the winding is inactive while the other half conducts.

To balance the losses between primary and secondary(s), primary and secondary copper areas should be approximately equal for forward converters and for Center-tapped primaries with center-tapped secondaries. For bridge or half-bridge primary with centertapped secondaries, the primary copper should be approximately 40%, with the secondaries totaling 60%.

## Triple-Insulated Wire

Agency safety requirements for input-output isolation have imposed a severe burden on high frequency transformer design. The purpose of high frequency operation is to reduce size, weight and cost, but creepage and clearance requirements essentially waste almost 1 cm of the winding breadth This can make the transformer considerably larger than it would otherwise be, especially with small transformers in low power applications.

Recently, the ability to extrude three layers of insulation over a single wire or over an entire Litz wire bundle holds out the possibility of reducing the substantial penalty incurred by creepage and clearance requirements, thus enabling significant size reduction. Individual conductors in a triple-insulated Litz cable are single insulated, minimizing the penalty of the thicker triple layers.

Although triple-insulated wire is much more costly than conventional magnet wire or Litz wire, reduced transformer size would make it cost-effective.

Teflon FEP is presently approved as an insulation material, and other materials are under review. As of 1997, agency specifications are undergoing revision, and the situation is quite volatile. The author has received conflicting opinions regarding the usability of triple-insulated wire. The transformer designer should consult an engineer conversant with the situation for guidance early in the design phase.

Some of the vendors who indicate they can supply triple-insulation wire include:


<table>
  <tbody>
    <tr>
        <td>Rubadue Wire Co., Inc. (CA)</td>
        <td>714-693-5512</td>
    </tr>
    <tr>
        <td>Furukawa Electric (GA)</td>
        <td>770-487-1234</td>
    </tr>
    <tr>
        <td>New England Elec. Wire (NH)</td>
        <td>603-838-6625</td>
    </tr>
    <tr>
        <td>Kerrigan Lewis Wire Prod. (IL)</td>
        <td>773-772-7208</td>
    </tr>
  </tbody>
</table>

## Optimized Winding Placement

A fundamental principle of magnetic device design is not to allow the total magnetic force, $\iota$, build up to a substantial level. In a transformer, the magnetic source is the ampere-turns of the primary winding. The magnetic "load" is the nearly equal and opposite ampere-turns of the secondary(s). If the primary winding is put on one leg of a simple C-core, and the secondaries across the other leg, then the full magnetic force appears across the two core halves, radiating considerable stray flux to the outside world, resulting in high EMI and high leakage inductance. But if the secondary winding conforms to the primary, i.e., is wound directly over the primary on the same core leg, then the ampere-turns introduced by the primary are offset by the secondary ampere-turns, turn for turn, and the total magnetic force never builds to a substantial value. There is almost zero magnetic potential across the core halves which act simply as a short-circuit return path for the flux. There is very little stray flux, and leakage inductance is small. On a toroidal core, all windings should be uniformly distributed around the entire core.

With an inductor or flyback transformer, the magnetic source is the primary winding, the "load" is the gap where the energy is stored. With a gapped ferrite core, put the winding directly over the gap. Better, since the winding is distributed along the center-leg, distribute the gap along the center-leg with two or three correspondingly smaller gaps. If the gap is distributed, as in a powdered metal toriod, then the winding should be uniformly distributed around the core.

*Ideally, the magnetic source and load should be as intimate and conformal as possible, being distributed in exactly the same way.*

A ferrite toroid with a discrete gap does not conform to a winding distributed around the toroid. This is a complete disaster in terms of stray flux.

Texas Instruments
3-9
SLUP132

# Inter-Winding Capacitance

Inter-winding capacitance causes feedthrough of common mode noise from the switched primary winding to the secondary. Unfortunately, techniques that reduce leakage inductance and eddy current losses—interleaving, broad window, close P to S spacing—cause increased interwinding capacitance.

The proper use of Faraday shields will reduce the adverse coupling of the interwinding capacitance. A Faraday shield is an electrostatic shield consisting of thin foil or metalized insulating film wrapped completely around the interwinding space between primary and secondary. Where the shield overlaps, it must be insulated from itself to avoid being a shorted turn. The shield should be much thinner than the penetration depth $D_{PEN}$ to avoid passive eddy current losses.

The shield should be tied directly to the quiet side of the transformer primary, with minimum lead inductance. It should *not* be grounded, or much common-mode EMI will be propagated to the input.<sup>(5)</sup> Primary to shield capacitive charging current will add to losses in the primary-side switch unless ZVT techniques are used.

## End-to-end capacitance

End-to-end capacitance, sometimes called "distributed capacitance", appears in shunt with a winding. In a transformer, this capacitance results in series and parallel resonances with mutual inductance and leakage inductances. In a filter inductor, the end-to-end capacitance, above resonance, passes the high frequency components of the switched waveform through to the output.

End-to-end capacitance has a negligible effect in low voltage, low impedance windings, but in high voltage windings, it is a serious problem. High voltage windings have many turns which are usually wound back and forth in multiple layers. Thus the end of the second layer is directly over the beginning of the first layer. The effect of the significant capacitance between these layers is magnified because of the large ac voltage across the many intervening turns.

A single layer winding will have very little end-to-end capacitance, although there is a possible sneak path from end to core to end, unless the core is tied to an ac quiet point.

In a multi-layer winding, end-to-end capacitance is reduced dramatically by sectionalizing the winding along the available length—a technique often used in RF chokes, probably impractical in SMPS magnetics.

The "bank winding" technique for reducing end-to-end capacitance is shown in Figure 3-11.

![Diagram of bank winding technique showing numbered turns in a specific layered sequence with arrows indicating winding direction](page_33_image_1_v2.jpg)

*Figure. 3-11 Bank Winding*

With bank winding, the capacitance between physically adjacent turns has little effect because there are few electrically intervening turns, thus low voltage across the capacitance, compared with the conventional "back and forth" winding technique.

## Points to Remember

* Paralleling windings or wires within windings succeeds only if the expected division of high frequency current results in the smallest energy transfer.

* **Skin Effect**: A single wire has an infinite number of parallel paths within itself. High frequency current flows in the paths near the surface and not the paths in the center because this minimizes energy expenditure.

* **Proximity effect**: In a pair of conductors or windings thicker than $D_{PEN}$, with opposing currents, high frequency current flows only on those surfaces closest to each other, and will spread across those surfaces, in order to minimize expended energy.

* If multiple layers are connected in parallel, HF current will flow only on the inner surface of the inner layer. If the layers are connected in series, the same current must flow in all layers, but if layer thickness is greater than $D_{PEN}$, opposing high frequency currents of great magnitude will flow on the inner and outer surfaces of each layer,

Texas Instruments
3-10
SLUP132

causing losses to rise exponentially with the number of layers.

* Know the rules, and make them work for you, rather than against you.

* Using curves derived from Dowell, subdivide conductors into smaller diameter paralleled wires (Litz) to achieve R<sub>AC</sub>/R<sub>DC</sub> of 1.5. But a point may be reached where increased voids and insulation cause R<sub>DC</sub> to rise to the point where further subdivision is unproductive.

* Leakage inductance energy must be absorbed by snubbers or clamps, usually resulting in load dependent losses. Leakage inductance is also the main cause of impaired cross-regulation between multiple outputs.

* Minimize leakage inductance *and* eddy current loss by using a window shape that maximizes winding breadth, and/or by interleaving the windings. There is a penalty in increased inter-winding capacitance.

* Leakage inductance is increased by physical separation mandated by agency high voltage isolation requirements. Consider using triple-insulated wire, especially in low-power applications where isolation penalty is more severe.

* Distribute transformer windings so as to intimately conform to each other, to minimize leakage inductance and external stray fields. Place inductor windings to conform to the gap as closely as possible, whether a distributed gap or a discrete gap, to prevent build-up of magnetic force which propagates stray field.

* Minimize the *effect* of leakage inductance by using the appropriate winding hierarchy—the highest power secondary should be closest coupled to the primary. Keep the lower power windings out high field intensity region between primary and high-power secondaries.

* Avoid center-tapped primary windings. It would be nice if center-tapped secondaries could be avoided, as well.

## References:

(R2) "Eddy Current Losses in Transformer Windings and Circuit Wiring," *Unitrode Seminar Manual SEM600*, 1988 (reprinted in the Reference Section at the back of this Manual)

(1) P. L. Dowell, "Effects of Eddy Currents in Transformer Windings," *PROC. IEE* Vol. 113, No. 8, August 1966

(2) B. Carsten, "High Frequency Conductor losses in Switchmode Magnetics," *HFPC Proceedings*, 1986

(3) K. O'Meara, "Proximity Losses in AC Magnetic Devices," *PCIM Magazine*, December 1996

(4) PROXY -- Proximity effect analysis, KO Systems, Chatsworth, CA, 818-341-3864

(5) B. Carsten, "Switchmode Design and Layout Techniques," *APEC'97 Tutorial*

Texas Instruments
3-11
SLUP132

Texas Instruments | 3-12 | SLUP132

# Section 4 – Power Transformer Design

## Power Transformer Design

This Section covers the design of power transformers used in buck-derived topologies: forward converter, bridge, half-bridge, and full-wave center-tap. Flyback transformers (actually coupled inductors) are covered in a later Section. For more specialized applications, the principles discussed herein will generally apply.

## Functions of a Transformer

The purpose of a power transformer in Switch-Mode Power Supplies is to transfer power efficiently and instantaneously from an external electrical source to an external load. In doing so, the transformer also provides important additional capabilities:

*   The primary to secondary turns ratio can be established to efficiently accommodate widely different input/output voltage levels.

*   Multiple secondaries with different numbers of turns can be used to achieve multiple outputs at different voltage levels.

*   Separate primary and secondary windings facilitate high voltage input/output isolation, especially important for safety in off-line applications.

## Energy Storage in a Transformer

Ideally, a transformer stores no energy–all energy is transferred instantaneously from input to output. In practice, all transformers do store some undesired energy:

*   Leakage inductance represents energy stored in the non-magnetic regions between windings, caused by imperfect flux coupling. In the equivalent electrical circuit, leakage inductance is in series with the windings, and the stored energy is proportional to load current squared.

*   Mutual inductance (magnetizing inductance) represents energy stored in the finite permeability of the magnetic core and in small gaps where the core halves come together. In the equivalent circuit, mutual inductance appears in parallel with the windings. The energy stored is a function of

the volt-seconds per turn applied to the windings and is independent of load current.

## Undesirable Effects of Energy Storage

Leakage inductance delays the transfer of current between switches and rectifiers during switching transitions. These delays, proportional to load current, are the main cause of regulation and cross regulation problems. Reference (R4) included in this manual explains this in detail.

Mutual inductance and leakage inductance energy causes voltage spikes during switching transitions resulting in EMI and damage or destruction of switches and rectifiers. Protective snubbers and clamps are required. The stored energy then ends up as loss in the snubbers or clamps. If the loss is excessive, non-dissipative snubber circuits (more complex) must be used in order to reclaim most of this energy.

Leakage and mutual inductance energy is sometimes put to good use in zero voltage transition (ZVT) circuits. This requires caution–leakage inductance energy disappears at light load, and mutual inductance energy is often unpredictable, depending on factors like how well the core halves are mated together.

## Losses and Temperature Rise

Transformer loss is sometimes limited directly by the need to achieve a required overall power supply efficiency. More often, transformer losses are limited by a maximum “hot spot” temperature rise at the core surface inside the center of the windings. Temperature rise (°C) equals thermal resistance (°C/Watt) times power loss (Watts).

$$\Delta T = R_T \times P_L$$

Ultimately, the appropriate core size for the application is the smallest core that will handle the required power with losses that are acceptable in terms of transformer temperature rise or power supply efficiency.

Texas Instruments
4-1
SLUP132

**Temperature Rise Limit**

In consumer or industrial applications, a transformer temperature rise of 40-50°C may be acceptable, resulting in a maximum internal temperature of 100°C. However, it may be wiser to use the next size larger core to obtain reduced temperature rise and reduced losses for better power supply efficiency.

**Losses**

Losses are difficult to predict with accuracy. Core loss data from core manufacturers is not always dependable, partly because measurements are made under sinusoidal drive conditions. Low frequency winding losses are easy to calculate, but high frequency eddy current losses are difficult to determine accurately, because of the high frequency harmonic content of the switched rectangular current waveshape. Section 3 discusses this problem extensively. Computer software can greatly ease the difficulty of calculating the winding losses, including high order harmonics<sup>(1)</sup>.

**Thermal Resistance**

Temperature rise depends not only upon transformer losses, but also upon the thermal resistance, R<sub>T</sub> (°C/Watt), from the external ambient to the central hot spot. Thermal resistance is a key parameter, unfortunately very difficult to define with a reasonable degree of accuracy. It has two main components: internal thermal resistance R<sub>I</sub> between the heat sources (core and windings) and the transformer surface, and the external thermal resistance R<sub>E</sub> from the surface to the external ambient.

Internal thermal resistance depends greatly upon the physical construction. It is difficult to quantify because the heat sources are distributed throughout the transformer. R<sub>I</sub> from surface to internal hot spot is not relevant because very little heat is actually generated at that point. Most of the heat generated in the core (other than in toroids) is near the transformer surface. Heat generated within the winding is distributed from the surface to the internal core. Although copper has very low thermal resistance, electrical insulation and voids raises the R<sub>T</sub> within the winding. This is a design area where expertise and experience is very helpful. Fortunately, internal thermal resistance is considerably smaller than external R<sub>E</sub> (except

with high velocity forced air cooling), and while R<sub>I</sub> shouldn’t be ignored, it usually is not critically important compared with R<sub>E</sub>.

External R<sub>E</sub> is mainly a function of air convection across the surface of the transformer—either natural convection or forced air. R<sub>E</sub> with natural convection cooling depends greatly upon how the transformer is mounted and impediments to air flow in its vicinity. A transformer mounted on a horizontal surface and surrounded by tall components, or mounted in a relatively small enclosure will have considerably greater R<sub>E</sub> than if it were mounted on a vertical surface, benefiting from the “chimney effect”. With forced air cooling, R<sub>E</sub> can be driven down to a very small value, depending on air velocity, in which case internal R<sub>I</sub> becomes the primary concern. With forced air cooling, thermal resistance and temperature rise often become irrelevant, because an absolute loss limit to achieve power supply efficiency goals becomes dominant.

For the average situation with natural convection cooling, a crude “rule of thumb” can be used:

$$ R_E = \frac{800^\circ\text{C - cm}^2\text{ / Watt}}{A_S\text{ in cm}^2} \quad ^\circ\text{C / Watt} $$

Where A<sub>S</sub> is the total surface area of the transformer, excluding the mounting surface. Calculating A<sub>S</sub> is time-consuming, but another rule of thumb simplifies this, as well. For a given class of cores, such as E-E cores in the ETD or EC series, the relative proportions are quite similar for all core sizes. Thus for all cores in the ETD or EC series, the usable surface area, A<sub>S</sub>, is approximately 22 times the winding window area, A<sub>W</sub>. Combining this with the equation above enables the window area, A<sub>W</sub>, from the core data sheet, to be used to directly calculate the external thermal resistance:

$$ R_E = \frac{36}{A_W\text{ in cm}^2} \quad ^\circ\text{C / Watt} $$

For pot cores or PQ cores, window areas are proportionately smaller, and not as consistent. A<sub>S</sub>/A<sub>W</sub> may range from 25 to 50, so that R<sub>E</sub> may range from 16/A<sub>W</sub> to 32/A<sub>W</sub> °C/W.

Texas Instruments
4-2
SLUP132

Experience is a great help in minimizing and crudely quantifying thermal resistance. In the final analysis, an operational check should be conducted with a thermocouple cemented at the hot spot near the middle of the centerpost, with the transformer mounted in a power supply prototype or mockup.

## Worst Case Losses

Transformer losses should be examined under worst-case conditions that the power supply is expected to operate over long periods of time, not under transient conditions.

Transformer losses can be put into three major categories: core hysteresis losses, core eddy current losses, and winding losses.

**Core hysteresis losses** are a function of flux swing and frequency. In all buck-derived applications under steady-state conditions, V<sub>IN</sub>•D = n•V<sub>O</sub>. Under fixed frequency operation, volt-seconds and therefore flux swing are constant. Hysteresis loss is therefore constant, regardless of changes in V<sub>IN</sub> or load current.

**Core eddy current loss**, on the other hand, is really I²R loss in the core material. If V<sub>IN</sub> doubles, Peak I²R loss quadruples, but since D is halved, average I²R loss doubles. Thus core eddy current loss is proportional to V<sub>IN</sub>. *Worst case is at high V<sub>IN</sub>.*

**Winding losses:** In buck-derived regulators, peak secondary current equals load current and peak primary current equals load current divided by the turns ratio:

$$ I_{Spk} = I_L \ ; \ I_{Ppk} = I_L / n $$

Peak currents are independent of V<sub>IN</sub>. But at constant peak currents (constant load), *rms current squared (and I²R loss) is proportional to duty cycle D and inversely proportional to V<sub>IN</sub>.* (With constant peak current, high order harmonics depend mostly on switching transitions and do not vary significantly with D.)

*In buck-derived regulators, winding loss is always greatest at low V<sub>IN</sub>.*

**Ferrite cores:** In most ferrite materials used in SMPS applications, hysteresis losses dominate up to 200-300kHz. At higher frequencies, eddy current losses take over, because they tend to vary with frequency squared (for the same flux swing and wave-shape).

Thus, *at frequencies up to 200-300kHz, worst case is at low V<sub>IN</sub> and full load* because of high winding losses. Once core eddy current losses become significant, they rise rapidly with frequency, especially at high V<sub>IN</sub>. (The increase in eddy current loss with high V<sub>IN</sub>, small D, is not shown in core manufacturer’s loss curves because they assume sinusoidal waveforms.) Winding losses also rise with frequency, especially at low V<sub>IN</sub>. To maintain a reasonable R<sub>AC</sub>/R<sub>DC</sub>, Litz wire with more strands of finer wire must be used, raising R<sub>DC</sub> because increased insulation and voids reduce the copper area. Thus, *at frequencies where core eddy current losses dominate, core loss worst case is at high V<sub>IN</sub>, full load. Winding loss worst case is always at low V<sub>IN</sub>, full load.*

**Laminated metal alloy and powdered metal cores:** Core eddy current losses dominate, hence worst case is at high V<sub>IN</sub>, full load. Winding losses are worst case at low V<sub>IN</sub>, full load.

## Balancing Core and Winding Losses

At SMPS operating frequencies, when the core is usually loss-limited, not saturation limited, total losses are at a broad minimum when core losses are approximately equal to or a little less than winding losses. Likewise, winding losses are at a minimum and well distributed by making the rms current density approximately equal in all windings. With a bridge or half-bridge primary, which has good winding utilization, and center-tapped secondaries which have poor utilization, rms current densities will be approximately equalized when the primary conductor cross-section area is 40% and the secondaries 60% of the available area. In most other cases, primary and secondary conductor areas should be 50%/50%, including: Forward converter (single-ended primary/secondary SE/SE), C.T. primary/C.T. secondary, bridge-half bridge primary/bridge secondary.

Texas Instruments
4-3
SLUP132

The above allocations can be impossible to achieve because the number of turns in each winding must be an integral number. In a low voltage secondary, 1.5 turns may be required for optimum balance between core and winding losses. With one turn, the flux swing and core loss may be much too large; with two turns the winding loss becomes too great. At either extreme, it may be impossible to meet temperature rise or absolute loss limits. A larger core may be required to resolve this problem.

## Window Utilization

This subject is discussed extensively in Section 3. As a reminder:

* Safety isolation requirements impose minimum dimensional limits for creepage and insulation thickness which can waste a high percentage of window area, especially in a small transformer. A bobbin also reduces the area available for windings.

Triple insulated wire satisfies the insulation thickness requirement and eliminates the creepage requirement. It is worth considering, especially for small transformers where creepage distances take up a large percentage of window area.

* In the reduced window area that is available for the windings, much of the actual winding area is taken up by voids between round wires and by wire insulation. In a winding consisting of many turns of single, round, insulated wires, only 70 - 75% of the area available for that winding is likely to be conductor metal -- "copper". With Litz wire, the copper area is reduced further. For every level of twisting, an additional 0.75 factor (approximate) applies. For example, with Litz wire 7 strands of 7 strands (49 total wires), the copper area would be .75 • .75 • .75 = 42% of the area available for that winding. On the other hand, a winding consisting of layers (turns) of copper foil or strap, there are no voids, only the insulation between turns. Winding area utilization could be as much as 80 - 90% copper area.

## Topology

The choice of circuit topology obviously has great impact on the transformer design, but a detailed discussion is beyond the scope of this topic.

There is a great deal of overlap in topology usage. Flyback circuits (flyback transformers are covered in Section 5) are used primarily at power levels in the range of 0 to 150 Watts, Forward converters in the range of 50 to 500 Watts, half-bridge from 100 to 1000 Watts, and full bridge usually over 500 Watts.

Full bridge and half-bridge topologies with full bridge secondaries have the best transformer efficiency because the core and the windings are fully utilized. With center-tapped secondaries, winding utilization and efficiency are reduced. With center-tapped primary *and* secondaries, winding utilization and efficiency are further reduced. All of the push-pull topologies have the further advantage that for a given switching frequency, giving the same output ripple filtering and closed loop capability, the frequency at which the transformer core and windings operate is halved, reducing core and ac winding losses.

Forward converter transformers have the poorest utilization and efficiency because neither the core nor the windings are used during the lengthy core reset interval.

## Frequency

There are several meanings to the term "frequency" in switching power supply applications, and it is easy for confusion to arise.

In this paper, "switching frequency", $f_S$, is defined as the frequency at which switch drive pulses are generated. It is the frequency seen by the output filter, the frequency of the output ripple and input ripple current, and is an important concept in control loop design. In a single-ended power circuit such as the forward converter, the power switch, the transformer, and the output rectifier all operate at the switching frequency and there is no confusion. The transformer frequency and the switching frequency are the same.

"Clock frequency" is the frequency of clock pulses generated in the control IC. Usually, the switching frequency is the same as the clock frequency, but not always. Occasionally, the control IC may divide the clock frequency to obtain a lower switching frequency. It is not unusual for a push-pull control IC to be used in a single-ended forward converter application, where only one of the two switch

Texas Instruments
4-4
SLUP132

drivers is used, to guarantee 50% max. duty cycle. In this case the switching frequency is half the clock frequency.

Confusion often arises with push-pull topologies. Think of the push-pull power circuit as a 2:1 frequency divider, with the transformer and the individual switches and individual rectifiers operating at a “transformer frequency”, $f_T$, which is one-half of the switching frequency. Collectively, the switches and rectifiers operate at the switching frequency, but the transformer operates at the transformer frequency. Some designers define “switching frequency” as the frequency that the individual switch and the transformer operate at, but this requires redefining the term “switching frequency” when dealing with output ripple and in control loop design.

## Duty Cycle

Duty cycle, D, is defined as the amount of time the power switch is on in relation to the switching period: $D = t_{ON}/T_S$.

In a single-ended forward converter, this is clearly understood, but in a push-pull circuit, ambiguity often arises. For example, in a half-bridge circuit operating at minimum $V_{IN}$, the duty cycle is likely to be in the vicinity of 90% (D = 0.9). The transformer is delivering power to the output 90% of the time, there is a voltage pulse applied to the filter input 90% of the time, etc. But individual power switches and individual rectifiers, which conduct only during alternate switching periods, can be said to operate at a duty cycle of 45%. That is true, but it is better to think of them as operating at D/2, retaining a consistent definition of D throughout the power supply design.

## Maximum Duty Cycle

In normal steady-state operation of a buck-derived regulator, $V_{IN} \cdot D$ is constant. The control loop changes duty cycle D inversely proportional to $V_{IN}$ to maintain a constant output voltage, $V_O$. ($V_{IN}D = n \cdot V_O'$), where n is the turns ratio $N_P/N_S$, and $V_O'$ equals output voltage $V_O$ plus diode forward voltage drop at full load.

At a fixed switching frequency and with normal steady-state operation, the volt-seconds applied to the transformer windings are constant, independent of line voltage or load current.

$$V_{IN}t_{on} = \frac{V_{IN}D}{f_S} = \frac{nV_O'}{f_S}$$

The maximum duty cycle, Dmax, associated with minimum $V_{IN}$ in normal steady-state operation, is limited by a variety of considerations:

* In a forward converter, a substantial portion of each switching period must be allowed for core reset. If the voltage backswing during reset is clamped to $V_{IN}$, the duty cycle must be limited to less than 50% because the time required for reset equals the switch ON time.

* In a push-pull converter (bridge, half-bridge, PPCT) duty cycle can approach 100% at the switching frequency (always think of D at the switching frequency, not the transformer frequency). However, it may be necessary to limit D to less than 90% to allow a current transformer to self-reset.

* Often the control IC limits the duty cycle for several reasons including allowing time for delays in turning off the switch.

* At low $V_{IN}$, if normal Dmax is right at the duty cycle limit, the regulator has no reserve volt-second capability and cannot respond rapidly to a sudden load increase occuring when $V_{IN}$ is low. It may be desirable to make the “normal” Dmax less than the absolute limit, Dlim, to provide a little headroom in this situation.

A potentially serious problem needs to be considered: During initial start-up of the power supply, or following a sudden large increase in load current which temporarily pulls down Vout, the control loop calls for full current, pushing the duty cycle to its absolute maximum limit, Dlim. The output filter inductor limits the current rate of rise, so that for several switching frequency periods, the duty cycle is at the limit, Dlim. During the transient event described above, Dlim could occur when $V_{IN}$ is maximum. Thus, the volt-seconds applied to the transformer windings could be several times larger than normal:

Limit $V_{IN}D = V_{INmax}D_{lim}$

Normal $V_{IN}D = V_{INmin}D_{max}$

Texas Instruments
4-5
SLUP132

The flux swing, also several times greater than normal, could saturate the core. (The increased core loss is not a problem—it is only temporary.)

This may not be a problem if the ratio limit/normal $V_{IND}$ is small and/or if the normal flux density swing, limited by core loss, is a small fraction of $B_{sat}$ ($B_{sat} - B_r$ for a forward converter). For example, if limit/normal $V_{IND}$ is 3:1, and if normal $\Delta B$ is 0.08T, then with $B_{sat}$ greater than 0.24T, there is no problem.

If this problem exists, soft-start circuitry can eliminate it during start-up, but soft-start has no effect when the load increases rapidly. A few IC control circuits have volt-second limiting capability, but the vast majority do not. The soft saturation characteristic of power ferrite material may be forgiving enough to allow the core to saturate, with the absolute current limit providing protection, but with sharp-saturation core materials, this is a likely disaster. If all else fails, the normal flux swing must be reduced to the point where the abnormal flux swing does not reach saturation.

# Restrictions on Number of Turns

Choices regarding the number of turns and turns ratios are often severely limited by low voltage secondaries. For a 5 Volt output the alternatives might be a 1-turn or a 2-turn secondary—a 2 to 1 step in the number of turns in every winding. For the same size core and window, this doubles the current density in the windings and accordingly increases the loss.

Choices may be further restricted when there are multiple low voltage secondaries. For example, a 2.5 to 1 turns ratio may be desirable between a 12 Volt and a 5 Volt output. This is easily accomplished with a 2-turn 5V secondary and a 5-turn 12V winding. But if the 5V secondary has only 1 turn, the only choice for the 12V secondary is 3 turns, which may result in excessive linear post-regulator loss. This problem could be handled by the use of fractional turns -- see reference (R6).

There are no hard and fast rules to follow in establishing the optimum turns for each winding, but there is some general guidance. First, define the ideal turns ratios between windings that will achieve the desired output voltages with the normal $V_{IND}$ established earlier. Later, when a specific core has been

tentatively selected, the turns ratios will translate into specific turns, but these are not likely to be the integral numbers required in practice. It then becomes a juggling act, testing several approaches, before reaching the best compromise with integral turns. The lowest voltage secondary usually dominates this process, because with small numbers the jumps between integral turns are a larger percentage. Especially if the lowest voltage output has the greatest load power, which is often the case, the lowest voltage secondary is rounded up or down to the nearest integral. Rounding down will increase core loss, rounding up will increase winding loss. If the increased loss is unacceptable, a different core must be used that will require less adjustment to reach an integral number of turns. The low voltage output is usually regulated by the main control loop.

Higher voltage secondaries can be rounded up to the next integral with less difficulty because they have more turns. However, it is unlikely that accuracy or load regulation will be acceptable, requiring linear or switched post-regulation.

Since the primary is usually higher voltage, the primary turns can usually be set to achieve the desired turns ratio without difficulty.

Once the turns have been established, the initial calculations must be redefined.

# Flux Walking

Faraday’s Law states that the flux through a winding is equal to the integral volt-seconds per turn. This requires that the voltage across any winding of any magnetic device must average zero over a period of time. The smallest dc voltage component in an applied ac waveform will slowly but inevitably “walk” the flux into saturation.

In a low frequency mains transformer, the resistance of the primary winding is usually sufficient to control this problem. As a small dc voltage component pushes the flux slowly toward saturation, the magnetizing current becomes asymmetrical. The increasing dc component of the magnetizing current causes an IR drop in the winding which eventually cancels the dc voltage component of the drive waveform, hopefully well short of saturation.

Texas Instruments
4-6
SLUP132

In a high frequency switchmode power supply, a push-pull driver will theoretically apply equal and opposite volt-seconds to the windings during alternate switching periods, thus "resetting" the core (bringing the flux and the magnetizing current back to its starting point). But there are usually small volt-second asymmetries in the driving waveform due to inequalities in MOSFET R<sub>DSon</sub> or switching speeds. The resulting small dc component will cause the flux to "walk". The high frequency transformer, with relatively few primary turns, has extremely low dc resistance, and the IR drop from the dc magnetizing current component is usually not sufficient to cancel the volt-second asymmetry until the core reaches saturation.

Flux walking is not a problem with the forward converter. When the switch turns off, the transformer magnetizing current causes the voltage to backswing, usually into a clamp. The reverse voltage causes the magnetizing current to decrease back to zero, from whence it started. The reverse volt-seconds will exactly equal the volt-seconds when the switch was ON. Thus the forward converter automatically resets itself (assuming sufficient reset time is allowed, by limiting the maximum duty cycle).

The flux walking problem is a serious concern with any push-pull topology (bridge, half-bridge or push-pull CT), when using voltage mode control..

One solution is to put a *small gap* in series with the core. This will raise the magnetizing current so that the IR drop in the circuit resistances will be able to offset the dc asymmetry in the drive waveform. But the increased magnetizing current represents increased energy in the mutual inductance which usually ends up in a snubber or clamp, increasing circuit losses.

A more elegant solution to the asymmetry problem is an automatic benefit of using current mode control (peak or average CMC). As the dc flux starts to walk in one direction due to volt-second drive asymmetry, the peak magnetizing current becomes progressively asymmetrical in alternate switching periods. However, current mode control senses current and turns off the switches at the same peak current level in each switching period, so that ON times are alternately lengthened and shortened. The initial volt-second asymmetry is thereby corrected, peak magnetizing currents are approximately equal in both directions, and flux walking is minimized.

However, with the half-bridge topology this creates a new problem. When current mode control corrects the volt-second inequality by shortening and lengthening alternate pulse widths, an ampere-second (charge) inequality is created in alternate switching periods. This is of no consequence in full bridge or push-pull center-tap circuits, but in the half-bridge, the charge inequality causes the capacitor divider voltage to walk toward the positive or negative rail. As the capacitor divider voltage moves away from the mid-point, the volt-second unbalance is made worse, resulting in further pulse width correction by the current mode control. A runaway situation exists, and the voltage will walk (or run) to one of the rails. This problem is corrected by adding a pair of diodes and a low-power winding to the transformer, as detailed in the Unitrode Applications Handbook.

## Core Selection: Material

Select a core material appropriate for the desired transformer frequency.

With power ferrites, higher frequency materials have higher resistivity, hence lower eddy current losses. However, the permeability is generally lower, resulting in greater magnetizing current, which must be dealt with in snubbers and clamps.

With metal alloy cores, the higher frequency materials have higher resistivity and require very thin laminations. Although saturation flux density is usually very much greater than with ferrite materials, this is usually irrelevant because flux swing is severely limited by eddy current losses.

Ferrite is the best choice in transformer applications except for mechanical ruggedness.

## Core Selection: Shape

The window configuration is extremely important. The window should be as wide as possible to maximize winding breadth and minimize the number of layers. This results in minimized R<sub>ac</sub> and leakage inductance. Also, with a wide window, the fixed creepage allowance dimension has less impact. With a wider window, less winding height is required, and the window area can be better utilized.

Texas Instruments
4-7
SLUP132

Pot cores and PQ cores have small window area in relation to core size, and the window shape is almost square. The creepage allowance wastes a large fraction of the window area, and the winding breadth is far from optimum. These cores are not as well suited for high frequency SMPS applications. One advantage of pot cores and PQ cores is that they provide better magnetic shielding than E-E cores, reducing EMI propagation.

EC, ETD, LP cores are all E-E core shapes. They have large window area in relation to core size, and the window has the desirable wide configuration.

Toroidal cores, properly wound, must have all windings distributed uniformly around the entire core. Thus the winding breadth is essentially the circumference of the core, resulting in the lowest possible leakage inductance and minimizing the number of winding layers. There is no creepage allowance because there is no end to the windings. (But there is a problem bringing the leads out.) Stray magnetic flux and EMI propagation are also very low.

The big problem with toroidal cores is the winding difficulty, especially with the shapes and gauge of conductors used in SMPS transformers. How can a 1-turn secondary be spread around the entire toroid? Automatic winding is virtually impossible. For this reason, toroidal shapes are seldom used in SMPS transformers.

Planar cores with their low profile are becoming more popular as SMPS frequencies progressively increase. Planar cores introduce a new set of unique problems which are beyond the scope of this discussion. Be assured that Faraday’s and Ampere’s Laws still apply, but in a planar core, flux density and field intensity change considerably throughout the important regions, making calculation much more difficult.

## Core Selection: Size

A novice in the art of transformer design usually needs some guidance in making an initial estimate of the core size appropriate for the application requirements. One widely used method, with many variations, is based on the core Area Product, obtained by multiplying the core magnetic cross-section area by the window area available for the winding.

There are many variables involved in estimating the appropriate core size. Core power handling capability does not scale linearly with area product or with core volume. A larger transformer must operate at a lower power density because heat dissipating surface area increases less than heat-producing volume. The thermal environment is difficult to evaluate accurately, whether by forced air or natural convection.

Some core manufacturers no longer provide area product information on their data sheets, often substituting their own methodology to make an initial core size choice for various applications.

The following formula provides a crude indication of the area product required:

$$ AP = A_W A_E = \left( \frac{P_O}{K \ \Delta B \ f_T} \right)^{4/3} \text{ cm}^4 $$

where:

* **$P_O$**: = Power Output
* **$\Delta B$**: = Flux density swing, Tesla
* **$f_T$**: = Transformer operating frequency
* **$K$**: = .014 (Forward converter, PPCT)
* **$K$**: = .017 (Bridge, half bridge)

This formula is based on current density of $420 \text{A/cm}^2$ in the windings, and assumes a window utilization of 40% copper. At low frequencies, the flux swing is limited by saturation, but above 50kHz (ferrite), $\Delta B$ is usually limited by core losses. Use the $\Delta B$ value that results in a core loss of $100 \text{mW/cm}^3$ (2 times the "flux density" given in the core loss curves).

These initial estimates of core size are not very accurate, but they do reduce the number of trial solutions that might otherwise be required. In the final analysis, the validity of the design should be checked with a prototype transformer operated in the circuit and the environment of the application, with the hot spot temperature rise measured by means of a thermocouple cemented to the center of the centerpost.

Texas Instruments
4-8
SLUP132

# Transformer Design Cookbook

The steps for designing a power transformer for SwitchMode Power Supplies is outlined below. A typical example is carried through to illustrate the process. There are many approaches to transformer design. The approach presented here appears the most logical and straightforward to the author.

It may be worthwhile to use software such as "Magnetic Designer" from Intusoft<sup>(2)</sup> for the initial design, using the approach defined herein for verification and tune-up. The author has not evaluated "Magnetic Designer" sufficiently to make an unqualified endorsement, but it should certainly make a good starting point and take a great deal of drudgery out of the process. It has the advantage of including an extensive core database.

## Initial Preparation

The first few steps in this process define application parameters that should not change, regardless of subsequent iterations in the selection of a specific core type and size.

If the results are not acceptable, start over from the very beginning, if that seems appropriate. Great difficulty in achieving an acceptable forward converter transformer design may be a subtle message that a half-bridge topology is perhaps a better choice.

**Step 1.** Define the power supply parameters pertaining to the transformer design:

* **VIN Range**: 100 - 190 V
* **Output 1**: 5 V, 50 A
* **Output 2**: none
* **Circuit Topology**: Forward Converter
* **Switching Freq, fs**: 200 kHz
* **Transformer Freq, ft**: 200 kHz
* **Max Loss (absolute)**: 2.5 W
* **Max °C Rise**: 40°C
* **Cooling Method**: Natural Convection

**Step 2.** Define absolute duty cycle limit $D_{lim}$, tentative normal $D_{max}$ at low $V_{IN}$ (to provide headroom for dynamic response), and normal $V_{IN} \cdot D$:

* **Absolute Limit, Dlim**: 0.47
* **Normal Dmax**: 0.42
* **Normal VIN•D**: $V_{INmin} \cdot D_{max} = 42\text{ V}$

* **VINmaxDlim**: 89.3 V

**Step 3.** Calculate output voltages plus diode and secondary IR drops at full load:

* **VO1'**: 5.0 + 0.4 = 5.4 Volts
* **VO2'**: n/a

**Step 4.** Calculate desired turns ratios: P-S1; S1-S2, etc. Remember that choices with low voltage secondaries will probably be limited.

* **n = Np/Ns1 = VIND/VO1'**: 42/5.4 = 7.8
* **Possible choices**: 8:1; 7:1; 15:2

## Core Selection

**Step 5:** Tentatively select core material, shape and tentative size, using guidance from the manufacturer's data sheet or using the area product formula given previously in this paper. Will a bobbin be used?:

* **Core Material**: Ferrite, Magnetics Type P
* **Core type, Family**: ETD
* **Core Size**: 34mm -- ETD34

**Step 6:** For the specific core selected, note: Effective core Area, Volume, Path Length. (cm)

* **Ae**: 0.97 cm²
* **Ve**: 7.64 cm³
* **le**: 7.9 cm

Window Area, Breadth, Height, Mean Length per Turn (' indicates net with bobbin, creepage).

* **Aw / Aw'**: 1.89 / 1.23 cm²
* **bw / bw'**: 2.36 / 1.5 cm
* **hw / hw'**: 0.775 / 0.6 cm
* **MLT**: 5.8 / 6.1 cm

## Define RT and Loss Limit

**Step 7:** Obtain thermal resistance from data sheet or calculate from window area (not bobbin area) from formula for EC and ETD series:

$$R_E = \frac{800}{22 \cdot A_w \text{ in cm}^2} = \frac{36}{1.89} = 19 \text{ °C/Watt}$$

Texas Instruments
4-9
SLUP132

Calculate loss limit based on max. temperature rise:

$$Plim = °Crise/R_T: = 40/19 = 2.1 Watts$$

The 2.1W limit applies, since it is less than the absolute limit from Step 1. Tentatively apportion half to core loss, half to winding loss.

**PClim**: 1 Watt
**PWlim**: 1.1 Watt

## Step 8: Loss Limited Flux Swing

Calculate max. core loss per cm³

$$PClim/Ve = 1/7.64 = 131 mw/cm^3 (= kW/m^3)$$

Using this core loss value, enter the core loss curve for the P material selected. At the *transformer* frequency, find "flux density" (actually peak flux density). Double it to obtain the loss-limited peak-peak flux density swing, $\Delta B$:

At 131 mw/cm³ and 200kHz:
$\Delta B = 2 \cdot 800 \text{ Gauss} = 1600G = 0.16 \text{ Tesla}$
Normal $\Delta \phi = \Delta B \cdot A_e$

**Step 9**: Using Faraday's Law, calculate the number of secondary turns:

$$\int E_{S1} dt = Vpk_{S1} t_{ON} = V_{O1}' \cdot T_S$$
$$N_{S1} = \int E_{S1} dt / \Delta \phi = V_{O1}' \cdot T_S / \Delta \phi$$
$$N_{S1} = \frac{V_{O1}' T_S}{\Delta B \times A_E} = \frac{5.4 \times 5 \times 10^{-6}}{.16 \times .97 \times 10^{-4}} = 1.74 \text{ Turns}$$

Rounding down to 1 turn will greatly increase the volts/turn, flux swing and core losses. Rounding up to 2 turns reduces core losses but increases winding loss. Since the result above is much closer to 2 turns, this will be adopted.

**Step 10**: Recalculate flux swing and core loss at 2 turns:

$$\Delta B(2 \text{ turns}) = 0.16T \frac{1.74 \text{ turns}}{2 \text{ turns}} = 0.14 \text{ Tesla}$$

From the core loss curves, loss at 0.14T/2 (700 Gauss) is $110mw/cm^3 \times 7.64cm^3$

**Core loss = 0.84 W**

**Step 11**: Finalize the choice of primary turns. A larger turns ratio results in lower peak current, larger D (less reserve), and more copper loss. From the possibilities defined in Step 4, trial solutions show the best choice to be $N_P = 15$ turns (7.5:1 turns ratio).

Recalculate normal VIND and flux swing under worst case $VIN_{max} D_{lim}$ conditions:

$$VIND = nVO' = 7.5 \cdot 5.4 = 40.5 V$$

$$\Delta Blim = 0.14T \cdot 89.3 / 40.5 = 0.31T \text{ -- OK}$$

**Step 12**: Define the winding structure.

An interleaved structure will be used, as shown in Figure 4-1, to minimize leakage inductance and winding losses.

![Diagram of an interleaved winding structure on a bobbin with 3 layers of 1 mil Mylar insulation.](page_45_layout_ocr_bgds_317_272_241_256.png)

Figure 4-1

The interleaved structure results in two winding sections. Primary windings of 15 turns in each section are connected in parallel. Primary current divides equally in the two paralleled windings because this results in the lowest energy transfer. Secondary windings of 1 turn copper foil in each section are connected in series, resulting in a 2-turn secondary. With only one turn in each section, the secondary windings can be much thicker than $D_{PEN}$ to minimize dc resistance without increasing the ac resistance.

<page_footer>
4-10
</page_footer>

Texas Instruments
4-10
SLUP132

**Step 12: Calculate DPEN at 200 kHz:**

$$Dpen = 7.6/\sqrt{f} = 7.6/\sqrt{200,000} = .017 \text{ cm}$$

**Step 13: Calculate dc and rms ac currents in each winding at VINmin and Dmax. (Ref. Section 3):**

$$ISdc = 50A \cdot Dmax = 50 \cdot 0.405 = 20.25A$$

$$ISac = ISdc((1-D)/D)^{1/2} = 24.5A$$

$$IPdc = ISdc/n = 20.25/7.5 = 2.7A$$

$$IPac = ISac/n = 24.5/7.5 = 3.27A$$

Primary current in each of the two paralleled sections is one-half the total primary current: 1.35Adc and 1.65Aac.

**Step 14: Define the primary winding:**

One layer of 15 turns spread across the available winding breadth of 1.3cm allows a maximum insulated wire diameter of 0.87mm. AWG 21 – 0.72mm copper will be used.

From Ref R2, pg 9, the effective layer thickness equals $0.83 \cdot dia(dia/spacing)^{1/2}$.

Q = (layer thickness)/DPEN
$$Q = 0.83 \cdot .072(.072/.087)^{1/2}/.017 = 3.19$$

From Dowell’s curves, Rac/Rdc for 1 layer is 3.1. This will result in unacceptable ac losses.

A Litz wire consisting of 100 strands #42 wire has a diameter of 0.81mm and a resistance of 0.545m$\Omega$/cm.

The dc resistance of the single layer is:

$$Rdc = \Omega/cm \cdot MLT \cdot Ns = .00055 \cdot 6.1 \cdot 15 = .05\Omega$$

Multiplying by $(1.35Adc)^2$, dc power loss is .091W in each section, for a total primary dc loss of 0.18W.

The diameter of each #42 wire is .064mm, but there are effectively ten layers of fine wire in the single layer of Litz wire. This is because the 100 strands are roughly equivalent to a 10 x 10 array, thus ten wires deep. Q is approximately 1/10 the value for solid wire, or 0.3, resulting in Rac/Rdc of 1.2. Thus, Rac = Rdc$\cdot$1.2, or .06$\Omega$.

Multiplying by 1.65A squared, the ac loss is 0.16W in each section, for a total primary ac loss of 0.32W. Adding the 0.18W dc loss,

**Total primary power loss = 0.5 Watts.**

Step 15: Define the secondary winding.

The secondary consists of two turns (two layers) of copper strip or foil, 1.3cm wide (full available winding breadth), and 0.13cm thick. There is one secondary layer in each of the two sections of the interleaved winding structure. This permits the thickness of the copper strip to be much greater than DPEN to minimize dc losses, without increasing ac losses. This is because ac current flows only on the outer side of each turn. As the conductor is made thicker, Rac/Rdc becomes larger, but Rdc decreases and Rac remains the same.

With a solid copper secondary, the layer thickness is the same as the conductor thickness, 0.1cm.

Q = Layer thickness/DPEN = 0.13/.017 = 7.6
Rac/Rdc = 7.5

This will be acceptable because the dc resistance is very low.

$$Rdc = \rho \cdot MLT \cdot Ns/(bw'h)$$
$$Rdc = 2.3 \cdot 10^{-6} \cdot 6.1 \cdot 2/(1.3 \cdot 0.13) = 166\mu\Omega$$
$$Pdc = 166\mu\Omega \cdot 20.25^2 = .068 \text{ W}$$
$$Pac = Rdc \cdot Rac/Rdc \cdot Iac^2 = 166\mu\Omega \cdot 7.5 \cdot 24.5^2$$
Pac = 0.75 W
Total secondary loss:
.068W + 0.75W = 0.82 W
Total copper loss:
0.82W + 0.5W = 1.32 W

Total core plus copper loss:

**0.84W + 1.32W = 2.16 Watts**

Thus, the total power loss is under the absolute limit of 2.5Watts, but slightly over the 2.1 Watt limit based on the desired max. temperature rise of 40°C.

Texas Instruments
4-11
SLUP132

# References:

(R2) “Eddy Current Losses in Transformer Windings and Circuit Wiring,” *Unitrode Seminar Manual SEM600*, 1988 (reprinted in the Reference Section at the back of this Manual)

(R4) “The Effects of Leakage Inductance on Switching Power Supply Performance,” *Unitrode Seminar Manual SEM100*, 1982 (reprinted in the Reference Section at the back of this Manual)

(R6) “How to Design a Transformer with Fractional Turns,” *Unitrode Seminar Manual SEM500*, 1987 (reprinted in the Reference Section at the back of this Manual)

(1) PROXY -- Proximity effect analysis, KO Systems, Chatsworth, CA, 818-341-3864

(2) “Magnetics Designer,” Magnetics design software, IntuSoft, San Pedro, CA 310-833-0710

Texas Instruments 4-12 SLUP132

# Section 5 — Inductor and Flyback Transformer Design

Filter inductors, boost inductors and flyback transformers are all members of the "power inductor" family. They all function by taking energy from the electrical circuit, storing it in a magnetic field, and subsequently returning this energy (minus losses) to the circuit. A flyback transformer is actually a multi-winding coupled inductor, unlike the true transformers discussed in Section 4, wherein energy storage is undesirable.

## Application Considerations

Design considerations for this family of inductors vary widely depending on the type of circuit application and such factors as operating frequency and ripple current.

Inductor applications in switching power supplies can be defined as follows (see Fig. 5-1):

*   Single winding inductors:
        *   Output filter inductor (buck-derived)
    *   Boost inductor
    *   Flyback (buck-boost) inductor
    *   Input filter inductor

*   Multiple winding inductors:
        *   Coupled output filter inductor <sup>(R5)</sup>
    *   Flyback transformer

![Schematic diagrams of Buck, Boost, Flyback (Buck-Boost), and Flyback Transformer circuit topologies.](page_48_image_1_v2.jpg)

Figure 5-1 Inductor Applications

Inductor design also depends greatly on the inductor current operating mode (Figure 5-2):

*   *Discontinuous inductor current mode*, when the instantaneous ampere-turns (totaled in all windings) dwell at zero for a portion of each switching period.

*   *Continuous inductor current mode*, in which the total ampere-turns do not dwell at zero (although the current may pass through zero).

In the continuous current mode, the ripple current is often small enough that ac winding loss and ac core loss may not be significant, but in the discontinuous mode, ac losses may dominate.

**Design limitations:** The most important limiting factors in inductor design are (a) temperature rise and efficiency considerations arising from core losses and ac and dc winding losses, and (b) core saturation.

**Output filter inductors (buck-derived) --single and multiple windings** are seldom operated in the *discontinuous* current mode because of the added burden this places on the output filter capacitor, and because it results in poor cross-regulation in multiple output supplies. Typically operated in the *continuous mode* with peak-peak ripple current much smaller than full load current, ac winding loss is usually not significant compared to dc loss.

Texas Instruments
5-1
SLUP132

![Inductor Current Modes diagrams showing discontinuous and continuous modes](page_49_chart_1_v2.jpg)

Figure 5-2 Inductor Current Modes

For example, assume full load $I_{dc}$ of 10A, and typical peak-peak triangular ripple current 20% of $I_{dc}$, or 2A (worst at high Vin). In this example, the worst-case rms ripple current is 0.58A (triangular waveform rms equals $I_{pp}/\sqrt{12}$), and rms ripple current *squared* is only .333, compared with the dc current *squared* of 100. Thus, for the ac $I^2R$ loss to equal the dc loss, the $R_{ac}/R_{dc}$ ratio would have to be as large as 300 (Section 3, Fig. 3-5). This is easily avoided. Therefore, ac winding loss is usually not significant.

Also, the small flux swing associated with small ripple current results in small core loss, with high frequency ferrite core material operating below 250kHz. Core utilization is then limited by saturation (at peak short-circuit current). However, the small flux swing may permit the use of lossier core materials with higher $B_{SAT}$, such as powdered iron, Kool-mu®, or laminated metal. This may enable reduced cost or size, but core loss then becomes more significant. Also, distributed-gap materials exhibit rounding of the B-H characteristics (Sec. 2, pg. 2-3), resulting in decreasing inductance value as current increases.

**Boost and input filter inductors and single winding flyback inductors** are often designed to operate in the *continuous mode*. As with the buck-derived filter inductors described previously, inductor

design is then usually limited by dc winding losses and core saturation.

However, many boost and flyback applications are designed to operate in the *discontinuous mode*, because the required inductance value is less and the inductor physical size *may* be smaller. But in the discontinuous mode, the inductor current must dwell at zero (by definition) during a portion of each switching period. Therefore, the peak of the triangular current waveform, and thus the peak-to-peak ripple must be *at least twice* the average current, as shown in Fig. 5-2(a). This very large ripple current results in a potentially serious ac winding loss problem. Also, the resulting large flux swing incurs high core loss. Core loss then becomes the limiting factor in core utilization, rather than saturation, and may dictate a larger core size than otherwise expected.

Thus, the circuit designer's choice of operating mode makes a substantial difference in the inductor design approach.

When **flyback transformers** are operated in the continuous inductor current mode, the total ampere-turns of all the windings never dwell at zero (by definition). However, the current in *each winding* of any flyback transformer is *always highly discontinuous*, regardless of inductor current mode. This is because current (ampere-turns) transfers back and forth between primary and secondary(s) at the switching frequency. As shown in Fig. 5-3, the current in each winding alternates from zero to a high peak value, even though the *total* ampere-turns are continuous with small ripple. This results in large ac winding loss, regardless of the operating mode.

However, the core sees the total ampere-turn ripple. Thus, core loss behaves in the same manner as with the single winding flyback inductor discussed previously - small core loss when designed and operated in the continuous mode, large core loss in the discontinuous mode.

![Flyback Transformer Currents diagram showing primary and secondary currents](page_49_layout_ocr_lndb_312_560_249_132.png)

Figure 5-3 - Flyback Transformer Currents

Texas Instruments
5-2
SLUP132

# Losses and Temperature Rise

The discussion in Section 4 regarding temperature rise limits, losses and thermal resistance in transformers (pp 4-1,2) is generally applicable to inductors, as well.

## Balancing Core and Winding Losses

When inductors are designed for the discontinuous mode, with significant core loss, total loss is at a broad minimum when core and winding losses are approximately equal. But when inductors are designed for the continuous mode, core loss is often negligible, so that the total loss limit can be allocated entirely to the windings.

## General Considerations -- Core

Ideal magnetic materials cannot store energy. Practical magnetic materials store very little energy most of which ends up as loss. In order to store and return energy to the circuit efficiently and with minimal physical size, a small non-magnetic gap is required in series with a high permeability magnetic core material. In ferrite or laminated metal alloy cores, the required gap is physically discrete, but in powdered metal cores, the gap is distributed among the metal particles.

Paradoxically, virtually all of the magnetic energy is stored the so-called "non-magnetic" gap(s). The sole purpose of the high permeability core material is to provide an easy, low reluctance flux path to link the energy stored in the gap to the winding, thus efficiently coupling the energy storage location (the gap) to the external circuit.

In performing this critically important function, the magnetic core material introduces problems: (a) core losses caused by the flux swings accompanying the storage and release of energy, and (b) core saturation, where the core material becomes non-magnetic and therefore high reluctance above a certain flux density level. The energy storage capability of a practical gapped core is thus limited either by temperature rise associated with core loss, or by core saturation.

**Stray Flux.** Another problem that must be faced is stray flux, associated with energy stored in a fringing field outside the gap. Stray flux couples noise and EMI to the external circuit and to the outside world. This stray energy also increases the inductance beyond its intended value by an amount that is difficult to predict.

To minimize stray flux, it is very important that the winding distribution conforms to the gap. When the gap is distributed throughout the core, as in pow-

dered metal cores, the winding(s) should be likewise distributed. Thus, a toroidal core shape should have the windings distributed uniformly around the entire core.

With a discrete gap, used with laminated metal alloy cores or ferrite cores, the winding should be directly over the gap. For example, if a pair of "C" core halves has a gap in one leg and the winding is placed on the opposite (ungapped) leg, as shown in Fig. 5-4a, the entire magnetic force introduced by the winding appears across the two core halves. This results in considerable stray flux propagated external to the device, in addition to the flux through the gap. The energy stored in the external stray field can easily equal the energy stored in the gap, resulting in an inductance value much greater than expected. The external stored energy is difficult to calculate, making the total inductance value unpredictable. Also, the additional flux in the stray field will cause the inductor to saturate prematurely.

However, when the same winding is placed on the gapped core leg, as in Fig. 5-4b, the entire magnetic force introduced by the winding is dropped across the gap directly beneath. The magnetic force across the two core halves is then nearly zero, and there is little external flux. The core then serves its intended purpose of providing an easy (low reluctance) return path for the flux, requiring very little magnetic force to do so, and propagating very little external field.

![Diagram of a C-core with a gap in one leg and a winding on the opposite leg, showing a large external stray magnetic field.](page_50_image_3_v2.jpg)

Fig. 5-4a Large External Field

![Diagram of a C-core with a winding placed directly over the gap, showing minimal external magnetic field.](page_50_image_2_v2.jpg)

Fig. 5-4b Minimal External Field

Texas Instruments
5-3
SLUP132

**Gap area correction:** Even when the winding is properly placed directly over a discrete gap, there will be a small but intense fringing field adjacent to the gap, extending outward beyond the boundaries of the core cross-section as shown in Fig 5-4b. Because of this fringing field, the effective gap area is larger than the core center-pole area. To avoid what could be a significant error, the inductance calculation must be based upon the effective gap area rather than the actual center-pole area. An empirical approximation is obtained by adding the *length* of the gap to the dimensions of the core center-pole cross-section.<sup>(1)</sup>

For a core with a rectangular center-pole with cross-section dimensions *a* and *b*, the effective gap area, $A_g$ is approximately:

$$A_{cp} = a \times b \text{ ; } A_g \approx (a + l_g) \times (b + l_g)$$ (1a)

For a round center-pole with diameter $D_{cp}$:

$$A_{cp} = \frac{\pi}{4} D_{cp}^2 \text{ ; } A_g \approx \frac{\pi}{4} (D_{cp} + l_g)^2$$

Resulting in a gap area correction factor:

$$\frac{A_g}{A_{cp}} \approx \left( 1 + \frac{l_g}{D_{cp}} \right)^2$$ (1b)

Thus, when $l_g$ equals $0.1D_{cp}$, the area correction factor is 1.21. The gap must be made larger by this same factor to achieve the desired inductance (see Eq. 3a).

The preceding correction factor is helpful when the correction is less than 20%. A more accurate correction requires finite element analysis evaluation, or trial-and-error evaluation.

After the number of turns and the gap length have been calculated according to steps 7 and 8 of the cookbook design procedure presented later in this section, verification is obtained by building a prototype inductor.

If the measured inductance value is too large, *do not* reduce the number of turns, or excessive core loss and/or saturation may result. Instead, increase the gap to reduce the inductance.

If the measured inductance is too small, the number of turns may be increased, but the core will then be under-utilized and winding losses may be excessive. It is best to raise the inductance by decreasing the gap length.

**Melted windings:** Another serious problem can result from the fringing field adjacent to the gap. Any winding turns positioned close to the gap will likely exist within the high flux density of the fringing field. In applications with large flux swings, huge eddy current losses can occur in those few turns close to the gap. Windings have been known to melt in this vicinity. This problem is most severe with flyback transformers and boost inductors designed for the discontinuous mode, because the flux swings at full load are very large. With filter inductors, or any inductors designed for continuous mode operation, flux swing is much less and the problem is much less severe.

Solutions for devices designed to operate with large flux swing: (1) Don't put winding turns in the immediate vicinity of the gap. Although the winding should be on the center-pole directly over the gap, a non-magnetic, non-conductive spacer could be used to substitute for the turns in the area where the fringing field is strong. (2) Distribute the gap by dividing it into two or three (or more) smaller gaps spaced uniformly along the center-pole leg under the winding. Since the fringing field extends out from the core by a distance proportional to the gap, several small gaps will dramatically reduce the extent of the fringing field. This also results in more accurate inductance calculation. (3) Eliminate the fringing field entirely by using a ferrite core with a powdered metal rod substituted for the ferrite center-leg. This distributes the gap uniformly among the metal particles, directly beneath the entire length of the winding, eliminating the fringing field. While this last method has been used successfully, it is usually not practical because of high cost, and greater ac core losses with metal powder cores.

**Gapping all legs:** It is tempting to avoid the cost of grinding the gap in the centerleg by merely spacing the two core halves apart, thus placing half the gap in the centerleg and the other half in the combined outer legs. But the outer leg gaps clearly violate the principle that the winding should be placed directly over the gap. A little more than half of the total magnetic force will exist across the centerleg gap, but the remaining force appears across the outer leg gap(s) and thus across the two core halves. This propagates considerable stray flux outside the inductor, radiating EMI, and the inductance value becomes larger and difficult to predict. The result is intermediate between Figures 5-4a and 5-4b.

Texas Instruments
5-4
SLUP132

There is one other benefit of spacing the core halves apart. Because the gap is divided, the smaller centerleg gap length reduces the fringing field and thus reduces the eddy current problem in the winding close to the gap.

A trick which greatly reduces the external stray flux in this situation is to place an external shorted turn around the entire outer periphery of the inductor. The shorted turn is made of wide copper strip placed co-axial with the inductor winding, encircling the entire outer surface of the inductor, outside the windings and outside the outer core legs, and closely conforming to the external shape. Any stray flux that escapes to the outside world will link to this external shorted turn, inducing in it a current which creates a magnetic field in opposition to the stray flux.

# Core Selection: Material

Select a core material appropriate for the desired frequency and inductor current mode.

Ferrite is usually the best choice for inductors designed to operate in the *discontinuous* mode at frequencies above 50kHz, when core loss associated with large flux swing limits core utilization.

However, in the continuous mode, with small ripple current and small flux swing, ferrite cores will often be limited by saturation. In this case, lossier core materials with greater saturation flux density, such as powdered iron, Kool-mu<sup>®</sup>, Permalloy powder, or even gapped laminated metal cores may enable reduced cost or size. But the rounded B-H characteristic of powdered metal cores can result in the perhaps unintended characteristic of a "swinging choke," whose inductance decreases at higher current levels.

# Core Selection: Shape

The core shape and window configuration is not critically important for inductors designed to operate in the continuous mode, because ac winding loss is usually very small.

But for inductors designed for discontinuous mode operation, and especially for flyback transformers, the window configuration is extremely important. The window should be as wide as possible to maximize winding breadth and minimize the number of layers. This minimizes ac winding resistance. For a flyback transformer, the wide window also minimizes leakage inductance, and the required creepage distance when line isolation is required has less impact. With a wider window, less winding height is required, and the window area utilization is usually better.

As discussed in Section 4, pot cores and PQ cores have small window area in relation to core size, and the window shape is not well suited for flyback transformers or discontinuous mode inductors.

EC, ETD, LP cores are all E-E core shapes, with large, wide windows which make them excellent choices with ferrite materials. These core shapes lend themselves to spiraled windings of wide copper strip, especially with inductors operated in the continuous mode, where ac winding losses are small.

Toroidal powdered metal cores, with windings distributed uniformly around the entire core, can be used in any inductor or flyback transformer application. Stray magnetic flux and EMI propagation is very low.

But a gapped ferrite toroidal core is a very bad choice. Windings distributed around the toroid will not conform to discrete gaps, resulting in large stray fields, radiated EMI, and inductance values that cannot be calculated.

# Optimum core utilization

The smallest size and lowest cost inductor is achieved by fully utilizing the core. In a specific application, optimum core utilization is associated with a specific optimum gap length (resulting in a specific effective permeability $\mu_e$ for cores with distributed gaps). The same core in a different application or at a different frequency may have a different optimum gap length.

The optimum gap length results in the core operating at maximum flux density (limited either by saturation or by core loss), and also at maximum current density in the windings (limited by winding loss). This is the best possible utilization of the core, resulting in the smallest size. The inductor design approach should therefore seek to achieve this optimum gap length (or optimum $\mu_e$ for a core with distributed gap).

Figure 5-5 shows the characteristic of a core with optimum gap, limited by core saturation and by max. current density in the windings. The area between the characteristic and the vertical axis indicates the energy storage capability. Any other slope (different gap size) results in less energy storage capability.

# Core Selection: Size

The discussion of core size for transformers in Section 4-8 is mostly relevant to inductors as well. The following Area Product formulae are intended to help provide a rough initial estimate of core size for inductor applications.

Texas Instruments
5-5
SLUP132

![Graph showing Bsat Limit and Current Density Limit for Stored Energy. The x-axis is labeled H, F, I and the y-axis has B, φ, and ∫Edt.](page_53_chart_1_v2.jpg)
Fig 5-5 Optimum Core Utilization

tor, $K_{PRI}$ is the ratio of the total copper area to the window area, $A_W$. For a flyback transformer, $K_{PRI}$ is the ratio of the primary winding copper cross-section area to the total window area.

The saturation-limited formula assumes winding losses are much more significant than core losses. $K_1$ is based on the windings operating at a current density of $420A/cm^2$, a commonly used "rule of thumb" for natural convection cooling.

In the core loss limited formula, core and winding losses are assumed to be approximately equal. Therefore, the winding losses are halved by reducing the current density to $297A/cm^2$ ($420 \times 0.707$). Thus, $K_2$ equals $0.707 \cdot K_1$.

In either formula, it is assumed that appropriate techniques are used to limit the increase in winding losses due to high frequency skin effect to less than 1/3 of the total winding losses.

Forced air cooling permits higher losses (but with reduced efficiency). $K$ values become larger, resulting in a smaller core area product.

The 4/3 power shown in both area product formulae accounts for the fact that as core size increases, the volume of the core and windings (where losses are generated) increases more than the surface area (where losses are dissipated). Thus, larger cores must be operated at lower power densities.

For the core loss limited case, $\Delta B_{MAX}$ may be approximated by assuming a core loss of $100\text{ mw/cm}^3$ — a typical maximum for natural convection cooling. For the core material used, enter the core loss curves at $100\text{ mw/cm}^3$ (Fig. 2-3). Go across to the appropriate switching (ripple) frequency curve, then down to the "Flux Density" scale (actually peak flux density). Double this number to obtain peak-peak flux density, $\Delta B_{MAX}$. If units are in Gauss, divide by 10,000 to convert $\Delta B_{MAX}$ to Tesla, then enter this value into the core loss limited Area Product formula.

In filter inductor applications, normally operated in the continuous inductor current mode, the ripple current is usually only 10-20% of the full load dc current. Ferrite cores will usually be limited by saturation flux density, not by core loss, at switching frequencies below 250 kHz. Boost and flyback inductors, and flyback transformers operated in the continuous current mode, where total ripple ampere-turns are a small fraction of full-load ampere-turns, may also be saturation limited. In these situations, it may be possible to reduce size, weight, and/or cost by using core materials that are lossier but have higher saturation flux density, such as Kool-Mu®, or metal alloy laminated cores.

When core loss is not severe, so that flux swing is limited by core saturation:

$$AP = A_W A_E = \left( \frac{L \cdot I_{SCpk}}{B_{MAX}} \cdot \frac{I_{FL}}{K_1} \right)^{4/3} \text{ cm}^4 \quad (2a)$$

When flux swing is limited by core loss:

$$AP = A_W A_E = \left( \frac{L \cdot \Delta I}{\Delta B_{max}} \cdot \frac{I_{FL}}{K_2} \right)^{4/3} \text{ cm}^4 \quad (2b)$$

where:

*   **L** = inductance, Henrys
*   **I<sub>SCpk</sub>** = max pk short-circuit current, A
*   **B<sub>MAX</sub>** = saturation limited flux density, T
*   **ΔI** = current swing, Amps (primary)
*   **ΔB<sub>max</sub>** = max flux density swing, Tesla
*   **I<sub>FL</sub>** = rms current, full load (primary)
*   **K<sub>1</sub>, K<sub>2</sub>** = $J_{MAX} \cdot K_{PRI} \times 10^{-4}$
*   **where:**
    *   **J<sub>MAX</sub>** = max. current density, A/cm²
    *   **K<sub>PRI</sub>** = primary copper area/window area
    *   **10<sup>-4</sup>** = converts dimensions from meters to cm


<table>
  <thead>
    <tr>
        <th>Application</th>
        <th>K<sub>PRI</sub></th>
        <th>K₁</th>
        <th>K₂</th>
    </tr>
  </thead>
  <tbody>
    <tr>
        <td>Inductor, single winding</td>
        <td>0.7</td>
        <td>.03</td>
        <td>.021</td>
    </tr>
    <tr>
        <td>Filter Inductor, multiple winding</td>
        <td>.65</td>
        <td>.027</td>
        <td>.019</td>
    </tr>
    <tr>
        <td>Flyback transformer — non-isolated</td>
        <td>0.3</td>
        <td>.013</td>
        <td>.009</td>
    </tr>
    <tr>
        <td>Flyback transformer — with isolation</td>
        <td>0.2</td>
        <td>.0085</td>
        <td>.006</td>
    </tr>
  </tbody>
</table>

For a single winding inductor, the term "primary" above refers to the entire winding.

$K_{PRI}$ represents the utilization of the window containing the winding. For a single winding induc-

Texas Instruments
5-6
SLUP132

However, when these applications are designed for discontinuous mode operation at full load, ripple ampere-turns are so large that the inductors will almost certainly be core loss limited.

If uncertain whether the application is core loss limited or saturation limited, evaluate both formulae and use the one which results in the largest area product.

These initial estimates of core size are not very accurate, but they do reduce the number of trial solutions that might otherwise be required. The detailed design process provides greater accuracy. In the final analysis, the validity of the design should be checked with a prototype operated in the circuit and in the environment of the application, with the hot spot temperature rise measured by means of a thermocouple cemented alongside the middle of the centerpost.

## Inductance calculation

Several methods are in common use for calculating inductance:

**Discrete gap length, $l_g$ :** The magnetic path length of any core with a discrete gap consists of very high permeability magnetic core material ($\mu_r = 3000 - 100,000$) in series with a small non-magnetic gap ($\mu_r = 1$). In practice, the reluctance of the magnetic material is so small compared to the gap reluctance, that it can usually be neglected. The corrected gap dimensions alone determine the inductance:

$$L = \mu_0 N^2 \frac{A_g}{l_g} \times 10^{-2} \text{ Henrys} \tag{3a}$$

(SI units, dimensions in cm)

$A_g$ = corrected gap area (page 5-4)

**Effective permeability, $\mu_e$ :** Whether the gap is discrete or distributed, it is a small total length of non-magnetic material in series with a much greater length of high permeability magnetic material. The actual core can be considered equivalent to a solid homogeneous core with the same overall core dimensions, made entirely of an imaginary material with permeability $\mu_e$, which typically ranges from 10 (for a large gap) to 300 (for a small gap). This concept is most useful for distributed gap powdered metal cores, where the total gap cannot be physically measured.

$$L = \mu_0 \mu_e N^2 \frac{A_e}{l_e} \times 10^{-2} \text{ Henrys} \tag{3b}$$

(SI units, dimensions in cm)

**Inductance Factor, $A_L$**, expressed in milliHenrys/1000 turns², or nanoHenrys/turn², is often stated by the manufacturer for pre-gapped ferrite cores or for distributed-gap powdered metal cores. It provides a convenient method for calculating inductance for an existing gapped core with a given number of turns, but it is awkward for determining the optimum gap length or the optimum effective permeability for best core utilization.

$$L = N^2 A_L \text{ nanoHenrys} \tag{3c}$$

In the inductor design process, the desired inductance is presumed to be a known circuit value. The optimum gap length, $l_g$, or effective permeability, $\mu_e$ to achieve that inductance is calculated by inverting the preceding formulae.

## Design Strategy

The general design procedure that will be followed is:

1. From the circuit design, define the circuit parameters including inductance value $L$, full load dc inductor current $I_{FL}$, worst case ripple $\Delta I_{pp}$, max peak instantaneous short-circuit current limit $I_{SCpk}$, absolute loss limit and max temperature rise. Worst case ripple is at max $V_{IN}$ for buck-derived, at min $V_{IN}$ for boost. Full load inductor current equals load current for buck only. Refer to Section 2.

2. Select the core material. Refer to Section 2.

3. Determine the maximum flux density and max. flux swing at which the core will be operated (limited either by saturation or by core loss). Define a conservative saturation limit, $B_{MAX}$ (perhaps 3000Gauss (0.3Tesla) for power ferrite). If the core is saturation limited, $B_{MAX}$ will be reached at $I_{SCpk}$. With a discrete gapped core, the gap has the most significant influence on the B-H characteristic, linearizing it until well into saturation. Therefore, if the core is saturation limited, maximum flux swing $\Delta B_{MAX}$ will be in the same proportion to $\Delta I_{pp}$ as $B_{MAX}$ is to $I_{SCpk}$:

$$\Delta B_{MAX} = B_{MAX} \frac{\Delta I_{pp}}{I_{SCpk}} \tag{4}$$

Texas Instruments
5-7
SLUP132

Divide the calculated $\Delta B_{MAX}$ value by two to convert peak-peak flux density to peak, and enter the core loss curve (Fig. 2-3) on the "flux density" axis (really *peak* flux density). At the ripple frequency curve, find the resulting core loss. If the core loss is much less than 100 mw/cm³, this confirms that the core is probably saturation limited, and the calculated $\Delta B_{MAX}$ value is probably valid. But if the indicated core loss is much greater than 100 mw/cm³, the core will probably be loss limited. $\Delta B_{MAX}$ must then be reduced to achieve an acceptable core loss (Step 5). If the core is loss limited, peak flux density at $I_{SCpk}$ will then be less than $B_{MAX}$.

The approach taken above equates flux density values with currents, based on the presumption of a linear core characteristic. This presumption is quite valid for a gapped ferrite or laminated metal core. On the other hand, powdered metal cores are quite non-linear over a substantial portion of their range. But in high frequency switching power supply applications, these cores will usually be limited by core loss to well below saturation flux density, where linearity is much better. Nevertheless, the determination of core loss and max. permissible flux swing are best accomplished by methods defined by the manufacturers of these cores. (Also, be aware that the permeability quoted by the manufacturer may not apply at the conditions of the application.)

4. **Tentatively select the core shape and size.** Inexperienced designers should use the area product formulae (Eq. 2a, 2b), or manufacturer's guidance. Record the important core dimensions.

5. **Determine loss limit.** First, define the thermal resistance from the data sheet or calculate $R_T$ according to page 4-2. Divide the temperature rise limit by the thermal resistance to calculate the temperature rise loss limit. Compare the temperature rise loss limit with the absolute loss limit, and use whichever is smaller.

If the core is limited by loss rather than by saturation, initially apportion half of the loss limit to the core and half to the windings. Then apply the core loss limit to the core loss curves to find the $\Delta B_{MAX}$ value that will produce that core loss.

6. **Calculate the number of turns, $N$,** that will provide the desired inductance value when operated at the max flux density swing as defined in Step 3 or Step 5.

$$E = N \frac{d\phi}{dt} = NA_e \frac{dB}{dt} \text{ Faraday's Law}$$
$$E = L \frac{\Delta I}{\Delta t}$$

Combining the above ($L$ in µH, $A_e$ in cm):

$$N = \frac{L \Delta I_{MAX}}{\Delta B_{MAX} A_e} \times 10^{-2} \text{ (5)}$$

$N$ must then be rounded to an integer value. If $N$ is rounded down to a smaller integer, the core may saturate, or, if the core is loss limited, core loss will be greater than planned. However, winding loss will be reduced. If $N$ is rounded up to a larger integer value, core loss will be reduced, but winding loss increased. When $N$ is a small number of turns, there is a very large increase in winding loss when rounding up vs. rounding down. It may be advantageous to round down to the smaller integral $N$ value if the reduced winding loss outweighs the increased core loss.

When an inductor has multiple windings, the lowest voltage winding with the fewest turns usually dominates the rounding decision. De-optimization caused by rounding sometimes forces the need for a larger core. It may be desirable to alter the turns ratio, or use a smaller inductance value (resulting in greater ripple current) to avoid increased losses or the need for a larger core.

Equation 5 can be applied to any winding provided $N$, $L$, and $\Delta I$ are all referred to that winding.

After the integer value of $N$ has been established, recalculate $\Delta B$, inverting Eq. 5, and determine the resulting core loss.

7. **Calculate the gap length** required to achieve the required inductance, using the $N$ value established in Step 6 (inverting the inductance formula: Eq. 3a, 3b).

For a discrete gap, the *effective* magnetic path length is the gap, $l_g$. The center-pole area, $A_e$ must be corrected for the fringing field (Eq. 1a or 1b) to obtain the effective gap area $A_g$.

$$l_g = \mu_0 N^2 \frac{A_g}{L} \times 10^4 \text{ (6a)}$$

Texas Instruments
5-8
SLUP132

$$l_g = \mu_0 N^2 \frac{A_e}{L} \left( 1 + \frac{l_g}{D_{CP}} \right)^2 \times 10^4 \quad (6b)$$

(SI units, $L$ in $\mu$H, dimensions in cm)

The solution is a bit messy: Assume a value for $l_g$ in the gap area correction factor term on the right and calculate a new $l_g$ value. Using this new $l_g$ value for the gap correction, recalculate. Iterate 2-3 times.

For a distributed gap in a powdered metal core, calculate the effective permeability of the composite material required to obtain the desired inductance (or calculate the inductance factor, $A_L$, discussed earlier):

$$\mu_e = \frac{L l_e}{\mu_0 N^2 A_e} \times 10^{-4} \quad (7)$$

($L$ in $\mu$H, dimensions in cm)

8. **Calculate the conductor size and winding resistance.** (Refer to the following cookbook sections for details.)

Winding resistance is calculated using the conductor cross-section area and length.

Resistivity of copper:

$$\rho_{cu} = 1.724 [1 + .0042(T - 20)] \times 10^{-6} \quad \Omega\text{-cm}$$

$$\rho_{cu} = 2.30 \times 10^{-6} \quad \Omega\text{-cm at } 100^\circ\text{C}$$

dc winding resistance:

$$R_x = \rho_{cu} \frac{l_x}{A_x} \quad \Omega \quad (8)$$

(Dimensions in cm)

9. **Calculate winding loss, total loss, and temperature rise.** If loss or temperature rise is too high or too low, iterate to a larger or smaller core size.

The cookbook design examples which follow will more fully illustrate this design process.

# Cookbook Example: Buck Output Filter Inductor

In Section 4, a forward converter transformer was designed for 5V, 50A output. This filter inductor will be designed as the output filter for this same power supply.

1. Define the power supply parameters pertaining to the inductor design. ($V_{in}$ for the inductor equals $V_{in}$ for the transformer divided by the 7.5:1 transformer turns ratio):

* **VIN Range**: 13.33 - 25.33 V
* **Output 1**: 5 V
* **Full Load Current, IFL**: 50 A
* **Circuit Topology**: Forward Converter
* **Switching Freq, fs**: 200 kHz
* **Max Duty Cycle**: .405 (at Min VIN)
* **Min Duty Cycle**: .213 (at Max VIN)
* **Max Ripple Current, $\Delta I_{pp}$**: 50A x 20% = 10 A
* **Max peak Current, Iscpk**: 65 A
* **Inductance, L**: 2.2 $\mu$H
* **Max Loss (absolute)**: 2.5 W
* **Max °C Rise**: 40°C
* **Cooling Method**: Natural Convection

2. **Select the core material, using guidance from the manufacturer's data sheet.**

* **Core Material**: Ferrite, Magnetics Type P

3. **Determine max. flux density and max. flux swing at which the core will be operated.** A saturation-limited $B_{MAX}$ of 0.3T (3000 Gauss) will be used. If the core is saturation limited, it will be at the $B_{MAX}$ limit when the peak current is at the short-circuit limit. The max. peak-peak flux density swing corresponding to the max. current ripple will then be:

$$\Delta B_{MAX} = B_{MAX} \frac{\Delta I_{pp}}{I_{SCpk}} = 0.3 \frac{10}{65} = .046 \text{ Tesla}$$

Dividing the peak-peak flux density swing by 2, the peak flux swing is .023T (230 Gauss). Entering the core loss curve for type P material (page 2-5) at 230 Gauss, and at the 200kHz ripple frequency, the core loss is approximately 4mw/cm$^3$. This is so much less than the 100 mw/cm$^3$ rule of thumb that core loss will be almost negligible, and core operation will be saturation limited at $I_{SCpk}$. The maximum flux density swing, $\Delta B_{MAX}$, is therefore .046T as previously calculated.

4. **Tentatively select core shape and size, using guidance from the manufacturer's data sheet or using the area product formula given previously.**

* **Core type, Family**: E-E core - ETD Series

Using the saturation limited Area Product formula, with $B_{MAX} = 0.3\text{T}$ and $K_1 = .03$, an Area Product of 0.74 cm$^4$ is required. An ETD34 core size will be used, with AP = 1.21 cm$^4$ (with bobbin).

Texas Instruments
5-9
SLUP132

**Core Size: 34mm -- ETD34**

For the specific core selected, note:

Effective core Area, Volume, Path Length, center-pole diameter (cm):
**A<sub>e</sub>**: 0.97 cm<sup>2</sup>
**V<sub>e</sub>**: 7.64 cm<sup>3</sup>
**l<sub>e</sub>**: 7.9 cm
**D<sub>CP</sub>**: 1.08 cm

Window Area, Breadth, Height, Mean Length per Turn (with bobbin):
**A<sub>w</sub>**: 1.23 cm<sup>2</sup>
**b<sub>w</sub>**: 2.10 cm
**h<sub>w</sub>**: 0.60 cm
**MLT**: 6.10 cm

5. Define R<sub>T</sub> and Loss Limit. Apportion losses to the core and winding. Thermal resistance from the data sheet is 19°C/Watt. Loss limit based on max. temperature rise:

$$ P_{lim} = °C_{rise}/R_T: = 40/19 = 2.1 \text{ Watts} $$

Compared to the absolute loss limit of 2.5W (Step 1), the temperature rise limit of 2.1W applies. Core loss is 4 mW/cm³ (Step 3):

$$ P_C = \text{mW/cm}^3 \times V_e = 4 \times 7.64 = 30\text{mW} $$

Therefore, winding loss can be as much as 2 Watts. However, since the core is larger than the Area Product calculation suggests, it should be possible to reduce the winding loss.

6. Calculate the number of turns that will provide the desired inductance value:

$$ N = \frac{L \Delta I_{MAX}}{\Delta B_{MAX} A_e} \times 10^{-2} \text{ (5)} $$

(L in µH, dimensions in cm)

$$ N = \frac{2.2 \cdot 10}{.046 \cdot 0.97} \times 10^{-2} = 4.93 \rightarrow 5 \text{ Turns} $$

7. Calculate the gap length that will achieve the required inductance value:

$$ l_g = \mu_0 N^2 \frac{A_e}{L} \left( 1 + \frac{l_g}{D_{CP}} \right)^2 \times 10^4 \text{ (6b)} $$

(L in μH, dimensions in cm)

$$ l_g = 4\pi \times 10^{-7} \cdot 5^2 \frac{0.97}{2.2} \left( 1 + \frac{l_g}{1.08} \right)^2 \times 10^4 $$
$$ l_g = 0.192 \text{ cm} $$

8. Calculate the conductor size, winding resistance, losses, and temperature rise.

From Step 4, window breadth, b<sub>w</sub> = 2.10cm, and height, h<sub>w</sub> = 0.60cm. The winding will consist of 5 turns (5 layers) of copper strip, 2.0cm wide, spiral wound, with .05mm (2 mil) low voltage insulation between layers.

At 50A full load current, 450 A/cm² requires a conductor area of 0.111cm², Dividing this conductor area by the 2.0cm width requires a thickness of .0555cm. Five layers, including .005cm insulation between layers, results in a total winding height of 0.3cm, half the available window height.

To reduce losses, increasing copper thickness to 0.1cm results in a total winding height of .525cm, and a conductor area of 0.2cm². Five turns with a mean length/turn = 6.1cm results in a total winding length of 30.5cm. Winding resistance:

$$ R_{dc} = \rho \frac{l}{A} = 2.3 \times 10^{-6} \cdot \frac{30.9}{0.2} = .000355 \Omega $$

**DC loss**: 50² · .000355 = 0.89 Watts

With reference to Section 3-4, the ac loss is calculated. Skin depth D<sub>PEN</sub> = .017cm at 200kHz. With a conductor thickness of 0.1cm, Q = 0.1/.017 = 5.9. Entering Dowell's curves, page 3-4, with Q=6 and 5 layers, R<sub>AC</sub>/R<sub>DC</sub> is approximately 100, so that R<sub>AC</sub> = .035Ω.

The rms value of the triangular ripple current waveform equals $\Delta I_{pp} / \sqrt{12}$ Since max $\Delta I_{pp}$ is 10A, $I_{rms} = 10 / \sqrt{12} = 2.9\text{A}$.

Therefore the ac loss is:

$$ P_{Lac} = I^2 R = 2.9^2 \cdot .035 = 0.29 \text{ Watts} $$

Total winding loss dc plus ac is:

$$ P_w = 0.89 + 0.29 = 1.18 \text{ Watts} $$

9. Since the core loss is only 30mW, the total loss, 1.21W, is considerably less than the 2.1W limit originally calculated. The windings operate with only 250 A/cm² at full load, accounting for the reduced loss. This is because the ETD34 core has an Area Product 65% greater than the calculated requirement. A smaller core could possibly have been used. However, the ETD34 core provides improved power supply efficiency.

Texas Instruments
5-10
SLUP132

# Coupled Filter Inductors

Buck-derived converters with multiple outputs often use a single filter inductor with multiple coupled windings, rather than individual inductors for each output. The design process for a coupled inductor, discussed in Ref. R5 is essentially the same as for a single-winding inductor.

The process is simplified by assuming that all windings are normalized and combined with the lowest voltage winding. Finally, divide the copper cross-section area into the actual multiple windings. Each winding will then occupy an area (A<sub>wN</sub>) proportional to its power output.

# Boost Inductor

In a simple boost application, the inductor design is essentially the same as for the buck converter discussed previously.

In switching power supplies, boost topologies are widely used in Power Factor Correction applications and in low voltage battery power sources. Otherwise, the boost configuration is rarely used.

In a PFC application, boost inductor design is complicated by the fact that the input voltage is not dc, but the continuously varying full-wave rectified line voltage waveform. Thus, as *V<sub>IN</sub>* changes with the line voltage waveform, the high frequency waveforms must also change. High frequency ripple current, flux swing, core loss and winding loss all change radically throughout the rectified line period.

The situation is further complicated by the fact that in different PFC applications, the boost topology may be designed to operate in one of a wide variety of modes:

* *Continuous mode, fixed frequency*
* *Continuous mode, variable frequency*
* *At the mode boundary, variable frequency*
* *Discontinuous mode, fixed frequency*
* *Discontinuous mode, variable frequency*
* *Continuous mode, transitioning to discontinuous during the low current portion of the line cycle, and at light loads.*

As in the buck-derived applications, the limiting factors for the boost inductor design are (a) losses, averaged over the rectified line period, and/or (b) core saturation at maximum peak current.

Worst case for core saturation is at maximum peak current, occurring at low line voltage at the peak of the rectified line voltage waveform. This is usually easy to calculate, regardless of the operating mode.

Note that the simple boost topology has no inherent current limiting capability, other than the series resistance of the line, rectifiers, and bulk filter capacitor. Thus, the boost inductor will *saturate momentarily* during start-up, while the bulk capacitor charges. The resulting inrush current is basically the same as with a simple capacitor-input filter, and is usually acceptable in low power applications. In high power applications, additional means of inrush current limiting is usually provided — a thermistor or an input buck current limiter. While saturation may be permissible during startup, the circuit must be designed so that the inductor does not saturate during worst-case normal operating conditions.

Calculating the losses averaged over the rectified line period is a difficult task. Averaged losses can be approximated by assuming *V<sub>IN</sub>* is constant, equal to the rms value of the actual rectified line voltage waveform.

Because input current is greatest at low input voltage, low frequency winding losses are greatest at low *V<sub>IN</sub>*.

For discontinuous mode operation, $\Delta I_{p-p}$ is greatest at low *V<sub>IN</sub>*. Therefore, core loss and ac winding loss are worst case at low line.

However, when the boost topology is operated in the continuous mode, max $\Delta I_{p-p}$ and worst case core loss and ac winding loss occur when *V<sub>IN</sub>* equals one-half of *V<sub>O</sub>*. But since $\Delta I_{p-p}$ is usually very much smaller than low frequency current, core loss and ac winding loss are usually negligible in continuous mode operation.

Because the boost inductor design follows the same pattern as the output filter inductor design previously covered, a cookbook example of boost inductor design is not given. It is left to the designer to determine the worst-case current values governing the design.

# Flyback Transformer Design

Figures 5-6 and 5-7 show the inductor current waveforms for continuous mode and discontinuous mode operation. All currents are normalized to their ampere-turn equivalent by multiplying primary and secondary currents by their respective winding turns. The ampere-turns driving the core are thus proportional to the normalized currents shown.

Texas Instruments
5-11
SLUP132

The design of the flyback transformer and calculation of losses requires definition of duty cycle, $D$, from which the transformer turns ratio, $n$, is calculated according to the relationship:

$$n = \frac{V_{IN}}{V_O'} \cdot \frac{D}{1 - D} \quad ; \quad D = \frac{nV_O'}{V_{IN} + nV_O'} \eqno(9)$$

where $V_O'$ equals output voltage plus rectifier, switch and IR drops referred to the secondary. The above relationship applies to discontinuous mode operation, and for discontinuous mode operation only at the mode boundary

Theoretically, a transformer-coupled flyback circuit can function with any turns ratio, regardless of $V_{IN}$ or $V_O$. However, it functions best, avoiding high peak currents and voltages, when $n$ is such that $D$ is approximately 0.5. (for discontinuous mode operation, at the mode boundary.) Circuit considerations and device ratings may dictate a turns ratio that results in a duty cycle other than 0.5. The turns ratio determines the trade-off between primary and secondary peak voltages and peak currents. For example, reducing $n$ reduces the duty cycle, reduces peak switch voltage and peak rectifier current, but increases peak switch current and peak rectifier voltage.

**Waveform Definitions:** Before flyback transformer design can be completed, the dc, ac and total rms current components of each waveform must be calculated. Current values must be calculated at each of the differing worst-case conditions relevant to core saturation, core loss and winding loss.

$D_P$ Duty Cycle, primary (switch) waveform
$D_S$ Duty Cycle, secondary (diode) waveform
$D_S = (1 - D_P)$ In the continuous mode and at the discontinuous mode boundary.
$I_{pk}$ Ripple current max peak
$I_{min}$ Ripple current min peak
$\Delta I_{pp}$ pk-pk Ripple current, $I_{pk} - I_{min}$
$I_{pa}$ average value of trapezoidal peak:
$$I_{pa} = (I_{pk} + I_{min}) / 2.$$

The following equations can be used to calculate the dc, rms, and ac values of trapezoidal waveforms (continuous mode operation - Fig. 5-6). They also apply to triangular waveforms (discontinuous mode - Fig. 5-8), by setting $I_{min}$ to zero:

$$I_{dc} = D \frac{(I_{pk} + I_{min})}{2} = D \cdot I_{pa} \eqno(10)$$

$$I_{rms} = \sqrt{D \left[ (I_{pk} \times I_{min}) + \frac{1}{3} (I_{pk} - I_{min})^2 \right]} \eqno(11)$$

For trapezoidal waveforms, Equation 11 can be simplified by ignoring the slope of the waveform top. If $\Delta I_{pp} = 0.5 \ I_{pa}$, the error is only 1%. If $\Delta I_{pp} = I_{pa}$, the error is 4%.

$$I_{rms} \approx \sqrt{D \cdot {I_{pa}}^2} \eqno(11a)$$

For triangular waveforms, Eq. 11 becomes:

$$I_{rms} = \sqrt{\frac{D}{3} {I_{pk}}^2} \eqno(11b)$$

For all waveforms:

$$I_{ac} = \sqrt{{I_{rms}}^2 - {I_{dc}}^2} \eqno(12)$$

Switching transition times are governed by transformer leakage inductance as well as by transistor and rectifier switching speeds. Thus it is important to minimize leakage inductance by using cores with long, narrow windows, and by interleaving the windings. Although switching transitions result in switch and rectifier losses, they have little effect on transformer loss.

## Continuous Mode Operation

With continuous mode operation, core loss is usually not significant because the ac ripple component of the total inductor ampere-turns is small compared with the full load dc component. But currents in the individual windings switch on and off, transferring ampere-turns back and forth from primary to secondary(s), as shown in Fig. 5-6. This results in very large ac current components in the windings that will likely result in significant high frequency winding losses.

The secondary current dc component is equal to output current, regardless of $V_{IN}$. At low $V_{IN}$ the primary dc and peak currents and the total inductor ampere-turns are greatest. Thus, the worst-case condition for core saturation and winding losses occurs at low $V_{IN}$.

On the other hand, the ac ripple component of the total inductor ampere-turns, and thus core loss, is greatest at high $V_{IN}$. But since core loss is usually negligible with continuous mode operation, this has little significance.

Texas Instruments
5-12
SLUP132

# Cookbook Example (Continuous Mode):

1. Define the power supply parameters pertaining to the flyback transformer design.

* **VIN**: 28 ± 4 V
* **Output 1**: 5 V
* **Full Load Current, IFL**: 10 A
* **Circuit Topology**: Flyback, Continuous Mode
* **Switching Freq, fs**: 100 kHz
* **Desired Duty Cycle**: 0.5 at 28V input
* **Max Ripple Current, $\Delta I_{pp}$**: 5 A @ 32V (secondary)
* **Peak Short-circuit Current**: 25A (secondary)
* **Secondary Inductance, L**: 6.8 μH (D=0.5, $\Delta I_{pp} = 5A$)
* **Max Loss (absolute)**: 2.0 W
* **Max Temperature Rise**: 40°C
* **Cooling Method**: Natural Convection

**Preliminary Calculations**: The turns ratio can be defined at nominal $V_{IN} = 28V$ and the desired duty cycle of 0.5:

$$n = \frac{V_{IN}}{V_O'} \frac{D}{1-D} = \frac{28}{5+0.6} \frac{0.5}{1-0.5} = 5$$

Before calculating winding losses, worst-case dc and ac current components, occurring at low $V_{IN}$, must be defined. First, the duty cycle, $D_P$ is defined at low $V_{IN}$:

$$D_{P24} = \frac{nV_O'}{V_{IN} + nV_O'} = \frac{5(5+0.6)}{24+5(5+0.6)} = 0.538$$
$$D_{S24} = 1 - D_{P24} = 0.462$$

Because the duty cycle and the turns ratio could possibly be changed to optimize the windings, current calculations are deferred until later.

2. Select the core material, using guidance from the manufacturer's data sheet.

**Core Material**: Ferrite, Magnetics Type P

3. Determine max. flux density and max. flux swing for core operation. A saturation-limited $B_{MAX}$ of 0.3T (3000 Gauss) will be used. If the core is saturation limited, $B$ will reach $B_{MAX}$ when peak current reaches the short-circuit limit. Assuming reasonable linearity of the gapped core B-H characteristic, $\Delta B_{MAX}$ with max. current ripple (at 32V) will be:

$$\Delta B_{MAX} = B_{MAX} \frac{\Delta I_{pp}}{I_{SCpk}} = 0.3 \frac{5}{25} = .06 \text{ Tesla (4)}$$

![Flyback Waveforms, Continuous showing primary and secondary current waveforms over time](page_60_layout_ocr_fzji_318_28_248_294.png)

Figure 5-6 Flyback Waveforms, Continuous

Dividing the peak-peak flux density swing by 2, the peak flux swing is .03T (300 Gauss). Entering the core loss curve for type P material (page 2-5) at 300 Gauss, and at 100kHz ripple frequency, the core loss is approximately 2.6 mw/cm³. This is so much less than the 100 mw/cm³ rule of thumb that core loss is negligible. Thus, $B_{MAX}$ is saturation limited at $I_{SCpk}$ of 25A, and $\Delta B_{MAX}$, is limited to only .06T, corresponding to $\Delta I_{p-p}$ of 5Amp.

4. Tentatively select the core shape and size, using guidance from the manufacturer's data sheet or using the area product formula.

**Core type, Family**: E-E core - ETD Series

Using the saturation limited Area Product formula, with $B_{MAX} = 0.3T$ and $K1 = .0085$, an Area Product of 1.08 cm⁴ is required. An ETD34 core size will be used, with AP = 1.21 cm⁴ (with bobbin).

**Core Size**: 34mm -- ETD34

For the specific core selected, note:

Effective core Area, Volume, Path Length, Center-pole diameter (cm):

* **Ae**: 0.97 cm²
* **Ve**: 7.64 cm³
* **le**: 7.9 cm
* **Dcp**: 1.08 cm

Texas Instruments
5-13
SLUP132

Window Area, Breadth, Height, Mean Length per Turn (with bobbin):
**A<sub>w</sub>**: 1.23 cm<sup>2</sup>
**b<sub>w</sub>**: 2.10 cm
**h<sub>w</sub>**: 0.60 cm
**MLT**: 6.10 cm

5. Define R<sub>T</sub> and Loss Limit. Apportion losses to the core and winding. Thermal resistance from the core data sheet is 19°C/Watt. Loss limit based on max. temperature rise:

$$P_{lim} = \text{°C}_{rise}/R_T = 40/19 = 2.1 \text{ Watts}$$

Since this exceeds the 2.0W absolute loss limit from Step 1, The 2.0W limit applies.

Core loss is:

$$P_C = \text{mW/cm}^3 \times V_e = 2.6 \times 7.64 = 20\text{mW}$$

Therefore, core loss is negligible. The entire 2.0 Watt loss limit can be allocated to the winding.

6. Calculate the number of secondary turns that will provide the desired inductance value:

$$N = \frac{L \Delta I_{MAX}}{\Delta B_{MAX} A_e} \times 10^{-2} \tag{5}$$

(L in µH, dimensions in cm)

$$N_s = \frac{6.8 \cdot 5}{.06 \cdot 0.97} \times 10^{-2} = 5.84 \rightarrow 6 \text{ Turns}$$

$$N_p = N_s \times n = 6 \times 5 = 30 \text{ Turns}$$

7. Calculate the gap length to achieve the inductance value with minimum N.

$$l_g = \mu_0 N^2 \frac{A_e}{L} \left( 1 + \frac{l_g}{D_{CP}} \right)^2 \times 10^4 \tag{6b}$$

(L in µH, dimensions in cm)

$$l_g = 4\pi \times 10^{-7} \cdot 5^2 \frac{0.97}{6.8} \left( 1 + \frac{l_g}{1.08} \right)^2 \times 10^4$$
$$l_g = .080 \text{ cm}$$

8. Calculate the conductor sizes and winding resistances:

From Step 4, window breadth, b<sub>w</sub> = 2.10cm, and height, h<sub>w</sub> = 0.60cm. A creepage allowance of 0.3 cm is necessary at each end of the windings. Winding width is 2.10cm minus (2x0.3) = 1.5cm.

**Secondary Side** - $V_{IN} = 24\text{V}, D_S = 0.462$
(Eq. 10, 11a, 12)

**Output dc Current, $I_{sdc}$**: 10 A
**Avg peak Current, $I_{spa}$**: $\frac{I_{DC}}{D_S} = \frac{10}{.462} = 21.65\text{A}$
**rms Current, $I_{srms}$**: $\sqrt{D_S \cdot {I_{pa}}^2} = 14.7\text{A}$
**ac Current, $I_{sac}$**: $\sqrt{{I_{rms}}^2 - {I_{dc}}^2} = 10.77\text{A}$

The secondary consists of 6 turns (6 layers) of copper strip, 1.5cm wide and .015 cm thick, spiral wound. Conductor area is .015x1.5 = .0225 cm<sup>2</sup>. Current density is 14.7A/.0225 = 650 a/cm<sup>2</sup>.

Six layers, including .005cm (2 mil) low voltage insulation between layers, results in a total winding height of 0.12cm.

Six turns with mean length/turn = 6.1cm results in a total winding length of 36.6cm. Winding resistance:

$$R_{dc} = \rho \frac{l}{A} = 2.3 \times 10^{-6} \cdot \frac{36.6}{.0225} = .0037\Omega$$

Calculating ac resistance: D<sub>PEN</sub> at 100kHz = .024cm. With a conductor thickness of .015cm, Q = .015/.024 = 0.625. Entering Dowell's curves, page 3-4, with Q = 0.625 and 6 layers, R<sub>AC</sub>/R<sub>DC</sub> is approximately 1.6.

$$R_{ac} = R_{dc} \times 1.6 = .0037\Omega \times 1.6 = .0059\Omega$$

**Primary Side** - $V_{IN} = 24\text{V}, D_P = 0.538$
(Eq. 10, 11a, 12)

Note that the primary and secondary average peak ampere-turns are always equal, and together constitute the dc ampere-turns driving the inductor core. Thus the primary avg. peak current, $I_{ppa} = I_{spa}/n$.

**avg. peak Current, $I_{Ppa}$**: $I_{Spa}/n = 21.65/5 = 4.33 \text{ A}$
**dc Current, $I_{Pdc}$**: $D \cdot I_{Ppa} = 0.538 \times 4.33 = 2.33\text{A}$
**rms Current, $I_{Prms}$**: $\sqrt{D_P \cdot {I_{Ppa}}^2} = 3.18\text{A}$
**ac Current, $I_{Pac}$**: $\sqrt{{I_{rms}}^2 - {I_{dc}}^2} = 2.16\text{A}$
**peak SC Current, $I_{SCpk}$**: 25/n = 5 A

Texas Instruments
5-14
SLUP132

The primary winding consists of 30 turns of Litz wire with OD of 0.127cm, in three layers, 10 turns in each layer. Litz wire OD enables 10 turns to fit across the 1.5cm winding breadth. The height of the 3-layer primary is $3 \times 0.127 = 0.381\text{cm}$.

The Litz wire consists of 150 strands of #40AWG wire (**OD=.0081cm**). From the wire tables, #40AWG wire has a resistance of .046 $\Omega/\text{cm}$ divided by 150 strands, resulting in a resistance of **.00031 $\Omega/\text{cm}$ at 100°C**.

The wire length equals 30 turns times MLT of $6.1\text{cm} = 183\text{cm}$.

Primary winding resistance:

$$R_{dc} = .00031\ \Omega / \text{cm} \times 183\text{cm} = .0567\ \Omega$$

To calculate the ac resistance, the 150 strand #40AWG Litz wire is approximately equivalent to a square array 12 wide by 12 deep (square root of 150 wires). There are therefore a total of **36 layers** of #40AWG wire (3 layers times 12).

Center-to-center spacing of the #40AWG wires equals the winding width of 1.5cm divided by 120 (10 Litz wires times 12 wide #40AWG wires within the Litz), a spacing, $s$, of **.0125cm**.

From Reference R2, pg 9, the effective layer thickness equals:

$$0.83d(d/s)^{1/2} = 0.83 \cdot .0081 \sqrt{.0081 / .0125}$$

$$= .0054\text{cm}$$

Therefore, referring to Figure 3-5,

$$Q = .0054\text{cm} / D_{PEN} = .0054 / .024 = .225$$

and with 36 layers, $R_{AC}/R_{DC} = 1.6$, and

$$R_{ac} = R_{dc} \times 1.6 = .0567 \times 1.6 = .090\Omega$$

9. Calculate winding loss, total loss, and temperature rise:

Secondary dc loss:

$$P_{Sdc} = {I_{dc}}^2 R_{dc} = 10^2 \cdot .0037 = 0.37\ \text{Watts}$$

Secondary ac loss:

$$P_{Sac} = {I_{Sac}}^2 \cdot R_{ac} = 10.77^2 \cdot .0059 = 0.68\ \text{W}$$

Total secondary winding loss -- dc plus ac is:

$$P_{sw} = 0.37 + 0.68 = 1.05\ \text{Watts}$$

The available winding height could permit a thicker secondary conductor. This would reduce dc loss, but the resulting increase in ac loss because of the larger Q value would exceed the dc loss reduction.

Primary dc loss ($R_{dc} = .0567\Omega$):

$$P_{Pdc} = {I_{Pdc}}^2 R_{dc} = 2^2 \cdot .0567 = 0.225\ \text{Watts}$$

Primary ac loss ($R_{ac} = .090\Omega$):

$$P_{Pac} = {I_{Pac}}^2 R_{ac} = 2.16^2 \times .090 = 0.42\ \text{W}$$

Total primary winding loss -- dc plus ac is:

$$P_{Pw} = 0.225 + 0.42 = 0.645\ \text{Watts}$$

Total winding loss:

$$P_w = 1.05 + 0.645 = 1.695\ \text{Watts}$$

Since the core loss is only 20mW, the total loss, 1.71W, is within than the 2.0W absolute loss limit.

The total winding height, including .02cm isolation: $0.12 + 0.381 + .02 = 0.521\text{cm}$, within the available winding height of 0.60cm.

Mutual inductance of 6.8µH seen on the secondary winding translates into 170µH referred to the primary ($L_P = n^2 L_S$).

Leakage inductance between primary and secondary calculated according to the procedure presented in Reference R3 is approximately 5µH, referred to the primary side. Interwinding capacitance is approximately 50pF.

If the windings were configured as an interleaved structure (similar to Figure 4-1), leakage inductance will be more than halved, but interwinding capacitance will double. The interleaved structure divides the winding into two sections, with only half as many layers in each section. This will reduce $R_{ac}/R_{dc}$ to nearly 1.0 in both primary and secondary, reducing ac losses by 0.35W, and reducing the total power loss from 1.71W to 1.36W. The secondary copper thickness could be increased, further reducing the losses.

### Discontinuous Mode Operation

Discontinuous mode waveforms are illustrated in Figure 5-7. By definition, the total ampere-turns dwell at zero during a portion of each switching period. Thus, in the discontinuous mode there are three distinct time periods, $t_T$, $t_R$, and $t_0$, during each switching period. As the load is increased, peak currents, $t_T$, and $t_R$ increase, but $t_0$ decreases. When $t_0$

Texas Instruments
5-15
SLUP132

becomes zero, the mode boundary is reached. Further increase in load results in crossing into continuous mode operation. This is undesirable because the control loop characteristic suddenly changes, causing the control loop to become unstable.

In the discontinuous mode, all of the energy stored in the inductor ($1/2 L I_{pk}^2$) is delivered to the output during each cycle. This energy times switching frequency equals output power. Therefore, if frequency, $L$, and $V_O$ are held constant, $1/2 L I_{pk}^2$ does not vary with $V_{IN}$, but is proportional to load current only, and $I_{pk}$ is proportional to the square root of load current. However, $V_{IN}$, $n$, $D$ and $L$ collectively do determine the maximum stored energy and therefore the maximum power output at the mode boundary.

The circuit should be designed so that the peak short-circuit current limit is reached just before the mode boundary is reached, with turns ratio, duty cycle and inductance value designed to provide the necessary full load power output at a peak current less than the current limit.

The circuit design can never be completely separated from the design of the magnetic components. This is especially true at high frequencies where the small number of secondary turns can require difficult choices. The ideal design for a discontinuous mode flyback transformer might call for a secondary with $1 \frac{1}{2}$ turns. The choice of a 1 turn or 2 turn secondary may result in a size and cost increase, unless the turns ratio and duty cycle are changed, for example.

![Discontinuous Waveforms showing primary and secondary current ramps for mode boundary at low Vin and full load at high Vin](page_63_layout_ocr_xnuz_43_430_256_285.png)

Figure 5-7 Discontinuous Waveforms

# Cookbook Example (Discontinuous Mode):

1. Define the power supply parameters pertaining to the flyback transformer design.

* **$V_{IN}$**: 28 ± 4 V
* **Output 1**: 5 V
* **Full Load Current, $I_{FL}$**: 10 A
* **Short Circuit Current**: 12 A
* **Circuit Topology**: Flyback, Discontinuous
* **Switching Freq, $f_s$**: 100 kHz
* **Desired Duty Cycle**: 0.5 at 24V, mode boundary
* **Estimated $I_{SCpk}$**: 45 A (secondary)
* **Est. Sec. Inductance**: 0.62μH (D=0.5, $\Delta I_{p-p}$=45A)
* **Max Loss (absolute)**: 2.0 W
* **Max Temperature Rise**: 40°C
* **Cooling Method**: Natural Convection

**Preliminary Calculations**: The turns ratio is defined based on min $V_{IN}$ (24V) and $V_O'$ (5.6V) and the desired duty cycle of 0.5 at the mode boundary:

$$n = \frac{V_{IN}}{V_O'} \frac{D}{1-D} = \frac{24}{5+0.6} \frac{0.5}{1-0.5} = 4.28 \rightarrow 4$$

Turns ratio, $n$, is rounded down to 4:1 rather than up to 5:1 because: (a) 4:1 is closer, (b) peak output current is less, reducing the burden on the output filter capacitor, and (c) primary switch peak voltage is less. The duty cycle at the mode boundary is no longer 0.5, and must be recalculated:

$$D_{P24} = \frac{V_O' \cdot n}{V_{IN} + V_O' \cdot n} = \frac{5.6 \times 4}{24 + 5.6 \times 4} = 0.483$$

$$D_{S24} = 1 - D_{P24} = 0.517$$

The peak secondary current at the mode boundary is:

$$I_{SCdc} = I_{SCpk} \frac{D_{S24}}{2}$$

$$I_{SCpk} = I_{SCdc} \frac{2}{D_{S24}} = 12 \frac{2}{0.517} = 46.4 \text{ A}$$

The peak short-circuit current limit on the primary side should therefore be set slightly below 11.6A (=46.4/n).

The inductance value required for the secondary current to ramp from 46.4A to zero at the mode boundary is:

Texas Instruments
5-16
SLUP132

$$ L = V_O' \frac{\Delta t}{\Delta i} = V_O' \frac{T \cdot D_{S24}}{\Delta i} $$
$$ L = 5.6 \frac{10 \cdot 0.517}{46.4} = 0.624 \text{ \mu H} $$

Before calculating winding losses, it is necessary to define worst-case dc and ac current components, occurring at low $V_{IN}$. Because the turns ratio and the duty cycle could possibly be changed to optimize the windings, current calculations will be deferred until later.

**2: Select the core material, using guidance from the manufacturer's data sheet.**

Core Material: Ferrite, Magnetics Type P

**3. Determine max. flux density and max. flux swing at which the core will be operated.** A saturation-limited $B_{MAX}$ of 0.3T (3000 Gauss) will be used. In the discontinuous mode, the current is zero during a portion of each switching period, by definition. Therefore $\Delta I$ always equals $I_{peak}$ and since they are proportional, $\Delta B$ must equal $B_{peak}$. $\Delta B_{MAX}$ and $B_{MAX}$ occur at low $V_{IN}$ when the current is peak short-circuit limited. To determine if $\Delta B_{MAX}$ is core loss limited, enter the core loss curve for type P material at the nominal $100 \text{mw/cm}^3$ loss limit, and at 100kHz ripple frequency, the corresponding max. peak flux density is 1100 Gauss. Multiply by 2 to obtain peak-peak flux density swing $\Delta B_{MAX}$ of 2200 Gauss, or 0.22 Tesla. Since in the discontinuous mode, $B_{MAX}$ equals $\Delta B_{MAX}$, then $B_{MAX}$ is also limited to 0.22T, well short of saturation. Thus, in this application the core is loss-limited at $\Delta B_{MAX} = 0.22\text{T}$, corresponding to $\Delta I_{p-p} = I_{SCpk} = 46\text{A}$.

**4. Tentatively select the core shape and size, using guidance from the manufacturer's data sheet or using the area product formula.**

Core type, Family: E-E core - ETD Series

Using the loss limited Area Product formula, with $\Delta B_{MAX} = 0.22\text{T}$ and $K2 = .006$, an Area Product of $0.31 \text{ cm}^4$ is required. An ETD24 core size will be used, with $\text{AP} = 0.37 \text{ cm}^4$ (with bobbin).

Core Size: 24mm - ETD24

For the specific core selected, note:

Effective core Area, Volume, Path Length, Center-pole diameter (cm):

**$A_e$**: 0.56 cm²
**$V_e$**: 3.48 cm³
**$l_e$**: 6.19 cm
**$D_{cp}$**: 0.85 cm

Window Area, Breadth, Height, Mean Length per Turn (' indicates reduced dimensions with bobbin):

**$A_w / A_w'$**: 1.02 / 0.45 cm²
**$b_w / b_w'$**: 2.07 / 1.72 cm
**$h_w / h_w'$**: 0.50 / 0.38 cm
**MLT**: 4.63 cm

**5. Define $R_T$ and Loss Limit, and apportion losses to the core and winding.** Thermal resistance from the core data sheet is 28°C/Watt. Loss limit based on max. temperature rise:

$$ \text{Plim} = \text{°C}_{rise} / R_T = 40 / 28 = 1.42 \text{ Watts} $$

Since this is less than the 2.0W absolute loss limit from Step 1, The 1.42W limit applies.

Preliminary core loss calculation:

$$ P_C = \text{mW/cm}^3 \times V_e = 100 \times 3.48 = 350 \text{ mW} $$

**6. Calculate the number of secondary turns that will provide the desired inductance value:**

$$ N = \frac{L \Delta I_{MAX}}{\Delta B_{MAX} A_e} \times 10^{-2} \tag{5} $$

(L in µH, dimensions in cm)

$$ N_S = \frac{0.63 \cdot 46}{.22 \cdot 0.56} \times 10^{-2} = 2.35 \rightarrow 2 \text{ Turns} $$
$$ N_P = N_S \times n = 4 \times 2 = 8 \text{ Turns} $$

Because $N_S$ was rounded down from 2.35 to 2 turns, flux density swing is proportionately greater than originally assumed:

$$ \Delta B_{MAX} = 0.22 \frac{2.35}{2} = 0.258 \text{ Tesla} $$

Divide by 2 to obtain peak flux density swing and enter the core loss curve at 0.13T (1300 Gauss) to obtain a corrected core loss of $160\text{mW/cm}^3$. Multiply by $V_e = 3.48 \text{ cm}^3$ for a corrected core loss of 560 mW.

If $N_S$ had been rounded up to 3 turns, instead of down to 2 turns, core loss would be considerably less, but winding loss would increase by an even greater amount, and the windings might not fit into the available window area.

**7. Calculate the gap length to achieve the inductance value:**

Texas Instruments
5-17
SLUP132

$$ \ell_g = \mu_0 N^2 \frac{A_e}{L} \left( 1 + \frac{\ell_g}{D_{CP}} \right)^2 \times 10^4 \quad (6b) $$

(L in $\mu$H, dimensions in cm)

$$ \ell_g = 4\pi \times 10^{-7} \cdot 2^2 \frac{0.56}{0.62} \left( 1 + \frac{\ell_g}{0.95} \right)^2 \times 10^4 $$

$$ \ell_g = .050 \text{ cm} $$

8. Calculate the conductor sizes and winding resistances:

From Step 4, window breadth, $b_w = 1.72 \text{ cm}$, and height, $h_w = 0.38 \text{ cm}$. A creepage allowance of $0.3 \text{ cm}$ is necessary at each end of the windings. Winding width is $1.72 \text{ cm}$ minus $(2 \times 0.3) = 1.12 \text{ cm}$.

**Secondary side**: $V_{IN} = 24\text{V}$, $D_s = 0.517$ (Eq. 11b, 12)

Output dc Current, $I_{sdc}$ : **12 A** (Short Circuit)

Peak S.C. Current, $I_{spk}$ : **46.4 A**

rms Current, $I_{srms}$ : $\sqrt{\frac{D_s}{3} \cdot {I_{pk}}^2}$
$= \sqrt{\frac{0.517}{3} \cdot 46.4^2} = 19.2 \text{ A}$

ac Current, $I_{sac}$ : $\sqrt{{I_{rms}}^2 - {I_{dc}}^2} = 15 \text{ A}$

Secondary conductor area for $450 \text{ A/cm}^2$ requires $19.2\text{A}/450 = .043 \text{ cm}^2$ (AWG 11). This is implemented with copper strip $1.12\text{cm}$ wide and $.038 \text{ cm}$ thickness, 2 turns, spiral wound.

![Diagram of interleaved flyback windings showing bobbin, layers, and mylar insulation](page_65_layout_ocr_uypa_58_510_237_177.png)

Figure 5-8 — Interleaved Flyback Windings

Two turns -- two layers, including $.005\text{cm}$ (2 mil) low voltage insulation between layers, results in a total winding height of $.081\text{cm}$.

Two turns with mean length/turn = $4.6 \text{ cm}$ results in a total winding length of $9.2 \text{ cm}$.

Secondary dc resistance:

$$ R_{dc} = \rho \frac{l}{A} = 2.3 \times 10^{-6} \cdot \frac{9.2}{.043} = .00049 \Omega $$

Calculating ac resistance: $D_{pen}$ at $100\text{kHz} = .024\text{cm}$. With a conductor thickness of $.033\text{cm}$, $Q = .038/.024 = 1.6$. Entering Dowell's curves, page 3-4, with $Q = 1.6$ and 2 layers, $R_{ac}/R_{dc}$ is approximately 2.5.

Secondary ac resistance (non-interleaved):

$$ R_{ac} = R_{dc} \times 2.0 = .00049 \Omega \times 2.5 = .00122 \Omega $$

If the windings are interleaved, forming two winding sections as shown in Fig. 5-8, there is one secondary turn in each section. Entering Dowell's curves with $Q = 1.6$ and one layer, $R_{ac}/R_{dc}$ is 1.5.

Secondary ac resistance (interleaved):

$$ R_{ac} = R_{dc} \times 1.5 = .00049 \Omega \times 1.5 = .0007 \Omega $$

**Primary side**: $V_{IN} = 24\text{V}$, $D_p = 0.483$ (Eq. 11b, 12)

Note that primary and secondary peak ampere-turns are always equal. Thus the primary peak current, $I_{Ppk} = I_{spk}/n$.

peak S.C. Current, $I_{Ppk}$ : $\frac{I_{spk}}{n} = \frac{46.4}{4} = 11.6 \text{ A}$

dc Current, $I_{Pdc}$ : $I_{Ppk} \frac{D_p}{2} = 11.6 \cdot \frac{0.483}{2} = 2.8 \text{ A}$

rms Current, $I_{Prms}$ : $\sqrt{\frac{D_p}{3} \cdot {I_{Ppk}}^2}$
$= \sqrt{\frac{0.483}{3} \cdot 11.6^2} = 4.65 \text{ A}$

ac Current, $I_{Pac}$ : $\sqrt{{I_{rms}}^2 - {I_{dc}}^2} = 3.71 \text{ A}$

Primary conductor area for $450 \text{ A/cm}^2$ requires $4.65\text{A}/450 = .010 \text{ cm}^2$ (AWG 17). This is implemented with copper strip $1.12 \text{ cm}$ wide and $.009 \text{ cm}$ thickness, 8 turns, spiral wound.

Texas Instruments
5-18
SLUP132

Eight layers, including .005cm (2 mil) low voltage insulation between layers results in a total winding height of 8x.014 = 0.112cm.

Eight turns with mean length/turn = 4.6 cm results in a total winding length of 36.8 cm.

Primary dc resistance:

$$R_{dc} = \rho \frac{l}{A} = 2.3 \times 10^{-6} \cdot \frac{36.8}{.01} = .0085 \Omega$$

Calculating ac resistance: $D_{PEN}$ at 100kHz = .024cm. With a conductor thickness of .009cm, Q =.009/.024 = .375. Entering Dowell's curves page 3-4, with Q = .375 and 8 layers, $R_{AC}/R_{DC}$ is approximately 1.2.

Primary ac resistance (non-interleaved):

$$R_{ac} = R_{dc} \times 1.2 = .0085 \Omega \times 1.2 = .01 \Omega$$

With the interleaved structure, there are only 4 layers in each winding section. Entering Dowell's curves, page 3-4, with Q = .375 and 4 layers, $R_{AC}/R_{DC}$ is 1.0.

Primary ac resistance (interleaved):

$$R_{ac} = R_{dc} = .0085 \Omega$$

10. Calculate winding loss, total loss, and temperature rise, using the interleaved structure:

Secondary dc loss ($R_{dc} = .00049 \Omega$):

$$P_{Sdc} = 12^2 \cdot .00049 = 0.07 \text{ Watts}$$

Secondary ac loss ($R_{ac} = .0007 \Omega$):

$$P_{Sac} = {I_{Sac}}^2 \cdot R_{ac} = 15^2 \cdot .0007 = 0.16 \text{ W}$$

Total secondary winding loss -- dc plus ac is:

$$P_{Sw} = 0.07 + 0.16 = 0.23 \text{ Watts}$$

Primary dc loss ($R_{dc} = .0085 \Omega$):

$$P_{Pdc} = {I_{Pdc}}^2 R_{dc} = 2.8^2 \times .0085 = .067 \text{ Watts}$$

Primary ac loss ($R_{ac} = .0085 \Omega$):

$$P_{Pac} = {I_{Pac}}^2 R_{ac} = 3.71^2 \times .0085 = 0.12 \text{ Watts}$$

Total primary winding loss -- dc plus ac is:

$$P_{Pw} = .07 + 0.12 = 0.19 \text{ Watts}$$

Total winding loss:

$$P_w = 0.23 + 0.19 = 0.42 \text{ Watts}$$

Total loss, including core loss of 0.56 W:

$$P_T = P_w + P_c = 0.42 + 0.56 = 0.98 \text{ W}$$

The total loss is well within the 1.42 Watt limit. The temperature rise will be:

$$^\circ C_{rise} = R_T \times P_T = 28 \times 0.98 = 27 ^\circ C$$

Total winding height, including two layers of .02cm isolation: 0.04 + 0.081 + .112 = 0.233 cm, well within the 0.38 cm available.

Leakage inductance between primary and secondary calculated according to the procedure presented in Reference R3 is approximately .08µH, referred to the primary. Interwinding capacitance is approximately 50pF.

If the windings were not interleaved (as shown in Figure 5-8), leakage inductance would be more than doubled, but interwinding capacitance would be halved. Interleaving also helps to reduce ac winding losses. This becomes much more significant at higher power levels with larger conductor sizes.

It is very important to minimize leakage inductance in flyback circuits. Leakage inductance not only slows down switching transitions and dumps its energy into a clamp, but it can steal a very significant amount of energy from the mutual inductance and prevent it from being delivered to the output.

## References

"R-numbered" references are reprinted in the Reference Section at the back of this Manual.

(R3) "Deriving the Equivalent Electrical Circuit from the Magnetic Device Physical Properties," *Unitrode Seminar Manual SEM1000*, 1995 and *SEM1100*, 1996

(R5) "Coupled Filter Inductors in Multiple Output Buck Regulators Provide Dramatic Performance Improvement," *Unitrode Seminar Manual SEM1100*, 1996

(1) MIT Staff, "Magnetic Circuits and Transformers," MIT Press, 1943

Texas Instruments
5-19
SLUP132

Texas Instruments 5-20 SLUP132

Oct 94

# Magnetic Core Properties

### Lloyd Dixon

## Summary:

A brief tutorial on magnetic fundamentals leads into a discussion of magnetic core properties. A modified version of Intusoft's magnetic core model is presented. Low-frequency hysteresis is added to the model, making it suitable for magnetic amplifier applications.

## Magnetic Fundamentals:

Units commonly used in magnetics design are given in Table I, along with conversion factors from the older CGS system to the SI system (systeme international - rationalized MKS). SI units are used almost universally throughout the world. Equations used for magnetics design in the SI system are much simpler and therefore more intuitive than their CGS equivalents. Unfortunately, much of the published magnetics data is in the CGS system, especially in the United States, requiring conversion to use the SI equations.

#### Table I - CONVERSION FACTORS, CGS to SI


<table>
  <thead>
    <tr>
        <th> </th>
        <th> </th>
        <th>SI</th>
        <th>CGS</th>
        <th>CGS to SI</th>
    </tr>
  </thead>
  <tbody>
    <tr>
        <td>FLUX DENSITY</td>
        <td>B</td>
        <td>Tesla</td>
        <td>Gauss</td>
        <td>10⁻⁴</td>
    </tr>
    <tr>
        <td>FIELD INTENSITY</td>
        <td>H</td>
        <td>A-T/m</td>
        <td>Oersted</td>
        <td>1000/4π</td>
    </tr>
    <tr>
        <td>PERMEABILITY (space)</td>
        <td>μ₀</td>
        <td>4π·10⁻⁷</td>
        <td>1</td>
        <td>4π·10⁻⁷</td>
    </tr>
    <tr>
        <td>PERMEABILITY (relative)</td>
        <td>μᵣ</td>
        <td> </td>
        <td> </td>
        <td>1</td>
    </tr>
    <tr>
        <td>AREA (Core, Window)</td>
        <td>A</td>
        <td>m²</td>
        <td>cm²</td>
        <td>10⁻⁴</td>
    </tr>
    <tr>
        <td>LENGTH (Core, Gap)</td>
        <td>ℓ</td>
        <td>m</td>
        <td>cm</td>
        <td>10⁻²</td>
    </tr>
    <tr>
        <td>TOTAL FLUX = ∫BdA</td>
        <td>ϕ</td>
        <td>Weber</td>
        <td>Maxwell</td>
        <td>10⁻⁸</td>
    </tr>
    <tr>
        <td>TOTAL FIELD = ∫Hdℓ</td>
        <td>F,MMF</td>
        <td>A-T</td>
        <td>Gilbert</td>
        <td>10/4π</td>
    </tr>
    <tr>
        <td>RELUCTANCE = F/ϕ</td>
        <td>R</td>
        <td> </td>
        <td> </td>
        <td>10⁹/4π</td>
    </tr>
    <tr>
        <td>PERMEANCE = 1/R = L/N²</td>
        <td>P</td>
        <td> </td>
        <td> </td>
        <td>4π·10⁻⁹</td>
    </tr>
    <tr>
        <td>INDUCTANCE = P·N²</td>
        <td>L</td>
        <td>Henry</td>
        <td>(Henry)</td>
        <td>1</td>
    </tr>
    <tr>
        <td>ENERGY</td>
        <td>W</td>
        <td>Joule</td>
        <td>Erg</td>
        <td>10⁻⁷</td>
    </tr>
  </tbody>
</table>

Figure 1 is the B-H characteristic of a magnetic core material — flux density (Tesla) vs. magnetic field intensity (A-T/m). The slope of a line on this set of axes is permeability ($\mu = B/H$). Area on the


<table>
  <tbody>
    <tr>
        <td>H</td>
        <td>B (FERRITE)</td>
    </tr>
    <tr>
        <td>[illegible]</td>
        <td>[illegible]</td>
    </tr>
  </tbody>
</table>

Fig 1. - Magnetic Core B-H Characteristic

surface of Fig. 1 represents energy per unit volume. The area enclosed by the hysteresis loop is unrecoverable energy (loss). The area between the hysteresis loop and the vertical axis is recoverable stored energy:

$$W/m^3 = \int HdB$$

In Figure 2, the shape is the same as Fig. 1, but the axis labels and values have been changed. Figure 2 shows the characteristic of a specific core made from the material of Figure 1. The flux density axis

![Diagram of a hysteresis loop for a ferrite core showing Flux (phi) vs. MMF.](page_68_image_1_v2.jpg)

Fig 2. - Core Flux vs. Magnetic Force

Texas Instruments R1-1 SLUP132

is transformed into the total flux, $\phi$, through the entire cross-sectional area of the core, while field intensity is transformed into total magnetic force around the entire magnetic path length of the core:

$$\phi = B \cdot A_e \quad ; \quad F = H \cdot \ell_e$$

The slope of a line on these axes is *permeance* ($P = \phi/F = \mu A_e/\ell_e$). Permeance is the inductance of one turn wound on the core.

Area in Fig. 2 represents total energy — hysteresis loss or recoverable energy.

Changing the operating point in Fig. 1 or Fig. 2 requires a change of energy, therefore it can not change instantaneously. When a winding is coupled to the magnetic core, the electrical to magnetic relationship is governed by Faraday's Law and Ampere's Law.

Faraday's Law:

$$\frac{d\phi}{dt} = \frac{E}{N} \quad ; \quad \phi = \frac{1}{N} \int E dt$$

Ampere's Law:

$$NI = \int H d\ell \approx H\ell$$

These laws operate bi-directionally. According to Faraday's Law, flux change is governed by the voltage applied to the winding (or voltage induced in the winding is proportional to $d\phi/dt$). Thus, electrical energy is transformed into energy lost or stored in the magnetic system (or stored magnetic energy is transformed into electrical energy).

Applying Faraday's and Ampere's Laws, the axes can be transformed again into the equivalent

electrical characteristic of the magnetic core wound with a specific number of turns, N, as shown in Figure 3.

$$\int E dt = NBA_e \quad ; \quad I = \frac{H\ell_e}{N}$$

Area in Fig. 3 again represents energy, this time in electrical terms: $W = \int EIdt$. The slope of a line in Fig 3 is inductance.

$$L = E \frac{dt}{di} = \mu N^2 \frac{A_e}{\ell_e}$$

## Low-Frequency Core Characteristics:

Ferromagnetic core materials include: Crystalline metal alloys, amorphous metal alloys, and ferrites (ferrimagnetic oxides).<sup>[1]</sup>

Figure 4 shows the low frequency electrical characteristics of an inductor with an ungapped toroidal core of an idealized ferromagnetic metal alloy. This homogeneous core becomes magnetized at a specific field intensity H (corresponding to specific current through the winding $I=H\ell/N$). At this magnetizing current level, all of the magnetic dipoles (domains) within the core gradually align, causing the flux to increase toward saturation. The domains cannot align and the flux cannot change instantaneously because energy is required. The changes occur at a rate governed by the voltage applied to the winding, according to Faraday's Law.

Thus, to magnetize this core, a specific magnetizing current, $I_M$, is required, and the time to accomplish the flux change is a function of the voltage applied to the winding. These factors combined —


<table>
  <thead>
    <tr>
        <th>I</th>
        <th>∫Edt</th>
    </tr>
  </thead>
  <tbody>
    <tr>
        <td>Negative Saturation</td>
        <td>Negative Max</td>
    </tr>
    <tr>
        <td>Positive Saturation</td>
        <td>Positive Max</td>
    </tr>
  </tbody>
</table>
Fig 3. - Equivalent Electrical Characteristic

![Diagram of an ideal magnetic core characteristic showing a rectangular hysteresis loop with labels for ∫Edt = NBA, R, Lo, 0, and I = Hℓ/N.](page_69_image_1_v2.jpg)

Fig 4. - Ideal Magnetic Core

Texas Instruments
R1-2
SLUP132

current, voltage, and time — constitute energy put into the core. The amount of energy put in is the area between the core characteristic and the vertical axis. In this case, none of this energy is recoverable — it is all loss, incurred *immediately* while the current and voltage is being applied.

The vertical slope of the characteristic represents an apparent infinite inductance. However, there is no real inductance — no recoverable stored energy — the characteristic is actually resistive. (A resistor driven by a square wave, plotted on the same axes, has the same vertical slope.)

When all of the domains have been aligned, the material is saturated, at the flux level corresponding to complete alignment. A further increase in current produces little change in flux, and very little voltage can exist across the winding as the operating point moves out on the saturation characteristic. The small slope in this region is true inductance — recoverable energy is being stored. With this ideal core, inductance $Lo$ is the same as if there were no core present, as shown by the dash line through the origin. The small amount of stored energy is represented by a thin triangular area *above* the saturation characteristic from the vertical axis to the operating point (not shown).

If the current is now interrupted, the flux will decrease to the *residual* flux level (point R) on the vertical axis. The small flux reduction requires reverse Volt-$\mu$seconds to remove the small amount of energy previously stored. (If the current is interrupted rapidly, the short voltage spike will be quite large in amplitude.) As long as the current remains at zero (open circuit), the flux will remain — forever — at point R.

If a negative magnetizing current is now applied to the winding, the domains start to realign in the opposite direction. The flux decreases at a rate determined by the negative voltage across the winding, causing the operating point to move down the characteristic at the left of the vertical axis. As the operating point moves down, the cumulative area between the characteristic and the vertical axis represents energy lost in this process. When the horizontal axis is reached, the net flux is zero — half the domains are oriented in the old direction, half in the new direction.

**The Effect of Core Thickness:** Fig. 1 applies only to a very thin toroidal core with Inner Diameter almost equal to Outer Diameter resulting in a single valued magnetic path length ($\pi \cdot D$). Thus the same field intensity exists throughout the core, and the entire core is magnetized at the same current level.

A practical toroidal core has an O.D. substantially greater than its I.D., causing magnetic path length to increase and field intensity to decrease with increasing diameter. The electrical result is shown in Figure 5. As current increases, the critical field intensity, H, required to align the domains is achieved first at the inner diameter. According to Ampere:

$$H = \frac{NI}{l} = \frac{NI}{\pi D}$$

Hold on to your hats!! At first, the domains realign and the flux changes in the new direction *only at the inner diameter*. The entire outer portion of the core is as yet unaffected, because the field intensity has not reached the critical level except at the inside diameter. The outer domains remain fully aligned in the *old* direction and the outer flux density remains saturated in the *old* direction. In fact, the core saturates completely in the *new* direction at its inner diameter yet the remainder of the core remains saturated in the *old* direction. Thus, complete flux reversal always takes place starting from the core inside diameter and progressing toward the outside.

In a switching power supply, magnetic devices are usually driven at the switching frequency by a

![Graph showing the effect of core thickness on the magnetic characteristic, plotting integral of Edt versus current I, with labels R, Lo, and 0.](page_70_image_1_v2.jpg)

Fig 5. - Effect of Core Thickness

Texas Instruments
R1-3
SLUP132

voltage source. A voltage across the winding causes the flux to change at a fixed rate. What actually happens is the flux change starts at the core inner diameter and progresses outward, at a rate equal to the applied volts/turn, E/N. The entire core is always saturated, but the inner portion is saturated in the new direction, while the outer portions remain saturated in the old direction. (This is the lowest energy state — lower than if the core were completely demagnetized.) There is in effect a boundary at the specific diameter where the field intensity is at the critical level required for domain realignment. Flux does *not* change gradually and uniformly throughout the core!

When the operating point reaches the horizontal axis, the net flux is zero, but this is achieved with the inner half of the core saturated in the new direction, while the outer half is simultaneously saturated in the old direction.

When voltage is applied to the winding, the net flux changes by moving the reversal boundary outward. The magnetizing current increases to provide the required field intensity at the larger diameter. If the O.D. of the core is twice the I.D., the magnetizing current must vary by 2:1 as the net flux traverses from minus to plus saturation. This accounts for the finite slope or "inductance" in the characteristic of Fig. 5. The apparent inductance is an illusion. The energy involved is *not* stored — it is all loss, incurred while the operating point moves along the characteristic — the energy involved is unrecoverable.

**Non-Magnetic Inclusions:** Figure 6 goes another step further away from the ideal, with


<table>
  <tbody>
    <tr>
        <td>Point</td>
        <td>Label</td>
    </tr>
    <tr>
        <td>V</td>
        <td>V</td>
    </tr>
    <tr>
        <td>S</td>
        <td>S</td>
    </tr>
    <tr>
        <td>R</td>
        <td>R</td>
    </tr>
    <tr>
        <td>0</td>
        <td>0</td>
    </tr>
    <tr>
        <td>Lo</td>
        <td>Lo</td>
    </tr>
  </tbody>
</table>

Fig 6. - Non-Magnetic Inclusions

considerable additional skewing of the characteristic. This slope arises from the inclusion of small non-magnetic regions in series with the magnetic core material. For example, such regions could be the non-magnetic binder that holds the particles together in a metal powder core, or tiny gaps at the imperfect mating surfaces of two core halves. Additional magnetic force is required, proportional to the amount of flux, to push the flux across these small gaps. The resulting energy stored in these gaps is theoretically recoverable. To find out how much energy is loss and how much is recoverable look at Figure 6. If the core is saturated, the energy within triangle S-V-R is recoverable because it is between the operating point S and the vertical axis, and *outside the hysteresis loop*. That doesn't ensure the *energy will be recovered* — it could end up dumped into a dissipative snubber.

Another important aspect of the skewing resulting from the non-magnetic inclusions is that the residual flux (point R) becomes much less than the saturation flux level. To remain saturated, the core must now be driven by sufficient magnetizing current. When the circuit is opened, forcing the magnetizing current to zero, the core will reset itself to the lower residual flux level at R.

**Reviewing some Principles:**

* Ideal magnetic materials do not store energy, but they do dissipate the energy contained within the hysteresis loop. (Think of this loss as a result of "friction" in rotating the magnetic dipoles.)

* Energy is stored, not dissipated, in non-magnetic regions.

* Magnetic materials *do* provide an easy path for flux, thus they serve as "magnetic bus bars" to link several coils to each other (in a transformer) or link a coil to a gap for storing energy (an inductor).

* High inductance does *not* equate to high energy storage. Flux swing is always limited by saturation or by core losses. High inductance requires less magnetizing current to reach the flux limit, hence *less* energy is stored. Referring to Figure 6, if the gap is made larger, further skewing the characteristic and *lowering* the inductance, triangle S-V-R gets bigger, indicating *more* stored energy.

Texas Instruments
R1-4
SLUP132

![Hysteresis loop with rounded corners showing non-homogeneous effects. Labels include V, S, Lo, ∫Edt, R, 0, and I.](page_72_layout_ocr_fwov_88_38_172_164.png)

Fig 7. - Non-Homogeneous Effects

![Skewed hysteresis loop with a large air gap. Labels include V, S, Lo, ∫Edt, R, and I(expanded scale).](page_72_layout_ocr_ejlb_316_38_242_163.png)

Fig 8. - Large Air Gap

**Non-Homogeneous Aspects:** Figure 7 is the same as Figure 6 with the sharp corners rounded off, thereby approaching the observed shape of actual magnetic cores. The rounding is due to non-homogeneous aspects of the core material and core shape.

Material anomalies that can skew and round the characteristic include such things as variability in ease of magnetizing the grains or particles that make up the material, contaminants, precipitation of metallic constituents, etc.

Core shapes which have sharp corners will paradoxically contribute to rounded corners in the magnetic characteristic. Field intensity and flux density are considerably crowded around inside corners. As a result, these areas will saturate before the rest of the core, causing the flux to shift to a longer path as saturation is approached. Toriodal core shapes are relatively free of these effects.

**Adding a Large Air Gap:** The cores depicted in Figures 4 - 7 have little or no stored recoverable energy. This is a desirable characteristic for Mag-amps and conventional transformers. But filter inductors and flyback transformers require a great deal of stored energy, and the characteristics of Figures 4 - 7 are unsuitable.

Figure 8 is the same core as in Fig. 7 with much larger gap(s) — a few millimeters total. This causes a much more radical skewing of the characteristic. The horizontal axis scale (magnetizing current) is perhaps 50 times greater than in Figure 7. Thus the stored, recoverable energy in triangle S-V-R,

outside of the hysteresis loop, is relatively huge. The recoverable energy is almost all stored in the added gap. A little energy is stored in the non-magnetic inclusions within the core. Almost zero energy is stored in the magnetic core material itself.

With powdered metal cores, such as Mo-Permalloy, the large gap is distributed between the metal particles, in the non-magnetic binder which holds the core together. The amount of binder determines the effective total non-magnetic gap. This is usually translated into an equivalent permeability value for the composite core.

**Core Eddy Current Losses:**

Up to this point, the low frequency characteristics of magnetic cores have been considered. The most important distinction at high frequencies is that the core eddy currents become significant and eventually become the dominant factor in core losses. Eddy currents also exist in the windings of magnetic devices, causing increased copper losses at high frequencies, but this is a separate topic, not discussed in this paper.

Eddy currents arise because voltage is induced within the magnetic core, just as it is induced in the windings overlaying the core. Since all magnetic core materials have finite resistivity, the induced voltage causes an eddy current to circulate within the core. The resulting core loss is in addition to the low frequency hysteresis loss.

Ferrite cores have relatively high resistivity. This reduces loss, making them well suited for high frequency power applications. Further improvements in

Texas Instruments
R1-5
SLUP132

![Core Eddy Current Model diagram showing a resistor RE in parallel with an inductor L](page_73_image_1_v2.jpg)

Fig 9. - Core Eddy Current Model

high frequency power ferrite materials focus on achieving higher resistivity. Amorphous metal cores and especially crystalline metal cores have much lower resistivity and therefore higher losses. These cores are built-up with very thin laminations. This drastically reduces the voltages induced within the core because of the small cross section area of each lamination.

The core can be considered to be a single-turn winding which couples the eddy current loss resistance into any actual winding. Thus, as shown in Figure 9, the high frequency eddy current loss resistance can be modeled as a resistor $R_E$ in parallel with a winding which represents all of the low frequency properties of the device.

In Figure 10, the solid line shows the low frequency characteristic of a magnetic core, with dash lines labeled $f_1$ and $f_2$ showing how the hysteresis loop effectively widens at successively higher frequencies. Curves like this frequently appear on manufacturer's data sheets. They are not very useful for switching power supply design, because they are based on frequency, assuming symmetrical drive waveforms, which is not the case in switching power supplies.

In fact, it is really not appropriate to think of








<table>
  <thead>
    <tr>
        <th>Frequency</th>
        <th>Loop Width</th>
    </tr>
  </thead>
  <tbody>
    <tr>
        <td>Low (solid line)</td>
        <td>Narrow</td>
    </tr>
    <tr>
        <td>f1 (dashed line)</td>
        <td>Medium</td>
    </tr>
    <tr>
        <td>f2 (dashed line)</td>
        <td>Wide</td>
    </tr>
  </tbody>
</table>

Fig 10. - L.F. Hysteresis plus Eddy Current

eddy current losses as *frequency* dependent. Losses really depend on rate of flux change, and therefore according to Faraday's Law, upon the applied volts/turn. Frequency is relevant only in the case of sinusoidal or symmetrical square wave voltage waveforms.

In a switching power supply operating at a fixed frequency, $f_s$, core eddy current losses vary with pulse voltage amplitude squared, and inversely with pulse width — exactly the same as for a discrete resistor connected across the winding:

$$ Loss = \frac{V_p^2}{R_E} \frac{t_p}{T} $$

If the pulse voltage is doubled and pulse width halved, the same flux swing occurs, but at twice the rate. $V_p^2$ is quadrupled, $t_p$ is halved — losses double.

If the flux swing and the duty cycle is maintained constant, eddy current loss varies with $f_s^2$ (but usually the flux swing is reduced at higher frequency to avoid excessive loss).

**Forward Converter Illustration:**

Figure 11 provides an analysis of transformer operation in a typical forward converter. Accompanying waveforms are in Fig. 12. The solid line in Fig. 11 is the low-frequency characteristic of the ferrite core. The dash lines show the actual path of the operating point, including core eddy currents reflected into the winding. Line X-Y is the mid-point of the low frequency hysteresis curve. Hysteresis loss will be incurred to the right of this line as the flux increases, to the left of this line when the flux decreases.

Just before the power pulse is applied to the winding, the operating point is at point R, the residual flux level. When the positive (forward) pulse is applied, the current rises rapidly from R to D (there is no time constraint along this axis). The current at D includes a low-frequency magnetizing component plus an eddy current component proportional to the applied forward voltage. The flux increases in the positive direction at a rate equal to the applied volts/turn.

As the flux progresses upward, some of the energy taken from the source is stored, some is loss. Point E is reached at the end of the positive

Texas Instruments
R1-6
SLUP132

![Hysteresis loop diagram showing core flux and eddy current loss regions with points A, B, C, D, E, R, X, Y.](page_74_layout_ocr_snvh_78_44_193_162.png)

Fig 11. - *Forward Converter Core Flux, $I_M$*

![Waveform diagrams for VL and IM showing switching pulses and reset intervals with points A, C, D, E, R.](page_74_layout_ocr_kust_376_39_125_173.png)

Fig 12. - *Forward Converter Waveforms*

pulse. The energy enclosed by X-D-E-Y-X has been dissipated in the core, about half as hysteresis loss, half eddy current loss as shown. The energy enclosed by R-X-Y-B-R is stored (temporarily).

When the power switch turns off, removing the forward voltage, the stored energy causes the voltage to rapidly swing negative to reset the core, and the operating point moves rapidly from E to A. Assuming the reverse voltage is clamped at the same level as the forward voltage, the eddy current magnitude is the same in both directions, and the flux will decrease at the same rate that it increased during the forward interval.

As the operating point moves from A to C, the current delivered into the clamp is small. During this interval, a little energy is delivered to the source, none is received from the source. Most of the energy that had been temporarily stored at point E is turned into hysteresis and eddy current loss as the flux moves from A to C to R. The only energy recovered is the area of the small triangle A-B-C.

Note that as the flux diminishes, the current into the clamp reaches zero at point C. The clamp diode prevents the current from going negative, so the winding disconnects from the clamp. The voltage tails off toward zero, while previously stored energy continues to supply the remaining hysteresis and eddy current losses. Because the voltage is diminishing, the flux slows down as it moves from C to D. Therefore the eddy current also diminishes. The total eddy current loss on the way down through the trapezoidal region A-C-R is therefore slightly less than on the way up through D and E.

In a forward converter operating at a fixed switching frequency, a specific V-$\mu$s forward pulse is required to obtain the desired $V_{OUT}$. When $V_{IN}$ changes, pulse width changes inversely. The transformer flux will always change the same amount from D to E, but with higher $V_{IN}$ the flux changes more rapidly. Since the higher $V_{IN}$ is also across $R_E$, the equivalent eddy current resistance, the eddy current and associated loss will be proportional to $V_{IN}$. Worst case for eddy current loss is at high line.

[1] T.G. Wilson, Sr., *Fundamentals of Magnetic Materials*, APEC Tutorial Seminar 1, 1987

Texas Instruments
R1-7
SLUP132

Texas Instruments R1-8 SLUP132

# Eddy Current Losses in Transformer Windings and Circuit Wiring

**Lloyd H. Dixon, Jr.**

## Introduction

As switching power supply operating frequencies increase, eddy current losses and parasitic inductances can greatly impair circuit performance. These high frequency effects are caused by the magnetic field resulting from current flow in transformer windings and circuit wiring.

This paper is intended to provide insight into these phenomena so that improved high frequency performance can be achieved. Among other things, it explains (1) why eddy current losses increase so dramatically with more winding layers, (2) why parallelling thin strips doesn't work, (3) how passive conductors (Faraday shields and C.T. windings) have high losses, and (4) why increasing conductor surface area will actually worsen losses and parasitic inductance if the configuration is not correct.

## Basic Principles

The following principles are used in the development of this topic and are presented here as a review of basic magnetics.

1. **Ampere's Law**: The total magneto-motive force along *any* closed path is equal to the total current enclosed by that path:

$$F = \oint H d\ell = I_t = NI \quad \text{Amps} \quad (1)$$

where F is the total magneto-motive force (in Amperes) along a path of length $\ell$ (m), $H$ is field intensity (A/m), and $I_t$ is the total current through all turns enclosed by the path.

2. **Conservation of energy**: At any moment of time, the current within the conductors and the magnetic field are distributed so as to minimize the energy taken from the source.

3. **Energy content of the field**: The magnetic field *is* energy. The energy density at any point in the field is:

$$w = \int H dB \quad \text{Joules/m}^3$$

where $B$ is the flux density (Tesla). In switching power supplies, almost all magnetic  energy is stored in air gaps, insulation between conductors, and within the conductors, where relative permeability $\mu_r$ is essentially 1.0 and constant. The energy density then becomes:

$$w = \frac{1}{2}BH = \frac{1}{2}\mu_0 H^2 \quad \text{J/m}^3$$

where $\mu_0$ is the absolute permeability of free space ($= 4\pi \cdot 10^{-7}$ in S.I. units). Total energy $W$ (Joules) is obtained by integrating the energy density over the entire volume, $v$, of the field:

$$W = \frac{1}{2}\mu_0 \int H^2 dv \quad \text{Joules}$$

Within typical transformers and inductors, the magnetic energy is almost always confined to regions where the field intensity $H$ is relatively constant and quite predictable. This often occurs in circuit wiring, as well. In these cases:

$$W = \frac{1}{2}\mu_0 H^2 A \cdot \ell \quad \text{Joules} \quad (2)$$

and from (1), $H\ell = NI$. Substituting for $H$:

$$W = \frac{1}{2}\mu_0 N^2 I^2 A / \ell \quad \text{Joules} \quad (3)$$

where $A$ is the cross-section area ($\text{m}^2$) of the region normal to the flux, and $\ell$ is the length of the region in meters (and the effective length of the field).

4. **Circuit inductance**: Inductance is a measure of an electrical circuit's ability to store magnetic energy. Equating the energy stored in the field from (3) with the same energy in circuit terms:

$$W = \frac{1}{2}LI^2 = \frac{1}{2}\mu_0 N^2 I^2 A / \ell$$
$$L = \mu_0 N^2 A / \ell \quad (4)$$

## Skin Effect

Figure 1 shows the magnetic field (flux lines) in and around a conductor carrying dc or low frequency current $I$. The field is radially symmetrical, as shown, only if the return current with its associated field is at a great distance.

At low frequency, the energy in the magnetic field is trivial compared to the energy loss in the resistance of the wire. Hence the current

Texas Instruments
R2-1
SLUP132

![Diagram showing cross-section and side view of an isolated conductor with uniform current distribution at low frequency.](page_77_image_1_v2.jpg)

Fig. 1 - Isolated Conductor at Low Frequency

distributes itself uniformly throughout the wire so as to minimize the resistance loss and the total energy expended.

Around any closed path outside the wire (and inside the return current), magneto-motive force $F$ is constant and equal to total current $I$. But field intensity $H$ varies inversely with the radial distance, because constant $F$ is applied across an increasing $\ell$ ($=2\pi r$).

Within the conductor, $F$ at any radius must equal the enclosed current at that radius, therefore $F$ is proportional to $r^2$.

![Diagram showing eddy current loops induced within a conductor at high frequency.](page_77_image_2_v2.jpg)

Fig. 2 - Eddy Current at High Frequency

At high frequency: Figure 2 is a superposition model that explains what happens when the frequency rises. The dash lines represent the uniform low frequency current distribution, as seen in Fig. 1. When this current changes rapidly, as it will at high frequency, the flux within the wire must also change rapidly. The changing flux induces a voltage loop, or eddy, as shown by the solid lines near the wire surface. Since this induced voltage is within a conductor, it causes an eddy current coincident with the voltage. Note how this eddy current reinforces the main current flow at the surface, but opposes it toward the center of the wire.

The result is that as frequency rises, current density increases at the conductor surface and decreases toward zero at the center. as shown in Fig. 3. The current tails off exponentially within the conductor. The portion of the conductor that is actually carrying current is

reduced, so the resistance at high frequency (and resulting losses) can be many times greater than at low frequency.

![Diagram comparing actual exponential current distribution with an equivalent rectangular distribution at high frequency.](page_77_image_3_v2.jpg)

Fig. 3 - High Frequency Current Distribution

**Penetration depth:** Penetration or skin depth, $D_{PEN}$, is defined as the distance from the surface to where the current density is $1/e$ times the surface current density ($e$ is the natural log base)[1]:

$$D_{PEN} = [\rho / (\pi \mu f)]^{1/2} \text{ m} \quad (5)$$

where $\rho$ is resistivity. For copper at 100°C, $\rho = 2.3 \cdot 10^{-6} \text{ \Omega-cm}$, $\mu = \mu_0 = 4\pi \cdot 10^{-7}$, and:

$$D_{PEN} = 7.5 / (f)^{1/2} \text{ cm} \quad (6)$$

From (6), $D_{PEN} = .024 \text{ cm}$ at 100 kHz, or $.0075 \text{ cm}$ at 1 MHz.

Eqs. (5) and (6) are accurate for a flat conductor surface, or when the radius of curvature is much greater than the penetration depth.

Although the current density tails off exponentially from the surface, the high frequency resistance (and loss) is the same as if the current density were constant from the surface to the penetration depth, then went abruptly to zero as shown on the right hand side of Fig. 3. This equivalent rectangular distribution is easier to apply.

**Equivalent circuit model:** Another way of looking at the high frequency effects in transformer windings and circuit wiring is through the use of an equivalent electrical circuit model. This approach is probably easier for a circuit designer to relate to.

Figure 4 is the equivalent circuit of the isolated conductor of Figs. 1 to 3. With current $I$ flowing through the wire, $L_x$ accounts for the energy $\frac{1}{2} L_x I^2$ stored in the external magnetic field. $L_x$ is the inductance of the wire at high frequencies.

Point A represents the outer surface of the conductor, while B is at the center. $R_i$ is the

Texas Instruments
R2-2
SLUP132

![Conductor Equivalent Circuit diagram showing external inductance Lx, surface point A, internal inductance Li, center point B, and resistance Ri elements.](page_78_image_1_v2.jpg)

Fig. 4 - Conductor Equivalent Circuit

resistance, distributed through the wire from surface to center. Think of the wire as divided into many concentric cylinders of equal cross section area. The $R_i$ elements shown in the drawing would correspond to the equal resistance of each of the cylinders. Likewise, the internal inductance $L_i$ accounts for the magnetic energy distributed through the cylindrical sections. The energy stored in each section depends on the cumulative current flowing through the elements to the right of that section in the equivalent circuit.

Note that external inductance $L_x$ of the wire (or the leakage inductance of a winding) limits the maximum $di/dt$ through the wire, depending on the source compliance voltage, no matter haw fast the switch turns on.

The time domain: If a rapidly rising current is applied to the wire, the voltage across the wire is quite large, mostly across $L_x$. Internal inductance $L_i$ blocks the current from the wire interior, forcing it to flow at the surface through the left-most resistance element, even after the current has reached its final value and the voltage across $L_x$ collapses. Although the energy demand of $L_x$ is satisfied, the voltage across the wire is still quite large because current has not penetrated significantly into the wire and must flow through the high resistance of the limited cross-section area at the surface. Additional source energy is then mostly dissipated in the resistance of this surface layer.

The voltage across this $R_i$ element at the surface is impressed across the adjacent $L_i$ elements toward the center of the wire, causing the current in $L_i$ near the surface to rise. Current cannot penetrate without a field being generated within the conductor, and this requires energy. As time goes on, conduction propagates from the surface toward the center (at B in the equivalent circuit), storing energy in $L_i$. More of the resistive elements conduct,

lowering the total resistance and reducing the energy going into losses. Finally, conduction is uniform throughout the wire, no further energy goes into the magnetic fields external or internal to the wire, and a small amount of energy continues to be dissipated in $R_i$ over time.

Note that the concept of skin depth bas no meaning in the time domain.

The frequency domain: Referring again to Fig. 4 with a sine wave current applied to the terminals, it is apparent that at low frequencies, the reactance of internal inductance $L_i$ is negligible compared to $R_i$. Current flow is uniform throughout the wire and resistance is minimum. But at high frequency, current flow will be greatest at the surface (A), tailing off exponentially toward the center (B).

Penetration depth (skin depth) is clearly relevant in the frequency domain. At any frequency, the penetration depth from Eq. (5) or (6) reveals the percentage of the wire area that is effectively conducting, and thus the ratio of dc resistance to ac resistance at that frequency.

Although the current waveforms encountered in most switching power supplies are not sinusoidal, most papers dealing with the design of high frequency transformer windings use a sinusoidal approach based on work done by Dowell in 1966.[2] Some authors use Fourier analysis to extend the sinusoidal method to non-sinusoidal waveforms.

## Proximity Effect

Up to this point a single isolated conductor has been considered. Its magnetic field extends radially in all directions, and conduction occurs across the entire surface.

When another conductor is brought into close proximity to the first, their fields add vectorially. Field intensity is no longer uniform around the conductor surfaces, so high frequency current flow will not be uniform.

For example, if the round wire of Fig. 1 is close to another wire carrying an equal current in the opposite direction (the return current path?), the fields will be additive between the two wires and oppose and cancel on the outsides. As a result, high frequency current flow is concentrated on the wire surfaces facing each other, where the field intensity is greatest, with

Texas Instruments
R2-3
SLUP132

little or no current on the outside surfaces where the field is low. This pattern arranges itself so as to minimize the energy utilized, hence inductance is minimized. As the wires are brought closer together, cancellation is more complete. The concentrated field volume decreases, so the inductance is reduced.

**Circuit wiring:** The field and current distribution with round wires is not easy to compute. A simpler and more practical example is given in Figure 5. The two flat parallel strips shown are actually the best way to implement high frequency wiring, minimizing the wiring inductance and eddy current losses. These strips could be two wide traces on opposite sides of a printed circuit board. (Don't use point-to-point wiring. It is much more important to collapse the loop and keep the outgoing and return conductors as intimate as possible, even if the wiring distances are greater.)

![Diagram showing two flat parallel strips with current flow indicators and dimensions l and w.](page_79_image_1_v2.jpg)

*Fig. 5 - Circuit Wiring - Flat Parallel Strip*

The + signs indicate current flow *into* the upper strip, the $\cdot$ indicates current *out of* the lower strip. Between the strips, the magnetic field is high and uniform, so the current is spread out uniformly on the inner surfaces. On the outside of the strips the field is very low, so the current is almost zero. This results in the minimum possible energy storage (and wiring inductance) for this configuration. If the breadth of the strip, $\ell$, is much greater than the separation, $w$, the energy is almost entirely contained between the two strips. Then $\ell$ and $w$ are the length and width of the field, and can be used to calculate the inductance. Converting Eq. (4) to cm and with N = 1 turn, the inductance per centimeter length of the 2-conductor strip is:

$$L = 12.5\ w/\ell \quad \text{nH/cm} \qquad (7)$$

If the strips have a breadth of 1 cm and are separated by 0.1 cm, the combined inductance of the pair is only 1.25 nH for each centimeter length, divided equally between each of the two conductors. If one conductor is much wider than the other, such as a strip vs. a ground plane, most of the inductance calculated in (6) is in series with the narrower conductor. This is good for keeping down noise in the ground returns.

Note that current penetration is from one side only -- the side where the field is. This means that a strip thicker than the penetration depth is not fully utilized. The equivalent circuit model of Fig. 4 still applies, with A at the surface adjacent to the field. But B becomes the *opposite* side of the strip, not the center, since there is no penetration from the side with no field.

**Bad practice:** Figures 6 and 7 show what *not* to do for circuit wiring (unless you want high inductance and eddy current losses). Although these strips have large surface areas, proximity effects in these configurations result in very little surface actually utilized. Remember that the field is concentrated directly between the two conductors so as to minimize the stored energy.

In Fig. 6 this results in current flow only at the edges facing each other. Also, because the concentrated field region is short, the energy density is very high, and the inductance is several times greater than in Fig. 5.

The Fig. 7 configuration is not quite as bad as Fig. 6 because the current does spread out somewhat in one of the two conductors, but it is still many times worse than the proper configuration in Fig. 5. The message is: large

![Diagram showing two strips side by side, illustrating bad wiring practice.](page_79_layout_ocr_qhjw_340_535_202_35.png)

*Fig. 6 - Bad Wiring Practice - Side by Side*

![Diagram showing two strips at a right angle, illustrating bad wiring practice.](page_79_layout_ocr_jyvg_373_613_128_100.png)

*Fig. 7 - Bad Wiring Practice - Right Angled*

Texas Instruments
R2-4
SLUP132

surface area doesn't improve high frequency performance if the configuration is wrong.

**Inductor Windings:** Figure 8 is a simple inductor. The winding consists of 4 turns in a single layer. Assuming a current of 1 Ampere through the winding, the total magneto-motive force $F = NI$ along any path linking the 4 turns is 4 Ampere-turns. The field is quite linear across the length of the window because of the addition of the fields from the individual wires in this linear array. The winding could have been a flat strip carrying 4 Amps with the same result.

![Diagram of an inductor winding showing magnetic field lines and an air gap labeled lg.](page_80_image_2_v2.jpg)

Fig. 8 - Inductor Winding

Without the ferrite core, the field outside of the winding would have been weak because of cancellation, but with the high permeability core, the external field is completely shorted out. This means the entire field, $F = NI$ is contained across the window inside the winding. Field intensity, $H$ equals $NI/l$. In the center, the entire field is compressed across the small air gap. Field intensity ($H_g = NI/l_g$) is therefore much greater within the gap, so the energy stored in the gap (using Eq. 2 or 3) is much greater than the energy in the much larger window.

At high frequency, current flow is concentrated on the inner surface of the coil, adjacent to the magnetic field. The field outside the coil is negligible, so no current flows on the outer surface.

**Transformer Windings:** Figure 9 shows a transformer with a four turn single layer primary and a 1 turn single layer copper strip secondary. In any transformer, the sum of the Ampere-turns in all windings must equal zero (except for a small magnetizing current which

![Diagram of transformer windings showing primary and secondary turns with magnetic field lines.](page_80_image_1_v2.jpg)

Fig. 9 - Transformer Windings

is neglected). So if the secondary load current is 4 A through 1 turn, the primary current through 4 turns must be 1 Amp. The fields tend to cancel not only outside both windings, but in the center of the two windings as well. Whatever field might remain is shorted out by the high permeability core which has no gap. Thus the field generated by the current in the windings, $F = 4\text{ A}$, exists only between the windings. So at high frequency, current flow is on the outside of the inner winding and on the inside of the outer winding, adjacent to the field.

## Multiple Layer Windings

Figure 10 shows a transformer with multilayer windings and its associated low frequency mmf ($F$) and energy density diagrams. One half of the core and windings are depicted. At low frequency, current (not shown) is uniformly distributed through all conductors, because they are much thinner than the penetration depth.

![Diagram of multiple layer windings with corresponding MMF (F=NI) and energy density (w) plots.](page_80_image_3_v2.jpg)

Fig. 10 - Multiple Layer Winding

Texas Instruments
R2-5
SLUP132

The primary winding has 8 turns arranged in two 4-turn layers, while the secondary has 3 turns of copper strip in 3 layers. With 2 Amp load current, the secondary has 3T · 2A = 6 A-T. The primary must also have 6 A-T, so primary current is 0.75 A.

As shown in the mmf diagram below the core in Fig. 10, there is no field outside of the primary or inside the secondary, but starting at the outside of the primary and moving toward the center, the field rises to its maximum value between the two windings. With uniform current distribution at low frequency, note how the field builds uniformly within each conductor according to Faraday's law, staying constant between the conductors. The energy density in the field goes up with the square of the field strength, as shown below the mmf diagram. The area under the energy density curve is the total leakage inductance energy stored in and between the windings.

So multiple layers cause the field to build. At high frequencies, it will be shown that the eddy current losses go up exponentially as the number of layers is increased. The number of layers should be kept to a minimum by using a core with a long narrow window to accommodate all the turns in fewer layers (this also causes a dramatic reduction in leakage inductance). The window shape illustrated in Fig. 10 is far from optimum.

**Interleaved Windings:** Another way to reduce the effective number of layers is to break up the winding into smaller sections through

interleaving, as shown in Figure 11.

With interleaving, each winding is essentially divided into two or more sections, as shown on each side of the dotted line in Fig. 11. The primary now has two sections a and b, each with 1 layer of 4 turns. The secondary is also divided down the middle into two sections of $1 \frac{1}{2}$ layers, 1 turn per layer. (This is why half layers are included in eddy current loss curves.) Note that the 2 amperes through the $1 \frac{1}{2}$ turns of secondary section (a) cancels the 0.75 A, 4 turns of primary section (a), and the field goes through zero in the middle of the center secondary turn at the dotted line. *F* builds up to only half the peak value compared to Fig. 10, and reverses direction between alternate winding sections. It will be shown that the reduced field causes a great reduction in eddy current losses.

Because of the reduced field, the total energy under the energy density curve in Fig. 11 is only 1/4 the total energy in Fig. 10. Thus, interleaving reduces the leakage inductance by a factor of 4!

**Multiple layers at high frequency:** Figure 12 is an enlarged section of Fig. 10 but at a high frequency where the penetration depth is 20% of the secondary winding strip thickness. The field strength and current density are the same as at low frequency in the spaces between the conductors. But *within* the conductors, current density, magnetic field and energy density all fall off rapidly moving in from the surface. (Dash lines show low frequency distributions.)

![Diagram of interleaved windings showing primary sections Pa and Pb and secondary sections Sa and Sb, with corresponding MMF (F=NI) and energy density (w) plots below.](page_81_image_2_v2.jpg)

Fig. 11 - Interleaved Windings

![Diagram showing multiple layers at high frequency with primary turns P1, P2 and secondary turns S3, S2, S1. Below are plots for MMF (F=NI) and energy density (w) showing high frequency skin effects compared to low frequency (dashed lines).](page_81_image_1_v2.jpg)

Fig. 12 - Multiple Layers at High Frequency

Texas Instruments
R2-6
SLUP132

The heavier lines showing the high frequency distributions are approximations based on the current distribution ending abruptly at the penetration depth. Actually, the slopes are steeper at the surfaces, and tail off within the wire.)

Notice that the total energy under the energy density curve is about half the amount at low frequency. This means the leakage inductance has decreased at high frequency, but only because the energy within the conductors is practically eliminated. This is not a very practical way to reduce leakage inductance -- the penalty is a huge increase in eddy current losses.

With the penetration depth 20% of the strip thickness, the ac resistance might be expected to be 5 times the dc resistance. But with three layers building up the field, the ac resistance is actually 32 times greater!

**Why multiple layers cause high losses:**
Figure 13 is an even more enlarged view of the 3 secondary layers of Fig. 12, together with their high frequency mmf diagram. Assume a current of 1 Ampere through the 3 layer winding. There is only one turn (strip) per layer.

To the right of layer S1, the mmf is 0. At the left of S1, F=1 A-T. The 1 Amp current in S1 is crowded into the 20% penetration depth adjacent to the field. Field F also cannot penetrate more than 20% into S1. This 1 A-T

field exists only between S1 and S2. F cannot penetrate S2, either. It must terminate on the right side of S2, but it cannot just magically disappear.

According to Faraday's law, for the mmf to be zero in the center of S2, the enclosed current must be zero. This requires a current of 1 Amp on the right surface of S2 in the *opposite direction to normal current flow* to cancel the 1 Amp in S1. Then, to achieve the 2 A-T field to the left of S2 requires a surface current of 2 Amps! (The net current in S2 is still 1 Amp.)

The 2 A-T field must be terminated at the right side of S3 with 2 A reverse current flow. Then 3 Amps must flow on the S3 left surface to support the 3 A-T field and to conform to the net 1 Amp through the winding.

If the current in each layer were just the 1 Amp, limited in penetration to 20% of the conductor thickness, the ac to dc resistance ratio, F<sub>R</sub>, would be 5:1. But the surface currents in successive layers become much larger, as discussed above. The tabulation above the conductors in Fig. 13 gives the current at each surface and the current squared, which indicates the relative power loss at each surface. The two surfaces of S2 together dissipate 1 + 4 = 5 times as much as S1, while dissipation in S3 is 4 + 9 = 13 times S1!

The average resistance of the 3 layers is (9+4+4+1+1)/3 = 19/3 = 6.333 times the resistance of layer S1. Since the ac resistance of S1 is already 5 times the dc resistance (because of the 20% penetration depth), the ratio of average ac resistance to the dc resistance, F<sub>R</sub>, is 31.67 : 1. Hardly negligible.

Referring to S3 with 3A and -2A at its surfaces, if conductor thickness is decreased or if frequency is decreased to improve penetration, the penetration "tails" of these opposing currents will reach across and partially cancel. When D<sub>pen</sub> is much larger than the conductor thickness, cancellation is complete, conductor current is 1 Amp uniformly distributed, and F<sub>R</sub> = 1.

Although each layer was a 1 turn strip carrying 1 Amp in this illustration, each layer could have been 10 turns carrying 0.1 Amps with the same results.


<table>
  <thead>
    <tr>
        <th>I²</th>
        <th>9</th>
        <th>4</th>
        <th>4</th>
        <th>1</th>
        <th>1</th>
        <th rowspan="2">= 19/3</th>
    </tr>
    <tr>
        <th>I</th>
        <th>3</th>
        <th>-2</th>
        <th>2</th>
        <th>-1</th>
        <th>1</th>
    </tr>
  </thead>
</table>

![Diagram showing surface currents in three layers S3, S2, and S1 with a corresponding MMF plot labeled F=NI below.](page_82_layout_ocr_ivud_49_476_251_244.png)

Fig. 13 - Surface Currents

Texas Instruments
R2-7
SLUP132

![Diagram showing passive winding losses with field distribution plots for different layers labeled P, S3, S2, and S1. The field intensity F=NI is plotted below the physical layers. Numerical values for current and field are shown above the layers.](page_83_layout_ocr_cpyt_47_37_250_242.png)

Fig. 14 - Passive Winding Losses

**Passive layers:** A passive layer is any conductor layer that is not actively "working" by carrying net useful current. Faraday shields and the non-conducting side of center-tapped windings are examples of passive layers.

Figure 14 shows what happens if a Faraday shield is inserted in the 3 A-T field between the secondary winding of Fig. 13 and the primary (off to the left). If the Faraday shield thickness is much greater than D<sub>PEN</sub>, 3 Amps must flow on each surface because the field cannot penetrate. At each surface, I<sup>2</sup> is 9 Amps squared, and both surfaces together dissipate 18 times as much as S1, or almost as much as all three secondary turns combined.

Faraday shields are always located where the field is highest. Their thickness should be less than 1/3 of D<sub>PEN</sub> keep the loss to an acceptable level.

For another example, consider a center-tapped secondary with sides A and B each side of the center-tap. If A is physically between B and the primary, A is a passive conductor in the high field region when B is conducting, but B is outside the field when A conducts. The additional passive dissipation in A will probable exceed the active dissipation in either A or B. This is one reason that single-ended transformers overtake or even surpass push-pull and half-bridge versions at frequencies above a few hundred kHz.

**Paralleled windings:** When ac resistance of a strip secondary winding is too high because the required strip thickness is too great, it is tempting to simply subdivide it into several thinner strips, insulated from each other. This doesn't work -- the parallel combination will have the same losses as an equivalent solid strip. This is because the individual thin strips occupy different positions in the field, causing eddy currents to circulate between the outer and innermost strips where they are connected in parallel at their ends, similar to what happens in a single solid strip.

Conductors can be successfully paralleled only when they experience the same field, averaged along their length:

1. Wires in the same layer can be paralleled, as long as they progress together from one layer to the next.

2. Litz wire -- fine wires woven or twisted in such a manner that they successively occupy the same positions in the field.

3. Portions of a winding at comparable field levels in different interleaved sections can be paralleled. For example the two four-turn primary sections in Fig. 11 could be paralleled. The field must remain apportioned equally between in the two sections or much more energy would be required. If the secondary in Fig. 11 were a single solid turn, it could be divided into two thinner paralleled turns.

**Calculating ac resistance:** It has been shown that it is not difficult to calculate F<sub>R</sub> when the conductor thickness is much greater than the penetration depth. It is also easy when the conductor thickness is much less than D<sub>PEN</sub> -- F<sub>R</sub> = 1. But the condition of greatest interest to the transformer designer is when the conductor thickness is in the same range as D<sub>PEN</sub>, and here the calculations are quite difficult.

Dowell solved the problem for sinusoidal waveforms in his 1966 paper.[2] The curves in Figure 15 are derived from Dowell's work. The vertical scale is F<sub>R</sub>, the ratio of R<sub>ac</sub>/R<sub>dc</sub>. The horizontal scale, Q, is the ratio of the effective conductor height, or layer thickness, to the penetration depth, D<sub>PEN</sub>. For strip or foil windings, the layer thickness is the strip thickness. For round wires touching each other in the layer, the effective layer thickness is 0.83 times

Texas Instruments
R2-8
SLUP132

<table>
  <thead>
    <tr>
        <th>Q</th>
        <th>10 Layers</th>
        <th>6 Layers</th>
        <th>4 Layers</th>
        <th>3 Layers</th>
        <th>2.5 Layers</th>
        <th>2 Layers</th>
        <th>1.5 Layers</th>
        <th>1 Layer</th>
        <th>0.5 Layers</th>
    </tr>
  </thead>
  <tbody>
    <tr>
        <td>0.25</td>
        <td>1.0</td>
        <td>1.0</td>
        <td>1.0</td>
        <td>1.0</td>
        <td>1.0</td>
        <td>1.0</td>
        <td>1.0</td>
        <td>1.0</td>
        <td>1.0</td>
    </tr>
    <tr>
        <td>0.5</td>
        <td>1.5</td>
        <td>1.3</td>
        <td>1.1</td>
        <td>1.0</td>
        <td>1.0</td>
        <td>1.0</td>
        <td>1.0</td>
        <td>1.0</td>
        <td>1.0</td>
    </tr>
    <tr>
        <td>1.0</td>
        <td>10.0</td>
        <td>6.0</td>
        <td>4.0</td>
        <td>3.0</td>
        <td>2.5</td>
        <td>2.0</td>
        <td>1.5</td>
        <td>1.0</td>
        <td>1.0</td>
    </tr>
    <tr>
        <td>2.0</td>
        <td>40.0</td>
        <td>25.0</td>
        <td>16.0</td>
        <td>12.0</td>
        <td>10.0</td>
        <td>8.0</td>
        <td>6.0</td>
        <td>4.0</td>
        <td>2.0</td>
    </tr>
    <tr>
        <td>4.0</td>
        <td>80.0</td>
        <td>50.0</td>
        <td>32.0</td>
        <td>24.0</td>
        <td>20.0</td>
        <td>16.0</td>
        <td>12.0</td>
        <td>8.0</td>
        <td>4.0</td>
    </tr>
    <tr>
        <td>10.0</td>
        <td>200.0</td>
        <td>125.0</td>
        <td>80.0</td>
        <td>60.0</td>
        <td>50.0</td>
        <td>40.0</td>
        <td>30.0</td>
        <td>20.0</td>
        <td>10.0</td>
    </tr>
  </tbody>
</table>

Fig. 15 - Eddy Current Losses - $R_{AC}/R_{DC}$

substituted for the original wire (taking care to handle this properly), there will be 40 wires, 20 per layer, 2 layers deep. Q is now 2. Entering Fig. 15 at Q=2 and 2 layers, $F_R$ is 5.2 -- it went up! The reason for this is the wire size is still too large for effective penetration and cancellation of the eddy currents, and the number of layers has been doubled with the extra eddy current surfaces this generates.

Subdividing again into 16 parallel wires

the wire diameter. For round wires spaced apart in a layer, the effective layer thickness is $.83 \cdot d \cdot (d/s)^{1/2}$, where $d$ is wire diameter and $s$ is the center-to-center spacing of the wires.

of 1/4 the original diameter there are 160 total wires, 40 per layer, 4 layers deep. Q is 1 and $F_R$ is down to 2.8.

Referring to the calculation of $F_R = 31.67$ on page 7, enter Fig. 15 with Q=5 and 3 layers. The resulting $F_R$ value agrees.

A third subdivision to 64 parallel wires with 1/8 the original diameter results in 640 total wires, 80 per layer, 8 layers. Q is 0.5 and $F_R$ finally reaches 1.5.

At the extreme right of Fig. 15 is the region where the conductor thickness is much greater then $D_{PEN}$ and $F_R$ is very large. The curves are parallel and have a +1 slope. On the extreme left, conductor thickness is much less than $D_{PEN}$ and $F_R$ approaches 1.0. In the center of the graph, the curves plunge downward as Q gets smaller. An $F_R$ of 1.5 is a good goal to achieve. With a much higher value, losses hurt too much. To go much below 1.5 is past the point of diminishing returns, requires much finer conductor sizes. Achieving $F_R$ of 1.5 requires a Q value ranging from 1.6 with 1 layer, to 0.4 with 10 layers.

Non-sinusoidal waveforms: Venkatramen[3] and Carsten[4] have applied Dowell's sine wave solution to various non-sinusoidal waveforms more relevant to switching power supplies. This is done by taking the Fourier components of the current waveform, then using Dowell's approach to calculate the loss for each harmonic and adding the losses. They have also redefined the way the data is presented in an attempt to make it more useful.

Starting with a conductor thickness much greater than $D_{PEN}$ and subdividing into smaller conductors usually makes $F_R$ worse before it gets better. For example, assume a single layer winding of 10 close spaced turns, and a Q of 4. $F_R$ from the Fig. 15 is 3.8 -- not good enough. If four parallel wires of half the diameter are

Their curves show that as the pulse width narrows, the effective ac resistance goes up because the higher frequency harmonics are more important. But the worst losses are not at narrow pulse widths. In most switching supplies, the peak pulse current is constant (at full load). The high frequency harmonics and losses are much the same regardless of pulse width, but the total rms, the dc and low frequency components get much worse as the pulse width widens. Worst case for total copper

Texas Instruments
R2-9
SLUP132

losses is probably near a duty ratio of 0.5.

In applications where current pulse widths in the vicinity of 0.5 duty ratio are the worst case conditions for copper losses, a shortcut method to achieve satisfactory results is to design the winding for an F<sub>R</sub> of 1.5 at the fundamental of the current waveform, then allow an extra 30-50% for additional losses due to the high frequency components.

## References

**[1]** D. G. Fink et al, *Electronics Engineer's Handbook*, McGraw-Hill, 1975

**[2]** P. L. Dowell, "Effects of Eddy Currents in Transformer Windings," *Proceedings IEE (UK)*, Vol. 113, No. 8, August, 1966, pp. 1387-1394.

**[3]** P. S. Venkatramen, "Winding Eddy Current Losses in Switch Mode Power Transformers Due to Rectangular Wave Currents," *Proceedings of Powercon 11*, 1984, Sec. A1.

**[4]** B. Carsten, "High Frequency Conductor Losses in Switchmode Magnetics," *High Frequency Power Converter Conference*, 1986, pp. 155-176

Texas Instruments
R2-10
SLUP132

# Appendix I -- Litz Wire

In switching power supply transformers, if the conductor thickness is similar to or greater than penetration (skin) depth at the operating frequency, ac current flows in only a portion of each conductor, resulting in high ac losses. This effect is magnified exponentially the more layers there are in the winding. To bring the ac losses back down to an acceptable level, the conductor thickness must be reduced.

Thin strip with a width equal to the winding width is often used, especially for low voltage, high current windings with few turns and large conductor area. Each turn is a layer and each turn must be insulated from the others. Strips cannot be subdivided into several paralleled thinner strips unless the individual strips are in different winding sections, otherwise unequal induced voltages will cause large eddy currents to circulate from one strip to another and losses will be high.

When strip or foil is not appropriate for a winding, the conductor can be divided into multiple strands of fine wire which are then connected in parallel at the terminations of the winding.

All wires in the group must be individually insulated and must encompass the identical flux to avoid eddy currents circulating from one wire to another through their terminating interconnections. If only a few wires in parallel are to be used, they can be laid together side-by-side (as though they were tied together as a flat strip). Each wire must have exactly the same number of turns as the other wires within each layer, to avoid cross-circulating eddy currents. This is not practical when large numbers of fine wires must be used.

Another solution is to interweave or twist the wires together in such a manner that each wire moves within the group to successively occupy each level within the field. But when this is done properly, voids are introduced, resulting in poor utilization of the available winding area compared with closely packed (untwisted) conductors.

Low power, high frequency Litz wire is usually woven from very fine wires, but the woven structure results in a large percentage of voids and poor copper utilization. Litz wire for power applications is usually made with a few wires twisted together in a strand and a few of these strands twisted into bigger strands, etc. The amount of twist required is moderate -- not enough to significantly increase the strand diameter or the length of the individual wires.

Consider a bundle of seven wires twisted into a strand, with one wire in the center. The packing structure is hexagonal -- as efficient as possible, with an outer surface which is almost circular. The amount of copper in this strand is .778 of a single solid wire with the same max. diameter as the strand. The outer six wires rotationally occupy each of the outside positions, but the center wire is fixed in its location. ac losses are actually improved by eliminating the seventh, inner wire. (In practice, it should be replaced by a non-conductive filler to maintain the shape of the strand.) This reduces the winding area utilization factor to .667 of the equivalent solid wire.

Even solid wire does not achieve 100% utilization of the winding area. The bottoms of the wires in each layer ride diagonally across the tops of the wires in the layer below, so they cannot pack down into the valleys between the wires below, except in a limited and unpredictable way. This means that round wire occupies the area of a square with sides equal to wire diameter, hence the utilization is $\pi/4$, or .785. If a six-wire strand described above is substituted for the solid wire, overall utilization is further reduced to $.785 \cdot .667 = .524$.

Table I shows the utilization factor of 3 to 6-wire strands. Although the utilization factors are quite similar, it will be shown that they do not perform equally well in achieving a multi-strand cable with a large number of wires.

## TABLE I
## Utilization Factor of Single Strands


<table>
  <thead>
    <tr>
        <th>Number of Wires:</th>
        <th>3</th>
        <th>4</th>
        <th>5</th>
        <th>6</th>
    </tr>
  </thead>
  <tbody>
    <tr>
        <td>Utilization Factor:</td>
        <td>.65</td>
        <td>.686</td>
        <td>.685</td>
        <td>.667</td>
    </tr>
  </tbody>
</table>

Texas Instruments
R2-11
SLUP132

It is not unusual to require *hundreds* of fine wires in parallel to achieve the required dc and ac resistances at 100 kHz or higher. This requires that strands be twisted into larger strands, and these twisted with each other, progressing to a cable containing the total number of fine wires needed to carry the desired high frequency current. The effective diameter of each strand is the circle of rotation of the outer extremities of the wires. Each level of twisting further reduces the utilization factor. As shown in Table II, much better utilization is achieved when more wires/strands are twisted together at one time, because fewer levels of twisting are required to achieve a similar number of wires.

For example, with 4 strands/twist, 4 wires twisted comprise a Level 1 strand, four Level 1 strands are twisted to obtain a Level 2 strand having 16 wires. Four Level 2 strands are then twisted resulting in a Level 3 strand with 64 wires, etc. Add levels until the desired number of wires is reached.

The utilization factors of Table II are further reduced by $\pi/4$ (.785) because round cable made according to Table II occupies a square portion of the winding space.

Instead of making up one cable containing all of the wires needed, it is often advantageous not to twist the final level. This may provide greater flexibility in fitting the winding to the

available breadth and height, and improves the utilization factor by eliminating one level of twisting.

For example, assume 256 wires of a given diameter are required. This could be achieved in one Level 4 cable using 4 strands/twist and 4 twist levels. The utilization is .22 compared with solid wire the same diameter as the cable, and $.22 \cdot .785 = .17$ of the winding space is copper. However if 4 Level 3 cables are used in parallel, the utilization is .32 compared to solid wire, and $.32 \cdot .785 = .25$ of the occupied winding area. Remember that each of the paralleled cables must have the same number of turns in each layer.

Insulation on the wires further reduces the utilization, especially with fine wires whose insulation is an increasing percentage of the wire area. With more and more turns of finer wire, the total area of the winding must increase if the desired copper area is maintained. When the maximum available window area is reached, improvement may still be obtained by going to more turns of finer wire, even though the dc resistance will increase, if the reduction in ac resistance is sufficient. Otherwise, the only solutions are: (a) Let the transformer run hotter, or (b) use a larger size core which will provide a bigger window (and fewer turns are usually required).

TABLE II

Utilization Factor vs. Twist Levels


<table>
  <thead>
    <tr>
        <th># Strands/Twist:</th>
        <th colspan="2">3</th>
        <th colspan="2">4</th>
        <th colspan="2">5</th>
        <th colspan="2">6</th>
    </tr>
    <tr>
        <th> </th>
        <th>Wires</th>
        <th>Util.</th>
        <th>Wires</th>
        <th>Util.</th>
        <th>Wires</th>
        <th>Util.</th>
        <th>Wires</th>
        <th>Util.</th>
    </tr>
  </thead>
  <tbody>
    <tr>
        <td>Level 1</td>
        <td>3</td>
        <td>.65</td>
        <td>4</td>
        <td>.69</td>
        <td>5</td>
        <td>.69</td>
        <td>6</td>
        <td>.67</td>
    </tr>
    <tr>
        <td>Level 2</td>
        <td>9</td>
        <td>.42</td>
        <td>16</td>
        <td>.47</td>
        <td>25</td>
        <td>.47</td>
        <td>36</td>
        <td>.44</td>
    </tr>
    <tr>
        <td>Level 3</td>
        <td>27</td>
        <td>.28</td>
        <td>64</td>
        <td>.32</td>
        <td>125</td>
        <td>.32</td>
        <td>216</td>
        <td>.30</td>
    </tr>
    <tr>
        <td>Level 4</td>
        <td>81</td>
        <td>.18</td>
        <td>256</td>
        <td>.22</td>
        <td>625</td>
        <td>.22</td>
        <td>1296</td>
        <td>.20</td>
    </tr>
    <tr>
        <td>Level 5</td>
        <td>243</td>
        <td>.12</td>
        <td>1024</td>
        <td>.15</td>
        <td> </td>
        <td> </td>
        <td> </td>
        <td> </td>
    </tr>
  </tbody>
</table>

Texas Instruments
R2-12
SLUP132

Oct 94

# Deriving the Equivalent Electrical Circuit from the Magnetic Device Physical Properties

### Lloyd Dixon

**Purpose:**

1. To define the electrical circuit equivalents of magnetic device structures to enable improved analysis of circuit performance.

2. To define the magnitude and location of relevant parasitic magnetic elements to enable prediction of performance effects

3. To manipulate parasitic elements to obtain improved or enhanced circuit performance

4. To encourage the circuit designer to be more involved with magnetic circuit design.

**Magnetic Definitions:**

Systeme International (SI) Units and Equations are used throughout this paper.

**Simplifying the Magnetic Structure:**

The first task is to take a magnetic device structure and reduce it to a few lumped elements — as few as possible for the sake of simplicity, because the equivalent electrical circuit will have just as many elements. This is not an easy task — just about everything is distributed, not lumped: the magnetic force from current in the windings, distributed flux, fringing flux adjacent to gaps, and stray fields. Boiling this down to a few elements with reasonable accuracy requires a little insight and intuition and experience — but it can be done.

Finite Element Analysis softwarc on the other hand is extremely accurate because it does just the opposite — it chops the structure up unto a huge number of tiny elements.<sup>[1]</sup> It is a useful tool which can provide a great deal of knowledge about what goes on inside the magnetic device, but it does not

provide a simple electrical equivalent circuit that lends itself to circuit analysis.

The magnetic structure shown in Figure 1 will be the first demonstration of this technique. This simple inductor is built upon a ferrite core, with air gaps to store the required inductive energy created by simply shimming the two core halves apart (not usually a good practice, but inexpensive).

![Magnetic structure of an inductor showing flux paths and windings](page_88_image_1_v2.jpg)

Fig 1. - Magnetic Structure - Inductor

The first thing to do is to simplify — judiciously. Looking at the inherent symmetry of the structure, the two outer legs can be combined into a single leg with twice the area. Fringing fields around the gaps will be ignored, except the effective gap area might be increased to take the fringing field into account.

The number of flux paths will be minimized, eliminating those that are trivial. For example, flux in the non-magnetic mateial adjacent to the core will be ignored, because it is trivial compared to the flux in the neighboring ferrite. On the other hand, if there were two windings, the small amount of flux between the windings must not be ignored — it constitutes the small but important leakage

Texas Instruments R3-1 SLUP132

inductance between the two windings.

The core will be divided into regions of similar cross-section and flux density. The distributed magnetic force from the winding will be lumped and assigned a specific location in the physical structure.

![Diagram of an ETD34 core with magnetic flux paths and calculations for maximum ampere-turns, energy storage, and gap length.](page_89_image_1_v2.jpg)

Fig 2. - Core Parameters and Utilization

For the purpose of illustration, the parameters of the core (ETD34) are given in Figure 2. The maximum ampere-turns obtainable is calculated from the window area times the max. current density in copper of $400A/cm^2$. The maximum flux at saturation equals the saturation flux density (0.25T) times the core area. From this, the maximum possible energy storage (in an appropriate gap) equals ½BH, for a total of 10mJ. The gap length required to achieve this full utilization is calculated as shown in Figure 2. These calculations are not relevant to the modeling process, but they help indicate the suitability of this core for the intended application.

**The Reluctance Diagram:** Next, a reluctance diagram will be created, modeling the physical structure. Reluctance is essentially magnetic impedance. It is a measure of the opposition to flux within any region of the magnetic device.

$$R = \frac{F}{\phi} = \frac{H\ell}{BA} = \frac{\ell}{\mu A}$$

The reluctance of each significant region of the device is calculated from its area, length and permeability, and inserted with its specific value into the appropriate location in the reluctance model, as shown in Figure 3. Again, because of inherent symmetry, the model can be simplified by

combining the two centerpost halves into a single element, likewise combining the outer leg portions on both sides of the gap. The magnetic field source, the ampere-turns of the winding, which is really a circulatory field is assigned to any discrete point where the flux is not divided. It would be incorrect to locate this source in series with the outer leg, because it would drive the flux in the stray field in the wrong direction.

![Simplified reluctance model diagram showing a magnetic circuit with reluctances Rc, Rcg, Ro, Rog, and Rs, along with formulas for calculating reluctance.](page_89_image_2_v2.jpg)

Fig 3. - The Simplified Reluctance Model

So the reluctance diagram includes the reluctance of the combined centerpost ferrite and also the centerleg gap, the combined outer leg ferrite and the outer leg gap, and the reluctance of the stray field outside the core (the calculation is an educated guess). This "magnetic circuit" can be analyzed just as though it were an electrical circuit. Remember that it is *not* an electrical circuit — reluctance is definitely not the same as resistance — it stores energy rather than dissipate it. But the reluctance diagram does follow the same rules as an electrical circuit, and the amount of flux in each path can be calculated based on the magnetic force and the reluctance.

Much can be learned by examining the reluctance model and playing "what if" games. Note that in each leg, the calculated gap reluctances are more than 100 times greater than the adjacent ferrite core legs. This indicates that the core reluctances could be eliminated, impairing accuracy by less than 1%. Note also that the flux in the stray field is actually larger than the flux in the outer leg of the core, because the stray field reluctance is less than the gap reluctance. This means that much noise is propagated outside the core, and the inductance

Texas Instruments
R3-2
SLUP132

value obtained depends heavily on the stray field, which is difficult to calculate. If the centerleg gap is eliminated and the outer leg gap correspondingly increase, the amount of stray field increases further.

On the other hand, if the outer leg gap is closed and the centerleg gap is widened, the stray field is almost eliminated, because the reluctance of the centerleg without gap is much less than the stray field reluctance. In this manner, the reluctance model is useful without even converting it to the equivalent electrical circuit.

# Magnetic-Electrical Duality:

Fifty years ago, E. Colin Cherry published a paper showing the duality between magnetic circuits and electrical circuits. [3] It is well know that two electrical circuits can be duals of each other — the Cuk converter is the dual of the flyback (buck-boost), for example. Electrical circuits that are duals are not therefore equivalent. Magnetic circuits and electrical circuits are in a different realm, and yet in this case *the duals are truly equivalent*.

A dual is created by essentially turning the circuit inside out and upside down. Some of the magnetic-electrical duality relationships and rules are:


<table>
  <thead>
    <tr>
        <th>Nodes</th>
        <th>Meshes (loops)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
        <td>Open</td>
        <td>Short</td>
    </tr>
    <tr>
        <td>Series Elements</td>
        <td>Parallel Elements</td>
    </tr>
    <tr>
        <td>Magn. Force</td>
        <td>Ampere-Turns</td>
    </tr>
    <tr>
        <td>dφ/dt</td>
        <td>Volts/turn</td>
    </tr>
    <tr>
        <td>Reluctance</td>
        <td>Permeance</td>
    </tr>
  </tbody>
</table>

**Polarity Orientation: Rotate in same direction**

**Circuits must be planar**

Permeance is the reciprocal of reluctance:

$$ P = \frac{1}{R} = \frac{\mu A}{l} $$

Permeance is actually the inductance for 1 turn. Multiply permeance by N<sup>2</sup> to obtain the inductance value referred to an N-turn winding.

Polarity Orientation means that for elements such as the windings that have polarity, to assign the proper polarity in the dual, rotate all polarity indications in the same direction from the original to the dual.

A **planar circuit** is defined as one that can be drawn on a plane surface with no crossovers. The duality process fails if there are crossovers, which can occur with complex core structures.<sup>[5]</sup> Actually, with only three windings on a simple core, if the reluctance model includes every theoretically possible flux linkage combination between windings, there will be crossovers. But most of these theoretical linkages are trivial, and should be ignored, for the sake of simplicity if nothing else. This is where common sense comes in.

**Creating the Dual:** The process for creating the electrical dual from the reluctance model is actually quite simple, as illustrated in Figure 4.

![Diagram showing the magnetic/electrical dual transformation with reluctance elements (RC, RO, RS, RCG, ROG) and flux paths overlaid with electrical nodes and dashed lines.](page_90_image_1_v2.jpg)

Fig 4. - The Magnetic / Electrical Dual

First, identify each mesh, or loop in the reluctance model. In this case there are 3 loops. (The outside is always considered a loop. Topologically a simple circle has two loops — the inside and the outside.) Put a dot in the center of each loop (any convenient location on the outside). These dots will be the nodes of the electrical circuit. Draw a dash line from electrical node to node though *every* intervening element. The dash lines are branches in the electrical circuit. The intervening elements become elements of the new circuit, but they are transformed: Reluctances become their reciprocal — permeances, the magnetic winding becomes the electrical terminals, with dφ1/dt translating into V1/N1 (Faraday's Law), and magnetic force translating into N1I1 in series with the terminals. Note that the 5 nodes in the original reluctance model are automatically converted into 5 loops in the electrical dual. (Don't forget the outside is a loop!)

Texas Instruments
R3-3
SLUP132

All of the values in the equivalent electrical circuit at this stage pertain to a one-turn winding. The electrical equivalent circuit is redrawn as shown in Figure 5:

![Equivalent electrical circuit diagram for a one-turn winding with associated formulas](page_91_image_2_v2.jpg)

Fig 5. - The Equivalent Electrical Circuit

If the winding has fifteen turns, permeances are converted to inductance values by multiplying by $15^2$. Likewise, terminal V/N is multiplied by 15 to become terminal voltage, and NI is divided by N to become terminal current. The final electrical equivalent circuit is shown below:

WITH N = 15 TURNS

![Final electrical equivalent circuit diagram with N = 15 turns](page_91_layout_ocr_ipyx_93_329_158_118.png)

Fig 6. - Final Electrical Equivalent Circuit

This simple example obviously produces a trivial result. There are five inductive elements which represent the five reluctances in the reluctance model. The five inductances combine to form a single inductance value of 10µH. But each of the five elements is clearly identifiable back to the reluctance it represents. Note that the series reluctances of the centerleg ferrite and centerleg gap show up as parallel inductances in Fig. 6, and the stray field reluctance which was in parallel with the outer leg are now series inductances. The circuit shows that the high inductance values contributed by the centerleg ferrite and outer leg ferrite are irrelevant in parallel with the much lower gap inductances. It shows that the stray field inductance makes a very significant contribution to the overall

inductance. But if the outer leg gap was closed up, its inductance would become infinite, making the stray field inductance irrelevant. The overall inductance would then equal the 14µH of the centerleg gap.

**A simple transformer:** A transformer with two windings is shown in Figure 7. The transformer has no gap — energy storage is undesirable. The flux between the two windings, although small, is very important because the energy contained between the windings constitutes leakage inductance.

![Diagram of a two-winding transformer with operational notes](page_91_image_3_v2.jpg)

Fig 7. - Two-Winding Transformer

Figure 8 is the reluctance model with specific values calculated for the same ETD34 core used in the previous example, but ungapped. The ampere turns in the two windings cancel except through the region between the windings ($R_{12}$). Thus, when the transformer is loaded, this is the only place the fields don't cancel, storing considerable leakage inductance energy as a function of load current.

![Transformer reluctance model diagram for ETD34 core with calculations](page_91_image_1_v2.jpg)

Fig 8. - Transformer Reluctance Model
Figure 9 goes through the duality process, and Figure 10 is the final result. In Fig. 10, an ideal

Texas Instruments
R3-4
SLUP132

transformer is added to one terminal pair to allow for a turns ratio other than 1:1, and to provide galvanic isolation.

![Diagram showing the transformer electrical dual with reluctance and electrical models](page_92_image_4_v2.jpg)

4 LOOPS, 4 NODES IN BOTH

Fig 9. - The Transformer Electrical Dual

WITH Np = 20 TURNS, Ns = 2 TURNS

![Transformer equivalent circuit diagram with values referred to primary](page_92_image_5_v2.jpg)

Fig 10. - Transformer Equivalent Circuit

**A Three-Winding Transformer:** Figure 11 is a three-winding transformer showing the physical structure and the equivalent electrical circuit. The reluctance model is not shown. The equivalent circuit model shows how the leakage inductances are distributed between windings and their magnitudes.

![Physical structure and equivalent circuit for a three-winding transformer](page_92_image_1_v2.jpg)

Fig 11. - Three-Winding Transformer

**Coupled Inductor:** Topic M7 in the Design Reference Section of the Seminar Manual describes the benefits of coupled filter inductors in multi-output buck regulators. Figure 12 shows the physical structure and resulting equivalent circuit which can provide insight into the design of this device.

![Physical structure of a coupled inductor with N1, N2 = 15 turns](page_92_image_6_v2.jpg)

![Equivalent circuit for a coupled inductor](page_92_image_7_v2.jpg)

Fig 12. - Coupled Inductor

**Fractional Turns:** Transformers with fractional turns have been featured in previous Seminars. Figure 13 provides insight into the design and behavior of this device.

![Diagrams and equivalent circuits for a transformer with fractional turns](page_92_image_2_v2.jpg)

Fig 13. - Transformer with Fractional Turns

**The Gyrator-Capacitor Approach:**

Another method for defining an equivalent electrical circuit of a magnetic device structure completely avoids the Reluctance/Duality approach that has been discussed up to this point.<sup>[4,5]</sup> The

Texas Instruments
R3-5
SLUP132

equivalent circuit layout achieved with the Gyrator-Capacitor follows exactly the pattern of the magnetic structure. This makes it somewhat easier to relate electrical performance back to the magnetic elements. A major advantage of this method is that it does not require that the magnetic circuit be "planar", as the Reluctance/Duality method does. Proponents of the Gyrator-Capacitor method cite these advantages.

However, the equivalent electrical circuit that results from this method looks nothing like a classical inductor or transformer. Inductive energy storage elements are replaced by capacitors (the electrical dual of inductance), and transformer windings are replaced by gyrators. (A gyrator is an ideal two-port element which one port reflects the reciprocal of the impedance at the other port, and scales the impedance according to a factor $r^2$.) In other words, the gyrators translate the *performance* of the equivalent circuit, employing capacitors, into its electrical dual, employing inductances, but one never actually sees the dualized equivalent circuit — the gyrators take care of it transparently. Figure 14 shows the equivalent circuit of a simple flyback converter modeled using the Gyrator-Capacitor method.

![Gyrator-Capacitor Model of a Forward Converter diagram showing magnetic structure and equivalent electrical circuit with gyrators and capacitors](page_93_image_1_v2.jpg)

Fig 14. - Gyrator-Capacitor Model of a Forward Converter

but it does not resemble the magnetic device physical structure, diminishing insight into the physical-electrical relationship, or

(2) An equivalent circuit with capacitos and gyrators replacing inductive elements whose layout closely resembles the structure of the magnetic device. This facilitates insight into the physical-electrical relationship, but severely diminishes insight into circuit analysis.

The author prefers to remain with the Reluctance/Duality method, but admits that it's probably a matter of what one is used to and more comfortable with.

## References:

[1] R. Severns, "Finite Element Analysis in Power Converter Design," *IEEE APEC Proc.* pp. 3-9, Feb. 1994

[2] Dauhajre and Middlebrook, "Modelling and Estimation of Leakage Phenomena in Magnetic Circuits," *IEEE PESC Record*, pp. 213-226, 1986

[3] E. C. Cherry, "The Duality Between Electric and Magnetic Circuits and the Formation of Transformer Equivalent Circuits," *Proc. Physical Soc. London*, Vol 62B pp.101-111, Feb. 1949

[4] D.C. Hamill, "Lumped Equivalent Circuits of Magnetic Components: The Gyrator-Capacitor Approach," *IEEE Trans. on Power Electronics*, vol. 8, no. 2, pp. 97-103, April 1993

[5] D.C. Hamill, "Gyrator-Capacitor Modeling: A Better Way of Understanding Magnetic Components," *IEEE APEC Proc.* pp. 326-332, Feb. 1994

So the choice is — do you prefer:

(1) A conventional electrical circuit whose magnetic elements include leakage and magnetizing inductances and transformer windings, etc. This facilitates intuitive and insightful circuit analysis,

Texas Instruments
R3-6
SLUP132

# THE EFFECTS OF LEAKAGE INDUCTANCE ON SWITCHING POWER SUPPLY PERFORMANCE

by

Lloyd H. Dixon, Jr.

## <u>INTRODUCTION.</u>

Leakage inductance is often the largest single factor in degrading the performance of a switching power supply. The effects of leakage inductance in buck and boost regulators differ markedly from flyback (buck-boost) circuits.

This paper describes the effects of leakage inductance on circuit losses, load regulation and cross-regulation with multiple outputs. Methods of minimizing leakage inductance in practical transformers and coupled inductors are discussed.

**<u>Forward Converter.</u>** The first example chosen is a forward converter with multiple outputs as shown in Figure 1. Transformer mutual inductance and leakage inductances are not shown. This two-transistor version facilitates non-dissipative clamping of the energy stored in these transformer inductances and also reduces transistor voltage rating requirements. The circuit of Figure 1 is the same as in the 250 Watt Forward Converter Design Review covered separately, with a second output, V<sub>2</sub>, providing 15 Volts at 3 Amperes in addition to the original 5 Volt, 50 Amp main output, V<sub>1</sub>.

![Schematic diagram of a forward converter with multiple outputs, showing input voltage VIN, transformer windings Np, N1, N2, and output voltages V1 and V2.](page_94_image_1_v2.jpg)

Figure 1. Forward Converter without Parasitic Inductances

In order to simplify the analysis, rectifier and transistor voltage drops are neglected. The effects of the parasitic inductances are most easily analysed in the equivalent circuit of Figure 2, in which the "ideal" transformer is eliminated. This is

Texas Instruments
R4-1
SLUP132

accomplished by normalizing the elements of the input and the #2 output according to their turns ratios with respect to the #1 main output:

![Forward Converter Equivalent Circuit Diagram](page_95_image_1_v2.jpg)

$$V_{IN}' = V_{IN}(N_1/N_p), \quad V_2' = V_2(N_1/N_2)$$
$$L_2' = L_2(N_1/N_2)^2, \quad C_2' = C_2(N_2/N_1)^2, \quad \text{etc.}$$

Figure 2. Forward Converter Equivalent Circuit

$L_m'$ is the normalized mutual inductance of the transformer. $L_{p1}$ is the leakage inductance between the primary and the main secondary, and $L_{12}'$ is the leakage inductance between main and #2 secondaries, all referred to the main secondary, $N_1$.

<u>**Operation with no Leakage Inductance.**</u> Circuit operation will first be examined with the assumptions that the leakage inductances $L_{p1}$ and $L_{12}'$ are zero, and the #2 output current, $I_2'$, is also zero. This is the basic buck regulator configuration with added mutual inductance, $L_m'$.

Referring to the waveforms of Figure 3, filter inductor current, $I_{L1}$, is the familiar triangular waveform superimposed upon the DC output current, $I_1$. $I_{L1}$ is carried entirely by rectifier $D_{A1}$ during the "on" time of the switching transistors, $t_{on}$, and free-wheels through $D_{A2}$ during the transistor "off" time. During $t_{on}$, voltage $V_{DB}$ at the input of the L-C filter equals $V_{IN}'$, but during the off time $V_{DB}$ is zero. The output voltage of an inductor input filter (with continuous inductor current) always equals the time averaged input voltage, therefore:

$$V_1 = V_{IN}'t_{on}/T \tag{1}$$

During $t_{on}$, the input voltage is impressed across the transformer causing a linearly increasing current, $I_{Lm'}$, through the mutual inductance. The maximum value of $I_{Lm'}$ at the end of $t_{on}$ is:

$$\max I_{Lm}' = V_{IN}'t_{on}/L_m' \tag{2}$$

Texas Instruments
R4-2
SLUP132

During $t_{on}$, normalized transistor current $I_{Q1}'$ is the sum of the filter inductor current, $I_{L1}$, and the mutual inductance current, $I_{Lm}'$. During the off time, $I_{Q1}'$ is zero. $I_{Lm}'$ cannot decrease instantaneously. This causes the voltage on $L_m'$ to reverse, forcing $I_{Lm}'$ to flow through the clamp diodes. Thus the energy which was stored in $L_m'$ will be recovered by pumping it back into the input source.

Since the reverse voltage across $L_m'$ equals $V_{IN}'$, $I_{Lm}'$ will decrease at exactly the same rate that it increased during the "on" time, thereby taking exactly the same time, equal to $t_{on}$, to reach zero again. This illustrates the fact that in order to reset the core each cycle, the reverse volt-seconds during


<table>
  <tbody>
    <tr>
        <td>Time</td>
        <td>IL1</td>
        <td>ID1A</td>
        <td>VDB</td>
        <td>VAB</td>
        <td>ILm'</td>
        <td>IQ1'</td>
        <td>ICLAMP</td>
    </tr>
    <tr>
        <td>0</td>
        <td>min</td>
        <td>0</td>
        <td>+VIn'</td>
        <td>0</td>
        <td>min</td>
        <td>min</td>
        <td>0</td>
    </tr>
    <tr>
        <td>ton</td>
        <td>max</td>
        <td>max</td>
        <td>+VIn'</td>
        <td>0</td>
        <td>max</td>
        <td>max</td>
        <td>0</td>
    </tr>
    <tr>
        <td>ton + reset</td>
        <td>mid</td>
        <td>0</td>
        <td>0</td>
        <td>-VIn'</td>
        <td>min</td>
        <td>0</td>
        <td>max</td>
    </tr>
    <tr>
        <td>end cycle</td>
        <td>min</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>min</td>
        <td>0</td>
        <td>0</td>
    </tr>
  </tbody>
</table>

Figure 3.

the "off" time must at least equal the volt-seconds during the "on" time. When the reverse clamp voltage is equal to the forward voltage, as in this case, the duty cycle must be limited to 50% maximum, otherwise $I_{Lm}'$ will continue to rise in subsequent cycles which will cause the core to saturate.

Normally, $I_{Lm}'$ will be less than 10% of the full load current through the switching transistors causing a negligible increase in transistor losses. Likewise, $I_{Lm}'$ has negligible effect upon the open loop line and load regulation. The energy stored in $L_m'$ can result in significant losses if dumped into dissipative clamps. However, this energy can be recovered by clamping to input or output, or otherwise put to good use such as providing auxiliary power for the control and drive circuits.

Using the transformer design of the 250 Watt Forward Converter Design Review as an example, the 92 turn primary and 6 turn secondary result in a turns ratio of 15.33. The minimum $V_{IN}$ of 200 Volts becomes 13 Volts $V_{IN}'$ referred to the secondary. Primary mutual inductance, $L_m$, is 25mH or a normalized $L_m'$ of 106uH referred to the secondary. From Equation 2, using a maximum $t_{on}$ of 12.5 usec (40 kHz operation), the maximum $I_{Lm}'$ is 1.5 Amps, negligible compared to the 50 Amp peak full load current in the secondary. The energy stored in $L_m'$ equals 5 Watts at 40 kHz. Most of this energy is not lost, but pumped back to the input.

<u>**Effects of Leakage Inductance with Single Output.**</u> Figure 4 shows the result of introducing a finite value of leakage inductance, $L_{p1}$, in the #1 main output. Assume $D_{2A}$ is open, completely disabling the #2 output.

Texas Instruments
R4-3
SLUP132

Lp1 has the effect of delaying the transfer of current between D1A and D1B at the beginning and end of the transistor "on" time. Referring to Figures 2 and 4, at the beginning of $t_{on}$, Lp1 prevents instantaneous transfer of the filter inductor current to D1A. D1B must continue to conduct a diminishing portion of the filter inductor current during time $t_1$ while the current through Lp1 and D1A rises to finally equal $I_{L1}$. The time required for this current transition, $t_1$, is simply:

$$t_1 = I_1 L_{p1} / V_{IN}' \quad (3)$$


![Waveforms showing current and voltage transitions in the circuit, including IL1, ID1A, ID1B, VDB, VAB, IQ1', and ICLAMP.](page_97_layout_ocr_lpwz_301_57_208_342.png)

Figure 4.

Although $V_{AB}$ jumps to $V_{IN}'$ at the very beginning of $t_{on}$, $V_{DB}$ remains at zero throughout $t_1$ because D1B remains conducting. With $t_{on}$ fixed (open control loop), output voltage $V_1$ is reduced by the volt-seconds represented in the shaded area averaged over cycle time, T. The open loop output voltage error is:

$$\Delta V_1 = V_{IN}' t_1 / T = V_{IN}' I_1 L_{p1} / V_{IN}' T = I_1 L_{p1} / T \quad [4]$$

Equation 4 shows that the output voltage error varies linearly with load current. Interestingly, the value $L_{p1}/T$ behaves just like an equivalent series resistance: "$R_{p1}$" = $L_{p1}/T$.

Energy is taken from the input source during $t_1$ and stored in $L_{p1}$:

$$W_{Lp1} = t_1 V_{IN}' I_1 / 2 = \frac{1}{2} L_{p1} I_1^2 \quad (5)$$

During time $t_c$, $L_{p1}$ delays transfer of current back to the free-wheeling rectifier, D1B. D1A and D1B both conduct during $t_c$, and $V_{DB}$ is zero. This has no effect on the output voltage since $V_{DB}$ is zero in any case at the end of $t_{on}$.

The voltage across $L_{p1}$ reverses during time $t_c$ in order to maintain its current flow. $V_{AB}$ becomes negative and the current from $L_{p1}$ flows through the clamp diodes (in addition to the mutual inductance current discussed previously). Thus, the energy stored in the leakage inductance is also recovered back to the input.

In summary, the leakage inductance between primary and secondary hurts the open loop load regulation, but this is not usually important because it is easily brought into spec by closing the the

Texas Instruments
R4-4
SLUP132

loop. The stored energy in the leakage inductance should either be recovered or put to good use, in exactly the same ways as the energy stored in the mutual inductance.

Continuing the 250 Watt Forward Converter example, the 92 turn primary consists of 4 layers of AWG19 wire, and the 6 turn secondary has 10 AWG18 wires in parallel to carry the high current. Assume the primary and secondary are not interleaved, that is, the entire primary is wound, then .01 cm insulation, then the entire secondary. Using the EC52 core, the primary to secondary leakage inductance, $L_{p1}$, referred to the secondary, is 0.52 uH. Applied to Equation 4, the open loop voltage error of the 5 Volt output will be 1.04 Volts at 50 Amp full load. For correction, a 20% increase in $t_{on}$ will be required under closed loop control. The energy stored in the leakage inductance at full load amounts to 26 Watts at 40 kHz, which will hopefully be recovered by clamping to the input.

If the primary is interleaved with the secondary, i.e., wind two layers of the primary, insulate, entire secondary, insulate, then the remaining 2 primary layers, $L_{p1}$ is reduced dramatically to 0.19 uH. Open loop output voltage error will be only .38 Volts and the energy stored equals 9.5 Watts at 40 kHz.

**<u>Effect on Cross-Regulation of Multiple Outputs.</u>** The waveforms of Figure 5 show the final step taken of drawing load current $I_2'$ from the #2 output and with a finite value of leakage inductance, $L_{12}'$, between secondaries.

$L_{12}'$ has the effect of causing an <u>additional</u> delay in the transfer of current between #2 output rectifiers $D_{2A}$ and $D_{2B}$. At the beginning of the "on" time, while current is increasing in $L_{p1}$, $D_{1A}$ and $D_{1B}$ are both conducting, holding voltage $V_{CB}$ to zero. This means that throughout time $t_1$ there is no voltage across $L_{12}'$ so that its current cannot start to increase. At the end of $t_1$, when the current through $L_{p1}$ finally equals $I_{L1}$, the current through $D_{1B}$ becomes zero and $V_{CB}$ is allowed to rise. Current through $L_{12}'$ and $D_{2A}$ then starts to increase toward $I_{L2}'$, throughout the interval $t_2$.

![Waveform diagrams showing currents ID1A, ID2A, voltages VDB, VFB, VAB, and current IQ1' with clamp current ICLAMP over time intervals t1 and t2.](page_98_layout_ocr_tmjx_295_326_208_394.png)

Figure 5.

Texas Instruments
R4-5
SLUP132

During $t_2$, $D_{2A}$ and $D_{2B}$ both conduct, sharing $I_{L2}'$. $V_{FB}$ is zero because $D_{2B}$ is conducting. The third waveform of Figure 5 shows that during $t_2$, $V_{FB}$ is zero but $V_{DB}$ is a positive value, the same as $V_{CB}$. The shaded areas represent the difference in volt-seconds applied to the inputs of the two filters. When averaged over the period $T$, this equates to a differential or cross-regulation voltage error between outputs 1 and 2. There is no way to correct for this error, other than by post-regulation.

To quantify this error we must know $V_{DB}$ and $t_2$. At the beginning of $t_2$, $V_{CB}$ is allowed to rise above zero and current through $L_{12}'$ starts to increase. This same increase in current must also occur through $L_{p1}$. Thus the two inductors are directly in series during $t_2$, so that the voltage across each is in direct proportion to its inductance value:

$$V_{DB} = V_{CB} = V_{L12'} = V_{IN}' L_{12}' / (L_{p1} + L_{12}')$$ (6)

$$t_2 = (L_{p1} + L_{12}') I_2' / V_{IN}'$$ (7)

$$\Delta V_{12}' = V_{DB} t_2 / T = I_2' L_{12}' / T$$ (8)

Note the similarity to Equation 4. The equivalent series resistance: "$R_{12}'$" = $L_{12}'/T$.

In the 250 Watt Forward Converter example using an EC52 transformer core, a portion of the window area allocated to the secondary will be used to add a 15 Volt, 3 Amp winding (45 Watts). Since 6 turns are used for the main 5 Volt winding, the 15 Volt output will require approximately 3 times as many, or 18 turns. It is important that the lower power 15 volt secondary should be wound <u>on top of</u> the higher power 5 Volt winding. The normalized leakage inductance between the secondaries will always be in series with the larger diameter winding because it has greater normalized inductance. Cross regulation voltage error is minimized, because the lower power output will have smaller normalized current changes through the leakage inductance.

The leakage inductance, $L_{12}'$ in series with the outer #2 secondary in the EC52 core is approximately 0.25 microHenries (normalized to the #1 winding). The cross regulation voltage error due to load changes in the 15 volt #2 output may be calculated using Equation 8 either normalized to the 5 volt #1 output or not normalized. The results are:

**Turns Ratio, n = $N_2/N_1$ = 18/6 = 3**
**Period T = 25 $\mu$sec**


<table>
  <thead>
    <tr>
        <th><u>Not Normalized</u></th>
        <th> </th>
        <th><u>Normalized</u></th>
    </tr>
  </thead>
  <tbody>
    <tr>
        <td>$V_2 = 15\text{ V}$</td>
        <td>$1/n$</td>
        <td>$V_2' = 5\text{ V}$</td>
    </tr>
    <tr>
        <td>$I_2 = 0-3\text{ A}$</td>
        <td>$n$</td>
        <td>$I_2' = 0-9\text{ A}$</td>
    </tr>
    <tr>
        <td>$L_{12} = 2.25\text{ }\mu\text{H}$</td>
        <td>$1/n^2$</td>
        <td>$L_{12}' = 0.25\text{ }\mu\text{H}$</td>
    </tr>
    <tr>
        <td>$\Delta V_{12} = 0.27\text{ V}$</td>
        <td>$1/n$</td>
        <td>$\Delta V_{12}' = .09\text{ V}$</td>
    </tr>
  </tbody>
</table>

It is worth mentioning a few additional points. In the example

Texas Instruments
R4-6
SLUP132

chosen, the leakage inductance between the secondaries is physically located in series with the low power #2 secondary. The effect of changing output #2 load current on cross-regulation has been demonstrated above. However, the cross-regulation due to changing #1 main output load is <u>theoretically perfect</u>. Both outputs will track each other perfectly when load #1 changes, and if #1 is closed loop regulated, both are regulated. This is because there is no intervening impedance to impair cross-regulation in series with the #1 output from the common feed point C in Figure 2. This is why it is important to locate this leakage inductance in series with the low power output which has less effect on cross-regulation.

Cross-regulation can be improved dramatically by winding the secondaries together (multifilar). That is, the wires of all secondaries are co-mingled in the same winding volume, rather than separate discrete secondaries wound on top of each other. This can make the leakage inductance between secondaries so small it becomes negligible. It is sometimes not practical to wind the secondaries multifilar, such as when copper foil is used for one or more secondaries.

It would be desireable to include the primary in the multifilar bundle to reduce the primary to secondary leakage inductance, but this is not practical in off-line applications because of the large turns ratio and the need for high voltage isolation between primary and secondaries.

Wiring inductance between the transformer secondaries and the filter inductor inputs (points D and F in Figure 2) has exactly the same effect as leakage inductance between secondaries; that is, wiring inductance has an adverse effect on cross-regulation. It is vital to minimize wiring lengths wherever the current is discontinuous. This is especially important with low voltage outputs and at higher power levels.

Be aware of the fact that after minimizing leakage and wiring inductances, the DC cross-regulation may be excellent, but the dynamic, or AC cross regulation will be pitifully bad if individual filter inductors are used in each output. This is true for any multiple output buck regulator, because a disturbance on any output is almost perfectly decoupled from all other outputs because of the high AC impedance of the filter inductors.

The solution to this problem is to put all output filter inductor windings on a common single core. This provides excellent AC coupling between the multiple outputs. The turns ratios between these windings must be the same as the voltage ratios between the respective outputs. The only problem with this technique is that slight offsets in voltage caused by rectifier forward drop variations will cause large circulating currents and output ripple at the switching frequency. The problem is solved by <u>deliberately introducing</u> a few percent of leakage inductance between the multiple windings of the filter inductor, which absorbs the voltage variations yet does not interfere significantly with the AC cross-coupling.

Texas Instruments
R4-7
SLUP132

Texas Instruments R4-8 SLUP132

# COUPLED FILTER INDUCTORS IN MULTIPLE OUTPUT BUCK REGULATORS

## PROVIDE DRAMATIC PERFORMANCE IMPROVEMENT

<u>Introduction:</u> When switching power supplies of the buck family (forward converter, full and half bridge, etc.) have more than one output as shown in Figure 1, separate filter inductors (L1, L2) are normally used in each output. These independent inductors hurt performance by decoupling and isolating the outputs from each other. Dynamic cross regulation is very poor and several other major problems are created because of the independent inductors. These problems are virtually eliminated if the inductors are coupled to each other by winding their separate coils on a single, common core [1].

Coupled filter inductors can provide additional benefits. Dramatic reduction in filter capacitance can be achieved by ripple current steering. Also, minimum load requirements can be reduced or even eliminated.

The coupled inductor technique is almost a panacea — designers who have mastered it are nearly unanimous in their acclaim. Its benefits far outweigh the few difficulties involved.

<u>Circuit Analysis with Independent Inductors:</u> The 180 Watt forward converter of Figure 1 has a 5V output and a 15V output (actually 15.8V intended to be post-regulated to 15V). A buck-derived regulator operated in the continuous inductor current mode, the DC output voltages must equal the time averaged voltages on the input side of their respective filter inductors. Using output #1 for example, with duty cycle D and with $V_{D1A} = V_{D1B} = V_{D1}$:

$$V_{o1} = (V_{in1} - V_{D1A}) \cdot D - V_{D1B} \cdot (1 - D) = V_{in1} \cdot D - V_{D1}$$ (1)

Note that there is always one rectifier in series with each inductor winding. As shown in (1), this results in a one-diode drop offset voltage from the ideal buck regulator relationship: $V_o = V_{in} \cdot D$. This has the same effect as single rectifier located in series with the output side of the inductor. Considering both outputs, the diode drop offset will be a larger proportion of the 5V output than the offset in the nominal 15V output. To correct for this offset error, the transformer turns ratio must differ slightly from the desired output voltage ratio.

![Schematic diagram of a Forward Converter with Two Outputs showing transformer, rectifiers D1A, D1B, D2A, D2B, inductors L1, L2, and output capacitors C1, C2.](page_102_image_1_v2.jpg)

Figure 1. Forward Converter with Two Outputs

Texas Instruments
R5-1
SLUP132

A well-designed control loop taken from the 5V output will provide good line regulation for both outputs and good load regulation for the controlled 5V output. The DC cross-regulation between the 5V and 15V outputs with load changes will be reasonably good if the transformer secondaries are tightly coupled and wiring inductance is minimized. Rectifier dynamic resistances and temperature coefficients are also significant factors in DC cross-regulation.

<u>**Disadvantages of Independent Inductors:**</u>

1. **Dynamic cross-regulation is very poor.** Output voltages will temporarily diverge from their DC levels when transient load changes occur. For example, a sudden load increase on the 15V output will cause its voltage to drop. This deviation must propagate through the high series impedance of inductor L2, the low shunt impedance of the input voltage source or free-wheeling rectifiers, and the high impedance of L1 in order to reach the controlled 5V output. As a result, the control loop is dynamically insensitive to load changes at the 15V output. It will keep the 5V output constant, but with large changes in load current, the 15V output will drop as much as 4 or 5 volts and take tens or hundreds of milliseconds to recover.

2. **Minimum load requirements.** Buck regulators are almost always designed to operate in the continuous inductor current mode, where the output voltage equals the average value of the chopped input voltage waveform, and the average inductor current equals the load current. A critical minimum load current must be sustained on each output, amounting to 1/2 the peak-peak ripple current through its filter inductor. Otherwise the inductor current tries to become negative at each minimum peak of the ripple current waveform, but it cannot because of the series rectifiers. The mode of operation becomes discontinuous and DC cross-regulation becomes very poor -- output voltages may diverge as much as 200-300%.

3. Each output should have independent current limiting to prevent saturation of the independent filter inductors under overload conditions.

4. Loop gain irregularities will occur because of interaction between the multiple outputs. With the transformer secondaries normally closely coupled, all outputs in the small-signal loop gain model are driven in parallel at the input of their respective filter inductors. One output is sensed for closed loop control. This controlled output is shunted by all the other outputs at the common driving point. The LC filters of these shunt outputs soak up much of the source current at their respective series resonant frequencies, causing reduced gain and significant phase shifts in the controlled output at these frequencies. This effect is especially severe with current mode control because of its characteristic high impedance at the driving point.

<u>**The Coupled Filter Inductor Circuit Approach:**</u> Refer again to the circuit of Figure 1, but consider that windings L1 and L2 are tightly coupled together on the same core. It is also vital that inductor windings L1 and L2 have exactly the same turns ratio as transformer secondary windings 1 and 2. This will be explained shortly.

From a DC standpoint, performance is identical to that described on the first page for independent inductors. Equation (1) applies, and the diode offset voltage problem and DC cross-regulation considerations are exactly the same.

Texas Instruments
R5-2
SLUP132

For a specific example, assume:

$$V_{D1A} = V_{D1B} = V_{D1} = 0.6V \text{ (Schottky); } V_{D2A} = V_{D2B} = V_{D2} = 1.0V \text{ (UES)}$$
$$Duty cycle, D = 0.4; V_{o1} = 5V; Turns ratio, n = N2/N1 = 3:1$$

The resulting circuit values apply with either independent or coupled inductors. Note how the disproportionate effect of the diode drops pushes the 15V output to 15.8 V:

$$V_{in1} = (V_{o1}+V_{D1})/D = 5.6V/0.4 = 14Vpk; V_{in2} = V_{in1} \cdot n = 14 \cdot 3 = 42Vpk$$

$$V_{o2} = V_{in2} \cdot D - V_{D2} = 42 \cdot 0.4 - 1.0 = 15.8V \text{ (for post regulation to 15V)}$$

During the time when the power MOS switch is ON:

$$V_{L1} = V_{in1}-V_{D1}-V_{o1} = 14-0.6-5 = 8.4V; V_{L2} = 42-1-15.8 = 25.2V$$

While the switch is OFF, the "B" rectifiers freewheel the inductor current:

$$V_{L1} = -V_{D1}-V_{o1} = -0.6-5 = -5.6V; V_{L2} = -1-15.8 = -16.8V$$

Note that during both the ON and OFF times, $V_{L2}$ is always exactly 3 times $V_{L1}$ (because the transformer turns ratio is 3:1 and $(V_{o2}+V_{D2})/(V_{o1}+V_{D1})$ is also 3:1). Therefore, the coupled inductor windings must also have the same 3:1 turns ratio or there will be a conflict between $V_{L1}$ and $V_{L2}$, which will cause a very large ripple current to circulate back and forth between the two output circuits. This will show up as a large ripple voltage across the highest impedance element in the circuit -- usually the output capacitor ESR, resulting in output ripple voltage much greater than expected. To prevent this from occurring, the transformer secondaries and corresponding inductor windings <u>must have identical turns ratios.</u>

**<u>Additional Problems and Limitations with the Coupled Inductor:</u>** If the "A" and "B" rectifiers in any output do not have identical forward drops, a voltage conflict is created similar to that caused by turns ratio inequality but much less severe. With tightly coupled inductor windings, output ripple voltage will increase by the amount of the rectifier mismatch. To solve this problem, it is not necessary to match each rectifier pair. A small amount of uncoupled leakage inductance or wiring inductance will provide enough series impedance to limit the mismatch induced ripple current. The corresponding ripple voltage will appear across the leakage inductance rather than at the output. As little as 2% leakage inductance will accomplish this purpose (it's hard to get much less than this). Try not to exceed 10% leakage inductance or dynamic cross-regulation will be impaired and spurious resonant conditions will be created.

Note that it is **<u>not</u>** necessary for the rectifier forward drops in one output to equal those in other outputs. Rectifier inequality between outputs causes a DC output voltage offset error, but does not increase ripple.

In addition, the timing of the waveforms across the transformer and coupled inductor windings must be identical in all outputs. Otherwise, voltage conflicts will occur during the times that the waveforms differ, causing very large current spikes to circulate between the outputs at these times. This means that independent secondary-side pulse width modulation cannot be used with coupled output inductors, ruling out the use of magnetic amplifier or Bisyn<sup>®</sup> PWM synchronous rectifier techniques for independent output regulation.

Texas Instruments
R5-3
SLUP132

# <u>Advantages of the Coupled Filter Inductor:</u>

1. AC cross-regulation is excellent because all outputs are dynamically coupled.

2. Large signal overshoot/undershoot is reduced because all outputs absorb or provide energy as necessary to support any output load change.

3. Although each output still requires a minimum load current greater than 1/2 the ripple current, the consequences of violating the critical minimum load current are less severe than with uncoupled inductors -- a 10 to 30% output voltage divergence vs. 200 to 300%

4. Simplified current limiting. A single primary side current limit will prevent inductor saturation, regardless of which output is overloaded.

5. Loop gain irregularities are eliminated because the coupled inductor is dynamically in common with all outputs combining them into a single circuit with one resonant frequency (unless leakage inductance is too large).

6. The single filter inductor is lower in cost and has smaller volume and mounting area compared with independent inductors.

## <u>Some Important Additional Advantages:</u>

5. The critical minimum load current required for each output can be adapted to suit the application. Most of the ripple current can be steered to the output with the most minimum load power, thereby reducing minimum load requirements on the other outputs.

6. Output filter capacitor size and cost can be reduced considerably by steering most of the ripple current to the highest voltage output, where capacitors are much more effective. This is because at a given frequency and power level, the filter capacitor impedance needed for a given % output ripple voltage increases with the output voltage <u>squared.</u> (How to steer the ripple current will be explained shortly.)

For example, if the filtering burden is placed on the 15V output by steering the ripple current there, filter capacitor impedance can be 3<sup>2</sup> or 9 times larger than needed at the 5V level -- for an electrolytic capacitor, ESR can be 9 times larger, and ESR is inversely proportional to volume, regardless of voltage rating. For a ceramic or film capacitor, 1/9 the C value is required, and C is proportional to volume and independent of voltage below 50-100V. In either case, by steering the ripple current to the 15V output instead of the 5V, the filter capacitor volume is reduced by a factor of 9, and cost by a comparable amount! The 5V output will still require a relatively small filter capacitor because of the small ripple current and switching noise spikes remaining in that output.

However, when the ripple current is steered to the highest voltage output, it may not have sufficient minimum load power to satisfy the critical minimum current requirement. This problem can be solved by sensing the load current in this output and if it drops to the critical level, switching in an additional dummy load. This takes care of the minimum load requirements of the entire supply. Another way to solve the minimum load problem is to use synchronous bi-directional switches instead of conventional rectifiers in this

Texas Instruments
R5-4
SLUP132

output. When the load current is less than 1/2 the peak-peak ripple current, the bi-directional switches will allow the inductor current to be negative at times during the switching cycle so that output voltage averaging and continuous mode operation is maintained even with no load.

7. With bi-directional switches instead of rectifiers, performance can be further optimized by steering most of the ripple current to a special high voltage "output" (really not an output in the normal sense) whose sole purpose is to provide the ultimate in cost-effective filtering. At the high voltage level (50V?), the capacitor required to handle the filtering task is <u>much</u> smaller (1/100?) and lower in cost. No minimum load is available at the high voltage level, but the bi-directional switches eliminate that requirement.

**<u>The Normalized Equivalent Circuit:</u>** These additional advantages of the coupled filter inductor and the principles of ripple current steering are more easily explained using a normalized equivalent circuit which reduces transformer and inductor windings to a 1:1 turns ratio and then combines all mutual elements. This equivalent circuit is intended to provide insight into instantaneous circuit behavior within the switching cycle. It is not comparable to the small signal state-space averaged models used for loop gain analysis at frequencies well below the switching frequency.

In the transformer driven circuit of Figure 1, secondary voltages $V_{in1}$ and $V_{in2}$ are positive values during the time the primary MOS switch is ON. During the OFF time, the voltages on all the transformer windings must be allowed to swing negative in order to reset the flux in the transformer core. Rectifiers D1A and D2A allow this negative swing to occur while the inductor freewheels its current through D1B and D2B.

Assuming D1A and D1B are matched and D2A and D2B are matched, the circuit of Figure 1 can be replaced by Figure 2. The transformer has been replaced by two pulse voltage sources whose voltages are identical to the transformer secondary voltages during the ON time, but are at zero during the OFF time instead of swinging negative. This permits the two rectifiers in each output to be replaced the single rectifiers D1 and D2. The two circuits function the same -- the voltage and current waveforms at the inductor inputs are identical and each inductor always has a series rectifier.

![Equivalent Sources circuit diagram](page_106_image_1_v2.jpg)

Fig 2 Equivalent Sources

The next step is to normalize the 15V output to the same impedance level as the 5V output. The actual transformer and inductor turns ratio, n, is 3:1. The 15V output is normalized to 5V by dividing its transformer and inductor turns by n, adjusting its voltages and current by n and impedances by $n^2$:

$$N2' = N2/n = N1$$

$$V_{in2}' = V_{in2}/n; \quad V_{D2}' = V_{D2}/n = 1/3 = .33V; \quad V_{O2}' = V_{O2} = 15.8/3 = 5.27V$$

$$I_{O2}' = I_{O2} \cdot n = 5 \cdot 3 = 15A; \quad L2' = L2/n^2; \quad C2' = C2 \cdot n^2; \quad ESR2' = ESR2/n^2$$

Texas Instruments
R5-5
SLUP132

Vin2' is now identical to Vin1, and can therefore be combined with it into the single source Vin1 as shown in Figure 3. Note how small V<sub>D2'</sub> is, reflecting its small proportionate effect on the 15V output. Note also that the power level of output #2 is the same as before. We can in fact think of output #2 as being at either the 15V level or the 5V level and translate back and forth according to the relationships established by the actual turns ratio. It doesn't matter to the inductor if the winding has 1/3 the turns at 3 times the current and 1/3 the voltage swings and 1/9 the circuit value of inductance.

![Circuit diagram showing normalized outputs with separate inductors L1 and L2' and diodes D1 and D2' on the input side.](page_107_image_3_v2.jpg)

Fig. 3 Normalized

In Figure 4, rectifiers D1 and D2' are moved to the output side of their respective inductor windings. This makes it clearer that the rectifiers simply act as DC offsets to the output voltage levels.

![Circuit diagram showing relocated diodes D1 and D2' to the output side of inductors L1 and L2'.](page_107_image_2_v2.jpg)

Fig. 4 Relocate Diodes

Figures 1 to 4 apply with either independent or coupled inductors. With independent inductors, Figure 4 is the final step in circuit simplification. However, if the inductors are coupled it is possible to go an important step further. In Figure 4, L1 and L2' have exactly the same normalized number of turns on the same core. Therefore they must have the same normalized mutual inductance values and the same induced volts/turn. Since they are directly connected on their input side, L1 and L2' can be combined into the single inductor L<sub>m</sub> as shown in Figure 5. But the coupling between the two outputs is never perfect because of leakage inductance between the windings and external circuit wiring inductance. L<sub>ℓ1</sub> and L<sub>ℓ2'</sub> represent the combined leakage and wiring inductance in each output, normalized to the 5V output level.

![Circuit diagram showing combined mutual inductance Lm with leakage inductances Ll1 and Ll2'.](page_107_image_1_v2.jpg)

Fig. 5 Combined Mutual Inductance

<u>Ripple Current Steering:</u> In a practical, well-designed multi-output buck regulator as shown in Fig. 5, mutual inductance L<sub>m</sub> is much greater than uncoupled inductances L<sub>ℓ1</sub> and L<sub>ℓ2'</sub>. These in turn have much higher impedance than the output capacitors (including ESR) at the switching frequency. So the total normalized ripple current to all outputs is determined almost entirely by L<sub>m</sub>. The total ripple current is apportioned between the normalized outputs by the uncoupled inductances L<sub>ℓ1</sub> and L<sub>ℓ2'</sub>. In other words, the ripple current can be steered to one output or the other or apportioned in any desired way according to the relative normalized values of the uncoupled inductances.

Texas Instruments
R5-6
SLUP132

If it is desired to steer most of the ripple current to the high voltage output, $L_{\ell 2}$ must be much smaller than $L_{\ell 1}$. Figure 6 gives a better view of this situation. The inductor should be designed to put the leakage inductance in series with the low voltage winding. This is accomplished by placing the high voltage inductor winding closest to the centerleg, with the low voltage winding immediately on top of it. In a well-designed inductor using ferrite E-E cores, the leakage inductance is usually less than 10% of the mutual inductance, and may be as low as 2% if the windings are interleaved. It will be greater than this with pot cores because of the poor window aspect ratio, and can be considerably less on a toroidal core.

![Circuit diagram showing ripple current steering with mutual and leakage inductances, diodes, capacitors, and ESR components.](page_108_chart_1_v2.jpg)

Fig 6 Ripple sent to #2

Effective ripple current steering and control can be achieved with uncoupled inductance values that are a very small fraction of the total inductance. In fact, uncoupled inductance should be kept as small as possible to avoid spurious resonances which can result in excessive phase shift and other closed loop problems. This means paying strict attention to minimizing wiring inductance as well as proper inductor design.

At frequencies above 100kHz, wiring inductance becomes a significant portion of the total uncoupled inductance and may in fact be larger than the leakage inductance in low voltage outputs. A comparable amount of wiring inductance in a high voltage output is much less significant than in a low voltage output. This is evident when the high voltage output is normalized to the low voltage level -- the wiring inductance is reduced by the square of the turns ratio. This makes it naturally easier to steer most of the ripple current to a high voltage output. Fortunately, this is where it is usually desired.

# Design Example -- 180 Watt Forward Converter:

* **Output #1**: 5 Volt, 20 Amp -- 100 Watts
* **Output #2**: 15.8 Volt, 5 Amp -- 80 Watts
* **(Normalized Output #2)**: 5.27 Volt, 15 Amp -- 80 W)

First, define the turns ratio for the transformer and coupled filter inductor. The number of turns should be proportional to the output voltages plus rectifier drops:

$$N2:N1 = (15.8+1):(5+0.6) = 16.8:5.6 = 3:1$$

The inductor windings are not required to have the same number of turns as the transformer secondaries, but they must have <u>identical turns ratios.</u>

Then, making the temporary assumption that the entire power output of the supply is concentrated in a single output (#1 - 5 Volts, 35 Amps, 180 Watts), the L and C values that would be required for this output are calculated.

The L value is calculated during the OFF time, when the inductor freewheels across the 5 volt output + 0.6 V rectifier drop. Assuming a maximum inductor

Texas Instruments
R5-7
SLUP132

Design the inductor with winding #1 outside #2. Leakage L in the 5V output #1 will approximate 700nH (10% of 7 µH) plus 100 nH wiring inductance for a total uncoupled inductance, $L_{l1} = 800\text{ nH}$. In output #2, leakage L is 0. Wiring L of 100 nH is divided by turns ratio 3:1 squared, so $L_{l2}'$ is only 11 nH.

$I_L$ distribution:
#1 = 6A · 11 / (800 + 11) = .08 A p-p
Normalized - #2 = 6A · 800 / (800 + 11) = 5.9 A p-p
Actual - #2 = 5.9A / 3 = 2 A p-p

<u>Critical min. load</u> on #1 output: .08/2 = <u>.04 A</u>; on #1 output: 2A/2 = <u>1 A</u>

Max. output voltage ripple = 1% p-p = .05V @ 5V ; .15V @ 15V

Capacitor requirements for 15V output #2:

$$C = \frac{\Delta I}{8f\Delta V} = \frac{2}{8 \cdot 0.1 \cdot .15} = 16.7\text{ \mu F}; \quad \text{ESR} = \Delta V / \Delta I = .15 / 2 = .075\text{ \Omega}$$

Capacitor requirements for 5V output #1 (Assume 0.5A p-p for safety margin):

$$C = \frac{\Delta I}{8f\Delta V} = \frac{0.5}{8 \cdot 0.1 \cdot .05} = 12.5\text{ \mu F}; \quad \text{ESR} = \Delta V / \Delta I = .05 / 0.5 = 0.1\text{ \Omega}$$

Using aluminum electrolytics, ESR requirements dominate. Capacitors used:

#2 Output: Panasonic HF 470µF, 25V, .07Ω, 1.7 cm dia. x 2.9 cm, $.63

#1 Output: Panasonic HF 1000µF, 10V, 0.1Ω, 1.3 cm dia. x 2.9 cm, $.44

If all ripple 6A p-p was in Output #1, 4 capacitors would be required:

Panasonic HF 2200 @ 16V, .008 Ω, (1.9 cm dia. x 3.6 cm)x4, Total cost $3.50

Refer to Design Reference Section M6 for the actual design of the coupled inductor. Start with the earlier temporary assumption and design a single winding inductor of 7 µH with a conductor area appropriate for 35 Amps. Then provide for the additional outputs by assigning part of the conductor and winding area to the other outputs in proportion to their relative power outputs. This will result in operation of all windings at the same current density and uniform distribution of power dissipated within the windings.

The #1 winding is actually only 20A, not 35A. Reduce its conductor area in proportion to this reduction in current. Its winding area will be reduced by the same proportion. The window area thus made available will exactly accommodate the #2 winding which has the same number of turns carrying 15A at the normalized 5V level. But with the 3:1 turns ratio, the actual 15V #2 winding will have 3 times the turns with 1/3 the conductor area for the same current density and same winding area. The measured inductance values of the windings will of course be proportional to the turns squared. In building the

Texas Instruments
R5-8
SLUP132

<u>Closing the Feedback Loop:</u> To avoid confusion, it is best to normalize all outputs to the one sensed for closed loop control, and draw the equivalent normalized circuit as shown in Figure 7. $L_{\ell 2}'$ is so small it is omitted. Note that mutual inductance $L_m$ with capacitor $C_2'$ is the main LC filter, but there are additional resonant LC circuits involved in the "downstream" lower voltage outputs such as $L_{\ell 1}$ and $C_1$. These spurious resonant circuits can cause ringing and instability unless their Q is less than 1. There are two cases to be considered:

If the first sequential output (in this case #2, 15V) is sensed for control, loop gain considerations are similar to a single output. The control loop will dampen the resonant circuit Q. This 15V output will be well controlled and regulated, but if downstream resonant circuit $L_{\ell 1}$-$C_1$ is underdamped under any load condition, the 5V output will exhibit shock-excited ringing at the $L_{\ell 1}$-$C_1$ resonant frequency. Make certain the downstream output is critically damped under all conditions.

![Small Signal Model circuit diagram](page_110_image_1_v2.jpg)

Fig. 7 Small Signal Model

If a downstream output such as #1, 5V is chosen to close the loop, there will be two (or more) LC circuits in cascade with two 180° phase lags which makes loop closing difficult, to say the least. Using current mode control eliminates inductor $L_m$ and its 90° phase lag which helps a lot. In addition, the downstream resonant circuit frequencies must be well above the loop gain crossover frequency and they must still be critically damped or their ringing will reflect into the upstream (#2, 15V) output.

In the design example, $L_m$ of 7 $\mu$H and $C_2'$ of $470 \cdot 3^2 = 4200 \mu$F resonate at 925 Hz, and the resonant impedances of L and C are .041 $\Omega$. Max. $ESR_2'$ is $.07 / 3^2 = .008 \Omega$, for a Q of $.041 / .008 = 5$, which will be reduced further by shunt load resistance and series rectifier dynamic resistance. If current mode control is employed, $L_m$ is absorbed in the equivalent current source and there is no longer a resonant condition. Then, if the loop gain crossover frequency is 10-20 kHz, the $L_m$-$C_2'$ phase shift will approach 90°.

In the downstream section, $L_{\ell 1}$ of 0.8 $\mu$H and $C_1$ of 1000 $\mu$F resonate at 5600 Hz with resonant impedances of .028 $\Omega$. Series $ESR_1$ of 0.1 $\Omega$ causes a heavily overdamped situation. Essentially, the capacitor ESR zero frequency of 1600 Hz is well below the resonant frequency and so this section behaves more like an L-R section, with 45° phase shift at 20 kHz, the $L_{\ell 1}$-$ESR_1$ pole frequency. This means the total phase shift is less than 135° up to 20 kHz, allowing the crossover frequency to be as high as 20 kHz if desired.

If it is necessary or desireable to raise the frequency and lower the Q of the downstream outputs, try hard to reduce the leakage and wiring inductances. (Large uncoupled inductance values are not needed to steer ripple currents and correct for rectifier mismatch.) A long stretched-out winding provides the lowest leakage inductance. For this reason, pot cores are poor, and toroidal

Texas Instruments
R5-9
SLUP132

cores are best of all. Leakage inductance may also be reduced by a factor of 3 or 4 by interleaving the coupled inductor windings. Split the high voltage winding into two series connected portions, each with half the total turns. Sandwich the entire low voltage winding between the two halves of the high voltage winding. The leakage inductance will be only 1/3 of the equivalent non-interleaved structure and it will appear in series with the low voltage (central) winding. In addition to the more leveraged wiring inductance of the low voltage output, this will steer most of the ripple current to the high voltage output where it is more easily and effectively filtered.

When the ripple current is steered to a high voltage output and/or at high frequencies, ceramic or film capacitors often become cost-effective in place of electrolytic capacitors, with ceramics offering considerable reduction in size. However, with an electrolytic capacitor, the ESR requirement dictates the capacitor size and the resulting C value is huge compared to the actual C requirement. This has one big advantage. The large C value results in a low L/C ratio and output surge impedance, making the output much stiffer when loop bandwidth is low. Even with high loop gain-bandwidth, under large signal conditions which inevitably occur at start-up and with large, rapid load changes, considerable output voltage over/undershoot will occur because of the much smaller C values of the ceramic or film capacitors.

In addition, if ceramic or film capacitors are used in the downstream outputs (which may be feasible and desirable because ripple current is much less than with independent inductors), the smaller C values with almost zero ESR will substantially raise the Q and resonant frequency and of these "downstream" resonant circuits. This worsens the output and loop gain stability problems mentioned earlier (lowering uncoupled inductance helps, but lowering C and eliminating ESR hurts).

In the design example, C1 could have been a 12.5 μF ceramic or film capacitor. The Lm-C1 resonant frequency would then be 50 kHz, with a resonant impedances of 0.25 Ω and no ESR to lower the Q. With minimum shunt load R of 0.25 Ω, this section is critically damped only under full load conditions, and Q will become quite large with light load. This is not acceptable. Although the resonant frequency is well above the highest possible loop gain crossover frequency, this Ll1-C1 section will cause shock-excited ringing at 50 kHz between the two outputs, no matter which is controlled. One solution to this problem might be to shunt the 12.5 μF capacitor with a 220 μF, 10 V electrolytic whose ESR of 0.22 Ω will keep the Q less than 1.

**REFERENCE:**

1. H. Matsuo and K. Harada, "New Energy Storage DC-DC Converter with Multiple Outputs," Solid State Power Conversion, Nov. 1978, pp 54–56.

<u>ADDENDUM 9/88 - Positive and Negative Outputs.</u> In Figure 1 with windings L1 and L2 coupled, suppose diodes D2A and D2B are reversed to provide -15.8 V output. The polarity of L1 must be opposite L2, otherwise the voltage waveforms across the windings will conflict catastrophically. The polarities may be reversed by driving the two coils from opposite ends, but this will generate considerable noise spikes in the outputs because the noisy end of each winding is physically close to — and therefore capacitively coupled to — the output end of the other winding. This problem can be eliminated by driving all windings from the same end, but reversing the rotational direction of the negative current windings vs. those with positive current, i.e., plus current windings could be "right-handed", while minus current windings are wound "left-handed". This is the approach to use when plus and minus outputs are taken from the same transformer secondary.

Referring again to Figure 1 (original diode polarities) with two positive outputs, the two windings are driven from the same end and there is no output noise problem. However, because the two transformer secondaries are independent, the 15.8 V output can be made negative simply by grounding the plus output terminal rather than the minus terminal. Thus, the coupled inductor sees "positive" current in the negative output and all windings are polarized the same.

Texas Instruments
R5-10
SLUP132

# HOW TO DESIGN A TRANSFORMER WITH FRACTIONAL TURNS

## Lloyd H. Dixon, Jr.

Fractional turns used in high frequency switching power supply transformers can reduce the number of turns otherwise needed to provide low voltage outputs and to obtain desired voltage resolution between several outputs. With fractional turns, half the number of turns or less may be required in all windings, significantly decreasing transformer size and cost. Unfortunately, fractional turns have inherently high leakage inductance, making their use impractical unless special techniques are employed. Several methods of accomplishing this are described.

<u>The Need for Fractional Turns:</u> The optimum number of turns in a transformer winding depends upon the maximum allowable flux swing and the operating frequency according to Faraday's Law (in SI units with dimensions in cm):

$$N_{(optimum)} = (V_N \Delta t / A_e \Delta B) \cdot 10^4$$

where $\Delta B$ is the flux swing (Tesla), $A_e$ is the centerleg area (cm$^2$), and $\Delta t$ is the time (approaching 1/2 the period) that voltage $V_N$ is across the winding.

In switching power supplies designed to operate at frequencies below 50 kHz, the optimum numbers of turns are so large that there is little need to use fractional turns. At higher frequencies, fractional turns become attractive for the following two reasons:

1. Optimum transformer design may call for less than one full turn for the lowest voltage secondary. This is likely to happen at high frequencies, high power levels, and especially with the 2 to 3 volt outputs required by the newer logic families.

2. With multiple secondaries, to obtain the desired output voltages with sufficient accuracy using integral turns may require several times the optimum number of turns. For example, with a 12 V and 5 V output, a turns ratio of 2.5:1 or 2.25:1 may be desired. If 1 turn is optimum for the 5 Volt output, 3 turns will provide too much voltage for the 12 Volt output, causing excessive losses in a linear post-regulator. Otherwise, 5 and 2 turns or 9 and 4 turns are necessary to achieve the desired voltage resolution.

In these examples, the actual number of turns required in all windings may be 2, 3, or 4 times greater than optimum. Slightly larger wire sizes are required because the larger transformer must operate at lower current density. This means the winding window area will be 2, 3, or 4 times larger and the core and transformer volume will be 2.8, 5.2, or 8 times larger, with a corresponding increase in cost. This can be a powerful incentive to use fractional turns!

<u>Implementing a Fractional Turn:</u> A fractional turn is really a full turn around a fraction of the total centerleg flux. With an E-E core shape having two outer legs of equal areas, each outer leg has 1/2 the total flux. A single turn around either outer leg will have an induced voltage equal to 1/2 the primary volts/turn. Such a turn is therefore equivalent to 1/2 turn. In

Texas Instruments
R6-1
SLUP132

![Diagram of a transformer core with three legs labeled 2, 1, and 3, showing windings A and B.](page_113_image_3_v2.jpg)

Figure 1A

![Diagram of a cross-shaped transformer core with windings labeled A, B, and C.](page_113_image_1_v2.jpg)

Figure 1B

Figures 2A and 2B show a transformer with multiple outer legs and its magnetic circuit equivalent. A single "fractional" turn is shown which encloses one or more (but not all) outer legs which are combined into leg #3 with magnetic cross-section area $A_3$ and permeance $P_3 = \mu A_3 / \ell_3$. The remaining outer leg(s) are collectively leg #2 with area $A_2$ and permeance $P_2$.

![Schematic diagram of a transformer with primary winding Np, secondary winding Ns, and a fractional turn F.](page_113_layout_ocr_ngya_136_274_169_149.png)

Figure 2A

![Magnetic circuit equivalent diagram showing permeances P1, P2, P3 and fluxes $\phi_1$, $\phi_2$, $\phi_3$, with an MMF source NpIm.](page_113_image_2_v2.jpg)

Figure 2B

With no secondary current, centerleg flux $\phi_1$ divides between outer legs #2 and #3 in proportion to their permeances and their areas (assuming magnetic lengths $\ell_3$ and $\ell_2$ are the same). Let $F = P_3 / (P_2 + P_3) = A_3 / (A_2 + A_3)$, the fraction of the total outer leg area enclosed by the fractional turn. This turn encloses a corresponding fraction of the total flux, $\phi_3 = F \cdot \phi_1$, and $d\phi_3/dt = F \cdot d\phi_1/dt$. From Faraday's law, the induced volts/turn equals the rate of change of the enclosed flux, so the voltage induced in the fractional turn equals $F$ times the primary volts/turn, $V_{in}/N_p$.

The full secondary turns around the centerleg and the primary turns link the same flux $\phi_1$ so that their volts/turn are nearly identical: $V_s/N_s = V_{in}/N_p$. Thus:

$$V_{out}/V_{in} = (N_s + F) / N_p \quad \text{(no load)}$$

Primary magnetizing ampere-turns $N_p I_m$ provide the magnetic potential needed to support the flux level in the core.

Texas Instruments
R6-2
SLUP132

<u>The Leakage Inductance Problem:</u> The full secondary turns are tightly coupled to the primary, although there is a small amount of leakage inductance in series with the full secondary turns due to stray flux between the windings. Unfortunately, the fractional turn has very high leakage inductance, and its induced voltage, $F \cdot V_{in}/N_p$, occurs only under no-load conditions.

When load current is drawn through the fractional turn, its voltage collapses. In fact, when a fractional turn is added to an otherwise stiff winding, the short-circuit current will probably be much less than the desired full load output current. Rather than helping matters, the performance of the winding is worsened by adding the fractional turn because of its leakage inductance.

As shown in Figure 3, secondary current through the full turns around the centerleg generates a magnetic potential, $N_s I_s$, which is cancelled by equal and opposite primary ampere-turns, $N_p I_p$. Magnetizing current, $I_m$, and centerleg flux, $\phi_1$, do not change significantly. However, current through the fractional turn creates a magnetic potential in leg #3 which easily diverts flux $\phi_3$ to leg #2. Because flux $\phi_3$ is diminished, the voltage induced in the fractional turn is reduced. So the fractional turn voltage decreases rapidly with increasing load. At higher load current levels (usually well below desired full load), $d\phi_3/dt$ will reverse and the voltage induced in the fractional turn becomes negative. When this happens, the total secondary voltage is less than it would have been without the fractional turn.

![Diagram of magnetic circuit with fluxes and MMF sources](page_114_image_1_v2.jpg)

Figure 3

The leakage inductance of the fractional turn is:

$$L = F(1-F) \cdot P = F(1-F) \cdot \mu A/\ell \cdot 10^{-2} \text{ Henrys}$$

$\ell$ (cm) - length of the outer legs
$A = A_2+A_3$ (cm$^2$) - combined areas of all outer legs
$F = A_3/A$ - fraction of total outer leg area linked to fractional turn
$\mu = \mu_o \mu_r = 4\pi \cdot 10^{-7} \cdot \mu_r$ - absolute permeability of the outer leg material
$P = P_2+P_3 = \mu A/\ell$ - permeance of all outer legs combined

This inductance of the fractional turn is equivalent to the inductance of a single turn wound on a core consisting of legs #2 and #3 in series. (Leg #1 has no effect.) The worst case is when the fractional turn links half the total outer leg area (effectively 1/2 turn). Whether the fractional turn is in series with one or more full turns around centerleg #1, or whether it is the entire secondary winding, it has the same leakage inductance. However, when the fractional turn is in series with several full turns, the power taken from it is only a small portion of the total transformer power. The adverse effect of the leakage inductance is then proportionately less, but it is more than enough to badly hurt cross-regulation in a multi-output supply.

Texas Instruments
R6-3
SLUP132

<u>The Solution to the Problem:</u> The solution is simple -- maintain the flux in outer leg portions #2 and #3 in exactly the same ratio regardless of secondary current; in other words prevent the flux from escaping from leg #3 to leg #2 when the load current increases.

One technique used to keep the flux balanced in the two outer legs of an E-E core is to put one turn around <u>each</u> outer leg as shown in Figure 4. The two outer core legs have the same area (and permeance). Each of these turns links half the centerleg flux and acts like a half turn. If these turns were

connected in series with the correct polarity, together they would become a full turn. But connected in parallel (with the same polarity) they act together like a single half-turn. Because of the parallel connection, the voltages induced across each turn must be identical, forcing equal flux in the two outer legs. This requires the opposing magnetic potentials in each outer leg to be the same ampere-turns which means the secondary current is shared equally by the two turns.

![Diagram of an E-E core with parallel turns around outer legs for flux balancing.](page_115_image_1_v2.jpg)

Figure 4

If the two outer legs had unequal flux, the voltages induced in the two paralleled turns would differ. This would cause a differential current to flow between these turns, applying magnetic potentials to each leg in a direction to eliminate the original flux inequality. Essentially, the cross-connection between the two turns forces the flux to divide equally between the two outer legs.

Note that even if the two outer legs have <u>different areas</u>, the flux in each leg is forced to be half the total flux, so that the paralleled turns still act like half turns.

While this technique eliminates the huge leakage inductance of a single half turn, it is far from ideal because there is much stray flux outside the core which is linked to the primary but not to the windings around the outer legs. This results in significant leakage inductance. Normally, to minimize leakage inductance caused by stray flux, good practice dictates the secondaries should be wound as intimately as possible with each other and with the primary.

Figure 5 shows a big improvement on the above technique which provides much better coupling to the primary, minimizing the leakage inductance of the half

turn secondary. Two half cylinders of copper foil or strip are placed directly over the primary winding, separated only by the minimum insulation required for primary-secondary isolation. The half cylinders must not directly contact each other. They are paralleled by means of a pair of tabs off one end of each half cylinder, cross-connected over the outside end of the core. Output from the winding may be taken from across this pair of tabs.

![Diagram showing copper foil half cylinders over the primary winding to minimize leakage inductance.](page_115_image_3_v2.jpg)

Figure 5

Texas Instruments
R6-4
SLUP132

The series inductance of this half turn approach is not quite as good as one full turn of copper strip because of the inductance of the cross-connected tabs. Further reduction in series inductance may be obtained by putting cross-connected tabs at <u>both</u> ends. The ultimate improvement is to divide the primary into two portions and interleave the secondary structure between the two primary portions.

Because the cross-connected half turns in Figure 5 force equal flux division, the outer legs are "stiffened", so that a half turn added to any other secondary(s) will also have low leakage inductance.

<u>Using a Separate Flux Balancing Winding:</u> Any windings that cross-connect the two outer legs will force the flux to divide equally between the two outer legs. It is not even necessary for the flux balancing winding to be one of the output windings. As shown in Figure 6, it may be a completely separate winding dedicated to the sole purpose of flux equalization between the outer legs. This enables a single wire half-turn to be added to <u>any</u> secondary with minimal series inductance by forcing the total flux to remain equally divided between the two outer legs.

This technique is useful when fractional turns are added to more than one secondary, and especially with the center-tapped secondaries used in push-pull converters, where a fractional turn must be added each side of center-tap. These situations are difficult to implement by the method shown in Figure 5.

![Diagram showing a separate flux balancing winding with cross-connected coils on the outer legs of a transformer core.](page_116_layout_ocr_eepn_376_283_170_54.png)

Figure 6

As shown in Figure 6, the flux balancing winding has two coils with equal numbers of turns cross-connecting the two outer legs at the point where they join the centerleg. Actually, this winding can be a single turn on each outer leg or many turns. It is better to use multiple turns because finer wire can then be used. By laying these fine wire turns side by side along the outer legs, interference with the bobbin is minimized, and eddy current problems are eliminated.

The ampere-turns of the flux balancing winding will be 1/2 the unbalanced amperes of the secondary half-turns. For example, assume two secondaries, 12 V, 3 A and 24 V, 2 A, each having a half turn in series with several other full turns. If the 3 A and 2 A half turns link the same outer leg, the worst case ampere-turns in the flux balancing winding will be (3+2)/2 = 2.5 A. With five turns on each outer leg, the current in each turn is 2.5/5 = 0.5 A. On the other hand, if the 2 A and 3 A half turns link to opposite legs, the worst case is with the 3 A secondary at full load and the 2 A secondary at no load. The maximum flux balancing ampere-turns will be half of 3, or 1.5 A-t, resulting in only 1.5/5 = 0.3 A in the five turn flux balance windings.

For this method of flux balancing to be the most effective in reducing leakage inductance, the flux balancing winding must have good coupling to the secondary half turn(s):

* Wind the flux balancing coils on the outer legs as close as possible to where the flux divides - close to the centerleg. If they are located further out on the outer legs, coupling to the secondary half turns on the centerleg is reduced.

Texas Instruments
R6-5
SLUP132

2. With a secondary half turn in series with several full turns wound helically along the centerleg, make sure this half turn is at the end of the centerleg adjacent to the flux balancing winding.

3. When the half turn is foil or strip along the length of the centerleg, put a flux balance winding at <u>both</u> ends of the centerleg.

4. When a secondary handles most of the total transformer power and has only 1/2 turn or 1 1/2 turns total, the method of Figure 5 works the best.

<u>Diverse Fractional Turn Values:</u> It is certainly possible to obtain fractional turn values other than 1/2. Referring back to Figure 1B, a cross core with four outer legs can provide 1/4, 1/2, or 3/4 turns. A slightly different technique is required to keep the flux divided equally among all <u>four</u> legs--a single flux balancing turn is put around each of the four legs and these four turns are paralleled. Because of the parallel connection, the voltages induced across each turn must be equal, which forces equal rates of flux change in each leg. Otherwise, current would flow in the flux balancing turns which would bring the flux changes back into equality.

In reference (1), the author cleverly provides the flux balancing winding by means of a double sided printed circuit board at one end of the centerleg where it interferes minimally with the transformer windings. Although this is a very simple and low cost method, the flux balancing turns are not close to the centerleg and the coupling to the secondary half turns is not as good as it might be. Also, cross cores are generally not optimally designed for high frequency power applications where a long narrow winding window is desirable to minimize leakage inductance and eddy current losses.

<u>Obtaining Any Fractional Value with an E-E Core:</u> It was stated earlier that the flux balancing winding would force equal flux in the outer legs even if they have unequal areas. Conversely, it is easy to obtain any desired induced voltage in the fractional turn by forcing unequal flux division between the two outer legs, even though their areas are equal. This makes it possible to take advantage of the better performance and cost available with modern E-E cores.

Unequal flux division between two outer legs of equal area is obtained by using unequal turns in the flux balancing windings. Suppose there are twice as many turns on leg #3 as on leg #2. The induced voltage across both windings must be equal because they are in parallel. This means the volts/turn and $d\phi_3/dt$ of leg #3 must be 1/2 of leg #2. Therefore 1/3 of the total flux goes to leg #3 with twice the turns, while 2/3 goes to leg #2.

Any secondary fractional turn linked to leg #3 will have only 1/3 of the primary volts/turn induced, while a fractional turn linked to leg #2 will have 2/3 of the primary volts/turn. Similarly, a 1:3 turns ratio in the flux balancing winding will result in a 1/4 : 3/4 flux division and corresponding fraction of the primary volts/turn induced in a fractional turn. Depending upon which leg is linked by the fractional turn, 1/4 turn or 3/4 turn is obtained. It is possible to obtain 1/2 turn in this configuration by putting one additional turn around the 1/4 turn leg!

Texas Instruments
R6-6
SLUP132

When the flux division is made unequal between two outer legs of equal area, obviously one outer leg has greater flux density (and flux swing) than the other, and probably greater flux density than the centerleg, as well. This could theoretically force a reduction in the operating flux level and reduce the core utilization to avoid saturating the high flux density leg. However, fractional turns will normally be used above 50-100 kHz, where the flux density swing is limited by core losses, not saturation. The only adverse result is that one outer leg will have greater core loss, the other leg less, for a net small increase in core loss.

<u>**Experimental Results:**</u> The data given in Table I was taken with a 20 turn primary winding over the centerleg of an EC41 ferrite core. Secondaries were placed directly over the primary (not interleaved) with 5 mil insulation in between. Leakage inductance was measured on the primary side with the various secondary configurations shorted because it is difficult to obtaining accurate measurements on the 1/2 turn low impedance secondary side. Equivalent secondary leakage inductance with the primary shorted was calculated from the measured primary values.

# TABLE I

<table>
  <thead>
    <tr>
        <th>Description</th>
        <th>Measured Primary</th>
        <th>Calculated Secondary</th>
        <th> </th>
    </tr>
  </thead>
  <tbody>
    <tr>
        <td>(1) Primary only (20 turns) -- no secondary</td>
        <td>1480. μH</td>
        <td>--</td>
        <td> </td>
    </tr>
    <tr>
        <td>(2) 1 Full turn copper strip secondary</td>
        <td>1.6 μH</td>
        <td>1 nH</td>
        <td>(Ideal)</td>
    </tr>
    <tr>
        <td>(3) 1 Half turn strip - no flux bal. wdg.</td>
        <td>944 μH</td>
        <td>885 nH</td>
        <td> </td>
    </tr>
    <tr>
        <td>(4) Same with flux bal. opposite tab end</td>
        <td>144 "</td>
        <td>91 "</td>
        <td> </td>
    </tr>
    <tr>
        <td>(5) Same with flux bal. wdg. at tab end</td>
        <td>38 "</td>
        <td>24 "</td>
        <td> </td>
    </tr>
    <tr>
        <td>(6) 2 Par. half turns, outer leg (Figure 4)</td>
        <td>42 μH</td>
        <td>26 nH</td>
        <td> </td>
    </tr>
    <tr>
        <td>(7) 2 Par. half turns over primary (Figure 5)</td>
        <td>8 "</td>
        <td>5 nH</td>
        <td> </td>
    </tr>
    <tr>
        <th> </th>
        <th> </th>
        <th> </th>
        <th>Measured Secondary</th>
    </tr>
    <tr>
        <td>(8) 5 turn wire sec. spread across centerleg</td>
        <td>2.9 μH</td>
        <td>181 nH</td>
        <td>185 nH</td>
    </tr>
    <tr>
        <td>(9) 5 1/2 turn secondary - no flux bal. wdg.</td>
        <td>17.5 "</td>
        <td>1320 "</td>
        <td>1580 "</td>
    </tr>
    <tr>
        <td>(10) Same with flux bal. opposite end</td>
        <td>4.2 "</td>
        <td>317 "</td>
        <td>307 "</td>
    </tr>
    <tr>
        <td>(11) Same with flux bal. same end</td>
        <td>2.8 "</td>
        <td>211 "</td>
        <td>207 "</td>
    </tr>
  </tbody>
</table>

Line (1) of Table I shows the open circuit primary inductance of 20 turns on the EC41 core. Line (2) demonstrates the lowest leakage inductance that can be obtained without interleaving the secondary between two primary half-sections. Dividing the 1.6 μH measured primary value by $(20/.5)^2$ gives 1 nH lowest possible leakage inductance for 1/2 turn - the ideal goal. (3) shows how bad a single half turn strip is without a flux balancing winding. Adding flux balancing opposite the tab end of the half turn (4) provides much improvement, but at the tab end (5) coupling between flux balance winding and the half turn is much better. Still, 24 nH is a long way from the 1 nH goal. It is just not possible for the flux balance winding at the one end of the centerleg to couple more effectively to the half turn along its entire length.

Line (6) shows the technique of Figure 4, with one turn of strip around each outer leg. The large amount of stray flux between these turns and the primary cause high leakage inductance. Best is (7), with the two half-cylindrical strips directly over the primary. Most of the 5 nH is in the cross-connected

Texas Instruments
R6-7
SLUP132

tabs at one end, and this could be further reduced by putting tabs at both ends. This is the best approach when most of the transformer power is in the half-turn (or 1 1/2 turn) winding.

Lines (8) - (11) show the results of adding a half turn to several full secondary turns, using wire instead of strip. The secondary impedance levels are high enough to take measurements from the secondary side as well. (8) shows that the 5 full turn secondary does not couple as tightly to the primary as the shorted strip in (2). This is because the 5 turns were spread across the centerleg with large spaces between turns (but this is much better than bunching the 5 turns in the center of the primary). Several parallel wires should have been used to fill the centerleg. The 185 nH is almost twice what it should be compared to (2). Note that with the additional half turn placed at the same end of the centerleg as the flux balance winding (11) the coupling is good and the additional leakage inductance of the half turn is only 22 nH. This compares to the half turn secondary alone in (5), but in (11) it is small by comparison to the leakage inductance of the 5 full secondary turns.

<u>**References:**</u>

1. G. Perica, "Elimination of Leakage Effects Related to the Use of Windings with Fractions of Turns," Proceedings of Power Electronics Specialists Conference (PESC), 1984, pp. 268-278

*Texas Instruments* | R6-8 | SLUP132

# WINDING DATA

## WIRE TABLE — Copper Wire — Heavy Insulation:


<table>
<thead>
<tr>
<th>AWG</th>
<th>DIAMETER</th>
<th>AREA</th>
<th>DIAMETER</th>
<th>AREA</th>
<th>OHMS/CM</th>
<th>OHMS/CM</th>
<th>AMPS</th>
</tr>
<tr>
<th> </th>
<th>Copper cm</th>
<th>Copper cm²</th>
<th>Insulatd cm</th>
<th>Ins. cm²</th>
<th>20 C</th>
<th>100 C</th>
<th>for 450A/cm²</th>
</tr>
</thead>
<tbody>
<tr>
<td>10</td>
<td>.259</td>
<td>.052620</td>
<td>.273</td>
<td>.058572</td>
<td>.000033</td>
<td>.000044</td>
<td>23.679</td>
</tr>
<tr>
<td>11</td>
<td>.231</td>
<td>.041729</td>
<td>.244</td>
<td>.046738</td>
<td>.000041</td>
<td>.000055</td>
<td>18.778</td>
</tr>
<tr>
<td>12</td>
<td>.205</td>
<td>.033092</td>
<td>.218</td>
<td>.037309</td>
<td>.000052</td>
<td>.000070</td>
<td>14.892</td>
</tr><tr>
<td>13</td>
<td>.183</td>
<td>.026243</td>
<td>.195</td>
<td>.029793</td>
<td>.000066</td>
<td>..000088</td>
<td>11.809</td>
</tr><tr>
<td>14</td>
<td>.163</td>
<td>.020811</td>
<td>.174</td>
<td>.023 800</td>
<td>.000083</td>
<td>.000111</td>
<td>9.365</td>
</tr><tr>
<td>15</td>
<td>.145</td>
<td>.016504</td>
<td>.156</td>
<td>.019021</td>
<td>.000104</td>
<td>.000140</td>
<td>7.427</td>
</tr><tr>
<td>16</td>
<td>.129</td>
<td>.013088</td>
<td>.139</td>
<td>.015207</td>
<td>.000132</td>
<td>.000176</td>
<td>5.890</td>
</tr><tr>
<td>17</td>
<td>.115</td>
<td>.010379</td>
<td>.124</td>
<td>.012164</td>
<td>.000166</td>
<td>.000222</td>
<td>4.671</td>
</tr><tr>
<td>18</td>
<td>.102</td>
<td>.008231</td>
<td>.111</td>
<td>.009735</td>
<td>.000209</td>
<td>.000280</td>
<td>3.704</td>
</tr><tr>
<td>19</td>
<td>.091</td>
<td>.006527</td>
<td>.100</td>
<td>.007794</td>
<td>.000264</td>
<td>.000353</td>
<td>2.937</td>
</tr><tr>
<td>20</td>
<td>.081</td>
<td>.005176</td>
<td>.089</td>
<td>.006244</td>
<td>.000333</td>
<td>.000445</td>
<td>2.329</td>
</tr><tr>
<td>21</td>
<td>.072</td>
<td>.004105</td>
<td>.080</td>
<td>.005004</td>
<td>.000420</td>
<td>.000561</td>
<td>1.847</td>
</tr><tr>
<td>22</td>
<td>.064</td>
<td>.003255</td>
<td>.071</td>
<td>.004013</td>
<td>.000530</td>
<td>.000708</td>
<td>1.465</td>
</tr><tr>
<td>23</td>
<td>.057</td>
<td>.002582</td>
<td>.064</td>
<td>.003221</td>
<td>.000668</td>
<td>.000892</td>
<td>1.162</td>
</tr><tr>
<td>24</td>
<td>.051</td>
<td>.002047</td>
<td>.057</td>
<td>.002586</td>
<td>.000842</td>
<td>.001125</td>
<td>.921</td>
</tr><tr>
<td>25</td>
<td>.045</td>
<td>.001624</td>
<td>.051</td>
<td>.002078</td>
<td>.001062</td>
<td>.001419</td>
<td>.731</td>
</tr><tr>
<td>26</td>
<td>.040</td>
<td>.001287</td>
<td>.046</td>
<td>.001671</td>
<td>.001339</td>
<td>.001789</td>
<td>.579</td>
</tr><tr>
<td>27</td>
<td>.036</td>
<td>.001021</td>
<td>.041</td>
<td>.001344</td>
<td>.001689</td>
<td>.002256</td>
<td>.459</td>
</tr><tr>
<td>28</td>
<td>.032</td>
<td>.000810</td>
<td>.037</td>
<td>.001083</td>
<td>.002129</td>
<td>.002845</td>
<td>.364</td>
</tr><tr>
<td>29</td>
<td>.029</td>
<td>.000642</td>
<td>.033</td>
<td>.000872</td>
<td>.002685</td>
<td>.003587</td>
<td>.289</td>
</tr><tr>
<td>30</td>
<td>.025</td>
<td>.000509</td>
<td>.030</td>
<td>.000704</td>
<td>.003386</td>
<td>.004523</td>
<td>.229</td>
</tr><tr>
<td>31</td>
<td>.023</td>
<td>.000404</td>
<td>.027</td>
<td>.000568</td>
<td>.004269</td>
<td>.005704</td>
<td>.182</td>
</tr><tr>
<td>32</td>
<td>.020</td>
<td>.000320</td>
<td>.024</td>
<td>.000459</td>
<td>.0053 &4</td>
<td>.007192</td>
<td>.144</td>
</tr><tr>
<td>33</td>
<td>.018</td>
<td>.000254</td>
<td>.022</td>
<td>.000371</td>
<td>.006789</td>
<td>.009070</td>
<td>.114</td>
</tr><tr>
<td>34</td>
<td>.016</td>
<td>.000201</td>
<td>.020</td>
<td>.000300</td>
<td>.008560</td>
<td>.011437</td>
<td>.091</td>
</tr><tr>
<td>35</td>
<td>.014</td>
<td>.000160</td>
<td>.018</td>
<td>.000243</td>
<td>.010795</td>
<td>.014422</td>
<td>.072</td>
</tr><tr>
<td>36</td>
<td>.013</td>
<td>.000127</td>
<td>.016</td>
<td>.000197</td>
<td>.013612</td>
<td>.018186</td>
<td>.057</td>
</tr><tr>
<td>37</td>
<td>.011</td>
<td>.000100</td>
<td>.014</td>
<td>.000160</td>
<td>.017165</td>
<td>.022932</td>
<td>.045</td>
</tr><tr>
<td>38</td>
<td>.010</td>
<td>.000080</td>
<td>.013</td>
<td>.000130</td>
<td>.021644</td>
<td>.028917</td>
<td>.036</td>
</tr>
<tr>
<td>39</td>
<td>.009</td>
<td>.000063</td>
<td>.012</td>
<td>.000106</td>
<td>.027293</td>
<td>.036464</td>
<td>.028</td>
</tr>
<tr>
<td>40</td>
<td>.008</td>
<td>.000050</td>
<td>.010</td>
<td>.000086</td>
<td>.034417</td>
<td>.045981</td>
<td>.023</td>
</tr>
<tr>
<td>41</td>
<td>.007</td>
<td>.000040</td>
<td>.009</td>
<td>.000070</td>
<td>.043399</td>
<td>.057982</td>
<td>.018</td>
</tr>
</tbody>
</table>

## <u>American Wire Gauge (AWG) Table Formulae:</u>

* **$D_X = \frac{2.54}{\pi} 10^{-AWG/20}$ cm**: Conductor Diameter
* **$D_X' = D_X + .028 / \sqrt{D_X}$ cm**: Includes Heavy Insulation
* **$A_X = \pi D_X^2 / 4$ cm²**: Wire Cross-Section Area
* **$R_X = \rho / A_X$ $\Omega$/cm**: Resistance/Length

Texas Instruments | R7-1 | SLUP132

Texas Instruments	R7-2	SLUP132

# TI Worldwide Technical Support

## Internet

**TI Semiconductor Product Information Center Home Page**
support.ti.com

**TI E2E™ Community Home Page**
e2e.ti.com

## Product Information Centers

* **Americas** Phone: +1(972) 644-5580
* **Brazil** Phone: 0800-891-2616
* **Mexico** Phone: 0800-670-7544
* **Fax**: +1(972) 927-6377
* **Internet/Email**: support.ti.com/sc/pic/americas.htm

## Europe, Middle East, and Africa

**Phone**
* **European Free Call**: 00800-ASK-TEXAS (00800 275 83927)
* **International**: +49 (0) 8161 80 2121
* **Russian Support**: +7 (4) 95 98 10 701

**Note**: The European Free Call (Toll Free) number is not active in all countries. If you have technical difficulty calling the free call number, please use the international number above.

* **Fax**: +(49) (0) 8161 80 2045
* **Internet**: support.ti.com/sc/pic/euro.htm
* **Direct Email**: asktexas@ti.com

## Japan

* **Phone** (Domestic): 0120-92-3326
* **Fax** (International): +81-3-3344-5317
* **Fax** (Domestic): 0120-81-0036
* **Internet/Email** (International): support.ti.com/sc/pic/japan.htm
* **Internet/Email** (Domestic): www.tij.co.jp/pic

## Asia

* **Phone** (International): +91-80-41381665
* **Phone** (Domestic): <u>Toll-Free Number</u>
  * **Note**: Toll-free numbers do not support mobile and IP phones.
  * **Australia**: 1-800-999-084
  * **China**: 800-820-8682
  * **Hong Kong**: 800-96-5941
  * **India**: 1-800-425-7888
  * **Indonesia**: 001-803-8861-1006
  * **Korea**: 080-551-2804
  * **Malaysia**: 1-800-80-3973
  * **New Zealand**: 0800-446-934
  * **Philippines**: 1-800-765-7404
  * **Singapore**: 800-886-1028
  * **Taiwan**: 0800-006800
  * **Thailand**: 001-800-886-0010
* **Fax**: +8621-23073686
* **Email**: tiasia@ti.com or ti-china@ti.com
* **Internet**: support.ti.com/sc/pic/asia.htm

> **Important Notice**: The products and services of Texas Instruments Incorporated and its subsidiaries described herein are sold subject to TI’s standard terms and conditions of sale. Customers are advised to obtain the most current and complete information about TI products and services before placing orders. TI assumes no liability for applications assistance, customer’s applications or product designs, software performance, or infringement of patents. The publication of information regarding any other company’s products or services does not constitute TI’s approval, warranty or endorsement thereof.

A122010

E2E is a trademark of Texas Instruments. All other trademarks are the property of their respective owners.

![Texas Instruments logo](page_122_image_1_v2.jpg)

SLUP132

# IMPORTANT NOTICE

Texas Instruments Incorporated and its subsidiaries (TI) reserve the right to make corrections, enhancements, improvements and other changes to its semiconductor products and services per JESD46, latest issue, and to discontinue any product or service per JESD48, latest issue. Buyers should obtain the latest relevant information before placing orders and should verify that such information is current and complete. All semiconductor products (also referred to herein as “components”) are sold subject to TI’s terms and conditions of sale supplied at the time of order acknowledgment.

TI warrants performance of its components to the specifications applicable at the time of sale, in accordance with the warranty in TI’s terms and conditions of sale of semiconductor products. Testing and other quality control techniques are used to the extent TI deems necessary to support this warranty. Except where mandated by applicable law, testing of all parameters of each component is not necessarily performed.

TI assumes no liability for applications assistance or the design of Buyers’ products. Buyers are responsible for their products and applications using TI components. To minimize the risks associated with Buyers’ products and applications, Buyers should provide adequate design and operating safeguards.

TI does not warrant or represent that any license, either express or implied, is granted under any patent right, copyright, mask work right, or other intellectual property right relating to any combination, machine, or process in which TI components or services are used. Information published by TI regarding third-party products or services does not constitute a license to use such products or services or a warranty or endorsement thereof. Use of such information may require a license from a third party under the patents or other intellectual property of the third party, or a license from TI under the patents or other intellectual property of TI.

Reproduction of significant portions of TI information in TI data books or data sheets is permissible only if reproduction is without alteration and is accompanied by all associated warranties, conditions, limitations, and notices. TI is not responsible or liable for such altered documentation. Information of third parties may be subject to additional restrictions.

Resale of TI components or services with statements different from or beyond the parameters stated by TI for that component or service voids all express and any implied warranties for the associated TI component or service and is an unfair and deceptive business practice. TI is not responsible or liable for any such statements.

Buyer acknowledges and agrees that it is solely responsible for compliance with all legal, regulatory and safety-related requirements concerning its products, and any use of TI components in its applications, notwithstanding any applications-related information or support that may be provided by TI. Buyer represents and agrees that it has all the necessary expertise to create and implement safeguards which anticipate dangerous consequences of failures, monitor failures and their consequences, lessen the likelihood of failures that might cause harm and take appropriate remedial actions. Buyer will fully indemnify TI and its representatives against any damages arising out of the use of any TI components in safety-critical applications.

In some cases, TI components may be promoted specifically to facilitate safety-related applications. With such components, TI’s goal is to help enable customers to design and create their own end-product solutions that meet applicable functional safety standards and requirements. Nonetheless, such components are subject to these terms.

No TI components are authorized for use in FDA Class III (or similar life-critical medical equipment) unless authorized officers of the parties have executed a special agreement specifically governing such use.

Only those TI components which TI has specifically designated as military grade or “enhanced plastic” are designed and intended for use in military/aerospace applications or environments. Buyer acknowledges and agrees that any military or aerospace use of TI components which have not been so designated is solely at the Buyer's risk, and that Buyer is solely responsible for compliance with all legal and regulatory requirements in connection with such use.

TI has specifically designated certain components as meeting ISO/TS16949 requirements, mainly for automotive use. In any case of use of non-designated products, TI will not be responsible for any failure to meet ISO/TS16949.


<table>
  <thead>
    <tr>
        <th>Products</th>
        <th> </th>
        <th>Applications</th>
        <th> </th>
    </tr>
  </thead>
  <tbody>
    <tr>
        <td>Audio</td>
        <td>www.ti.com/audio</td>
        <td>Automotive and Transportation</td>
        <td>www.ti.com/automotive</td>
    </tr>
    <tr>
        <td>Amplifiers</td>
        <td>amplifier.ti.com</td>
        <td>Communications and Telecom</td>
        <td>www.ti.com/communications</td>
    </tr>
    <tr>
        <td>Data Converters</td>
        <td>dataconverter.ti.com</td>
        <td>Computers and Peripherals</td>
        <td>www.ti.com/computers</td>
    </tr>
    <tr>
        <td>DLP® Products</td>
        <td>www.dlp.com</td>
        <td>Consumer Electronics</td>
        <td>www.ti.com/consumer-apps</td>
    </tr>
    <tr>
        <td>DSP</td>
        <td>dsp.ti.com</td>
        <td>Energy and Lighting</td>
        <td>www.ti.com/energy</td>
    </tr>
    <tr>
        <td>Clocks and Timers</td>
        <td>www.ti.com/clocks</td>
        <td>Industrial</td>
        <td>www.ti.com/industrial</td>
    </tr>
    <tr>
        <td>Interface</td>
        <td>interface.ti.com</td>
        <td>Medical</td>
        <td>www.ti.com/medical</td>
    </tr>
    <tr>
        <td>Logic</td>
        <td>logic.ti.com</td>
        <td>Security</td>
        <td>www.ti.com/security</td>
    </tr>
    <tr>
        <td>Power Mgmt</td>
        <td>power.ti.com</td>
        <td>Space, Avionics and Defense</td>
        <td>www.ti.com/space-avionics-defense</td>
    </tr>
    <tr>
        <td>Microcontrollers</td>
        <td>microcontroller.ti.com</td>
        <td>Video and Imaging</td>
        <td>www.ti.com/video</td>
    </tr>
    <tr>
        <td>RFID</td>
        <td>www.ti-rfid.com</td>
        <td> </td>
        <td> </td>
    </tr>
    <tr>
        <td>OMAP Applications Processors</td>
        <td>www.ti.com/omap</td>
        <td>TI E2E Community</td>
        <td>e2e.ti.com</td>
    </tr>
    <tr>
        <td>Wireless Connectivity</td>
        <td>www.ti.com/wirelessconnectivity</td>
        <td> </td>
        <td> </td>
    </tr>
  </tbody>
</table>

Mailing Address: Texas Instruments, Post Office Box 655303, Dallas, Texas 75265
Copyright © 2014, Texas Instruments Incorporated