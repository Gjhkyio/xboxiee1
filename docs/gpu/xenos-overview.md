# Xenos overview — ATI C1, 500 MHz, unified shaders

> Parent die + daughter eDRAM package. See siblings for pipeline/tiling, eDRAM, bandwidth.

## Identity — CONFIRMED

| Attribute | Value | Confidence | Evidence |
|---|---|---|---|
| Designer | ATI (now AMD), eDRAM by NEC | CONFIRMED | Wikipedia Xenos; Copetti; XenonLibrary GPU (search mirror) |
| Codename | C1 (“PR-friendly” Xenos); later Gunga (65 nm); Vejle (45 nm XCGPU); Oban (32 nm) | CONFIRMED family; per-stepping PARTIALLY CONFIRMED | Wikipedia; XenonLibrary chip matrix (Y1/Y2/Rhea/Elpis/Kronos/XCGPU/Oban) |
| Lineage | R400 “Crayola” branch (not R520/R300); R500 naming avoided; later R600/TeraScale + Imageon Z430/Adreno 200 cousins | PARTIALLY CONFIRMED (ATI lineage debated; Wikipedia pairs R520, Copetti disputes) | Copetti “Architecture of Xenos” + Wikipedia; document disagreement, don’t resolve |
| Clock | 500 MHz parent + 500 MHz daughter (target clocks per Beyond3D note) | CONFIRMED as shipped target; PARTIALLY CONFIRMED as exact silicon guarantee | Beyond3D lineage; Wikipedia 500 MHz |
| Process | 90 nm TSMC parent (launch); 65 nm Gunga/80→65 nm eDRAM shrinks; 45 nm Vejle combined; 32 nm Oban integrated | PARTIALLY CONFIRMED (convergent tables, needs fab docs) | Wikipedia; ConsoleMods; XenonLibrary matrix |
| Transistors | ~232M parent + ~105M daughter (80M DRAM + ~70M logic per Beyond3D math) = 337M package | PARTIALLY CONFIRMED (Beyond3D via ATI architects; 150M figure explicitly corrected as wrong in article) | Beyond3D article lineage; Wikipedia package 337M |
| API | Superset DirectX 9.0c / “DirectX Xbox 360”, Shader Model 3.0+ , MEMEXPORT, tessellation, predicated tiling | CONFIRMED at feature-name level; instruction details UNKNOWN in Cycle 1 | Beyond3D caps table; Copetti |

## Why unified — analysis (INFERRED, cited)

- Pre-Xenos: fixed rasterizer → programmable vertex (SGI/Reality, Flipper heritage via ArtX→ATI) → programmable pixel (Nvidia). Vertex/pixel imbalance idles silicon; unified pool lets any ALU do vertex or pixel, improving utilization + power gating. Copetti + Beyond3D reasoning. Mark as analysis, not ATI datasheet quote.
- ATI power argument: clock-gate idle arrays vs discrete vertex/pixel blocks; low-power DVD modes, block-level gating. Beyond3D “Power and Die Savings”. PARTIALLY CONFIRMED (vendor claim via press).

## What Cycle 1 does NOT claim

- No register map, no command-buffer format, no microcode. Those are UNKNOWN until Xenia GPU code + libxenon framebuffer + RE writeups are audited in Cycle 2.
- No invented ALU counts beyond cited groupings (see pipeline page).

## Sources / References

- Wikipedia “Xenos (graphics chip)”, `https://en.wikipedia.org/wiki/Xenos_(graphics_chip)` — 500 MHz, 232M+105M, 240 units in 3×80, 16 TF/TA, eDRAM 10 MB 256 GB/s, 240 GFLOPS. Tertiary convergence. Accessed 2026-10-04.
- Copetti Graphics “Overview / Architecture of Xenos”, `https://www.copetti.org/writings/consoles/xbox-360/` — R400 vs R520 dispute, unified-shader debut, R600/Imageon lineage. Accessed 2026-10-04.
- Beyond3D “ATI Xenos” (`http://www.beyond3d.com/articles/xenos/`, via mirror thread `https://www.pcreview.co.uk/threads/beyond3d-article-on-ati-xenos-the-graphics-processor-of-xbox-360.1999893/`) — 232M correction, 500 MHz targets, unified arrays, MEMEXPORT/tessellation. Accessed 2026-10-04 via search mirror; original to be Archive-verified Cycle 2.
- XenonLibrary “GPU” chip matrix (Y1/Y2/Rhea/Elpis/Kronos/XCGPU/Oban), `https://xenonlibrary.com/wiki/GPU` — search-verified 2026-10-04; direct fetch 403, needs retry/Archive. Marked accordingly.
- TechPowerUp “ATI Xbox 360 GPU 90 nm Specs”, `https://www.techpowerup.com/gpu-specs/xbox-360-gpu-90nm.c1919` — 181 mm², 232M, 240 shaders, 16 TMUs/ROPs lineage. Tertiary.
