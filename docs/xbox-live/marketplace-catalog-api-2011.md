# Marketplace catalog query API — public CDN service (2011, historical)

> This is the ONLY 360-era store query API with a solid public writeup found to date. It is a READ-ONLY catalog feed, not a purchase/auth API. Service is long dead (store closed 2024-07-29). Do not present as working.

## What was documented — CONFIRMED as 2011 public research (service itself UNCONFIRMED today)

Author: Den Delimarsky, “Querying The Xbox Live Game Marketplace — From Anywhere”, 2011-05-18, `https://den.dev/blog/query-xbox-marketplace/` (fetched 2026-10-04).

- Base: `https://catalog-cdn.xboxlive.com/Catalog/Catalog.asmx/Query` — NOT usable as VS service reference (403); usable via WebClient/HttpWebRequest with explicit params.
- Call: `?methodName=FindGames` (author: “only method used in the marketplace to get content”; others may exist — UNCONFIRMED).
- Param style: repeated `Names=<name>&Values=<value>` pairs, NOT normally-named query params. Example skeleton:
  `.../Query?methodName=FindGames?Names=UserTypes&Values=1&Names=CategoryIds&Values=3027` (incomplete example per author).
- Required-ish set (author’s “new games” set): Locale=`en-us`, LegalLocale=`en-us`, Store=`1`, PageSize (max 300; total in `totalItems`), PageNum, DetailView (3 boxart / 4 slideshow / 5 ratings+capabilities), AvatarBodyTypes (`3`+`1`), OrderDirection, OfferFilterLevel, MediaTypes, OrderBy, ImageFormats (`4`=JPEG), ImageSizes, OfferTargetMediaTypes, CategoryIds (`3027` = Xbox LIVE Games in examples), UserTypes (`2`+`3`).
- MediaTypes seen: `1`/`21` (GoD/full), `23` (Arcade), `19` (demo), `37` (indie), `18` (add-on), `20` (theme), `22` (gamerpic), `30`/`34` (video). CategoryIds seen: `3000` genres root, `3001` Other, `3002` arcade-genre bucket, `3005` Family, `3006` Fighting, `3007` Music, `3008` Platformer, `3009` Racing, `3010` RPG, `3011` Shooter, `3012` Strategy, `3013` Sports, `3018` Card&Board, `3019` Classics, `3022` Puzzle, `3027` XBL Games. All values are author-observed (2011); treat as historical, PARTIALLY CONFIRMED.
- Response: Atom feed (`xmlns:live="https://www.live.com/marketplace"`), `live:totalItems`/`numItems`, per-entry title/media (`mediaType`, `titleId`/`effectiveTitleId`, dev/pub, dates, `ratingId`/descriptors, `gameCapabilities` offline/online/coop/leaderboards, `offerCounts` per targetMediaType/userType, ratings aggregate/count), `categories`, `slideShows` with `fileUrl` under `download.xbox.com/content/images/...`. Full Guwange example on page.
- Author’s explicit boundary: “endpoints listed here are used as a catalog and a download service. You cannot download any of the listed content by knowing the information returned… You should not even attempt to do so… illegal.” Purchase/download of licensed content is out of scope here.

## Per-type / per-genre / per-letter query builders (verbatim patterns, historical)

Full URL patterns for New/Demos/Arcade/GoD/Indie/Videos/Add-Ons/Themes/Gamerpics, every genre bucket, and TitleFilters `A`–`Z` are on the page. Do not duplicate all ~25 URLs here; link the page. All PARTIALLY CONFIRMED (2011) and dead today.

## What this is NOT (explicit non-coverage)

- Purchase, license, payment (PayPal-era), download authorization, account auth (Live ID/XSTS), console-signed license acquisition, title-specific entitlements — UNKNOWN / not publicly documented in verifiable form found in Cycle 3. No endpoints invented here.
- Modern Xbox services (XSAPI/REST for One/Series/PC) are separate — see `xbox-live-services-public.md`.

## Sources / References

- Den Delimarsky, “Querying The Xbox Live Game Marketplace — From Anywhere” (2011-05-18), `https://den.dev/blog/query-xbox-marketplace/` — base URL, FindGames, Names/Values pattern, param sets, Atom schema, per-type URLs. Fetched 2026-10-04. Evidence: dated public RE with full XML sample.
- Status anchor: Xbox Wire store-closure notice 2023-08-17 (see `marketplace-closure-2024.md`) — service dead post-2024-07-29.
