# Title IDs, Media IDs, Offer IDs (identity roles)

> What these numbers ARE and where they appear. No instructions to change/spoof them, no purchase calls.

## Roles — PARTIALLY CONFIRMED (convergent across Free60 pages + catalog writeup)

| ID | Size/shape | Where it appears | Role |
|---|---|---|---|
| TitleID | 32-bit hex, e.g. `4D5307E6` (Halo 3 per Free60 GPD) | XEX `0x40006` Execution ID; STFS `0x360`; GPD filename `<titleID>.gpd`; dash GPD `FFFE07D1`; catalog `titleId/effectiveTitleId`; ConsoleMods title list | Identity of the title across exec, package, profile, catalog |
| MediaID | 32-bit + per-media variants; multidisc list `0x406FF` | XEX Execution ID + security header `@0x140`; STFS `0x354`; TU binding (Version/BaseVersion) | Identity of a pressing/media set; TUs target TitleID+MediaID |
| OfferID | 32-bit, randomized per purchasable unit | Catalog offers; Halo-4-beta brute-force anecdote (landaire) | Purchase-unit key; no documented call here |
| CategoryID | numeric (3000 root, 3027 XBL Games, genre buckets) | Catalog `FindGames` + feed `categories` | Catalog taxonomy (2011 snapshot) |
| Content GUIDs | `urn:uuid:` media/image/instance | Catalog feed + `download.xbox.com` art URLs | CDN object keys (historical host) |

## Public lists (existence, queued ingest)

- ConsoleMods Title-ID list (publisher-grouped, e.g. `IM (494D)` Imagine/Future + `494D07ED` starter pack …) — `https://consolemods.org/wiki/Xbox_360:List_of_Every_Xbox_360_Title_ID`.
- Digiex 87k-link/9792-TitleID scrape (per-region availability) — `https://digiex.net/threads/87000-marketplace-download-links-download.16750/`.
- Se7enSins/SmackTalks TitleID-changer threads exist (modding context) — NOT cited as authority, NOT reproduced here.

## Cross-buy caveat — UNCONFIRMED (community reports only)

Video-comment reports that One-store purchase of some OG-Xbox titles (e.g. Ninja Gaiden Black, Jade Empire + DLC cases) does not entitle the 360 copy. Single-source community claims; needs official entitlement-mapping source. Do not state as fact.

## Sources / References

- Free60 XEX (Execution ID/MediaID), STFS (TitleID/MediaID/Version), GPD (filename + title entries + art URL patterns). Fetched 2026-10-04.
- Den Delimarsky 2011 (titleId/GUIDs/CategoryIds). Fetched 2026-10-04.
- ConsoleMods + Digiex lists (above) — search-verified 2026-10-04.
