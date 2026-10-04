# Xbox Live services — public surface and hard boundaries

> Purpose: separate what IS publicly documented (modern XSAPI/REST, unofficial wrappers) from 360-era private purchase/auth APIs, which have NO verifiable public documentation found in Cycle 3. Nothing invented here.

## Public and official (modern, NOT 360-private) — CONFIRMED existence

| Surface | What it is | Source |
|---|---|---|
| XSAPI (Xbox services API, aka Xbox Live API) + REST endpoints | Two ways to reach Xbox services: client wrapper (auth/encoding/HTTP/async + game-events-only features) vs direct REST (web-service calls, non-XSAPI endpoints). GDK: C-based API only; WinRT/C++11 for XDK/Creators info-only. `libHttpClient` underneath. | Microsoft Learn “Xbox services API overview” (GDK 2510–2610, 2022-08-01), `https://learn.microsoft.com/en-us/gaming/gdk/docs/services/fundamentals/xbox-services-api/live-introduction-to-xbox-live-apis?view=gdk-2604` — fetched 2026-10-04 |
| `microsoft/xbox-live-api` repo | XSAPI SDK repo (access via ID@Xbox/Creators). | `https://github.com/microsoft/xbox-live-api` — search-verified 2026-10-04 |
| REST reference | `atoc-xboxlivews-reference` hierarchy under Learn. | Linked from XSAPI page — queued Cycle 4 |
| OpenXBL (`xbl.io`) | Unofficial wrapper: API key + user-authorized access to profiles/achievements/friends/clips/presence/activity. | `https://xbl.io/` + StackOverflow “Where to start understanding Xbox APIs” — search-verified 2026-10-04 |

> These are One/Series/PC-era services. They do NOT document 360-era console purchase flows, `marketplace.xbox.com` checkout, or console license signing. Do not cite them for 360 behavior.

## 360-era private surface — explicit UNKNOWN list (Cycle 3)

No verifiable public documentation found for: console purchase/checkout calls, payment-instrument handling, license-acquisition protocol (console-signed CON licenses for Marketplace content), auth token flows used by the 360 dash (beyond historical Hive hostnames), title-service matchmaking/sockets packet formats, or per-title service contracts. Forum claims without captures/code are UNCONFIRMED. This list stays UNKNOWN until packet captures, RE writeups with code, or official history appear.

## Related historical notes (descriptive only)

- 360 Store + `marketplace.xbox.com` purchasing ended 2024-07-29 (see closure page). Previously-purchased content remains playable/re-downloadable + back-compat path via One/Series/`xbox.com`.
- GPD title art URL patterns on Free60 GPD page (`image.xboxlive.com`, `tiles.xbox.com`, `avatar.xboxlive.com`, `marketplace.xbox.com/en-US/Title/<id>`) are historical host patterns, not current API docs.

## Sources / References

- Microsoft Learn XSAPI overview (above) — public surface definition. Fetched 2026-10-04.
- `microsoft/xbox-live-api`, `https://github.com/microsoft/xbox-live-api` — SDK existence. Search-verified.
- OpenXBL, `https://xbl.io/` — unofficial wrapper existence. Search-verified.
- apis.io Microsoft-Xbox provider entry — achievements/leaderboards/multiplayer/matchmaking/social/presence/cloud-saves listing. Search-verified, tertiary.
