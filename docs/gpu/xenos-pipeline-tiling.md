# Xenos pipeline, shaders, texturing, tiling

> Micro-architecture as reported in Beyond3D/Copetti lineage. No invented registers.

## Shader array — PARTIALLY CONFIRMED

| Claim | Detail | Source chain |
|---|---|---|
| 3 SIMD arrays × 16 ALU (?) / 80 vector units each = 240 vector units; 48 ALUs phrasing in early press | Early “48 ALUs” shorthand vs “3×80 units, 10 FLOPs per unit per cycle (5×MAD), 240 GFLOPS, 240B shader ops/s” | Beyond3D; Wikipedia 240 GFLOPS/240 units; Copetti. Keep both phrasings, note press simplification. |
| Each vector unit Vec4 + scalar (“5D”/cycle), FP32 internal, no partial-precision requirement | FP32 IEEE, 10 FLOPs/cycle | Beyond3D lineage |
| Dynamic scheduling: any array vertex or pixel at a snapshot; load-balancing via vertex/pixel export-buffer occupancy equation (ATI declined details) | Scheduler exists; exact equation UNKNOWN | Beyond3D “Shader Type Load Balancing” |
| Threading: 16-wide threads (16 verts or 4×2×2 quads), many independent threads to hide latency/texture stalls; ~95% array efficiency claimed in ATI testing | Efficiency figure is vendor claim | Beyond3D “Thread Handling” |
| Grouper/scan-converter needed (threads span multiple tris of same state; small-tri efficiency) | Design note | Beyond3D |
| Caps exceed SM3.0; Table of vertex-vs-pixel caps unified; MRT 4 targets with per-target blend; Hierarchical-Z + Hierarchical-Stencil; Alpha-to-Mask; kill works for verts (retired post-setup); 32-instruction?/loop limits + F-Buffer for longer shaders | Feature names CONFIRMED; limits PARTIALLY CONFIRMED | Beyond3D “Capabilities” (chart on original page) |

## Texture units — PARTIALLY CONFIRMED

- 16 filtered (TF, Bilinear/clock, Trilinear/Aniso via multi-cycle loop + per-unit address processor with offset/shader ability) + 16 vertex-fetch (unfiltered/point) = 16+16 samplers. All UMA memory fetchable, not eDRAM. 64 texture formats, DXTC/S3TC + ATI2N/3Dc, no float compression. Via Beyond3D “Texture Processing”. Needs ATI/XDK cross-check.

## ROP/eDRAM operation — PARTIALLY CONFIRMED

- 8 pixels/cycle; 192 “processing elements” = 8×MSAA compare/write paths; double-Z when no color; 32 color or 64 Z/stencil ops per cycle with 4×MSAA; 8 px×4×MSAA sustained without lossless compression due to 256 GB/s (26–134 GB/s demand calc in article). Beyond3D “Pixel and eDRAM Operation”.
- Parent→daughter link is 1/8 eDRAM BW (common color per samples + losslessly packed Z per 2×2 quad); unpack to samples on daughter; resolve on daughter; write-back to UMA efficient sequential. Same source.
- Formats: FP10 (10-10-10-2, 3b exp/7b mantissa, ±32 range) same cost/size as 32-bit int; INT16/FP16 also; orthogonal MSAA across formats. Same source.
- Hierarchical-Z: tile-coarse max-Z, 64 px/cycle discard, Z-only pass populates; sized for HDTV (smaller than PC range). Same source.

## Tiling (predicated) — PARTIALLY CONFIRMED

- Formula cited: `Back = Pixels×MSAA×(Color+Z)`; Front in UMA only; 10 MB fits 720p/1080i/640×480 without MSAA and 640×480 4×MSAA at 32+32-bit, but not HD+MSAA → split into tiles (2–3 tiles typical; 720p 4×MSAA ≈3 tiles @ ~95% of 2× perf per ATI quote). Beyond3D “Tiled Rendering” with charts on original page.
- Method: Z-only pass records per-object screen extents; per-tile re-process (transformed verts cached); resolve tile → UMA while next renders. Similar to TBDR but with larger tiles + Z-prepass optimization. Same source.
- Render-to-texture via eDRAM then to UMA (optionally resolved or kept MS); sizes must fit 10 MB. Same source.

## Display/forum note

- Max 4×MSAA (no higher; 2×/0× selectable; fixed sample pattern, horizontal axis note). Beyond3D. PARTIALLY CONFIRMED.

## Sources / References

- Beyond3D Xenos series via mirror (see `xenos-overview.md` Sources) — shader arrays, texture, ROP/eDRAM, Hi-Z, tiling, MEMEXPORT/tessellation/display/power sections. Accessed 2026-10-04. Original charts at `http://www.beyond3d.com/articles/xenos/index.php?p=05` and `?p=09` to be Archive-verified Cycle 2.
- Copetti Graphics (unified-shader context), `https://www.copetti.org/writings/consoles/xbox-360/` — corroborates unified debut + triple-memory framing.
- Wikipedia Xenos specs (240 units, 16 TF/TA, 4 Gpix/s, 8 Gtex/s, 16 Gsamples/s 4×MSAA) — tertiary convergence.
