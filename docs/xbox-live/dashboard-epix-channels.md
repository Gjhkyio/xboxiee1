# Dashboard EPIX channels and staging mode (historical RE, 2010–2011 era)

> Source: landaire.net, “MITMing the Xbox 360 Dashboard for Fun and RCE” (2024-07-30), `https://landaire.net/mitming-the-xbox-360-dashboard-for-rce-and-fun/` (fetched 2026-10-04). Descriptive RE history, not an operational guide. All hosts dead or repurposed today.

## Manifests — PARTIALLY CONFIRMED (author-observed, 2010–2011)

- Retail root: `http://epix.xbox.com/epix/en-US/homepage.xml`; beta audiences: `.../beta/preview_green/...`, `.../beta/takehome_green/...`; alternate domain `epix-preview.xbox.com` held all test channels. Manifests carried channels/slots/ads (`XBOX360` → `epix://xbox360channel.xml`; `XBOX_PRE_RELEASE` with slots, `shallowimg` under `epix.xbox.com/shaXam/...JPG`, `epix` nodes with `LUAXZP` `.lzp` Lua packs + `param url=http://live:11/xedl/...`).
- Files were RSA-signed (screenshot of manifest header sig on page); Lua packs likewise. MITM trick was mirroring + hosts-file/`epix.xbox.com→127.0.0.1` re-pathing (`/beta/preview_green/` stripped), NOT signature forgery. PartnerNet-vs-ProdNet `marketplace.xboxlive.com` hosts swap also described (Emma’s success after author’s failure).
- Old repo commits in this project referenced `epix.xbox.com/*.dashhome.xml` (deleted Jun 2026) — consistent with EPIX dashboard file family, but those exact files were never analyzed here.

## Environments and Live Hive — PARTIALLY CONFIRMED (author-observed via devkit recoveries)

- Alt Live envs on dev launcher: `int2`, `vint`, others. `vint` catalog roots: `CatalogCDNUriRoot=http://catalog.vint.xboxlive.com`, `CatalogUriRoot=http://catalog.vint.xboxlive.com` (ports 80/802/804 variants in Hive dump on page) + `ContractManagerUriRoot=http://contractfd.test.xboxlive.com/v2`, `CloudStorageStatus`, `CommunityGamesTrialExpirationInSeconds=480`, etc. “Live Hive” = key-value store for Live settings.
- `int2` manifests exposed Gold-offer tests (author anecdote: $1 Gold rotation → $6/year). Anecdote, UNCONFIRMED as general fact; preserved as author report with abuse details omitted.

## Staging mode — PARTIALLY CONFIRMED (IDA observation, with author correction)

- “Preview Tool” (tiny dash-channel app, expiring, Live-checked) enabled preview mode → dash FPS/debug overlay + internal channels without MITM.
- IDA: Preview Tool calls `XamSetStagingMode()` → sets global; `XamVerifyXSignerSignature` honors devkit/staging allowance and debug-prints `Signature not trusted, but ok since we're in staging mode or on a devkit`. Author correction: allowance needs caller flag for untrusted sigs; modern dash behavior may differ. No signature-bypass instructions here.
- Author hypothesis (explicitly unconfirmed on page): dash/`XamGetStagingMode()` switches EPIX CDN/path, possibly via Live Hive override. Mark INFERRED/UNCONFIRMED.

## Archive

- Author’s saved manifests: `https://archive.org/details/epix-playground-manifests` (Lua scripts NOT mirrored; `epix-preview.xbox.com` dead). Queued for Cycle 4 ingestion (file list + hashes, no re-host of signed assets beyond citation).

## Sources / References

- landaire.net article above — all sections. Fetched 2026-10-04. Evidence: dated photos, XML, IDA screenshots, Archive link.
- Context: Emma (@carrot_c4k3) Hulu-Plus-era RE motive; Archangel/Halo-4-beta offer-ID brute-force anecdote (descriptive only).
