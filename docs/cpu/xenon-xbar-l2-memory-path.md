# Xenon XBAR, L2 and memory path (CPU → GPU → GDDR3)

## XBAR — CONFIRMED at role level

- XBAR (“Crossbar”) interconnects 3 PPEs; mesh topology with dedicated lanes; runs at full 3.2 GHz. Contrasted with Cell EIB ring for 12 nodes. Source: Copetti “Inside Xenon: The messenger” citing Brown. CONFIRMED as reported design; exact lane widths beyond FSB section remain UNKNOWN.
- PPSS (PowerPC Processor Storage Subsystem, Cell-era) is gone in Xenon; interfacing via XBAR + shared L2. Copetti. PARTIALLY CONFIRMED.

## Front-Side Bus (Xenon ↔ Xenos) — PARTIALLY CONFIRMED (precise numbers single-lineage)

| Claim | Value | Source chain |
|---|---|---|
| Two unidirectional PHY lanes, each 16 buses @5.4 GHz serial | 5.4 GHz | Copetti citing Siljenberg |
| CPU inner interface 64-bit @1.35 GHz; GPU inner 128-bit @675 MHz | as listed | Copetti citing Brown |
| Math: 10.8 GB/s per direction; 21.6 GB/s aggregated FSB (Free60 phrasing) | 10.8 / 21.6 | Copetti math; Free60 “21.6 GB/s front side bus (aggregated 10.8+10.8)” |
| GPU↔GDDR3: 2 controllers, 1×1024-bit bus each (per Copetti), 128-bit GDDR3 @700 MHz = 22.4 GB/s | 22.4 GB/s | Copetti; Wikipedia tech specs converge on 22.4 GB/s |

> Numbers converge across Copetti/Free60/Wikipedia, but ultimate primary is IBM/ATI. Keep PARTIALLY CONFIRMED until IBM Brown + ATI specs re-verified via Archive in Cycle 2. Do not present as measured.

## CPU latency note — PARTIALLY CONFIRMED

- “~600 cycles per cache miss to memory (PIX profiler sample tests)” — Copetti citing SDK PIX utility. Useful for UMA intuition (shared L2 + long road CPU→GPU→RAM). Single secondary; needs XDK/PIX primary. Mark PARTIALLY CONFIRMED, not a datasheet guarantee.

## UMA context — CONFIRMED (layout), INFERRED (tradeoff language)

- 0 MB dedicated CPU RAM; 512 MB GDDR3 next to GPU shared by CPU/GPU (UMA like original Xbox). CONFIRMED layout.
- Initial 256 MB plan doubled to 512 MB over Sony fear; Samsung 1.4 GHz hope settled to 700 MHz; HDD made optional for cost — Copetti citing Takahashi. Treat as PARTIALLY CONFIRMED history (book secondary).
- Address tiling + path-finding in GPU memory controllers to cut latency/congestion — Copetti. PARTIALLY CONFIRMED.

## Sources / References

- Copetti, CPU “messenger / main memory / memory controller” sections, `https://www.copetti.org/writings/consoles/xbox-360/` — XBAR mesh @3.2 GHz, L2 mesh 256-bit @1.6 GHz, PHY/FSB/GDDR3 figures, PIX ~600-cycle note. Fetched 2026-10-04.
- Free60 “Xenon CPU”, `https://free60.org/Hardware/Console/Xenon_%28CPU%29/` — 21.6 GB/s FSB, 51.2 GB/s L2 (256-bit×1600 MHz). Fetched 2026-10-04.
- IBM Brown + Siljenberg (via Copetti bib `cpu-brown`, `cpu-siljenberg`) — primaries to fetch Cycle 2.
