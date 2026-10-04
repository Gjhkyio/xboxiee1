# Bandwidth and interconnects — Xenos as northbridge

> Numbers are contemporary target/spec figures, not lab measurements. Keep PARTIALLY CONFIRMED until fab/ATI primaries re-verified.

## Table — PARTIALLY CONFIRMED (Beyond3D/Copetti lineage)

| Link | Cited figure | Notes |
|---|---|---|
| System RAM (GDDR3) ↔ Xenos | 22.4 GB/s (128-bit @700 MHz) | 2×64-bit crossbar partitions inside Xenos per Beyond3D |
| CPU (Xenon) ↔ Xenos FSB | 10.8 GB/s each direction, simultaneously | PHY 2×16-lane serial @5.4 GHz; CPU 64-bit @1.35 GHz, GPU 128-bit @675 MHz endpoints |
| ROP ↔ eDRAM | 256 GB/s | Framebuffer/Z/color bottleneck removal; no lossless compression needed per article calc |
| Parent die ↔ daughter die | ~32 GB/s (1/8 eDRAM BW) | Common color + packed Z per 2×2 quad |
| Xenos ↔ Southbridge | 500 MB/s each direction (2× PCIe lanes) | Audio/I-O controller link |
| CPU L2 | 51.2 GB/s (256-bit ×1600 MHz) | Shared 1 MB |
| GPU texture/vertex fetch | Entire UMA fetchable (512 MB) | Not eDRAM |

## XPS (Xbox Procedural Synthesis) — PARTIALLY CONFIRMED

- CPU as decompressor generating geometry on-the-fly for GPU via L2-locking + `xDCBT` streaming (L1-direct, L2-bypass on read; write-streaming L1-bypass to L2). High-BW transient streams avoid thrashing. Via Beyond3D + Wikipedia XPS bullet + Copetti `xdcbt` note. Exact instruction behavior + coherency hazard see `xenon-cores-threads-vmx.md`.

## Sources / References

- Beyond3D bandwidth diagrams `bandwidths.gif` / `edrambandwidth.gif` (via mirror) — figures above. Accessed 2026-10-04.
- Copetti memory-controller section — 10.8 GB/s lanes, 22.4 GB/s GPU-RAM, tiling/path-finding. `https://www.copetti.org/writings/consoles/xbox-360/`. Accessed 2026-10-04.
- Free60 Xenon CPU — 21.6 GB/s aggregated FSB, 51.2 GB/s L2. `https://free60.org/Hardware/Console/Xenon_%28CPU%29/`. Fetched 2026-10-04.
