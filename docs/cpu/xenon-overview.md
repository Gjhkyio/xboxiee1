# Xenon overview — IBM Waternoose / XCPU

> CPU top page. Core details in siblings. Labels per row.

## Identity — CONFIRMED

| Attribute | Value | Confidence | Evidence |
|---|---|---|---|
| Codename (IBM) | Waternoose | CONFIRMED | Free60 Xenon CPU page |
| Codename (Microsoft) | XCPU / Xenon | CONFIRMED | Free60; Copetti |
| ISA | 64-bit PowerPC, full ISA available (per Free60 wording) | CONFIRMED as reported wording; micro-detail PARTIALLY CONFIRMED | Free60; IBM PowerPC docs lineage |
| Cores | 3 symmetrical cores on single die | CONFIRMED | Free60; Copetti; Wikipedia |
| Threads | 2-way SMT per core = 6 HW threads | CONFIRMED | Same |
| Clock | 3.2 GHz per core (9.6 GHz aggregate throughput phrasing in Free60) | CONFIRMED | Free60; Copetti; tech specs |
| Process (launch) | 90 nm; later 65 nm SOI; then 45 nm / 32 nm combined XCGPU/Oban | CONFIRMED at family level; per-stepping details in revisions page | Wikipedia tech specs; ConsoleMods |
| Package | 31×31 mm FC-PBGA 2-2-2 (per Free60) | PARTIALLY CONFIRMED (single wiki source) | Free60 Xenon CPU |
| Die | 168 mm²; ~1 core ≈28 mm²; 165M transistors (Free60 figure) | PARTIALLY CONFIRMED | Free60 (needs IBM primary cross-check) |
| Endianness | Big-endian | CONFIRMED | Free60; XEX header is big-endian (Free60 XEX) |
| Execution | In-order (no OoO) | CONFIRMED as widely reported | Copetti “Revisiting old paradigms”; Stokes/Shimpi contemporary analysis cited therein |
| Peak | 115 GFLOPS theoretical; 9.6B dot-products/s; VPR 1089 cited | PARTIALLY CONFIRMED (single-source figures) | Free60 specs list |
| Security | On-die ROM for private keys (Free60 wording: “ROM storing Microsoft private encrypted keys, used to decrypt game data” — Wikipedia tech specs wording) + eFuses | PARTIALLY CONFIRMED (existence widely reported; exact contents/usage not public) | Wikipedia tech specs; Free60 Fusesets (Cycle 2) |

> Do not confuse Xenon (CPU) with Xenos (GPU) or Xenon (launch motherboard). See glossary.

## Relation to Cell/PPU — PARTIALLY CONFIRMED + INFERRED context

- Xenon PPEs derive from same IBM POWER lineage as Cell’s PPE/PPU; Xenon has 3× PPE, no SPEs; Cell has 1× PPE + 8 SPEs (1 disabled/1 reserved in PS3). Reported consistently in Copetti (with diagrams) and contemporary press. CONFIRMED at block-count level.
- Business history (IBM+Sony+Toshiba Cell 2001, IBM+Microsoft Xenon 2003, IP-sharing requirement, homogeneous-vs-heterogeneous choice) follows Copetti narrative citing Takahashi book, Shippy quote, Brown IBM paper. Treat motive/quote context as PARTIALLY CONFIRMED (secondary citing primary); do not overclaim without reading primaries.
- Out-of-order omission rationale (area/power, app-specific, TLP-vs-ILP) is Copetti analysis citing Stokes/Shimpi/Etsion. Mark INFERRED where it interprets tradeoffs.

## Linux note (historical, CONFIRMED as Free60 report)

Free60 reports SMP across 3 cores works under Linux, secondary threads disabled due to unanalyzed stability issue at time of writing, and poor general-purpose performance without PPU-aware GCC (merged in GCC 4.4 per page). This is a dated observation; keep as historical, not current guidance. See `docs/research/free60.md`.

## Sources / References

- Free60 Wiki — “Xenon CPU”, `https://free60.org/Hardware/Console/Xenon_%28CPU%29/` — spec list + Linux SMP note + IBM external links. Fetched 2026-10-04. Core evidence for table.
- Copetti — “Xbox 360 Architecture”, CPU chapters, `https://www.copetti.org/writings/consoles/xbox-360/` — XBAR/L2/PPE/VMX/memory-path narrative + bibliography (Brown, Siljenberg, Gschwind, Biallas, Stokes, Shimpi). Fetched 2026-10-04.
- Wikipedia — “Xbox 360 technical specifications”, `https://en.wikipedia.org/wiki/Xbox_360_technical_specifications` — 90 nm→65 nm SOI→45/32 nm combined, 1 MB L2 @ half clock, heatsink note. Tertiary convergence only.
- Wikipedia — “Xenon (processor)”, `https://en.wikipedia.org/wiki/Xenon_(processor)` — tri-core PowerPC @3.2 GHz baseline. Tertiary.
- IBM Jeffrey Brown — “Application-customized CPU design: The Microsoft Xbox 360 CPU story”, developerWorks (archived: `https://web.archive.org/web/20081205055833/http://www-128.ibm.com:80/developerworks/power/library/pa-fpfxbox/index.html?ca=drs-`) — primary IBM account, linked from Free60. Not yet re-fetched in Cycle 1; priority for Cycle 2.
