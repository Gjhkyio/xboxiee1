# Bootloaders — 1BL, CB/CB_A/CB_B, CD, CF/CG (retail)

> Expands Free60 “Boot process” per-stage notes. No keys, no bypass steps. Anything not on the Free60 page is UNKNOWN here.

## 1BL (inside CPU) — PARTIALLY CONFIRMED

- Lives in CPU ROM; loads + decrypts CB(_A) to RAM; RotSumSHA1 + RSA-signature verify; on success jumps to CB(_A).
- Reversed pseudocode linked as `../1bl_Code/` on Free60 page (not audited Cycle 1).
- Xbox-Reversing search excerpt adds: mapped at `0x8000020000000000`, sets HW regs, CB at `0x8000020000010000`, CB decrypt key = 1BL key + salt in CB header. Queued for Cycle-2 fetch; do not treat addresses as CONFIRMED yet.

## CB / CB_A / CB_B — PARTIALLY CONFIRMED

- Slims (and newer Phats): CB_A loads/decrypts CB_B, RotSumSHA1 vs known hash, jumps to CB_B. Older Phats: single CB.
- CB(_B) starts a VM that (per Free60 bullets): inits PCI bridge; disables GPU PCIe JTAG test port; inits serial; talks to SMC to clear “handshake” bit; inits memory; RROD if memory init fails.
- Then loads/decrypts CD, hash-checks, jumps to CD.
- Dumps/RE examples linked as `../CB_Code/` (not audited Cycle 1).

## CD — PARTIALLY CONFIRMED

- Loads/decrypts CE, hash-checks, LZX-decompresses base kernel.
- Checks patch slots; if present loads/decrypts corresponding CF, signature-verifies CF, stays resident but jumps to CF.
- Up to 2 CF/CG pairs.

> Note: page says “CE” where chain shorthand says CD→CF→CD. Preserve source wording; do not normalize. CE vs CD naming + CF/CG vs patch-slot wording needs Cycle-2 disambiguation (likely CD contains CE loader / CG is kernel patch payload).

## CF / CG — PARTIALLY CONFIRMED

- CF reads CG data location from NAND header + remaining CG blocks from CF header; decrypts CG in RAM with key from CF decryption; RotSumSHA1 vs known hash; LZX-delta applies patch to base kernel; jumps back to CD; CD finishes → HV reset vector.

## Open questions (UNKNOWN, Cycle 2)

- Exact RotSumSHA1 definition, RSA key sizes/owners, LZX variant, NAND header layout, fuse checks, SMC handshake bytes, POST codes per stage, CB_A/CB_B split introduction version, JTAG-disable register, memory-init failure RROD pattern.

## Sources / References

- Free60 “Boot process”, `https://free60.org/System-Software/Boot_Process/` — all bullets above. Fetched 2026-10-04.
- Free60 `1bl_Code` / `CB_Code` (linked from page) — queued.
- XenonLibrary “Bootloaders” — queued re-verify.
- `https://github.com/TEIR1plus2/Xbox-Reversing` — queued full read.
