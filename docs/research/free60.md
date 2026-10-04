# Free60 project — research landscape

## What it is — CONFIRMED

- Community free-software / Linux-on-360 effort + wiki documenting hardware, boot, formats, hacks, homebrew, Linux ports, dev toolchains. Goals met Mar 2007 via hypervisor software vulnerability enabling Linux (Wikipedia “Free60” summary). Wiki now at `https://free60.org/`, source `https://github.com/Free60Project/wiki` (Material for MkDocs).
- Cycle-1 audited pages: `System-Software/Boot_Process`, `Hardware/Console/Xenon_(CPU)`, `System-Software/Formats/XEX`, `System-Software/Formats/STFS`. All fetched 2026-10-04.

## Why it matters here

- Best Cycle-1 boot/format evidence (chain, per-stage roles, header tables) despite XEX page’s own “Speculation” caveat.
- Extensive nav: Hacks (Bad Update, RGH, SMC/JTAG, King Kong), HW (Accessories, Console Revisions/Case/DVD/Ethernet/Fusesets/HDD/Memory/Motherboard/RF, 8051/LevelShifter, NAND bad-blocks/reading), System SW (FMIM/GPD/PEC/SPA/STFS/XDBF/XCP/XEX, FATX/GDFX, Error Codes, Kernel, Shadowboot, XConfig, XDK Kernel), Linux/LibXenon/toolchain, Xenos framebuffer.
- Queued Cycle 2: `1bl_Code`, `CB_Code`, `Fusesets`, `NAND_Reading`, `FATX`, `GDFX`, `Kernel`, `Shadowboot`, `XConfig`, `LibXenon`, `Xenos_Framebuffer`, hack pages (descriptive/architectural only, no bypass instructions).

## Confidence

- CONFIRMED as existence/scope of project + wiki structure (direct fetch).
- Technical claims inherit per-page labels (see sibling docs).

## Sources / References

- Free60 Wiki home/nav (via fetched pages), `https://free60.org/System-Software/Boot_Process/` etc. Fetched 2026-10-04.
- Wikipedia “Free60”, `https://en.wikipedia.org/wiki/Free60` — Mar-2007 hypervisor vuln milestone. Search-verified 2026-10-04.
- GitHub `Free60Project/wiki`, `https://github.com/Free60Project/wiki` — edit/raw links on every page. Search-verified 2026-10-04.
