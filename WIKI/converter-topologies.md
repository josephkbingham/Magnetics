# Converter Topology Inventory

## Scope

This page is a topology inventory for mapping converter families to magnetic components before adding per-topology design input sheets. It covers DC/DC, AC/DC, and DC/AC converter families, and records whether the current repository source set already supports each entry. [source: /magnetics-wiki-schema.md §3] [source: /magnetics-wiki-schema.md §4.1]

The repository schema already identifies topology-specific magnetics as a required knowledge entity, including PSFB transformers, flyback magnetics, push-pull transformers, PFC boost inductors, output filters, EMI common-mode chokes, DC chokes, and line-frequency transformer design. [source: /magnetics-wiki-schema.md §3]

The present source set distinguishes three magnetic roles that recur across converter topologies:

- **True transformer:** used in buck-derived circuits such as forward, full bridge, and half bridge; ideal energy storage is zero, with practical stored energy appearing in leakage and magnetizing inductance. [source: TI SLUP132 §2 Core Limitations in SMPS Applications] [source: TI SLUP132 §4 Power Transformer Design]
- **Energy-storage inductor:** used as a filter, boost, input, or DC choke element; the required energy is stored mainly in a gap or distributed-gap material. [source: TI SLUP132 §2 Core Limitations in SMPS Applications] [source: TI SLUP132 §5 Inductor and Flyback Transformer Design]
- **Flyback coupled inductor:** a flyback transformer is a multi-winding coupled inductor, not a true transformer, because the magnetizing inductance stores the transferred energy. [source: TI SLUP132 §2 Core Limitations in SMPS Applications] [source: TI SLUP132 §5 Flyback Transformer Design]

## DC/DC Topologies

| Topology | Isolation role | Primary magnetic component to design | Source status |
| --- | --- | --- | --- |
| Buck | Non-isolated | Output filter inductor | Covered by [Buck Output Filter Inductor Design](./buck-output-filter-inductor-design.md) and [Worked Example: Buck Gapped Core](./worked-example-buck-gapped-core.md). [source: Erickson & Maksimovic Ch. 11 §11.1-§11.2] [source: Hurley & Wolfle Ch. 3 Example 3.1] |
| Synchronous buck / multiphase buck | Non-isolated | One inductor per phase, or coupled phase inductors | Seed entry; needs source-backed treatment before design equations are added. [UNVERIFIED] |
| Boost | Non-isolated | Boost inductor | TI states that simple boost-inductor design follows the buck-output-filter pattern, while PFC boost operation requires line-cycle-dependent current and loss treatment. [source: TI SLUP132 §5 Boost Inductor] |
| Buck-boost / inverting flyback inductor | Non-isolated | Single-winding flyback or buck-boost inductor | TI groups filter inductors, boost inductors, and flyback inductors as power-inductor family members that store and return magnetic energy. [source: TI SLUP132 §5 Inductor and Flyback Transformer Design] |
| SEPIC / Cuk / Zeta | Topology variant dependent | One or more inductors, sometimes coupled | Seed entry; topology-specific magnetics inputs and equations are not yet source-backed in this wiki. [UNVERIFIED] |
| Isolated flyback | Isolated | Gapped flyback coupled inductor | TI treats flyback transformers as coupled inductors and gives separate CCM and DCM design discussions. [source: TI SLUP132 §5 Flyback Transformer Design] |
| Forward | Isolated | True transformer plus output filter inductor; reset path must be defined | TI lists forward converters as buck-derived transformer applications and distinguishes single-ended reset from push-pull reset behavior. [source: TI SLUP132 §4 Power Transformer Design] [source: TI SLUP132 §2 Core Saturation] |
| Push-pull | Isolated | True transformer plus output filter inductor | Push-pull transformers need volt-second balance because asymmetry in positive and negative volt-seconds can drive flux walking. [source: TI SLUP132 §2 Core Saturation] |
| Half bridge | Isolated | True transformer plus output filter inductor | TI lists half bridge as a buck-derived transformer topology and notes bridge or half-bridge primary winding utilization effects. [source: TI SLUP132 §4 Power Transformer Design] [source: TI SLUP132 §3 Window Utilization] |
| Full bridge / PSFB | Isolated | True transformer plus output filter inductor; leakage target is either a parasitic maximum or a functional ZVT/ZVS energy target | TI lists bridge-derived transformer design and notes that leakage and magnetizing energy can be used in zero-voltage-transition circuits with caution. [source: TI SLUP132 §4 Power Transformer Design] |
| LLC / series resonant / parallel resonant | Isolated | Transformer, magnetizing inductance, resonant inductance, and resonant capacitor relationship | Seed entry; resonant-converter-specific input fields are not yet source-backed in this wiki. [UNVERIFIED] |

