# Xenon cores, threads and VMX128

## Per-core caches — CONFIRMED

| Item | Value | Source |
|---|---|---|
| L1I per core | 32 KiB | Free60 Xenon CPU; Copetti |
| L1D per core | 32 KiB | Same |
| L2 shared | 1 MB, 8-way set-associative, 128 B lines, @1.6 GHz (half CPU clock), 256-bit bus per PPE, ~51.2 GB/s cited | Free60 (51.2 GB/s figure); Copetti (mesh, 256-bit @1.6 GHz, 8-way, 128 B lines) |
| L2 lockable by GPU | Reported (for procedural synthesis / direct GPU reads) | Free60 spec bullet; Copetti; Beyond3D lineage (XPS) |

Cache-line width (128 B) and 8-way choice rationale (6 threads contending, balancing miss-rate vs lookup cost vs Smithfield comparison) is Copetti explanation. Mark rationale INFERRED; geometry CONFIRMED via convergence.

## SMT — CONFIRMED

- 2 HW threads per core, 6 total. Dual-issue PPE.
- Register files: Free60 cites `2× (128×128-bit) per core`; Copetti/VMX section cites 128×128-bit per thread doubled to 256 per core via duplication. Slight wording difference — document as convergence, not contradiction: both describe per-thread duplication for dual-issue/TLP.
- Free60 Linux historical note: secondary threads disabled for stability at time of writing. Historical only.

## VMX128 — CONFIRMED at feature level, PARTIALLY CONFIRMED at encoding detail

| Claim | Confidence | Evidence |
|---|---|---|
| Each core has VMX128 vector unit (evolved VMX) | CONFIRMED | Free60; Copetti |
| 128×128-bit registers per HW thread (256 per core with duplication) | CONFIRMED as reported | Copetti “The new vector units”; Free60 “128 VMX-128 registers per HW thread” |
| Opcode extends register specifier 5→7 bits via last-five-bits trick; subset of VMX integer mul/add incompatible | PARTIALLY CONFIRMED | Copetti citing Gschwind + Biallas; needs IBM primary re-fetch |
| New dot-product (up to 3×fp32) + D3D compression-format helpers | PARTIALLY CONFIRMED | Copetti citing Brown; needs IBM/XDK primary |
| `xdcbt` (extended Data Cache Block Touch, L1-fill bypassing L2) added then purged from compiler due to incoherency + branch-predictor hazard | PARTIALLY CONFIRMED (single detailed secondary with named Microsoft engineer anecdote) | Copetti citing Lanterman + Dawson; treat as strong lead, not primary fact |
| VMX128 vs Cell SPE speed comparison “too divergent to quantify” | INFERRED (analysis) | Copetti reasoning (SPE dual-issue + local-store/DMA vs PPE any-address access) |

> Do not invent VMX opcodes, encodings, or intrinsics. No opcode table is published in Cycle 1. Cycle 2 must consult IBM PowerPC VMX + VMX128 notes (Gschwind) and Xenia CPU recompiler source for observable behavior, not as ISA authority.

## Programming model — SMP — CONFIRMED as documented model

- Xenon is Symmetric Multi-Processing: 3 homogeneous cores sharing memory; abstraction via virtual threads + OS scheduler; 6 threads exposed. Copetti “Programming styles” + standard SMP definition. CONFIRMED as model description.
- Scalability/cross-compatibility claims are analysis (INFERRED).

## Sources / References

- Free60 “Xenon CPU”, `https://free60.org/Hardware/Console/Xenon_%28CPU%29/` — caches, SMT, VMX-128 bullets. Fetched 2026-10-04.
- Copetti Xbox 360, CPU sections (“Inside Xenon: messenger/leaders”, “new vector units”, “new but short-lived instruction”, “programming styles”), `https://www.copetti.org/writings/consoles/xbox-360/` — detailed narrative + bibliography entries `cpu-gschwind`, `cpu-biallas`, `cpu-brown`, `cpu-lanterman`, `cpu-dawson`. Fetched 2026-10-04.
- IBM Gschwind et al. VMX/Cell references (via Copetti bib) — to be fetched Cycle 2.
