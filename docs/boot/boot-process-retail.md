# Retail boot process — chain overview

> Authoritative Cycle-1 source: Free60 “Boot process”. Devkit differences in sibling.

## Chains — CONFIRMED as Free60-documented flow (not as independently re-verified silicon trace)

```text
Slim (and newer Phat):        1BL → CB_A → CB_B → CD → CF → CD → HV → Kernel → Dashboard
Older Phat:                   1BL → CB    → CD → CF → CD → HV → Kernel → Dashboard
Devkit Phat (summary):        1BL → SB → SC → SD → HV → Kernel → Dashboard
```

- Source: `https://free60.org/System-Software/Boot_Process/` (fetched 2026-10-04). Page notes process differs between Devkit/Retail and boxes with secondary CB loader (Trinity/some Jaspers).
- Each bootloader verifies next (RotSumSHA1 hash checks on retail; signature checks on devkit SD/SE per page). Details in `bootloaders-1bl-cb-cd-cf.md`.
- Up to 2 CF/CG patch pairs for delta-patching base kernel (LZX). CF loads CG per NAND header + CF header blocks, decrypts with key from CF decryption, delta-applies to base kernel in RAM, returns to CD → HV reset vector. Same source.

## Kernel handoff (devkit POST list, as reported — PARTIALLY CONFIRMED)

Free60 lists post-handoff init (memory manager, stacks, objects, phase-1 thread/processors, keyvault, HAL phase 1, SFC, security, `INIT_KEY_EX_VAULT`, settings, power, video, audio, `bootanim.xex`, SATA, Shadowboot (non-retail), dump/root, STFS, XAM) then ordered XEX loads:

```text
xam.xex → xbdm.xex → xstudio.xex → ximecore.xex → Xam.Community.xex (disk)
→ huduiskin.xex → xshell.xex (devkit) / dash.xex (retail)
then unload huduiskin.xex + bootanim.xex → dashboard
```

> Treat names/order as reported devkit observation. Retail differences + HAL/SFC specifics are Cycle 2 (need kernel/HV sources + POST audit).

## Confidence

| Claim | Confidence |
|---|---|
| Existence/order of 1BL/CB/CD/CF/HV/Kernel stages | CONFIRMED as Free60-documented architecture (single strong community source; corroborated by XenonLibrary Bootloaders + Xbox-Reversing notes — to be fetched Cycle 2) |
| Hash-vs-signature distinction retail/devkit | PARTIALLY CONFIRMED (single page) |
| Per-function pseudocode addresses, keys, salts, ROT algorithms | UNKNOWN in Cycle 1 — do not cite without `1bl_Code`/`CB_Code` audit (queued) |

## Sources / References

- Free60 Wiki “Boot process”, `https://free60.org/System-Software/Boot_Process/` — full chain + per-stage paragraphs + devkit kernel list + Core OS executables. Fetched 2026-10-04. Evidence: community RE documentation with links to `1bl_Code`/`CB_Code`.
- XenonLibrary “Bootloaders”, `https://xenonlibrary.com/wiki/Bootloaders` — chain-loaded verification summary (search-verified; direct 403 on 2026-10-04, needs Archive retry). Corroboration queued.
- GitHub `TEIR1plus2/Xbox-Reversing` README (1BL/CB_A notes: 1BL at `0x8000020000000000`, CB at `...00010000`, key=1BL key+salt in CB header) — found via search 2026-10-04; full fetch queued Cycle 2. Do not quote addresses as CONFIRMED until source re-read.
