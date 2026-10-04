# XEX — Xbox 360 executable container

> WARNING: Free60’s own page is titled “File Format Speculation”. Treat everything here as PARTIALLY CONFIRMED at best until Xenia `xex` loader + `xextool` lineage are audited Cycle 2. No invented fields.

## What XEX is (as reported)

- Crypto/packing container for PPC PE executables (Free60 analogy: UPX/TEEE Burneye). 360 grabs needed sections into memory, decrypts/decompresses on demand (not all-at-once). PARTIALLY CONFIRMED (single speculative source).
- Code often AES-CBC encrypted (per-file changing key, “probably derived from RSA block + secret public key in box” — source’s wording, UNCONFIRMED mechanism) + Microsoft LDIC compression (Xbox1 heritage note). Debug XEXs may be unencrypted/unpacked. PARTIALLY CONFIRMED existence; key-derivation UNCONFIRMED.
- Big-endian header (explicit). CONFIRMED as format observation.

## Header — 24 bytes (as tabled on Free60)

| Offset | Len | Type | Info |
|---|---|---|---|
| 0x0 | 0x4 | ASCII | `XEX2` magic |
| 0x4 | 0x4 | flags | Module flags bitfield (see below) |
| 0x8 | 0x4 | u32 | PE data offset |
| 0xC | 0x4 | u32 | Reserved |
| 0x10 | 0x4 | u32 | Security Info offset |
| 0x14 | 0x4 | u32 | Optional header count |

Flags (bit per Free60): 0 Title Module, 1 Exports To Title, 2 System Debugger, 3 DLL Module, 4 Module Patch, 5 Patch Full, 6 Patch Delta, 7 User Mode. PARTIALLY CONFIRMED.

## Optional headers (as tabled)

Each 8 bytes: ID u32 + data/offset u32. Size rule (per page): `ID & 0xFF == 0x01` → data inline; `== 0xFF` → data holds size; else size = value in DWORDs ×4. PARTIALLY CONFIRMED (needs parser cross-check).

IDs (verbatim from page, not verified): `0x2FF Resource Info`, `0x3FF Base File Format`, `0x405 Base Reference`, `0x5FF Delta Patch Descriptor`, `0x80FF Bounding Path`, `0x8105 Device ID`, `0x10001 Original Base Address`, `0x10100 Entry Point`, `0x10201 Image Base Address`, `0x103FF Import Libraries`, `0x18002 Checksum Timestamp`, `0x18102 Enabled For Callcap`, `0x18200 Enabled For Fastcap`, `0x183FF Original PE Name`, `0x200FF Static Libraries`, `0x20104 TLS Info`, `0x20200 Default Stack Size`, `0x20301 Default FS Cache Size`, `0x20401 Default Heap Size`, `0x28002 Page Heap Size+Flags`, `0x30000 System Flags`, `0x40006 Execution ID`, `0x401FF Service ID List`, `0x40201 Title Workspace Size`, `0x40310 Game Ratings`, `0x40404 LAN Key`, `0x405FF Xbox 360 Logo`, `0x406FF Multidisc Media IDs`, `0x407FF Alternate Title IDs`, `0x40801 Additional Title Memory`, `0xE10402 Exports by Name`.

Execution ID (`0x40006`) per page: MediaID[4], Version[4], BaseVersion[4], TitleID[4]. Ratings (`0x40310`): ESRB/PEGI/PEGI-FI/PEGI-PT/BBFC/CERO/USK/OFLC-AU/OFLC-NZ/KMRB/Brasil/FPB bytes. LAN Key 16 B. All PARTIALLY CONFIRMED.

Security Info (FileHeaderOffset table per page): HeaderSize, ImageSize, 0x100 RSA sig @0x8, resulting size @0x10C, LoadAddress @0x110, MediaID[16] @0x140, AES seed[16] @0x150, SHA input[0x14] @0x164, Region @0x178, SHA[0x14] @0x17C, ImageDataCount + 24 B entries. PARTIALLY CONFIRMED.

## History/tools strings (as listed, UNCONFIRMED usefulness)

- Strings: `XAdu`, `$UPDATES`, `MEDIA`, `\Device\CdRom0\default.xex`, `installupdate.exe`, `xam.xex`, `xboxkrnl.exe`, libs `XUIRNDR/XAUD/XGRAPHC/XRTLLIB/XAPILIB/LIBCMT/XBOXKRNL/D3D9/XUIRUN`.
- Freely-available XEXs at time of writing (all Archive links on page): Nov/Dec 2005 back-compat `default.zip`, XP MCE Rollup2 `XboxMcx.xex` via cabextract, HD-DVD update. Historical only; do not re-host.
- Tools: `xextools-0.2` (xexread replacement), `xexdump` (perl + windows). Links on page are Archive-hosted. Cycle 2: audit Xenia `src/xenia/kernel/xex*.cc` + modern `xextool`.

## Inspection aid (PSEUDOCODE — incomplete, educational only)

```python
# PSEUDOCODE — XEX header peek (educational; no decrypt/decompress)
# INCOMPLETE: does not handle optional headers, security info, or sections.
import struct
def peek_xex_header(path):
    with open(path,'rb') as f:
        magic, flags, pe_off, _, sec_off, opt_count = struct.unpack('>4sIIIII', f.read(24))
    assert magic == b'XEX2', magic
    return {"flags": hex(flags), "pe_offset": hex(pe_off), "sec_offset": hex(sec_off), "opt_count": opt_count}
```

## Sources / References

- Free60 Wiki “XEX (File Format Speculation)”, `https://free60.org/System-Software/Formats/XEX/` — header/flags/optional-ID/security tables, crypto/compression notes, strings, history, tools. Fetched 2026-10-04. Self-declared speculation; propagate downgrade.
- Xenia project (queued Cycle 2): `https://github.com/xenia-project/xenia` — kernel XEX loader as observable-behavior cross-check. Not yet audited.
