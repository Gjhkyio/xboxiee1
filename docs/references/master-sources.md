# Master sources (Cycle 1 — verified 2026-10-04 unless noted)

> Priority order per `docs/methodology/source-priority.md`. Each entry: URL, title, author/date when known, what evidence it provides, access note.

## Primary / near-primary (to be fully fetched Cycle 2)

1. IBM Jeffrey Brown — “Application-customized CPU design: The Microsoft Xbox 360 CPU story”, developerWorks. `https://web.archive.org/web/20081205055833/http://www-128.ibm.com:80/developerworks/power/library/pa-fpfxbox/index.html?ca=drs-` — IBM account of Xenon design. Linked from Free60 Xenon CPU. Not yet re-fetched Cycle 1.
2. IBM Gschwind et al. VMX/Cell notes; Biallas opcode note; Siljenberg PHY note — via Copetti bib (`cpu-gschwind`, `cpu-biallas`, `cpu-siljenberg`). To be fetched Cycle 2.
3. ATI architects via Beyond3D “ATI Xenos” series, original `http://www.beyond3d.com/articles/xenos/` (targets `?p=05`, `?p=09`, `bandwidths.gif`, `edrambandwidth.gif`). Cycle 1 via mirror thread `https://www.pcreview.co.uk/threads/beyond3d-article-on-ati-xenos-the-graphics-processor-of-xbox-360.1999893/` — 232M/105M split, 500 MHz targets, shader/texture/ROP/tiling/MEMEXPORT/power. Original needs Archive verification.
4. FCC/teardown/datasheets — queued Cycle 2 (no claims yet).

## Public source code (queued for audit, not yet cited as authority)

5. Xenia upstream, `https://github.com/xenia-project/xenia` — CPU/GPU/kernel reimplementation. Search-verified.
6. Xenia Canary fork, `https://github.com/xenia-canary/xenia-canary` — experimental fork. Search-verified.
7. Free60 wiki source, `https://github.com/Free60Project/wiki` — edit/raw provenance for every wiki claim. Search-verified.
8. Velocity, `https://github.com/Gualdimar/Velocity` — STFS tooling (listed on Free60 STFS). Not yet audited.
9. extract360.py, `https://github.com/rene0/xbox360/blob/master/extract360.py` — STFS analysis (listed, Py2.5-era). Not yet audited.
10. `https://github.com/TEIR1plus2/Xbox-Reversing` — 1BL/CB notes (search excerpt only Cycle 1). Full read queued.

## Well-documented RE / hardware reference (fetched or search-verified Cycle 1)

11. Free60 Wiki — Boot process, `https://free60.org/System-Software/Boot_Process/` — chain + per-stage + devkit + kernel/XEX order. Fetched 2026-10-04. Evidence: RE documentation with `1bl_Code`/`CB_Code` links.
12. Free60 Wiki — Xenon CPU, `https://free60.org/Hardware/Console/Xenon_%28CPU%29/` — specs + Linux SMP note + IBM links. Fetched 2026-10-04.
13. Free60 Wiki — XEX, `https://free60.org/System-Software/Formats/XEX/` — self-declared “Speculation”; header/ID/security tables + tools/history. Fetched 2026-10-04.
14. Free60 Wiki — STFS, `https://free60.org/System-Software/Formats/STFS/` — CON/PIRS/LIVE/PEC/volume/file/hash tables + C# snippets + tools. Fetched 2026-10-04.
15. XenonLibrary — Main, `https://xenonlibrary.com/wiki/Main_Page`; GPU, `https://xenonlibrary.com/wiki/GPU`; Bootloaders, `https://xenonlibrary.com/wiki/Bootloaders`; Errors, `https://xenonlibrary.com/wiki/Errors` — hardware reference scope + chip matrix + eDRAM + chain summary. Search-verified 2026-10-04; direct article fetch 403, Archive retry queued.
16. ConsoleMods Wiki — Buying Guide, `https://consolemods.org/wiki/Xbox_360:Buying_Guide` — PCB P/N, CPU/GPU/eDRAM, amps/PSU, NAND, MFG windows, HANA/KSB, POST_OUT, Phison/Hynix warnings, photos. Accessed 2026-10-04.

## Specialist analysis (fetched Cycle 1)

17. Copetti — Xbox 360 Architecture, `https://www.copetti.org/writings/consoles/xbox-360/` — CPU/XBAR/L2/FSB/GDDR3/Xenos synthesis + bibliography. Fetched 2026-10-04.
18. TechPowerUp — ATI Xbox 360 GPU 90 nm, `https://www.techpowerup.com/gpu-specs/xbox-360-gpu-90nm.c1919` — 181 mm², 232M, 240 shaders. Tertiary. Search-verified.
19. VGCL — Every Xbox 360 Model, `https://www.videogameconsolelibrary.com/xbox-360-models/` (2026-06-08) — 8-rev narrative + RROD account. Search-verified.
20. Weekend Modder — Identify console, `https://weekendmodder.com/identify.html` — HDMI/power check, J2C1/J2C3 orientation, IHS photos. Search-verified.

## Tertiary (convergence only)

21. Wikipedia — Tech specs, `https://en.wikipedia.org/wiki/Xbox_360_technical_specifications`; Xenon, `https://en.wikipedia.org/wiki/Xenon_(processor)`; Xenos, `https://en.wikipedia.org/wiki/Xenos_(graphics_chip)`; Free60, `https://en.wikipedia.org/wiki/Free60` — baselines only. Accessed 2026-10-04.
22. Emulation General Wiki — Xenia, `https://emulation.gametechwiki.com/index.php/Xenia`; Xenia Quickstart, `https://github.com/xenia-project/xenia/wiki/quickstart` — scope + no-system-files note. Search-verified.

## Archive / history (examples cited on Free60 pages, not re-verified Cycle 1)

- Back-compat `default.zip` (Nov/Dec 2005), MCE Rollup2 `XboxMcx.xex`, HD-DVD update, `xextools-0.2`, `xexdump` — links on Free60 XEX page (Archive-hosted). Historical only.
