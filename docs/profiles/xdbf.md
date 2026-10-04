# XDBF — Xbox Data Base File (generic database)

> Source: Free60 “XDBF” (fetched 2026-10-04). PARTIALLY CONFIRMED. Used for GPD and SPA; SPA linked into XEX at compile, dash generates GPD/save metadata/images from it; XAM DataFile class handles ops.

## Header — 24 bytes (0x18), PARTIALLY CONFIRMED

Byte order follows magic: LE magic → whole file LE (GFWL); BE magic → Xbox file.

| Offset | Len | Type | Info |
|---|---|---|---|
| 0x0 | 0x4 | ASCII | Magic `0x58444246` (`XDBF`) |
| 0x4 | 0x4 | u32 | Version `0x10000` |
| 0x8 | 0x4 | u32 | Entry table length (entries) |
| 0xC | 0x4 | u32 | Entry count (used) |
| 0x10 | 0x4 | u32 | Free-space table length (entries) |
| 0x14 | 0x4 | u32 | Free-space entry count |

Table lengths are multiples of 512 by preference; reader accepts smaller (per page).

## Entry table — PARTIALLY CONFIRMED

- Each entry 18 bytes (0x12); table bytes = EntryTableLength × 18; only first EntryCount used.
- Entry: namespace u16 @0x0 (see GPD namespaces), ID u64 @0x2, OffsetSpecifier u32 @0xA, Length u32 @0xE.

## Free-space table — PARTIALLY CONFIRMED

- Each entry 8 bytes: OffsetSpecifier u32 @0x0 + Length u32 @0x4. Updated on size change. Last entry is not free space: OffsetSpecifier = data length (file len − header − tables), Length = −1 − OffsetSpecifier.

## Data offset formula (verbatim)

`((EntryTableLength × 18) + (FreeSpaceTableLength × 8) + 24) + OffsetSpecifier`

## Sources / References

- Free60 “XDBF”, `https://free60.org/System-Software/Formats/XDBF/` — all tables above + GPD/SPA/XAM notes. Fetched 2026-10-04.
- Queued: emoose `Xbox360Container.bt` 010 template + `stfschk`, Free60 SPA/PEC pages.
