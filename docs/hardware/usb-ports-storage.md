# USB ports and USB storage (hardware + layout)

> Hardware facts from Free60 “USB” (fetched 2026-10-04) + layout from Free60 “FATX” USB section. Page keeps its own Confirmed-vs-Speculation split.

## Ports — PARTIALLY CONFIRMED

- 3× standard USB 2.0 (2 front + 1 back) on launch hardware (per Free60 USB). Slim/E port counts differ — queued (spec: Trinity 3×USB + optical noted on VGCL; verify per model).
- Kinect on Phat needs power-split cable (USB + mains AC) because tilt motor exceeds USB power; Slim S/E have dedicated AUX/Kinect port (see `peripherals/kinect.md`).

## USB storage support — CONFIRMED as dated feature (2010-04-06)

- Official 360-configured USB support from 2010-04-06 (kernel 2.0.9199.0 era). Hidden `Xbox360/Data0000–0003` files; Data0000 = Cache/SysExt + perf + geometry; Data0001 = Data-partition FAT. Config = first 2 sectors (0x400) of Data0000 with Type1 (console cert 0x228) vs Type2 (MS pre-config 0x100, SATA-pubkey/HDDSS verification). Full table in `docs/filesystem/fatx.md`. 16 GB-era cap + over-cap crash note (historical xboxhacker link).

## Page’s own claims (preserve split)

- CONFIRMED (page): USB-HDD mod to “get around DRM” + llama.com Archive link (historical mod context; no instructions reproduced here).
- SPECULATION (page, do not cite): iPod/FAT32 via media center, no NTFS; HFS Mac-iPod reads; USB DMA read-only question (page itself calls it “most likely impossible”: no slave-initiated DMA in USB spec; OTG/driver issues; dash/FS-driver gating instead).

## Sources / References

- Free60 “USB”, `https://free60.org/Hardware/Console/USB/` — ports, 2010-04-06 support, hidden-folder mount, confirmed/speculation split. Fetched 2026-10-04.
- Free60 “FATX” USB Drive Layout + kernel 9199 row — cross-refs.
