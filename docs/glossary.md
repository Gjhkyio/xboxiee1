# Glossary (Cycle 1 seed — growing)

> Each entry: meaning, where it appears, confidence, relevant sources. Xenon vs Xenos disambiguation first.

| Term | Meaning | Appears in | Confidence | Sources |
|---|---|---|---|---|
| Xenon (CPU) | IBM Waternoose / XCPU; 3×PPE @3.2 GHz, 6 threads, VMX128, 1 MB L2 | CPU docs, boot 1BL | CONFIRMED | Free60 Xenon CPU; Copetti |
| Xenon (motherboard) | Launch 90/90 nm board, no HDMI, 203 W | Revisions | CONFIRMED | ConsoleMods; Wikipedia |
| Xenos (GPU) | ATI C1 parent @500 MHz; unified shaders; northbridge+mem controller | GPU docs | CONFIRMED | Wikipedia Xenos; Copetti; Beyond3D |
| XCGPU / Vejle | 45 nm combined CPU+GPU (Trinity/Corona); Vejle die | Revisions | PARTIALLY CONFIRMED | ConsoleMods; XenonLibrary matrix |
| Oban | 32 nm combined + on-die eDRAM (Winchester) | Revisions | PARTIALLY CONFIRMED | Wikipedia; XenonLibrary |
| Gunga | 65 nm Xenos shrink | GPU/revisions | PARTIALLY CONFIRMED | XenonLibrary; Wikipedia |
| Y1/Y2/Rhea/Elpis/Kronos | GPU steppings across Zephyr/Falcon/Jasper | Revisions/GPU | PARTIALLY CONFIRMED | XenonLibrary matrix; ConsoleMods |
| Edifis / Styx-90 / Styx-65 | eDRAM steppings | eDRAM | PARTIALLY CONFIRMED | XenonLibrary; Wikipedia |
| PPE / PPU | PowerPC Processor Element/Unit; Xenon has 3 (no SPEs) | CPU | CONFIRMED | Copetti; Free60 |
| SPE / SPU | Synergistic Processor (Cell-only, not in Xenon) | CPU context | CONFIRMED | Copetti PS3 compare |
| VMX / VMX128 | SIMD unit; VMX128 = 128 regs/thread, D3D/dot-product ext | CPU | CONFIRMED feat.; PARTIALLY encoding | Copetti; Free60 |
| XBAR | Mesh interconnect for 3 PPEs @3.2 GHz | CPU | CONFIRMED role | Copetti |
| EIB | Cell Element Interconnect Bus (PS3 compare, ring) | CPU context | CONFIRMED | Copetti |
| UMA | Unified Memory Architecture (shared 512 MB) | Memory/arch | CONFIRMED | Copetti |
| GDDR3 | Graphics DDR3 SDRAM type (512 MB) | Memory | CONFIRMED | Copetti; specs |
| PHY (FSB) | 2×16-lane serial CPU↔GPU link @5.4 GHz →10.8 GB/s/dir | CPU/GPU BW | PARTIALLY CONFIRMED | Copetti |
| XPS | Xbox Procedural Synthesis (CPU→GPU streaming via L2-lock/`xDCBT`) | CPU/GPU | PARTIALLY CONFIRMED | Beyond3D; Wikipedia |
| `xDCBT` | Extended Data Cache Block Touch (L1-fill bypassing L2; later purged) | CPU | PARTIALLY CONFIRMED | Copetti |
| ROP | Render Output Unit (8 in Xenos package) | GPU/eDRAM | PARTIALLY CONFIRMED | Wikipedia; Beyond3D |
| MSAA | Multisample AA (max 4× on Xenos per article) | GPU | PARTIALLY CONFIRMED | Beyond3D |
| Hi-Z / Hi-Stencil | Hierarchical culling buffers | GPU | PARTIALLY CONFIRMED | Beyond3D |
| MRT | Multiple Render Targets (4, per-target blend) | GPU | PARTIALLY CONFIRMED | Beyond3D |
| MEMEXPORT | Shader-array → RAM fetch/push (GPGPU precursor) | GPU | PARTIALLY CONFIRMED | Beyond3D |
| 1BL | CPU-ROM first bootloader | Boot | PARTIALLY CONFIRMED | Free60 |
| CB / CB_A / CB_B | Early bootloaders (+VM: PCI/JTAG-UART/SMC/memory) | Boot | PARTIALLY CONFIRMED | Free60 |
| CD / CE / CF / CG | Later stages; CE base kernel (LZX) + CF/CG delta patches | Boot | PARTIALLY CONFIRMED | Free60 (CE wording preserved) |
| HV | Hypervisor (target of CD jump; kernel+dashboard after) | Boot | CONFIRMED existence | Free60 |
| SB/SC/SD/SE | Devkit counterparts (SC=HW-init VM; SE=pre-patched HV+kernel) | Boot devkit | PARTIALLY CONFIRMED | Free60 |
| SMC | System Management Controller (handshake bit per CB) | Boot/HW | PARTIALLY CONFIRMED | Free60 (detail queued) |
| POST | Power-On Self-Test output codes (kernel list reference) | Boot | PARTIALLY CONFIRMED | Free60 |
| XEX / XEX2 | Executable container (PPC PE + crypto/pack) | Executables | PARTIALLY CONFIRMED | Free60 XEX |
| STFS / CON / PIRS / LIVE | Secure Transacted FS + package signing classes | Packages | PARTIALLY CONFIRMED | Free60 STFS |
| SVOD | Descriptor/type for on-demand volumes (0x1 vs STFS 0x0) | Packages | PARTIALLY CONFIRMED | Free60 STFS |
| PEC | Profile Embedded Content (STFS-algo, avatar use) | Packages | PARTIALLY CONFIRMED | Free60 STFS |
| ANA / HANA / KSB / PSB | Video-encoder / clockgen + southbridge generations | Revisions/HW | PARTIALLY CONFIRMED | ConsoleMods; revisions |
| RROD / RoD | Red Ring (of Death) / Ring of Light error segments | Revisions/research | CONFIRMED existence | XenonLibrary Errors; guides |
| JTAG / RGH / Bad Update | Public hack families (descriptive only here) | Research | CONFIRMED existence | Free60 Hacks nav |
| XDK | Xbox Development Kit (XLAST/XDK kernel queued) | Research/boot | CONFIRMED existence | Free60 nav |
| PIX | CPU profiler in SDK (600-cycle miss anecdote) | CPU/memory | PARTIALLY CONFIRMED | Copetti |
| LDIC / LZX | MS compression (XEX sections / kernel) | Exec/boot | PARTIALLY CONFIRMED | Free60 |
| RotSumSHA1 | Hash noted in boot verification (exact def UNKNOWN) | Boot | UNCONFIRMED def | Free60 wording only |
