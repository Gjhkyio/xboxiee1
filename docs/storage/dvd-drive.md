# DVD drive — models, interface, on-disc layout (as documented)

> Source: Free60 “DVD Drive” (fetched 2026-10-04). Page explicitly splits Confirmed Facts vs Speculation — preserved here.

## Models — PARTIALLY CONFIRMED

- Hitachi-LG GDR-3120L (multi ROM revs), Toshiba/Samsung TS-H943 (MS25/MS28), BenQ VAD6038, Lite-On DG16D2S. Assignment by factory/batch/date. Per page.

## Interface — PARTIALLY CONFIRMED

- 7-pin SATA standard + custom 2×6-pin ~2 mm power (Molex Milli-Grid-like; Hirose also). Boots (rapid power-light flash like ejecting) with SATA+power unplugged. Internal name `\Device\CdRom0\`. Per page.
- Main LG processor Panasonic MN103S94FDA (Confirmed Facts section). Per page.
- Drive↔console pairing via DVD key in drive FW; interchange requires key match; kernels ≥4532(?) also expect same model string (page’s “?” preserved — UNCONFIRMED threshold).

## On-disc — PARTIALLY CONFIRMED + Speculation split

- CONFIRMED (page): BCA present but not used as security check; fake ToC (video section only); hotswap + debug-ATAPI end-of-disc trick + scene-tool offset hack (Xbox1 tools + changed read offset) to reach game area; standard area ~0xDB0 sectors (~7 MB) DVD-Video “this is a game disc”; game data at LBA offset 0x1FB20 (past nominal leadout) but DVD-compliant ECC/seed/EDC/layout; unreadable ring between areas (weak/empty sectors hypothesis).
- SPECULATION (page, do not cite as fact): 12× DVD+R/RW + CD-DA/CD-ROM/CD-R/RW/WMACD/MP3CD/JPEG-PhotoCD + Xbox1 back-compat list; “doesn’t work on standard PC yet”; visible thin ring on PGR3 disc as laser barrier.
- XDVDFS raw FS similar to Xbox1 disks; raw-ISO extraction tools exist (names/versions queued; no bypass/FW-flash instructions here).

## Sources / References

- Free60 “DVD Drive”, `https://free60.org/Hardware/Console/DVD_Drive/` — models, power/SATA, CdRom0, MN103S94FDA, BCA/ToC/hotswap/offsets, confirmed-vs-speculation split. Fetched 2026-10-04.
