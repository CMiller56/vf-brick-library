# Advanced Rocket Engines (Haidn / RTO-EN-AVT-150)

**Brick id (folder):** `Advanced_Rockets`  
**Chunks:** 66  
**Package:** `Advanced_Rockets_portable.zip` (~1.5 MB)  
**Export gate waived:** False  
**Search smoke:** PASS (2026-07-22)

## Purpose

Technical reference brick on **advanced chemical rocket engines** — propulsion basics, cycles, turbomachinery, and related mission context from an educational notes paper.

## Audience

Aerospace / propulsion engineers, students, and tinkerers studying liquid rocket engines (not flight certification).

## Sources

- **Primary:** Haidn, O.J. — *Advanced Rocket Engines* (RTO Educational Notes **RTO-EN-AVT-150**, Paper 6).  
  Institute of Space Propulsion, DLR (German Aerospace Center).  
  Cited in-source as available via RTO / NATO STO educational materials (see original PDF attribution).
- File as ingested: `AdvanceRocketEnginesEN-AVT-150-06.pdf` (~40 pages).

## License / rights

**Important:** This brick is a **derived retrieval package**, not an official NATO STO / DLR / author publication and **not** a redistribution of the original PDF as the system of record.

- Source text is educational material associated with **NATO RTO / STO** publication **RTO-EN-AVT-150**.
- Confirm current redistribution terms on the **NATO STO / RTO** site (or rights holder) before commercial use or mass republication.
- Keep the original PDF as system of record when rights allow you to hold it.
- **Not affiliated with or endorsed by** NATO STO, DLR, or the author.

If you cannot legally host derived educational text in your jurisdiction, do not redistribute this ZIP.

## Known limits / residual

- Small brick (66 chunks) — depth is paper-scale, not a full textbook.
- **1 open** high-priority craft flag remains: `garbled_extraction` on a fragment-line region (`chunk-0039`) — dual-stream / math debris style; inspect before trusting that slice.
- 1 waived thin/low-extraction stub on a late chunk.
- Equations and dense figures may be incomplete in plain text extract (honest PDF limits).
- Classification in craft brief may still say “Internal” from build metadata — treat as **technical reference**, not classified material.

## How to use

1. Unzip `Advanced_Rockets_portable.zip` (or load the ZIP if your tooling supports it).
2. Point **VF Runtime Connect** / Engine `load_kb` at the brick (see `HANDOFF_README.md` inside).
3. Prefer questions on cycles, turbopumps, propellants, and basics from this paper — ground answers in citations.
4. Chat LLM is **not** bundled.

## Feedback

Working knowledge package, not frozen perfection. Issues with retrieval, missing sections, or rights concerns welcome via the brick-library issue tracker or VectorForge channels. We re-cut packs as the factory improves.
