# Magnetics Wiki

This repository is a source-backed markdown knowledge base for transformer and inductor design in power electronics. It is built from raw textbook extracts, application notes, datasheets, and design calculations, then normalized into a linked wiki under `WIKI/` using the rules in `magnetics-wiki-schema.md`.

## Repository Structure

- `Raw/`: raw source material awaiting ingestion or re-ingestion.
- `WIKI/`: compiled, linked, citation-backed wiki pages.
- `SOURCE_NOTES/`: source-specific notes used during ingestion to map coverage, extract equations, and track unresolved gaps.
- `magnetics-wiki-schema.md`: the governing schema for wiki content, linking, traceability, GIC modeling, and conflict resolution.

## Current Coverage

The wiki currently covers:

- electromagnetic fundamentals
- air-gap behavior and saturation
- distributed-gap versus discrete-gap tradeoffs
- core materials and losses
- CCM buck output-filter inductor design
- thermal/core-selection methodology for inductors
- a worked buck-inductor example
- verification and measurement methods
- practical transformer modeling
- transformer design methodology
- transformer insulation
- high-frequency winding and core effects

Start at [WIKI/index.md](WIKI/index.md).

## Ingestion Workflow

1. Add source files to `Raw/`.
2. Create or update a note in `SOURCE_NOTES/` for that source.
3. Extract equations, constraints, tradeoffs, and worked examples into linked pages in `WIKI/`.
4. Cite every factual claim to a specific source section.
5. Mark unsupported claims as `[UNVERIFIED]` instead of filling gaps from memory.
6. Record the change in [WIKI/changelog.md](WIKI/changelog.md).

## Content Rules

- Every wiki page must link to at least one other wiki page.
- Use GIC framing where applicable: Geometry, Input, Constraint.
- Prefer higher-priority sources when conflicts exist.
- Keep factual sections clinical and source-specific.

See [magnetics-wiki-schema.md](magnetics-wiki-schema.md) for the full ruleset.