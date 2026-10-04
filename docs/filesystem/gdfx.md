# GDFX — Game Disc Format for Xbox (disc/SVOD filesystem)

> Source: Free60 “GDFX” (fetched 2026-10-04). PARTIALLY CONFIRMED, short page. Also noted on Free60 “360 System Software” page as `GDFX/XSF` on X360 CD/DVD media.

## Placement — PARTIALLY CONFIRMED

- Used on game discs and SVOD devices. SVOD variant has extra sectors with a hash of 2 segments (4098 bytes); each segment 2048 bytes; first segment starts with `440816472` (LE); 32nd segment is a descriptor (page wording preserved; numeric base/format ambiguous — do not reinterpret).

## Descriptor (32nd segment) — PARTIALLY CONFIRMED

| Offset | Len | Type | Info |
|---|---|---|---|
| 0 | 20 | string | `MICROSOFT*XBOX*MEDIA` |
| 20 | 4 | int | Root Sector |
| 24 | 4 | int | Root Size |
| 28 | 8 | FileTime | Creation Time |

## Directory entries — PARTIALLY CONFIRMED

| Offset | Len | Type | Info |
|---|---|---|---|
| 0 | 2 | int | unk |
| 2 | 2 | int | unk |
| 4 | 4 | int | Sector |
| 8 | 4 | int | Size |
| 12 | 1 | int | Flags? |
| 13 | 1 | int | namelength |
| 14 | namelength | string | name |

Dirent attribute bitmask (verbatim): READONLY 0x1, HIDDEN 0x2, SYSTEM 0x4, DIRECTORY 0x10, ARCHIVE 0x20, DEVICE 0x40, NORMAL 0x80, TEMPORARY 0x100.

## Relation to DVD on-disc work (descriptive)

- Pairs with `docs/storage/dvd-drive.md` (fake ToC, 0xDB0 video sectors, game data at LBA 0x1FB20, XDVDFS lineage). GDFX = logical FS above that layout. Extraction tooling queued (no FW/dump instructions here).

## Sources / References

- Free60 “GDFX”, `https://free60.org/System-Software/Systems/GDFX/` — all tables above. Fetched 2026-10-04.
- Free60 “360 System Software”, `https://free60.org/System-Software/360_System_Software/` — GDFX/XSF placement line. Search-verified.
- Queued: emoose GDFX template coverage, Xenia SVOD/GDFX code.
