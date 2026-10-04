# HDD — 360 hard-disk module (as documented)

> Source: Free60 “HDD” (fetched 2026-10-04). Dated (20 GB era); later 60/120/250/320/500 GB + Slim modules need Cycle-3 datasheets. No invented later specs here.

## Units cited — PARTIALLY CONFIRMED (era-specific)

- Samsung HM020GI Rev YU100-06 (18.63 GB), Seagate ST920217AS Rev 3.01/LD25.1 (20 GB), Hitachi HTS541020G9SA00 Travelstar Rev C60D (20 GB). Required for Xbox1 back-compat (per page lede).

## Confirmed Facts (page wording) — PARTIALLY CONFIRMED

- Not locked; zeroed drive readable only with correct headers.
- FATX partition present.
- Validity requires plaintext HDD info + MS logo PNG (license/copyright interop note + US-case comment preserved as page commentary, not legal advice).
- 360 serial required to format; fresh 20 GB formats to ~13 GB visible.

## Speculation (page wording) — UNCONFIRMED

- No evidence of encryption at time of writing (cleartext entries); FATX = big-endian Xbox1-FATX variant; Linux driver work + CVS support in progress (historical).

## Power — PARTIALLY CONFIRMED

- SATA power table on page: 3.3 V (1–3) NC; GND (4–6,10,12) connected with mate sequencing; 5 V (7–9) connected; Reserved 11 NC; 12 V (13–15) NC → 3.5″ drives won’t spin without external 12 V. Cites SATA PHY spec Rev 1.0 Table 17 p.117 (Archive link on page).

## Queued

- Later HDD sizes, Slim/E modules (XenonLibrary Hard Drive Original vs S/E), security-sector/RSA details (see FATX page), ConsoleMods Files-and-Directories (`https://consolemods.org/wiki/Xbox_360:Files_and_Directories` — search-verified, full read queued).

## Sources / References

- Free60 “HDD”, `https://free60.org/Hardware/Console/HDD/` — models, facts/speculation split, SATA power table, xbox-linux links. Fetched 2026-10-04.
