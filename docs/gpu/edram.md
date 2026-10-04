# eDRAM daughter die — 10 MB “Intelligent Memory” (NEC)

## Specs — PARTIALLY CONFIRMED (convergent, single lineage for some figures)

| Attribute | Value | Confidence | Evidence |
|---|---|---|---|
| Capacity | 10 MB | CONFIRMED | Wikipedia; Copetti; XenonLibrary; Beyond3D |
| Clock | 500 MHz (target) | PARTIALLY CONFIRMED | Beyond3D note “target clocks, small room” + MS 500 MHz announcement |
| Internal BW (ROP↔eDRAM) | 256 GB/s | CONFIRMED as widely cited | Wikipedia; Beyond3D edrambandwidth diagram; Copetti triple-memory framing |
| Process | 90 nm NEC (launch); 80 nm half-shrink (2008); 65 nm Styx-65 (2010); integrated Vejle 45 nm / Oban 32 nm later | PARTIALLY CONFIRMED | Wikipedia; XenonLibrary eDRAM variants (Oban/Styx-90/Styx-65/Edifis) |
| Transistors | ~105M (80M DRAM + logic incl. FSAA) | PARTIALLY CONFIRMED | Beyond3D math; Wikipedia 105M |
| Logic (“Intelligent Memory”) | 192 parallel pixel processors for color, alpha compositing/blending, Z/stencil, 4×MSAA at little cost | PARTIALLY CONFIRMED (marketing + arch description) | Wikipedia; Beyond3D ROP section |
| ROPs | 8 ROPs; 4 Gpix/s no-MSAA (8×500 MHz); 16 Gsamples/s 4×MSAA; 32 Gsamples/s Z-only; 8 Gsamples/s Z (2×8×500 MHz), 32 Gsamples/s with 4×AA | PARTIALLY CONFIRMED | Wikipedia spec list; Beyond3D |
| Filtering/tiling helpers | Bilinear/trilinear/aniso, alpha-to-coverage, HW tessellation assist, predicated tiling | PARTIALLY CONFIRMED | Wikipedia line; Beyond3D tiling/tessellation sections |
| Access | Xenos-only (not CPU/texture units); front-buffer lives in UMA, back/z/stencil in eDRAM | CONFIRMED as reported architecture | Copetti “Organising the content”; Beyond3D |

## Variants — PARTIALLY CONFIRMED (XenonLibrary matrix, needs direct re-verify)

- Edifis 90 nm (Y1/Y2), Styx-90 (Rhea/Elpis-era), Styx-65 (Kronos/XCGPU Vejle), integrated Oban 32 nm. Source: XenonLibrary GPU eDRAM specs/variants (search-verified, direct 403 on 2026-10-04). Cross-check with ConsoleMods per-board GPU/eDRAM column in Cycle 2.

## What it holds (typical) — CONFIRMED pattern

- Z-buffer, stencil, back/intermediate framebuffer, custom small buffers; bulk textures/vertices stay in GDDR3. Copetti + Beyond3D agree.

## Sources / References

- Wikipedia Xenos eDRAM bullets, `https://en.wikipedia.org/wiki/Xenos_(graphics_chip)` — 10 MB, 256 GB/s, NEC, 192 PEs, 8 ROPs rates. Accessed 2026-10-04.
- Beyond3D Xenos (mirror, see `xenos-overview.md`) — 256 GB/s removes FB bottleneck, no lossless compression needed, parent↔daughter 1/8 BW, resolve/write-back, FP10. Accessed 2026-10-04.
- Copetti “Organising the content”, `https://www.copetti.org/writings/consoles/xbox-360/` — triple-memory framing (512 MB GDDR3 shared + 10 MB Xenos-only). Accessed 2026-10-04.
- XenonLibrary “GPU — eDRAM Specifications/Variants”, `https://xenonlibrary.com/wiki/GPU` — 10 MB 256 GB/s + logic list + Oban/Styx variants. Search-verified 2026-10-04; direct fetch blocked (403), must Archive-verify.
