# STFS — Secure Transacted File System (CON / PIRS / LIVE) + PEC

> Single strong source Cycle 1: Free60 “STFS”. Keep PARTIALLY CONFIRMED until Velocity/py360/xenia STFS code audited. No invented offsets beyond page tables.

## What STFS is (as documented)

- FS for 360 packages (saves/content/games/pictures/etc.). SHA1 chain + RSA signature. Two categories: read-only (PIRS/LIVE, Microsoft-signed) vs writable (CON, console-signed). PEC (Profile Embedded Content) reuses STFS algorithms with different header (avatar items/clothing per page). PARTIALLY CONFIRMED.
- Magic at 0x0: `CON ` (console-signed; saves/profiles/cache), `PIRS` (MS-signed, non-Live e.g. updates), `LIVE` (MS-signed over Live e.g. Marketplace). PARTIALLY CONFIRMED.

## Signatures (verbatim tables, PARTIALLY CONFIRMED)

CON (console cert + sig): cert size @0x004(2), console ID @0x006(5), part number @0x00B(0x14 ASCII), console type @0x01F(1=devkit/2=retail), date @0x020(8 ASCII), exponent @0x028(4), modulus @0x02C(0x80), cert sig @0x0AC(0x100), sig @0x1AC(0x80).
LIVE/PIRS: package sig @0x004(0x100) over 0x32C content-ID/header SHA1 + 0x128 padding @0x104.

## Metadata V1 (offsets verbatim, PARTIALLY CONFIRMED)

Licenses 0x022C(0x100: entries of LicenseID XUID/PUID/consoleID 8 + bits 4 + flags 4); header SHA1 @0x032C(0x14, from 0x344 to first hash table); HeaderSize @0x0340; ContentType @0x0344; MetadataVer @0x0348; ContentSize @0x034C(8); MediaID @0x0354; Version @0x0358; BaseVersion @0x035C; TitleID @0x0360; Platform @0x0364(2=360/4=PC); ExecType @0x0365; DiscNo @0x0366; Discs @0x0367; SaveID @0x0368; ConsoleID @0x036C(5); ProfileID @0x0371(8); VolumeDesc @0x0379(0x24); FileCount @0x039D; CombinedSize @0x03A1(8); DescType @0x03A9(0=STFS/1=SVOD); Reserved @0x03AD; pad @0x03B1(0x4C); DeviceID @0x03FD(0x14); DisplayName @0x0411(0x900, 0x80/locale); Description @0x0D11(0x900); Publisher @0x1611(0x80); Title @0x1691(0x80); TransferFlags @0x1711; ThumbSizes @0x1712/0x1716; Thumbs @0x171A(0x4000)/0x571A(0x4000).

V2 delta: SeriesID @0x03B1(0x10), SeasonID @0x03C1(0x10), SeasonNo @0x03D1(2), EpisodeNo @0x03D3(2), pad @0x03D5(0x28); thumbs 0x3D00 at 0x171A/0x571A + additional name/desc 0x300 blocks at 0x541A/0x941A.

ContentType enum (verbatim): 0x1 SavedGame, 0x2 Marketplace, 0x3 Publisher, 0x1000 360 Title, 0x2000 IPTV Pause, 0x4000 InstalledGame, 0x5000 Xbox Original/Title (page lists twice — preserve, don’t fix), 0x7000 GoD, 0x9000 AvatarItem, 0x10000 Profile, 0x20000 GamerPic, 0x30000 Theme, 0x40000 Cache, 0x50000 StorageDownload, 0x60000 XboxSavedGame, 0x70000 XboxDownload, 0x80000 Demo, 0x90000 Video, 0xA0000 GameTitle, 0xB0000 Installer, 0xC0000 Trailer, 0xD0000 Arcade, 0xE0000 XNA, 0xF0000 LicenseStore, 0x100000 Movie, 0x200000 TV, 0x300000 MusicVideo, 0x400000 GameVideo, 0x500000 PodcastVideo, 0x600000 ViralVideo, 0x2000000 CommunityGame.

TransferFlags bits: 2 DeepLink, 3 DisableNetStorage, 4 Kinect, 5 MoveOnly, 6 DeviceID, 7 ProfileID (bits 0–1 None).

## Volume descriptors (verbatim)

STFS: size @0x00(0x24), reserved @0x01, block-separation @0x02, filetable blocks @0x03(2 BE?), filetable block # @0x05(24b), top hash @0x08(0x14), alloc @0x1C, unalloc @0x20.
SVOD: size 0x24, cache elements @0x01, worker CPU @0x02, worker pri @0x03, hash @0x04(0x14), dev feats @0x18, data count @0x19(24b), data offset @0x1C(24b), pad.

## File listing + hash/block math (as documented, PARTIALLY CONFIRMED, code may be imperfect per page)

- Listing at FileTableBlockNumber (0x37E ref on page — ambiguous offset context; preserve wording, verify Cycle 2). Entry 0x40: name 0x28 ASCII null-padded, flags+namelen @0x28 (bits 7 dir / 6 consecutive / 0–5 len), alloc blocks @0x29(24b LE) + copy @0x2C, start block @0x2F(24b LE), path indicator @0x32(2 BE, 0xFFFF=root else Vth entry), size @0x34(4 BE), update/access FAT timestamps @0x38/0x3C. Ends with null entry. Dirs nest.
- Blocks 0x1000, first at 0xC000; every 0xAA blocks a level-0 hash block; every 0xAA² (0x70E4) a level-1. Block→offset/hash-pos C# snippets on page (page warns “may not work perfectly”). Do not present snippets as tested; link page.
- Hash record 0x18: SHA1 @0x0(0x14), status @0x14 (0x00 unused / 0x40 free-prev-used / 0x80 used / 0xC0 newly-alloc), next @0x15(24b). FAT-like chaining; consecutive-bit vs table walk per flags.
- PEC: block0 @0x3000, hashtable0 @0x1000/0x2000; header: console cert @0x000(0x228), SHA1(0x23C–0x1000) @0x228(0x14), unknown @0x23C(8), STFS vol-desc @0x244(0x24), unknown @0x268(4), ProfileID @0x26C(8), unknown @0x274(1), ConsoleID @0x275(5).

## Tools (as listed, historical)

Velocity (Gualdimar releases), extract360.py (rene0/xbox360, Py2.5-era), py360, wxPirs 1.1 (LIVE/PIRS ok, CON weak per page), Le Fluffie (DJ Shepherd; create/extract CON/LIVE/PIRS with creation caveats), XLAST (XDK, redist prohibited). All need Cycle-2 source verification; XLAST is not to be shared.

## Sources / References

- Free60 Wiki “STFS”, `https://free60.org/System-Software/Formats/STFS/` — all tables above + C# snippets + tools. Fetched 2026-10-04. Strong single source; needs code audit.
- Queued Cycle 2: Velocity `https://github.com/Gualdimar/Velocity`, `rene0/xbox360` extract360.py, Xenia STFS/SVOD code.
