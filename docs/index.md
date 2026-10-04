# Index — Xbox 360 Technical Encyclopedia

> Navigation hub. Every link must resolve to a real file. No placeholder links to non-existent docs.

## 0. Methodology

- [Confidence levels](methodology/confidence-levels.md) — `CONFIRMED / PARTIALLY CONFIRMED / INFERRED / UNCONFIRMED / UNKNOWN`
- [Source priority](methodology/source-priority.md)
- [Contribution and quality gates](methodology/contribution-gates.md)

## 1. Architecture

- [System overview](architecture/overview.md)

## 2. CPU — Xenon

- [Xenon overview](cpu/xenon-overview.md)
- [Cores, threads and VMX128](cpu/xenon-cores-threads-vmx.md)
- [XBAR, L2 cache and memory path](cpu/xenon-xbar-l2-memory-path.md)

## 3. GPU — Xenos + eDRAM

- [Xenos overview](gpu/xenos-overview.md)
- [Unified shaders, ROPs, texturing, tiling](gpu/xenos-pipeline-tiling.md)
- [eDRAM daughter die](gpu/edram.md)
- [Bandwidth and interconnects](gpu/bandwidth-interconnects.md)

## 4. Memory

- [Unified 512 MB GDDR3](memory/unified-memory-512mb-gddr3.md)

## 5. Boot

- [Retail boot process](boot/boot-process-retail.md)
- [Bootloaders: 1BL, CB/CB_A/CB_B, CD, CF/CG](boot/bootloaders-1bl-cb-cd-cf.md)
- [Devkit boot (SB/SC/SD/SE)](boot/boot-devkit.md)

## 6. Hardware revisions

- [Motherboards Xenon → Winchester](hardware/revisions.md)

## 7. Executables and packages

- [XEX format](executables/xex-format.md)
- [STFS / CON / PIRS / LIVE](packages/stfs.md)

## 8. Research landscape

- [Free60 project](research/free60.md)
- [XenonLibrary](research/xenonlibrary.md)
- [Xenia emulator](research/xenia.md)
- [Copetti practical analysis](research/copetti-analysis.md)

## 9. References

- [Master sources](references/master-sources.md)
- [Glossary](../glossary.md)

## 10. Hardware I/O and debug (Cycle 2)

- [Southbridge and I/O](hardware/southbridge-io.md)
- [POST bus](hardware/post-bus.md)

## 11. Storage and filesystems (Cycle 2)

- [NAND flash system](storage/nand-flash-system.md)
- [DVD drive](storage/dvd-drive.md)
- [HDD module](storage/hdd-module.md)
- [FATX filesystem](filesystem/fatx.md)

## 12. System software (Cycle 3)

- [Kernel versions and stack](system/kernel-versions-stack.md)

## 13. Profiles and databases (Cycle 3)

- [XDBF](profiles/xdbf.md)
- [GPD](profiles/gpd.md)

## 14. Xbox Live and Marketplace (Cycle 3)

- [Catalog query API 2011, historical](xbox-live/marketplace-catalog-api-2011.md)
- [Dashboard EPIX channels, historical RE](xbox-live/dashboard-epix-channels.md)
- [Public services and hard boundaries](xbox-live/xbox-live-services-public.md)
- [Marketplace closure 2024](xbox-live/marketplace-closure-2024.md)

## 15. Reverse engineering (Cycle 3)

- [RE tooling notes](reverse-engineering/re-tooling-notes.md)

---

## Planned (not yet created — do not link until files exist)

Cycle 4+: USB, Ethernet, audio/video, SMC, RF, hypervisor ABI, kernel exports, XAM, GDFX/GDF, XConfig, saves, matchmaking/sockets, updates/errors, XDK/devkits, Xenia source walk.
