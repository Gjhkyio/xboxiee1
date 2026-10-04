# Copetti “Xbox 360 Architecture — A Practical Analysis” — secondary synthesis

## What it is — CONFIRMED

- Long-form practical analysis by Rodrigo Copetti, part of “Architecture of Consoles” series. Home: `https://www.copetti.org/writings/consoles/xbox-360/`. Fetched 2026-10-04 (CPU + Graphics + Memory sections + bibliography). Also in DRM-free eBook/print compilations; classic/blink editions for accessibility/vintage.
- Structure mirrors PS3 article for side-by-side comparison; pre-reads PS3 Cell. Photos (models S/E, Xenon rev motherboard, Xenos+eDRAM package, GDDR3 path), diagrams (main arch, crossbar, PPE, programming, traditional vs unified pipeline), game screenshots (720p examples).

## Strengths for this repo

- Per-section bibliography with named primaries: IBM Brown (XCPU story), Siljenberg (PHY), Gschwind (VMX), Biallas (opcode trick), Lanterman/Dawson (`xdcbt`), Stokes/Shimpi (in-order debate), Takahashi (business history), Shippy (Cell quote), ATI merger/Shimpi-5800 (GPU context), Baumann (eDRAM), etc. Lets us follow chains to primaries Cycle 2.
- Explicit numbers used Cycle 1: XBAR @3.2 GHz mesh; L2 1 MB 8-way 128 B lines 256-bit @1.6 GHz; PHY 16×5.4 GHz; CPU 64-bit @1.35 GHz / GPU 128-bit @675 MHz →10.8 GB/s; GPU-RAM 22.4 GB/s (128-bit @700 MHz, 2×1024-bit internal); CPU miss ~600 cycles via PIX; VMX128 128 regs/thread (256/core); R400/Crayola vs R520 dispute; UMA 512 MB + 10 MB eDRAM split.

## Limits (must respect)

- Secondary synthesis + analysis. Motive/tradeoff language (homogeneous choice, OoO omission, TLP-vs-ILP, cost decisions) is INFERRED/interpretive even when well-cited. Vendor figures (95% shader efficiency, 95% 720p-4×MSAA tiling perf) are vendor claims via press.
- R520-vs-R400 disagreement with Wikipedia must stay documented as disagreement, not resolved.

## Sources / References

- Copetti article, `https://www.copetti.org/writings/consoles/xbox-360/` — main synthesis. Fetched 2026-10-04.
- Book/program pages: `https://www.copetti.org/writings/consoles/materials/book/`, `https://www.copetti.org/writings/consoles/` — edition/provenance. Search-verified.
- Video intro `https://youtu.be/uZXHQT3NRss` — overview only, not cited for specs.