## AC/DC Topologies

| Topology | Isolation role | Primary magnetic component to design | Source status |
| --- | --- | --- | --- |
| Line-frequency transformer rectifier | Isolated transformer stage | Line-frequency transformer, followed by rectifier/filter magnetics as needed | The schema identifies line-frequency transformer design as in scope; a source-backed page has not yet been added. [source: /magnetics-wiki-schema.md §3] |
| Diode bridge plus bulk capacitor | Non-isolated front end | EMI common-mode choke, differential-mode choke, or DC choke as required | The schema identifies EMI common-mode choke and DC choke design as in scope; topology-specific treatment is not yet source-backed. [source: /magnetics-wiki-schema.md §3] |
| Boost PFC | Non-isolated front end | Boost inductor | TI states that PFC boost design is complicated by the continuously varying full-wave rectified line voltage and multiple possible operating modes. [source: TI SLUP132 §5 Boost Inductor] |
| Interleaved boost PFC | Non-isolated front end | Multiple boost inductors, or coupled/interphase inductors | Seed entry; interleaved PFC magnetics are not yet source-backed in this wiki. [UNVERIFIED] |
| Bridgeless / totem-pole PFC | Non-isolated front end | Boost inductor or inductors plus EMI magnetics | Seed entry; bridgeless and totem-pole PFC magnetics are not yet source-backed in this wiki. [UNVERIFIED] |
| Off-line isolated flyback | Isolated | Flyback coupled inductor with safety insulation | TI identifies flyback transformers as coupled inductors and notes that separate windings provide isolation; insulation requirements are covered in [Transformer Insulation](./transformer-insulation.md). [source: TI SLUP132 §5 Flyback Transformer Design] [source: Hurley & Wolfle Ch. 5 §5.4] |
| Off-line forward / half bridge / full bridge | Isolated | True transformer plus output inductor and EMI magnetics | TI treats forward, bridge, and half-bridge converters as buck-derived transformer applications; primary-secondary isolation is a transformer function in off-line applications. [source: TI SLUP132 §4 Power Transformer Design] |
| Active-clamp flyback / active-clamp forward | Isolated | Flyback or forward magnetic with clamp/reset energy constraints | Seed entry; active-clamp-specific magnetics inputs are not yet source-backed in this wiki. [UNVERIFIED] |
| LLC AC/DC stage | Isolated | Resonant transformer and resonant inductance | Seed entry; LLC-specific magnetics inputs are not yet source-backed in this wiki. [UNVERIFIED] |

## DC/AC Topologies

No inverter-specific design source has been ingested. The entries below are planning placeholders until inverter, UPS, motor-drive, or grid-tied inverter sources are added. [UNVERIFIED]

| Topology | Isolation role | Primary magnetic component to design | Source status |
| --- | --- | --- | --- |
| Single-phase half-bridge inverter | Topology variant dependent | Output L, LC, or LCL filter; EMI choke | Seed entry. [UNVERIFIED] |
| Single-phase full-bridge / H-bridge inverter | Topology variant dependent | Output L, LC, or LCL filter; EMI choke | Seed entry. [UNVERIFIED] |
| Three-phase two-level voltage-source inverter | Topology variant dependent | Per-phase output reactors, sine filters, common-mode chokes, or motor-drive chokes | Seed entry. [UNVERIFIED] |
| Multilevel inverter | System architecture dependent | Output filter inductors, balancing magnetics if used, EMI magnetics | Seed entry. [UNVERIFIED] |
| Push-pull transformer inverter | Isolated | Transformer; volt-second balance must be checked | Push-pull transformer flux walking is source-backed, but the inverter topology entry still needs a DC/AC-specific source. [source: TI SLUP132 §2 Core Saturation] [UNVERIFIED] |
| Resonant inverter | Application dependent | Resonant inductor, transformer if isolated, and output/load network | Seed entry. [UNVERIFIED] |

## Common Magnetics Input Fields

Every future topology-specific design sheet should begin with the GIC structure required by the repository schema: Geometry, Input, and Constraint. [source: /magnetics-wiki-schema.md §4.2]

For inductor-specific designs, use [Inductor Design Inputs](./inductor-design-inputs.md) as the common input checklist before applying a topology-specific procedure. [source: TI SLUP132 §5 Design Strategy]

