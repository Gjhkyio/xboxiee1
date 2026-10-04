# Xenia emulator — open-source 360 research implementation

## What it is — CONFIRMED (project existence/scope)

- “Experimental, free and open-source Xbox 360 emulator for Windows, and other OSes” (Emulation General Wiki). No 360 system files required (Xenia wiki Quickstart: “Xenia doesn’t require any Xbox 360 system files”). Research-purpose reimplementation of Xenon CPU, Xenos GPU, kernel/syscalls at HLE level (community descriptions; code audit queued).
- Repos: `https://github.com/xenia-project/xenia` (upstream) and experimental fork `https://github.com/xenia-canary/xenia-canary` (xb script, setup docs). Topic `https://github.com/topics/xbox360` lists Xenia + ISO→GoD tools.
- Related: `rexdex/recompiler` (360→Windows exe converter, 2017, HN discussion notes “emulate kernel at syscall level, don’t touch userland” — UNCONFIRMED characterization until code read); XenonRecomp (360→C++ tool, 2026 social posts — UNCONFIRMED, queued).

## Why it matters here

- Best observable-behavior oracle for CPU/GPU/kernel: CPU recompiler, GPU command-processor, XEX loader, STFS/SVOD, kernel exports. Cycle 2 must walk `src/xenia/kernel/*`, `src/xenia/cpu/*`, `src/xenia/gpu/*` with file:line citations. Nothing from Xenia is cited as ISA authority in Cycle 1.
- Management: Xenia Manager (`https://xenia-manager.github.io/`) — updates/patches/per-game configs; RetroBat wiki notes no BIOS + no manual control config (secondary, queued verification).

## What Cycle 1 does NOT do

- No build/run instructions beyond repo links. No game-specific compatibility claims. No syscall tables (UNKNOWN until source walk).

## Sources / References

- Emulation General Wiki “Xenia”, `https://emulation.gametechwiki.com/index.php/Xenia` — experimental FOSS 360 emulator scope. Search-verified 2026-10-04.
- Xenia wiki “Quickstart”, `https://github.com/xenia-project/xenia/wiki/quickstart` — sysreq + no-system-files note. Search-verified 2026-10-04.
- GitHub `xenia-project/xenia`, `https://github.com/xenia-project/xenia` — upstream. Search-verified 2026-10-04.
- GitHub `xenia-canary/xenia-canary`, `https://github.com/xenia-canary/xenia-canary` — fork. Search-verified 2026-10-04.
- Tech Insider “Xenia vs Canary vs Cxbx-Reloaded” (2026), `https://tech-insider.org/ca/xenia-vs-xenia-canary-vs-cxbx-reloaded-2026/` — research-effort framing (Xenon/Xenos/kernel). Secondary, queued.
