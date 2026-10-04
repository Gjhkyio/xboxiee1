# Unified memory — 512 MB GDDR3

## Facts — CONFIRMED (layout), PARTIALLY CONFIRMED (exact clocks/BW lineage)

| Item | Value | Confidence |
|---|---|---|
| Total | 512 MB GDDR3 SDRAM on motherboard next to GPU (256 MB front + 256 MB back on early boards) | CONFIRMED (Copetti photo + multiple specs) |
| Shared (UMA) | CPU + GPU share same chips; flexible CPU/GPU split (like original Xbox UMA) | CONFIRMED |
| Type | GDDR3 (same family as Wii/PS3 VRAM per Copetti) | CONFIRMED as reported |
| Clock | 700 MHz (1.4 GHz hoped, settled 700 MHz per Copetti history) | PARTIALLY CONFIRMED |
| Bus | 128-bit (2×64-bit partitions in Xenos crossbar; 2 controllers ×1024-bit internal per Copetti) | PARTIALLY CONFIRMED |
| BW GPU↔RAM | 22.4 GB/s | Convergent (Copetti/Wikipedia/Beyond3D) |
| CPU↔RAM path | CPU→FSB→GPU→GDDR3 (no direct CPU RAM) | CONFIRMED |
| Initial plan | 256 MB doubled to 512 MB (Sony-fear account) | PARTIALLY CONFIRMED (book secondary via Copetti) |
| Cost tradeoff | HDD made optional to hold retail price | PARTIALLY CONFIRMED (same history) |

## Implications (analysis, INFERRED)

- Far CPU incurs high miss penalty (~600 cycles via PIX sample, Copetti). Hence L2 importance + XPS/L2-locking + tiling/path-finding optimizations.
- No CPU-private fast RAM: streaming/compression (XPS) and cache discipline matter more than on split-pool designs.

## Cycle 2 TODO (UNKNOWN)

- Chip densities/vendors per revision, jeb? Samsung/Qimonda/Hynix lots, address-tiling algorithm, SFC/NAND vs DRAM map, physical memory map. Mark UNKNOWN until teardowns/datasheets + Xenia memory code audited.

## Sources / References

- Copetti “Inside Xenon: Main Memory / Memory Controller”, `https://www.copetti.org/writings/consoles/xbox-360/` — UMA, GDDR3, 700 MHz, 22.4 GB/s, tiling, PIX ~600 cycles, 256→512 MB history. Accessed 2026-10-04.
- Free60 “Memory” (`https://free60.org/Hardware/Console/Memory/` — not yet fetched; queued Cycle 2) + Xenon CPU FSB/L2 figures.
- Wikipedia tech specs — 512 MB GDDR3 @700 MHz, 22.4 GB/s convergence.
