# Inductor Design Inputs

## Scope

This page defines the input contract needed before designing a power inductor for a converter topology. It applies to buck output inductors, boost inductors, input/filter inductors, buck-boost or flyback inductors, and coupled output filter inductors. Flyback transformers are included only where they behave as energy-storage coupled inductors rather than true transformers. [source: TI SLUP132 §5 Inductor and Flyback Transformer Design] [source: TI SLUP132 §2 Core Limitations in SMPS Applications]

The required inputs come from the converter electrical design first. The magnetic design then turns those inputs into core size, gap or effective permeability, turns, conductor choice, losses, and temperature rise. [source: TI SLUP132 §5 Design Strategy] [source: Hurley & Wolfle Ch. 3 §3.2]

## GIC

### Geometry

The inductor geometry is a single winding or coupled winding set on a gapped or distributed-gap core. Required geometry data includes effective core area $A_e$, window area $A_w$, magnetic path length $l_e$, core volume $V_e$, mean length per turn $MLT$, gap length or effective permeability, and usable window factor $k_u$. [source: Erickson & Maksimovic Ch. 11 §11.1.2-§11.1.5] [source: Hurley & Wolfle Ch. 3 §3.2]

### Input

The converter must provide inductance value $L$ or ripple-current target, full-load current, worst-case peak-to-peak ripple current $\Delta I_{pp}$, maximum peak instantaneous short-circuit current $I_{SCpk}$, switching frequency, operating mode, allowed loss, and allowed temperature rise. [source: TI SLUP132 §5 Design Strategy]

### Constraint

The finished inductor must satisfy required inductance, avoid saturation at the specified peak current, keep core loss and winding loss inside the allowed loss budget, fit the winding into the usable window, and meet the allowed temperature rise. [source: Erickson & Maksimovic Ch. 11 §11.1 opening paragraphs] [source: Hurley & Wolfle Ch. 3 eq. 3.5, 3.8, 3.24, 3.35]

## Minimum Input Checklist

| Input group | Required inputs |
| --- | --- |
| Converter identity | Topology name, conversion class, magnetic role, isolation requirement, number of outputs, and whether the inductor is a filter inductor, boost inductor, input inductor, flyback/buck-boost inductor, coupled output inductor, EMI choke, or DC choke. [source: /magnetics-wiki-schema.md §3] [source: TI SLUP132 §5 Inductor and Flyback Transformer Design] |
| Operating mode | CCM, DCM, boundary mode, fixed-frequency operation, variable-frequency operation, and any light-load mode transitions. TI lists these mode distinctions explicitly for boost/PFC inductors. [source: TI SLUP132 §5 Boost Inductor] |
| Voltage waveform at the inductor | Voltage across the inductor during each switching interval, duration of each interval, duty-cycle limits, and the worst-case input/output voltage condition that maximizes ripple. Turns and flux swing are set from the volt-second relation $E = N A_e\,dB/dt$ and $E = L\,\Delta I/\Delta t$. [source: TI SLUP132 §5 Design Strategy eq. 5] |
| Inductance or ripple target | Target inductance $L$, or allowed $\Delta I_{pp}$ from output/input ripple and control requirements. TI begins the inductor design process with $L$ and worst-case ripple current; Erickson and Maksimovic describe the buck inductor value as being selected so ripple is a small fraction of full-load DC current. [source: TI SLUP132 §5 Design Strategy] [source: Erickson & Maksimovic Ch. 11 §11.1 opening paragraph] |
| Current set | Full-load DC current $I_{FL}$, average current, RMS current, AC ripple current, peak current, minimum current, overload current, and $I_{SCpk}$. The current set must match the actual waveform for the topology and operating mode. [source: TI SLUP132 §5 Design Strategy] [source: TI SLUP132 §5 Flyback Transformer Design eq. 10-12] |
| Frequency and timing | Switching frequency or frequency range, ripple frequency, duty-cycle range, on/off times, and line-frequency sweep for PFC or rectified-line applications. [source: TI SLUP132 §4 Topology] [source: TI SLUP132 §5 Boost Inductor] |
| Loss and thermal limits | Absolute loss limit, allowed temperature rise, ambient temperature, cooling method, thermal resistance if known, and whether the loss budget is split between core loss and winding loss. [source: TI SLUP132 §5 Design Strategy] [source: TI SLUP132 §4 Losses and Temperature Rise] |
| Core operating limits | Candidate material, $B_{max}$, allowed $\Delta B$, saturation margin, core-loss curve or core-loss model, and whether the design is saturation-limited or loss-limited. [source: TI SLUP132 §5 Design Strategy] [source: Erickson & Maksimovic Ch. 10 §10.3.1] |
| Core geometry candidates | Core family/shape, $A_e$, $A_w$, $V_e$, $l_e$, $MLT$, center-pole dimension for gap fringing, manufacturer $A_L$ data, and available gap or effective-permeability options. [source: TI SLUP132 §5 Design Strategy] [source: Hurley & Wolfle Ch. 3 §3.2] |
| Winding constraints | Allowed window fill $k_u$, conductor type, current density target, maximum DC resistance, AC resistance target, layer count, insulation thickness, creepage/clearance if isolation or safety spacing applies, and termination constraints. [source: Erickson & Maksimovic Ch. 11 eq. 11.10-11.13] [source: Hurley & Wolfle Ch. 3 eq. 3.18] |
| Mechanical constraints | Maximum footprint, height, mounting method, cooling airflow, vibration or potting requirements, and nearby heat sources. The repository schema includes thermal and mechanical constraints as a magnetics design entity. [source: /magnetics-wiki-schema.md §3] |
| Verification targets | Inductance tolerance, inductance versus bias-current curve, saturation-current limit, DCR, AC resistance, core-loss or temperature-rise test condition, and converter waveform acceptance limits. [source: /magnetics-wiki-schema.md §3] [source: Hurley & Wolfle Ch. 8 §8.1-§8.3.3] |

