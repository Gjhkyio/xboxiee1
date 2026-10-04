# Kernel and system software — versions and stack (Cycle 3 start)

> Grounds the software side. Syscall-level ABI remains UNKNOWN in this cycle; only versions + load order + observable modules are documented.

## Kernel version table — PARTIALLY CONFIRMED (Free60, dated 2011)

Source: Free60 “Kernel”, `https://free60.org/System-Software/Kernel/` (fetched 2026-10-04). Latest on that page: `2.0.13146.0` (2011-05-19). Check on console via System → Console Settings → System Info (`K:2.0.XXXX.0`).

| Version | Date | Note on page |
|---|---|---|
| 2.0.1888.0 | 2005-11-22 | Original shipped |
| 2.0.2241.0 | 2005-11-22 | Launch update |
| 2.0.2255.0 | 2006-01-30 | Blocklist for certain .xex |
| 2.0.2258.0 | 2006-03-02 | — |
| 2.0.2858.0 | 2006-06-05 | — |
| 2.0.4532.0 | 2006-10-31 | New identifier X `2BB7-8E09-0188-D795` |
| 2.0.4548.0 | 2006-11-30 | — |
| 2.0.4552.0 | 2007-01-09 | Fix unsigned-code vuln |
| 2.0.5759.0 | 2007-05-09 | Instant Messaging |
| 2.0.5766.0 | 2007-08-07 | Wireless guitars |
| 2.0.6683.0 | 2007-12-04 | Fall update; timing attack (CB-dependent) |
| 2.0.6717.0 | 2008-08-06 | Scalability |
| 2.0.7357.0 | 2008-11-19 | NXE dash |
| 2.0.7363.0 | 2009-02-03 | HDMI audio fix |
| 2.0.7371.0 | 2009-04-02 | Live fixes |
| 2.0.8495–8498 | 2009-07/08 | Preview → public dash |
| 2.0.8507.0 | 2009-09-23 | Prep for newer dash |
| 2.0.8955.0 | 2009-10-28 | 3rd-party storage block, WPA2 |
| 2.0.9199.0 | 2010-04-06 | USB storage support |
| 2.0.12611.0 | 2010-11-01 | Kinect dash, ESPN, SysExt partition |
| 2.0.12625.0 | 2011-01-19 | AP2.5 to Reach/Blops/MW2, boot-to-disc fix |
| 2.0.13146.0 | 2011-05-19 | XGD3 media, DVD FW reflash (0272/04421C/02510C), AP2.5 Samsung, +1 GB usable, PayPal |

> Page is frozen in 2011. Later kernels (14717+ POST-removal era, 17559 final) are NOT on this page — queued from POST page + ConsoleMods scene history. Do not backfill versions from memory.

## Stack as observed — PARTIALLY CONFIRMED

- After HV: kernel inits per POST `0x60–0x79` (HAL0 → … → STFS → XAM load), then loads `xam.xex → xbdm.xex → xstudio.xex → ximecore.xex → Xam.Community.xex → huduiskin.xex → xshell.xex/dash.xex` (Free60 Boot page; devkit wording). Retail deltas queued.
- XAM = system UI/services host (DataFile class handles XDBF per Free60 XDBF page). `XamSetStagingMode` / `XamVerifyXSignerSignature` / `XamGetStagingMode` names appear only in landaire dashboard RE (descriptive, see dashboard-epix page). No syscall numbers published here.
- Xenia reimplements `xboxkrnl` + `XAM` + `XBDM` modules in C++ (`src/xenia/kernel/xboxkrnl/*`, e.g. `xboxkrnl_video.cc`, `xboxkrnl_module.cc`). Existence CONFIRMED via repo fetch; behavior mapping queued file-by-file.

## Explicitly UNKNOWN (no invention)

- Hypervisor call numbers, kernel export ordinals, object/security model internals, scheduler/IPC specifics. Xenia source walk is the Cycle-4 path, cited per file:line.

## Sources / References

- Free60 “Kernel”, `https://free60.org/System-Software/Kernel/` — version table. Fetched 2026-10-04.
- Free60 “Boot process” + “POST” — init sequence + module order. Fetched 2026-10-04.
- Free60 “XDBF” — XAM DataFile note. Fetched 2026-10-04.
- Xenia `xboxkrnl_video.cc` / `xboxkrnl_module.cc`, `https://github.com/xenia-project/xenia/blob/master/src/xenia/kernel/xboxkrnl/...` — module reimplementation existence. Search-verified 2026-10-04.
