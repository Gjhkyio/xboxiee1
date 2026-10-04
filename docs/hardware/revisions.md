# Motherboard revisions — Xenon → Winchester

> Convergence of ConsoleMods Buying Guide (photos + PCB P/N) + Wikipedia revisions table. Per-cell confidence in notes.

## Phat/Fat (2005–2010)

| Codename | PCB P/N (ConsoleMods) | CPU | GPU / eDRAM | HDMI | PSU | NAND | Notes |
|---|---|---|---|---|---|---|---|
| Xenon | X803600-011 | 90 nm Waternoose DD2/DD2.1/DD3 | 90 nm Y1 + 90 nm Edifis | No (ANA) | 203 W, 16.5 A/12 V | 16 MB | Launch 2005–early 2007; small then extended GPU heatsink; low-Tg underfill + CPU caps issues. Refurb fixed-Y1/Elpis exist. |
| Zephyr A/B/C | A X810385-004; B/C X810387-006/007 | 90 nm Waternoose DD3 | A Y1/Edifis; B Y2/Edifis; C Rhea/Styx-90 | Yes (HANA) | 203 W | 16 MB | First HDMI (HANA integrates clockgen); Elite-first then white; low-Tg on all three GPU variants per guide. |
| Falcon | X812320-003 | 65 nm Loki | 90 nm Rhea + Styx-90 | Yes | 175 W, 14.2 A | 16 MB | First 65 nm CPU; cheaper power; Al full heatsink later; Rhea fixed to high-Tg ~Mar 2008 (seen late Apr); avoid pre-Apr 2008 per guide. |
| Opus | Falcon PCB, no HDMI | 65 nm (Falcon-class) | 90 nm (Falcon-class) | No (unique AV, Falcon PCB) | 175 W | 16 MB | Refurb-only Xenon replacement (2008); uncommon vs Elpis. |
| Jasper | X815842-002 | 65 nm Zeus* | 65 nm Zeus + 90 nm eDRAM (Kronos+Styx-65 on very late) | Yes | 150 W, 12.1 A | 16/256/512 MB | Late Nov 2008–mid 2009; new PSB southbridge; Arcade NAND holds dash updates; some new units patched JTAG. *Rare late Kronos. |
| Elpis | Xenon PCB | 90 nm | Fixed Elpis (modified Rhea) + Styx-90-class | No | 203 W | 16 MB | Refurb Xenon (service ~2009+); FW mod for Elpis GPU; CPU caps may still be bad. |
| Tonasket (“Jasper V2/Kronos”) | X820379-001 | 65 nm | 65 nm Kronos + 65 nm Styx-65 | Yes | 150 W | 16/512 MB | Late 2009–mid 2010; cleaned PCB; XFreedom RF; slim GPU heatsink (no heatpipe); all new units JTAG-patched per guide, RGH possible. Most reliable Phat per guide. |

## Slim/360 S + E (2010–2016)

| Codename | PCB P/N | XCGPU | eDRAM | HDMI | PSU | Flash | Notes |
|---|---|---|---|---|---|---|---|
| Trinity (S) | X850590-003 | 45 nm Vejle (CPU+GPU+eDRAM? — Vejle + Styx-65 per XenonLibrary) | Styx-65 | 1.2 | 135 W, 10.83 A | 16 MB (4 GB MU as detachable module on 4 GB SKUs) | Mid-2010–Jul 2011; smaller PCB; single combined chip; 3×USB + optical + keyed power. Reliable; rare dead CGPU per guide. |
| Corona V1/V2 (S) | X857330-003 / X859085-00x | 45 nm Vejle-class | Styx-65-class | 1.2 | 120 W, 9.6 A | 16 MB or 4 GB MMC (Phison PS7000) | Aug 2011–2012; HANA+ENET PHY into KSB southbridge; 4 GB on-board NAND; Neversoft GH audio desync on KSB (rhythm-game note); late 004 removed POST_OUT trace (RGH still via postfix/direct BGA per guide). Avoid 4 GB Phison (fails over time) per guide. |
| Waitsburg (“Corona V3/V4”) (S) | X862605-002 | 45 nm Vejle-class | 65 nm-class | 1.2 | 120 W | 16 MB or 4 GB eMMC (Hynix) | 2012–2013; 4 GB TSOP+Phison → combined eMMC; POST vias standard-removed. Avoid 4 GB Hynix (fails) per guide. |
| Stingray (E) | Waitsburg-derived | 45 nm-class | 65 nm-class | 1.2 | 120 W | 16 MB / 4 GB eMMC | Jun 2013+ (360 E); Waitsburg slightly modified for E. |
| Winchester (E) | — | 32 nm Oban (eDRAM on-die) | on-die | 1.2 | 120 W | 16 MB-class | Aug 2014+; board simplification; RGH patched (HW); SW-only path per community (needs Cycle-2 verification, currently UNCONFIRMED here). |

