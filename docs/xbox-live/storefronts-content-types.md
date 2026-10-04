# Storefronts and content types — 360 Store system (historical)

> Console + web + modern back-compat fronts. Purchase flows are NOT documented (no verifiable public source); this page covers what the store WAS, what content existed, and where it lives now.

## Fronts — CONFIRMED (official)

| Front | Status | Source |
|---|---|---|
| Xbox 360 Store on console | Retired 2024-07-29; no new purchases | Xbox Support “XBOX 360 Store and XBOX 360 Marketplace FAQ”, `https://support.xbox.com/en-US/help/xbox-360/store/xbox-360-marketplace-update` (search-verified 2026-10-04; page is JS-heavy, full fetch queued via Archive) |
| `marketplace.xbox.com` web marketplace | Retired same date; product pages (e.g. `/en-US/Product/.../<guid>`) now historical/Archive-only | Kinect Fun Labs marketplace URL cited on Wikipedia Kinect refs (Archive 2011-10-26); Reddit 2024 workaround threads (community only) |
| Modern `xbox.com` (One/Series + web) | Active for BACK-COMPAT 360 + OG-Xbox titles only: `https://www.xbox.com/en-US/games/xbox-360`, `https://www.xbox.com/en-US/games/backward-compatibility` | Search-verified 2026-10-04 |
| Xbox Games Store (formerly Xbox LIVE Marketplace) | Historical name lineage; Wikipedia notes archived 360 Marketplace snapshot “with 400 pieces of content” | `https://en.wikipedia.org/wiki/Xbox_Games_Store` — tertiary, queued full read |

## Content universe (as observed across catalog + STFS + GPD)

Map store nabídka to on-console types (STFS ContentType + catalog MediaTypes). Historical values from den.dev 2011 + Free60 STFS; dead today, preserved for identification:

| Store bucket | Catalog MediaType (2011) | STFS ContentType | Notes |
|---|---|---|---|
| Games on Demand / full | 1, 21 | 0x07000 GoD / 0x1000 360 Title / 0x4000 Installed | TitleID + MediaID per XEX execution ID |
| Arcade (XBLA) | 23 | 0x0D000 Arcade | Single-file STFS typical |
| Indie (XNA/Community) | 37 | 0x2000000 Community | Sunsetting earlier than 2024; exact date queued |
| Demos/trials | 19 | 0x08000 Demo | — |
| Add-ons/DLC/TU | 18 | 0x00002 Marketplace (DLC container) | Title-update vs store-DLC split queued (some TUs in-game, some store-listed) |
| Themes/gamerpics | 20 / 22 | 0x30000 Theme / 0x20000 GamerPic | — |
| Videos (game/video/movie/TV/music/viral/podcast) | 30 / 34 | 0x9000–0x600000 family | Movies&TV app dead on 360 post-closure |
| Avatar items | — | 0x09000 Avatar Item (often PEC-wrapped) | — |
| Saves/profiles | — (CON) | 0x00001 SavedGame / 0x10000 Profile / cache 0x40000 | Console-signed, not purchased |

## Identifiers (roles only, no spoofing instructions)

- TitleID (32-bit, e.g. `4D5307E6` Halo 3): XEX `0x40006` Execution ID + STFS `0x360` + GPD filename + catalog `titleId/effectiveTitleId`. See `title-ids-media-ids.md`.
- MediaID: per-pressing disc/content identity in XEX/StFS; title updates bind TitleID+MediaID+Version/BaseVersion.
- OfferID (32-bit, randomized per offer; Halo-4-beta brute-force anecdote on landaire page): catalog purchase-unit key. No purchase-call documentation exists here.
- GUIDs (`urn:uuid:...`): catalog media/image/instance IDs; `download.xbox.com/content/images/<title-guid>/1033/...` art pattern (den.dev sample).

## Preservation references (existence only, no links to copyrighted blobs)

- Digiex “87000+ Marketplace download links” (9792 TitleIDs scraped, per-region) — `https://digiex.net/threads/87000-marketplace-download-links-download.16750/` — search-verified; treat link-rot per title as UNKNOWN until sampled.
- ConsoleMods “List of Every Xbox 360 Title ID” — `https://consolemods.org/wiki/Xbox_360:List_of_Every_Xbox_360_Title_ID` — search-verified; queued full ingest (publisher/article structure).
- landaire EPIX manifests — `https://archive.org/details/epix-playground-manifests` — dash-channel preservation, not game content.

## Sources / References

- Xbox Support FAQ (above) + Xbox Wire 2023-08-17 closure notice (see `marketplace-closure-2024.md`).
- Den Delimarsky 2011 catalog writeup (MediaTypes/CategoryIds/GUIDs) — see `marketplace-catalog-api-2011.md`.
- Free60 STFS ContentType table — see `docs/packages/stfs.md`.
- Wikipedia Xbox Games Store + Kinect refs (marketplace URL pattern proof).
