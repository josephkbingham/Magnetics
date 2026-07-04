# Magnetic-Mechanical Analogy Reference

## Source

- File: `Raw/Magnetic_Mechanical_Analogy_Reference.md` (text extraction of `Raw/Magnetic_Mechanical_Analogy_Reference.docx`)
- Bibliographic identity: *The Magnetic–Mechanical Analogy — Inductance, Reluctance, Permeability, Air Gaps, and Saturation — Mapped to Springs and Masses*, internal Engineering Reference Document, Rev A, July 2026.
- Cite as: `[source: Magnetic-Mechanical Analogy Ref. §N]`, where `N` matches the document's own numbered sections (1-13, with 10.1-10.3 as subsections).

## Scope

A from-scratch derivation of a three-level spring-mass analogy for magnetic components: circuit terminals (L as mass), the internal magnetic circuit (reluctance as spring constant, via Hopkinson's law), and the material itself (permeability as mechanical compliance). The coil is treated explicitly as a gyrator reconciling the circuit and magnetic-circuit levels. Not tied to a specific textbook; it is a derived teaching/reference document, lowest in the source hierarchy for numeric material properties (§4.3 of the schema) but original for the analogy framework itself.

## Distinctive Contributions

- explicit three-level (circuit / magnetic-circuit / material) analogy connected by the coil-as-gyrator, resolving the "inductor is a mass at the terminals but a spring inside" apparent contradiction
- physical explanation for why reluctance stores/returns energy rather than dissipating it, and why series reluctances (core + gap) map to parallel springs
- resolution of the "gap paradox": three true but seemingly contradictory statements about permeability, reluctance, and stored energy, reconciled by identifying what each statement holds constant (same B vs. same current vs. same saturation limit)
- a compact four-equation summary for computing core flux density $B$ from different known quantities (design check, magnetic-circuit view, gap-dominated approximation, Faraday volt-second form), with guidance on which to use when
- an explicit gap-lowers-$B$ derivation via effective magnetic length, $B = \mu_0 NI / (\ell_c/\mu_r + \ell_g)$, with a worked numeric comparison (100 mm ferrite path, $\mu_r = 2500$, 1 mm gap: 26x increase in effective magnetic length, 3.1 T to 0.12 T at fixed NI)
- a worked 10x-reluctance-increase comparison table showing $L$, $I_{sat}$, and $E_{max}$ scaling
- a master variable map and a side-by-side key-equations table consolidating all three levels

## Wiki Pages Fed By This Source

- `WIKI/magnetic-mechanical-analogy.md` (new page)

## Candidate Follow-On Updates

- `WIKI/equation-reference.md`: added the gap-dominated effective-magnetic-length form of $B$ as a cross-reference to the existing reluctance/gap equations.

## Notes

- This source is self-consistent with the existing Erickson & Maksimovic reluctance/gap/saturation equations already in the wiki ($\mathcal{R} = \ell/(\mu A)$, $L = N^2/\mathcal{R}$, $I_{sat} = B_{sat}A_c(\mathcal{R}_c+\mathcal{R}_g)/n$) — it reframes them mechanically rather than contradicting them.
- Its typical-$B_{sat}$-by-material table (MnZn ferrite 0.4-0.5 T, powdered iron/sendust 1.0-1.5 T, silicon steel 1.5-2.0 T, amorphous/nanocrystalline 1.2-1.56 T) is a refinement of, and consistent with, the broader ranges already cited from Erickson & Maksimovic (0.25-0.5 T ferrite, 0.5-1 T powdered iron, 1-2 T iron/silicon steel) — no conflict, treated as the same hierarchy tier (peer reference material) pending a manufacturer datasheet citation.
- Per the source-hierarchy rule (schema §4.3), this document ranks alongside application notes: useful for derivations and conceptual framing, but any numeric material property it states should defer to a manufacturer datasheet or measured data if one is later ingested.
