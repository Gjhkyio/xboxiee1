# NAND flash system — proprietary MS format

> Source: Free60 “NAND Flash System” (fetched 2026-10-04). PARTIALLY CONFIRMED (single detailed RE source). XenonLibrary “Nand” corroboration queued.

## Role — PARTIALLY CONFIRMED

- NAND holds console-specific (keyvault, config blocks) + system (bootloaders, kernel/HV, dashboard files). Split: keyvault/bootloaders/config section + dashboard-files section. Files stored transactionally (revertable changes). Per Free60 lede.
- Sizes per revision: 16 MB base; 256/512 MB Jasper Arcade (MU in NAND); 16 MB or 4 GB (Phison MMC/eMMC/Hynix) Corona/Waitsburg (see revisions page).

## Basic geometry — PARTIALLY CONFIRMED

- Pages (usually 512 B + 16 B EDC/ECC spare; 64 B spare on big-block) combine into blocks (usually 16 pages; 32 for big-block). Per page.
- Metadata (non-eMMC) per page: block number, flags, checksum; 3 layouts tabled: Small Block, Big Block on Small NAND, Big Block (C structs on page — copy verbatim there, do not re-derive here). Includes BlockID, FsSequence, BadBlock, FsSize, FsPageCount, FsBlockType:6 + ECC bits, 14-bit ECD.
- Custom ECC/EDC algorithm with C `checkEcc` on page (LE byte order, poly `0x6954559` in loop, `~val` finalize, compare spare 0xC–0xF). Presented as-is; not tested here. Mark code UNVERIFIED (copied from source, not executed).

## Image header anchors — PARTIALLY CONFIRMED

- Byte 0 must be 0xFF (else invalid image, per page).
- Copyright string at 0x10 (read in two parts skipping year; some valid images “zeropair” variant).
- Flash version @0x2 (2 B); CB offset @0x8 (4 B); CF1 offset after (4 B); keyvault offset @0x6C (4 B); SMC length + offset @0x78 (4 B each).

## SMC + XeLL layout notes (historical, PARTIALLY CONFIRMED)

- SMC section header “finish later” on page — explicitly incomplete. Do not fill.
- XeLL 1.3 MB example layout (offsets for header/exploit/padding/SMC/keyvault/CB 1921/CD 1921/CE 1888/CF-CG 4532 + backup/main XeLL). Historical exploit-image map (JTAG-era versions 1921/1888/4532/4548). Preserve as example, not universal map. Versions vary by console/dash; do not generalize.

## Queued

- XenonLibrary “Nand” (`https://xenonlibrary.com/wiki/Nand` — chips hold system SW/SMC/etc; 256/512 MB + 4 GB contain MU), Free60 `NAND_Bad_Blocks`, `NAND_Reading`, `Fusesets`, ConsoleMods NAND tooling (descriptive only).

## Sources / References

- Free60 “NAND Flash System”, `https://free60.org/System-Software/NAND_File_System/` — all sections above + C code + XeLL map. Fetched 2026-10-04.
- XenonLibrary “Nand” — search excerpt 2026-10-04; full read queued.
