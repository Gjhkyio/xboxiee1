# Marketplace closure (2024-07-29) — official status and preservation impact

## Official change — CONFIRMED (Microsoft)

- Source: Xbox Wire, “The Xbox 360 Store Will Close July 2024…” (2023-08-17), `https://news.xbox.com/en-us/2023/08/17/xbox-360-store-will-close-july-2024/` (search-verified 2026-10-04; full fetch queued).
- From 2024-07-29: no NEW games/DLC/entertainment purchases via 360 Store on console nor `marketplace.xbox.com`; Microsoft Movies & TV app dead on 360 (TV/movie no longer viewable on 360).
- Unaffected per MS: playing/re-downloading previously-purchased 360 content (on 360 AND via back-compat on One/Series X|S); multiplayer where publishers still run servers; purchasing back-compat 360/OG-Xbox titles on One/Series/`xbox.com` (with FPS Boost/Auto HDR/faster loads where applicable).

## Impact on this repo’s API docs — analysis (INFERRED, labeled)

- `catalog-cdn.xboxlive.com` 2011 query surface and `epix.xbox.com` dash channels are dead/repurposed. Keep them as HISTORICAL (2010–2011 observations) with “do not present as working” banners. No live probing from this repo.
- Preservation-relevant open work (UNKNOWN, queued): title-by-title purchased-content re-download paths, back-compat entitlement mapping quirks (e.g. One-store purchase ≠ 360 entitlement in some OG-Xbox cases per community video comments — UNCONFIRMED, needs official/RE source), patch-vs-store-DLC delivery split (e.g. in-game vs marketplace DLC).

## Sources / References

- Xbox Wire 2023-08-17 closure notice (above). Search-verified 2026-10-04.
- GeekWire 2023 preservation-angle coverage (search excerpt) — queued full read.
- AtariAge/Reddit megathreads — community impact only, not technical authority.
