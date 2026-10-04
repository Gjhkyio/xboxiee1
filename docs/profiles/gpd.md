# GPD — Game Profile Data (XDBF profile)

> Source: Free60 “GPD” (fetched 2026-10-04). PARTIALLY CONFIRMED. Profiles = many `<titleID>.gpd` (e.g. `4D5307E6.gpd` Halo 3); dash GPD `FFFE07D1.gpd` holds cross-title info + sync.

## Namespaces / IDs — PARTIALLY CONFIRMED

Namespaces: 1 Achievement, 2 Image, 3 Setting, 4 Title, 5 String, 6 Achievement-Security (GFWL offline?) / Avatar Award (360, PEC-only).

IDs: `0x100000000` = Sync List, `0x200000000` = Sync Data (PEC: 1 and 2); per-namespace Sync List/Data for Settings/Achievements/Title/Assets; `0x8000` = title info (string/image namespaces); achievement/image entry ID must match enclosed ID. Long setting-ID list on page (0x10040003 vibration … 0x63E80068 avatar metadata …); deterministic by type/max-length per pastebin sample (UNVERIFIED link, queued).

## Structures (verbatim, PARTIALLY CONFIRMED)

- Achievement: size 0x1C @0x0; ach ID @0x4; image ID @0x8; gamerscore @0xC; flags @0x10 (type bits 0–2: 1 Completion/2 Leveling/3 Unlock/4 Event/5 Tournament/6 Checkpoint/7 Other; bit3 show-unachieved(!secret); 0x10000 earned-online; 0x20000 earned; 0x100000 edited?); unlock FILETIME @0x14; name/unlocked-desc/locked-desc null-terminated Unicode from 0x18.
- Setting: SettingID @0; DOS time @4; unknown @6; DataType @8 (0 Context/1 Int32/2 Int64/3 Double/4 String/5 Float/6 Binary/7 DateTime/0xFF Null; 7 unknown null bytes @9); string/binary prefixed with Int32 length.
- Image: PNG blobs (C# save/load snippet on page).
- Title (only `FFFE07D1.gpd`, XDBF entry ID = title ID, type String): title ID @0x0; ach count @0x4; unlocked @0x8; GS total @0xC; GS unlocked @0x10; unknown @0x14; online-unlocked count @0x15; avatar assets earned/max + male/female splits @0x16–0x1B; flags @0x1C (0x1 offline-needs-sync / 0x2 image-needs-download / 0x10 avatar-needs-download / 0x20 ? — “rest unknown”); last-played @0x20; title name Unicode @0x28. Online tile URLs on page (image/tiles/avatar/marketplace patterns, historical hosts — see Xbox Live docs for status).
- Avatar Award (PEC GPD only; images in game GPD): size 0x2C; GUID @4; ImageID @20; flags @24; unlock time @28; subcategory @36; unknown @40; name/descs Unicode @44. Server image URLs on page (download/avatar hosts, historical).
- String: null-terminated Unicode, len = entry length.
- Sync List: items of (EntryID u64, SyncID u64); count = (len/16)−1. Sync Data: next ID @0x0, last-synced ID @0x8, last-synced time @0x10. “IDs between last and next are pushed — confirm?” (page’s own question preserved).

## Sources / References

- Free60 “GPD”, `https://free60.org/System-Software/Formats/GPD/` — all tables above + URL patterns + pastebin ref. Fetched 2026-10-04.
- Free60 “XDBF” (base format), “PEC” (queued full read).
