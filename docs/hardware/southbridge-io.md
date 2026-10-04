# Southbridge and I/O — ANA / HANA / KSB / PSB (Cycle 2 start)

> Status: skeleton with CONFIRMED family names; register maps UNKNOWN. Needs XenonLibrary Southbridge/Motherboard + ConsoleMods Motherboard Information + Scribd Xenon theory-of-ops cross-check.

## What is established — CONFIRMED at block level

| Claim | Confidence | Evidence |
|---|---|---|
| Southbridge = I/O controller: peripherals, audio out/decompression, drives, memory units, SMC | CONFIRMED as role | XenonLibrary “Southbridge” search excerpt 2026-10-04 |
| Link Xenos↔Southbridge = 2× PCIe lanes, ~500 MB/s per direction | PARTIALLY CONFIRMED | Beyond3D lineage (see bandwidth page) |
| ANA = launch video encoder/DAC (Xenon, no HDMI) | CONFIRMED | ConsoleMods (Xenon uses ANA); revisions table |
| HANA = HDMI + clockgen integration (Zephyr+ through Trinity Phat/Slim) | CONFIRMED | ConsoleMods (Zephyr first HDMI via HANA; HANA on all Phat + Trinity) |
| PSB = updated southbridge on Jasper (per Wikipedia revisions note) | PARTIALLY CONFIRMED | Wikipedia tech specs Jasper bullet |
| KSB = Corona+ southbridge merging HANA + Ethernet PHY (audio desync note on Neversoft GH) | PARTIALLY CONFIRMED | ConsoleMods Corona note; Motherboard Information “same KSB” line |
| SMC lives in/behind Southbridge (I/O + SMC per Scribd excerpt) | PARTIALLY CONFIRMED | Scribd “Xenon-Motherboard-theory-of-operations” search excerpt (needs full read) |

## Per-revision mapping (from revisions page, no new claims)

- Xenon/Elpis/Opus-class: ANA or Falcon-class AV (Opus unique AV on Falcon PCB).
- Zephyr→Jasper→Tonasket→Trinity: HANA (+ PSB on Jasper, XFreedom RF on Tonasket).
- Corona/Waitsburg/Stingray/Winchester: KSB (HANA-integrated).

## UNKNOWN (explicit)

- Pinouts, PCIe config space, audio-decompression engine programming, SATA bridge details, USB/Ethernet PHY wiring, SMC protocol bytes, 8051/8052 firmware roles, level-shifter nets. All require boardview/teardown + XenonLibrary Motherboard/Southbridge full reads + Free60 8051/SMC pages.

## Sources / References

- XenonLibrary “Southbridge”, `https://xenonlibrary.com/wiki/Southbridge` — role statement. Search excerpt 2026-10-04; full fetch queued (403 pattern).
- XenonLibrary “Motherboard”, `https://xenonlibrary.com/wiki/Motherboard` — central-component + Southbridge/ANA/HANA/Ethernet context. Search excerpt only; queued.
- ConsoleMods “Motherboard Information”, `https://consolemods.org/wiki/Xbox_360:Motherboard_Information` — KSB continuity Corona→Winchester. Search excerpt; queued full read.
- Scribd “Xenon-Motherboard-theory-of-operations”, `https://www.scribd.com/document/466526002/Xenon-Motherboard-theory-of-operations` — South Bridge = IO + peripherals + SMC; ANA definition start. Search excerpt only; queued (Scribd access limits).
- Beyond3D lineage for PCIe BW (see `docs/gpu/bandwidth-interconnects.md`).
