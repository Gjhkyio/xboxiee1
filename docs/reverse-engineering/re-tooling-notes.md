# RE tooling notes — emoose + x360-research (Cycle 3)

## emoose/xbox-reversing — CONFIRMED (repo fetched 2026-10-04)

`https://github.com/emoose/xbox-reversing` — “Information & parsers for under-documented Xbox360 structures/file formats (STFS/GDFX/XDBF/XEX…)”, BSD-3-Clause, 81 stars / 6 forks at fetch.

- `stfschk/` — verify hashes+signature of STFS (LIVE/PIRS/CON); README + `templates/Xbox360Container.bt` (010 Editor, mainly Anthony + emoose additions); cross-refs Free60 STFS. Queued: run against known-good vectors? No — only document, never ship copyrighted packages.
- `xbox360.py` + `x360_imports.py` — IDA 7.0+ Python loader for (uncompressed) XEX incl. pre-1888 betas (needs PyCrypto); near-parity with xorloser Xex Loader except compressed-XEX (no LZX in py2.7) + imports-window API gap. Native-DLL successor: `emoose/idaxex`. Queued: version-pin + loader behavior notes.
- `templates/` — 010 Editor installs via Options → Compiling → Templates.

## InvoxiPlayGames/x360-research (“Emma’s Xbox 360 Research Notes”) — PARTIALLY CONFIRMED (search-verified, full read queued)

`https://github.com/InvoxiPlayGames/x360-research` — personal reversing/research notes (own RE + other projects/fellow hackers), git-repo-as-wiki. Shoutouts: DrSchottky X360 tutorials (razielconsole), TEIR1plus2 Xbox-Reversing. Removal-request policy for homebrew authors noted. Topics include XUSB peripheral auth (“Xbox Security Method 3” per invoхi site snippet — UNCONFIRMED detail until read).

## How to use these here

- Cite file:line for every parser claim from Cycle 4 on. Never present parser output schemas as console-ground-truth without Free60/Xenia triangulation.
- 010 templates and IDA loaders are analysis aids; keep license attributions (BSD-3-Clause, Anthony credits).

## Sources / References

- emoose repo (above) — fetched 2026-10-04.
- InvoxiPlayGames repo + `https://invoxiplaygames.uk/` snippet — search-verified 2026-10-04; full fetch queued.
- TEIR1plus2 `Xbox-Reversing`, DrSchottky tutorials — queued.
