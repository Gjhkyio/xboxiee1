# Xbox 360 Technical Research Encyclopedia — xboxiee1

> **Status:** Research in progress. Long-range, evidence-only technical library.
> **Language:** English primary (technical), with Spanish navigation where useful.
> **Rule:** Zero invention. Every important technical claim needs a real source or an explicit confidence label.

## Objective

Build a technical knowledge base that allows a technically capable reader to understand, from the ground up:

```text
hardware → firmware → boot → hypervisor → kernel → APIs → executables →
storage → networking → formats → services → debugging → reverse engineering → emulation
```

and to distinguish at every step what is:

- `CONFIRMED` — documented by primary source, verifiable code, or multiple independent technical sources.
- `PARTIALLY CONFIRMED` — supported by strong evidence but with gaps or single-source dependency.
- `INFERRED` — reasonable deduction from observed behavior or secondary analysis, explicitly marked.
- `UNCONFIRMED` / `UNKNOWN` — reported but not verified, or currently unknown.

This repository is **not** an app, frontend, backend, SaaS, or product. It is a documentation and research repository. Code appears only as документаl aids: parsers, inspection scripts, clearly-marked pseudocode.

## Repository

- Canonical: `https://github.com/Gjhkyio/xboxiee1.git`
- Branch: `main`
- All research output must live inside this repo and be pushed to GitHub. Local-only work does not count as done.

## How to navigate

- Start: [`docs/index.md`](docs/index.md)
- Methodology: [`docs/methodology/confidence-levels.md`](docs/methodology/confidence-levels.md)
- Glossary: [`docs/glossary.md`](docs/glossary.md)
- Master sources: [`docs/references/master-sources.md`](docs/references/master-sources.md)

### Topical entry points

| Area | Path |
|---|---|
| System architecture overview | `docs/architecture/overview.md` |
| CPU (Xenon) | `docs/cpu/` |
| GPU (Xenos) + eDRAM | `docs/gpu/` |
| Memory (unified 512 MB GDDR3) | `docs/memory/` |
| Boot process + bootloaders | `docs/boot/` |
| Hardware revisions | `docs/hardware/` |
| Executables (XEX) | `docs/executables/` |
| Packages (STFS/CON/PIRS/LIVE) | `docs/packages/` |
| Research projects (Free60, XenonLibrary, Xenia) | `docs/research/` |

## Truthfulness rules (binding)

1. Do not invent APIs, functions, structs, protocols, offsets, registers, commands, formats, versions, specs, internal names, or behaviors.
2. Do not present hypotheses as facts. Do not present rumors as official documentation.
3. Every document must have a `Sources / References` section with URL, title, author/date when available, and what evidence it provides.
4. When sources contradict, document the contradiction. Do not silently pick one.
5. Mark pseudocode as `PSEUDOCODE`. Mark incomplete examples as incomplete.
6. No credentials, secrets, tokens, personal data, or illicitly obtained material.
7. Security/DRM/crypto: document only publicly-analyzed behavior, existing research, and limitations. No invented details.

See [`docs/methodology/confidence-levels.md`](docs/methodology/confidence-levels.md) and [`docs/methodology/source-priority.md`](docs/methodology/source-priority.md).

## Contributing research

- Prefer many small specialized Markdown files over one giant file. Example: split `gpu.md` into `xenos-overview.md`, `xenos-unified-shaders.md`, `xenos-edram.md`, etc., when evidence justifies it.
- Include technical tables (`component | function | evidence | source | confidence | notes`) where useful.
- Diagrams in Mermaid/text only for demonstrated connections. No invented wiring.
- Verify links before commit. Remove unsupported claims or downgrade their confidence.
- Commit frequently with descriptive messages. Push to `main` after each research block.

## Legal / scope

Research, interoperability, learning, emulation, and technical understanding. Not a piracy guide. Not a malware guide. Not a credential-theft guide. Authentication/security sections cover only publicly documented architecture and published reverse-engineering analysis.

## Current coverage (Cycle 1)

This cycle establishes the skeleton + first evidence-backed core:

- Architecture overview (Copetti, Wikipedia tech specs, Beyond3D via secondary citations)
- Xenon CPU (Free60, Copetti, IBM developerWorks via archive)
- Xenos GPU + eDRAM (Wikipedia Xenos, Beyond3D article lineage, Copetti, XenonLibrary mirror notes)
- Unified memory
- Retail boot chain 1BL→CB→CD→CF→HV→Kernel (Free60 Boot_Process)
- Revisions Xenon→Winchester (ConsoleMods, Wikipedia tech specs)
- XEX container (Free60 XEX page — marked as early speculation + header tables)
- STFS (Free60 STFS page)
- Research landscape (Free60, XenonLibrary, Xenia, Copetti)

All Cycle-1 docs are intentionally conservative: where Free60 itself marks a page as speculation, we propagate that label.

## Roadmap

- [ ] Cycle 2: Southbridge (ANA/HANA/KSB), NAND/SFC, DVD, HDD, USB, Ethernet, Audio/Video, SMC, RF, POST
- [ ] Cycle 3: Hypervisor, kernel, XAM, syscalls, memory layout, interrupts/timers/scheduling
- [ ] Cycle 4: Filesystems FATX/GDFX/GDF, XDBF/GPD, XConfig, profiles/saves/achievements
- [ ] Cycle 5: Xbox Live historic/technical, networking, content pipelines, updates
- [ ] Cycle 6: Security chain deep-dive (public analysis only), XDK/devkits, RROD/errors, teardown/FCC
- [ ] Cycle 7: Emulation (Xenia source walk), tooling (libxenon, xextool lineage), RE case studies

## Sources

See [`docs/references/master-sources.md`](docs/references/master-sources.md) for the prioritized source list used in Cycle 1.
