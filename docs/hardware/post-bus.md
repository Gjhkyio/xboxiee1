# POST bus — power-on self-test codes

> Source: Free60 “POST” (fetched 2026-10-04), crediting `xdevwiki.tk POST_Codes`. PARTIALLY CONFIRMED (single curated table, broad but needs per-code validation). Descriptive only; no glitch timing instructions.

## What POST is — PARTIALLY CONFIRMED

- 8-bit diagnostic bus; bootloaders write progress codes; hang point indicates failing stage. RGH-era use was tracking init to pick reset moment (RGH1: CB verifying CD hash; post-14717 bootloaders removed codes + added random delays — per page, historical countermeasure note).
- Holds last code persistently → readable with multimeter (bit order 76543210; example `00111010 = 0x3A = CD auth success` per page).

## Electrical/pinout — PARTIALLY CONFIRMED

- Phat: `DBG_WN_POST_OUT0..7 / BIT7..BIT0` = FT6U8/FT6U2/FT6U3/FT6U4/FT6U5/FT6U6/FT6U7/FT6U1 (verbatim table).
- Levels: 1.2 V Phat / 1.8 V Slim (per page). Needs board-level verification before probing; do not probe without proper level handling.

## Writing POST (as documented)

- Write 8-bit code shifted left 56 to real-mode `0x8000020000061010` (PPC asm on page: build address in r7 via `li/oris/rldicr/ori`, `li r3,code; rldicr r3,r3,56,7; std r3,0(r7)`; paging caveat noted). Preserved as documentation; not a how-to.

## Code domains (full table on source — summary here, details there)

- `0x10–0x1E` 1BL progress (FSB config, CB fetch/header/verify, HMAC/RC4/SHA/RSA/branch) + `0x81–0x98` 1BL panics (machine-check … sig-verify … size).
- `0xD0–0xDB` CB_A (Slim): entry/self-copy to `0x800002000001C000`, fuse copy, CB_B offset/header/fetch/HMAC/RC4/SHA-verify/branch (RGH2 note at `0xDA` per page) + `0xF0–0xF3` CB_A panics.
- `0x20–0x3B` CB: SoC/secotp/seceng/SYSRAM(EDRAM)/3BL-CC + CD fetch/HMAC/RC4/SHA/RSA + HWINIT/TLB-relocate/PCI-INIT + branch with memory-encryption setup + `0x9B–0xB0` CB panics (secotp/fuses/SMC-HMAC/CB-revocation/HWINIT/CD-auth/interrupt/RAM-size/console-type).
- `0x40–0x53` CD: paging, CE fetch/HMAC/RC4/SHA-verify (RGH1 note at `0x49`), CF load, LZX expand, caches, fuses, CF1/CF2 slots, HV branch + cert verify + `0xB1–0xB8` CD panics.
- `0xC1–0xC8` CE/CF LZX/CG-auth panics (LDI frag/window/decompress).
- `0x58–0x5E` HV init (SoC MMIO, XEX training, keyring/keys, SoC interrupts) + `0xFF` fatal.
- `0x60–0x79` Kernel init (HAL0, processes, debugger, memory, stacks, objects, phase1 thread/processors, keyvault, HAL1, SFC, security, key-ex-vault, settings, power, video, audio, bootanim+XMA/XAudio, SATA, shadowboot, dump, sysroot, drivers, STFS, XAM load).

> Full per-code table lives on the Free60 page; do not duplicate all 100+ rows here until validated. This file is the index + electrical + method summary.

## Sources / References

- Free60 “POST”, `https://free60.org/POST/` — pinout, read/write method, full domain table, RGH-era notes, xdevwiki credit. Fetched 2026-10-04.