| Field group | Inputs to collect |
| --- | --- |
| Converter identity | Conversion class, topology name, isolation requirement, control/modulation method, rectification method, and number of outputs. [source: /magnetics-wiki-schema.md §3] |
| Electrical operating range | Input voltage range or AC line range, output voltage rails, output current/load range, power level, overload/short-circuit condition, hold-up or transient requirement, and expected operating modes. [source: /magnetics-wiki-schema.md §4.2] |
| Timing and waveform set | Switching frequency or frequency range, transformer frequency where different from switching frequency, duty-cycle limits, volt-second intervals, current waveform shape, and dc/rms/ac current components for each winding. [source: TI SLUP132 §4 Topology] [source: TI SLUP132 §5 Flyback Transformer Design] |
| Magnetic role | True transformer, energy-storage inductor, coupled filter inductor, flyback coupled inductor, EMI choke, or DC choke. [source: TI SLUP132 §2 Core Limitations in SMPS Applications] [source: /magnetics-wiki-schema.md §3] |
| Core constraints | Candidate material, core shape, $A_e$, $A_w$, $V_e$, path length, gap strategy, $B_{max}$, $\Delta B$, core-loss limit, and saturation margin. [source: /magnetics-wiki-schema.md §3] [source: /magnetics-wiki-schema.md §4.2] |
| Winding constraints | Turns ratio, integer-turn limits, conductor type, dc resistance, ac resistance, current density, window fill, layer count, interleaving, winding hierarchy, creepage, clearance, and insulation system. [source: TI SLUP132 §3 Window Utilization] [source: Hurley & Wolfle Ch. 5 §5.4] |
| Thermal and loss limits | Ambient temperature, cooling method, allowed temperature rise, total magnetic loss budget, core/winding loss split, and maximum hot-spot temperature. [source: TI SLUP132 §4 Losses and Temperature Rise] [source: /magnetics-wiki-schema.md §3] |
| Parasitic targets | Leakage inductance target or maximum, interwinding capacitance target, common-mode noise constraints, coupling coefficient target, and whether leakage energy is parasitic or intentionally used. [source: TI SLUP132 §4 Energy Storage in a Transformer] |
| Verification | Inductance versus bias, saturation-current check, winding resistance, ac resistance, core-loss check, thermal test, hipot/insulation test where applicable, and converter-level waveform validation. [source: /magnetics-wiki-schema.md §3] [source: Hurley & Wolfle Ch. 8 §8.1-§8.3.3] |

## Topology-Specific Input Hooks

| Topology family | Additional inputs needed before magnetic design |
| --- | --- |
| Buck output filter | Inductance target or ripple-current target, $V_{in,min}$, $V_{in,max}$, $V_{out}$, load-current range, minimum CCM load, saturation current, and output-capacitor ripple interaction. [source: Erickson & Maksimovic Ch. 11 §11.1-§11.2] |
| Boost / PFC boost | Rectified line or DC input profile, output bus voltage, operating mode, ripple target across the line cycle, worst-case saturation current, inrush/current-limit behavior, and averaged loss condition. [source: TI SLUP132 §5 Boost Inductor] |
| Flyback | CCM/DCM/boundary mode, duty-cycle target, turns ratio or reflected voltage, primary and secondary peak currents, clamp/snubber leakage-energy limit, isolation requirement, and winding rms/ac current components. [source: TI SLUP132 §5 Flyback Transformer Design] |
| Forward / half bridge / full bridge | Turns ratio, output rectifier drops, duty-cycle range, transformer volt-second interval, output-filter inductor requirement, reset or volt-second-balance condition, and winding utilization target. [source: TI SLUP132 §4 Power Transformer Design] [source: TI SLUP132 §3 Window Utilization] |
| Push-pull | Same inputs as bridge-derived transformers, plus explicit positive/negative volt-second balance and flux-walking tolerance. [source: TI SLUP132 §2 Core Saturation] |
| Coupled multi-output buck-derived converters | Output voltage set, output power split, controlled rail, cross-regulation requirement, coupled-inductor turns ratios, leakage or uncoupled inductance target, and minimum-load behavior. [source: TI SLUP132 R5-1] [source: TI SLUP132 R5-2 to R5-3] |
| Resonant converters | Resonant tank gain range, $L_m$, $L_r$, $C_r$, frequency sweep range, load range, and whether leakage is part of $L_r$. [UNVERIFIED] |
| DC/AC inverter filters | Fundamental output frequency, modulation method, DC bus range, target ripple/THD, grid or load impedance, filter type, damping method, and common-mode EMI target. [UNVERIFIED] |

## Related Pages

- [Index](./index.md)
- [Inductor Design Inputs](./inductor-design-inputs.md)
- [Electromagnetic Fundamentals](./electromagnetic-fundamentals.md)
- [Buck Output Filter Inductor Design](./buck-output-filter-inductor-design.md)
- [Practical Transformer Model](./practical-transformer-model.md)
- [Transformer Design Methodology](./transformer-design-methodology.md)
- [Coupled Filter Inductors](./coupled-filter-inductors.md)
- [Transformer Insulation](./transformer-insulation.md)
