# FATX (XTAF) — filesystem + partition map (as documented)

> Source: Free60 “FATX” (fetched 2026-10-04). PARTIALLY CONFIRMED (single detailed source). Big-endian throughout FS structures (note: security-sector sector-count field is little-endian exception on page).

## Layout — PARTIALLY CONFIRMED

- 4 parts: header (BOOT-like), FAT, root cluster/data region. Sometimes “XTAF” from LE magic `XTAF`; derived/cleaned MS-DOS FAT. No on-media MFT; consumer (360 / FreeBSD `geom_xbox360`) knows offsets. Big-endian multibyte.
- Entry 64 B: namelen @0x00 (0xE5 = deleted) / attrs @0x01 / name @0x02 (0x2A, 0x00/0xFF padded) / first cluster @0x2C / size @0x30 / cdate @0x34 / ctime @0x36 / wdate @0x38 / wtime @0x3A / atime @0x3C–0x3E. DOS-format time/date bits. No `.`/`..` (must remember parent cluster). `name.txt` UTF-16BE @0x2 holds volume label (volume bit unused). Filename charset/limits: 42-char max, 240 path, 4 GB file, 4096/dir, `[A-Za-z0-9 $._]` per observed images.
- Chainmap: offset = part offset + 0x1000; entry 2 B if clusters < 0xFFF0 else 4 B; size = entries×clusters; data area = chainmap end; cluster N offset = data + (N−1)×cluster size. Cluster sizes 4/8/16/32/64 KB (8/0x10/0x20/0x40/0x80 sectors/cluster).
- Partition header @part+0: magic `XTAF`, ID, sectors/cluster, root cluster.

## Partitions — PARTIALLY CONFIRMED (offsets verbatim, verify before tooling)

- MU: `0x0` 0x7FF000 cache (SFCX) + rest data (FATX).
- Retail HDD: sec sector `0x2000` (0x204–0x80000 range note); cache `0x80000` 0x80000000 (SFCX); game cache `0x80080000` 0xA0E30000 (SFCX); SysExt `0x10C080000` 0xCE30000 (FATX sub-part, Kinect/Avatar since 12611); SysExt2 `0x118EB0000` 0x8000000; Xbox1 BC `0x120EB0000` 0x10000000; Data `0x130EB0000`→end.
- Devkit HDD: 0x18 table @0 (magic 0x00020000 @0x0) with Content sector @0x8 (0x633000 → raw 0xC6600000), len @0xC; Dash sector @0x10 (0x5B3000 → 0xB6600000), len @0x14 (0x80000 → 0x10000000). Retail offsets kernel-built-in (no table).
- USB (360-configured, hidden `Xbox360/Data0000–0003`): cache `0x8000400` 0x12000400; SysExt `0x8115200` 0x8000000; SysExt2 `0x12000400` 0xDFFFC00; Data `0x20000000`→EOF. Config = first 2 sectors (0x400) of Data0000: Type1 cert 0x228 (console cert 0x1A8 + sig 0x80, device ID @0x228, size @0x23C=0x228, dev size @0x240, R/W KB/s @0x248/0x24A) vs Type2 (device sig 0x100 + pad, same tail, size=0x100 → verify via SATA pubkey/HDDSS). Sig = SHA1(device-ID→end, 0x1D8 B) + console-privkey; perf fields’ later use UNKNOWN. 16 GB max-era note + >max crash note (xboxhacker link, historical).
- “Josh” sector @0x800: magic `Josh` + console cert (+0x80 sig) + 2× STFS vol-descs @0x22C/0x250 (upper flag bits set = cache hint?) + unknowns @0x274/0x278 + TitleIDs @0x27C/0x280. Purpose UNKNOWN per page.
- Security sector @0x2000: serial @0x0(0x14 ASCII), FW @0x14(8), model @0x1C(0x28), logo hash @0x44(0x14), sector count @0x58(4 LE!), RSA sig @0x5C(0x100), logo size @0x200, logo @0x204. Smaller-drive sector on bigger drive → clipped capacity.

## Sources / References

- Free60 “FATX”, `https://free60.org/System-Software/Systems/FATX/` — all tables above + USB/Josh/security details. Fetched 2026-10-04.
- Queued: Free60 GDFX, ConsoleMods Files-and-Directories, xbox-linux partitioning/FAT-difference pages (linked from HDD page).