## Topology-Specific Additions

| Topology family | Extra inputs required |
| --- | --- |
| Buck output filter | $V_{in,min}$, $V_{in,max}$, $V_{out}$, output-current range, minimum CCM load, allowed output ripple, output capacitor ESR/ripple-current limit, worst-case $\Delta I_{pp}$ at maximum input voltage, and peak current under current-limit or short-circuit operation. TI states that buck-derived worst-case ripple is at maximum input voltage and that full-load inductor current equals load current for buck only. [source: TI SLUP132 §5 Design Strategy] |
| Boost inductor | $V_{in,min}$, $V_{in,max}$, $V_{out}$, output power, input-current waveform, current-limit behavior, inrush/startup condition, operating mode, and worst-case current values. TI states that boost saturation worst case occurs at maximum peak current and that boost-inductor design follows the buck-output-filter pattern after the worst-case currents are defined. [source: TI SLUP132 §5 Boost Inductor] |
| PFC boost inductor | AC line range, rectified line waveform, line frequency, output bus voltage, power level, mode across the line cycle, averaged-loss condition, low-line peak current, and ripple/current waveforms through the rectified line period. TI states that PFC boost design changes across the full-wave rectified line cycle and must account for changing ripple current, flux swing, core loss, and winding loss. [source: TI SLUP132 §5 Boost Inductor] |
| Buck-boost / single-winding flyback inductor | Input range, output voltage polarity and magnitude, CCM/DCM/boundary mode, peak current, zero-current dwell time for DCM, ripple target, and switch/diode current stress limits. TI groups single-winding flyback inductors with filter and boost inductors as power inductors that store and return magnetic energy. [source: TI SLUP132 §5 Inductor and Flyback Transformer Design] |
| Flyback coupled inductor | Turns ratio or reflected voltage, primary and secondary current waveforms, duty-cycle target, CCM/DCM/boundary mode, $I_{pk}$, $I_{min}$, $\Delta I_{pp}$, winding RMS/AC currents, leakage-energy clamp limit, and isolation/insulation requirements. [source: TI SLUP132 §5 Flyback Transformer Design] [source: Hurley & Wolfle Ch. 5 §5.4] |
| Coupled output filter inductor | Output voltage set, output power split, controlled output, minimum-load behavior, transformer secondary turns ratios, matching coupled-inductor turns ratios, common inductance target, allowed uncoupled/leakage inductance, and cross-regulation requirement. [source: TI SLUP132 R5-1] [source: TI SLUP132 R5-2 to R5-3] |
| DC/AC inverter output inductor | DC bus range, fundamental output frequency, PWM frequency, modulation method, target ripple current, allowed THD or ripple voltage, load/grid impedance range, filter topology, damping method, and common-mode EMI target. Inverter-specific magnetics sources have not yet been ingested. [UNVERIFIED] |

## Design-Ready Definition

An inductor design is ready to start when the converter inputs define $L$, $I_{FL}$, $\Delta I_{pp}$, $I_{pk}$, $I_{SCpk}$, $f_s$, the inductor voltage waveform, loss limit, temperature-rise limit, and packaging constraints. The first magnetic calculation can then choose a material and core, estimate $B_{max}$ and $\Delta B$, calculate turns, calculate the gap or effective permeability, and check winding loss and temperature rise. [source: TI SLUP132 §5 Design Strategy] [source: Hurley & Wolfle Ch. 3 §3.2]

## Related Pages

- [Converter Topology Inventory](./converter-topologies.md)
- [Equation Reference](./equation-reference.md)
- [Buck Output Filter Inductor Design](./buck-output-filter-inductor-design.md)
- [Thermal Design And Core Selection](./thermal-design-and-core-selection.md)
- [Air Gap And Saturation](./air-gap-and-saturation.md)
- [Distributed Gap And Fringing](./distributed-gap-and-fringing.md)
- [Verification And Measurement](./verification-and-measurement.md)
- [Index](./index.md)
