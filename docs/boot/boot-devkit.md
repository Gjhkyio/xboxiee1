# Devkit boot — SB/SC/SD/SE (as reported)

> Single-source (Free60). Keep PARTIALLY CONFIRMED.

## Chain (Free60 summary)

```text
Phat devkit: 1BL → SB → SC → SD → HV → Kernel → Dashboard
```

- Devkit bootloaders “nearly identical” to retail counterparts, but instead of hardcoded hash checks, devkits verify SD and SE by signature checks.
- SC = hardware-init VM run by SB (parallel to retail CB VM role).
- Devkits do not update over air; use pre-patched SE (HV+kernel) without delta CF/CG pairs.

## Retail vs devkit table (as reported)

| Aspect | Retail | Devkit |
|---|---|---|
| CB stage | CB or CB_A→CB_B + hash checks | SB (+SC VM) |
| CD/CF/CG delta patching | Yes (up to 2 pairs, LZX) | No (pre-patched SE) |
| Verification style | Hardcoded hash (+ 1BL RSA per page) | Signature checks for SD/SE |
| Shadowboot | Not on retail | Initialized (per kernel list) |

## Confidence

- PARTIALLY CONFIRMED (single wiki page, no second source in Cycle 1). Needs XDK kernel + Shadowboot pages (`System-Software/Shadowboot`, `XDK_Kernel`) in Cycle 2.

## Sources / References

- Free60 “Boot process” Devkit section, `https://free60.org/System-Software/Boot_Process/` — chain + 3 bullets + kernel list. Fetched 2026-10-04.