> Winchester/Oban 32 nm on-die claim: Wikipedia table says “New XCGPU combining eDRAM into main die”. XenonLibrary lists Oban 32 nm. Keep PARTIALLY CONFIRMED pending teardown/die-shot source.

## Identification quick rules (community, PARTIALLY CONFIRMED)

- Boxy no-HDMI + 203 W → Xenon (or Opus/Elpis refurb — check PCB/ports/service sticker Q2-2008+ rule in guide).
- Boxy HDMI → Zephyr/Falcon/Jasper/Tonasket — check PSU (203/175/150 W), MFG date (Apr/May 2008 Falcon fix; Nov 2008+ Jasper), NAND size (256/512 MB ⇒ Jasper+ Arcade).
- Slim S: Trinity = J2C1/J2C3 headers both vertical/parallel; Corona = one vertical + one horizontal (Weekend Modder). MFG ≤07-2011 Trinity-lean; ≥08-2011 Corona-lean.
- Slim E: Corona (IHS present) vs Winchester (no IHS) via XCGPU photo (Weekend Modder).

## Power/thermal arc (analysis, INFERRED)

203 W →175 W →150 W →135 W →120 W tracks CPU/GPU shrinks + integration (90/90 →65/90 →65/65 →45 combined →32 combined). RROD association strongest Xenon/Zephyr (low-Tg + caps + heat cycling → GPU joint cracking narrative in VGCL/Reddit guides). Treat failure-mechanism phrasing as community analysis, not materials-science primary.

## Sources / References

- ConsoleMods Wiki “Buying Guide — Console Configurations / Motherboard Comparison”, `https://consolemods.org/wiki/Xbox_360:Buying_Guide` — PCB P/N, CPU/GPU/eDRAM per rev, amps, NAND, MFG windows, heatsinks, HANA/KSB, POST_OUT, Phison/Hynix warnings. Accessed 2026-10-04. Primary evidence for table.
- Wikipedia “Xbox 360 technical specifications — Motherboards / List of revisions”, `https://en.wikipedia.org/wiki/Xbox_360_technical_specifications` — codenames, nm, HDMI, PSU, dates, Elpis/Tonasket/Trinity/Corona/Waitsburg/Stingray/Winchester notes. Tertiary convergence. Accessed 2026-10-04.
- VGCL “Every Xbox 360 Model: Xenon to Winchester Explained”, `https://www.videogameconsolelibrary.com/xbox-360-models/` (2026-06-08) — 8-revision narrative, RROD heat-cycling account, ID rules. Accessed 2026-10-04. Secondary.
- Weekend Modder “Identify your console and motherboard type”, `https://weekendmodder.com/identify.html` — HDMI/power-socket check, J2C1/J2C3 orientation, Corona-vs-Winchester IHS photos. Accessed 2026-10-04. Evidence: photos.
- XenonLibrary chip matrix (Y1/Y2/Rhea/Elpis/Kronos/Vejle/Oban + Styx/Edifis) — search-verified 2026-10-04; direct fetch 403, Archive retry queued.
