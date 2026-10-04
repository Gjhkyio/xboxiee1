# Confidence levels — binding scale

> Methodology. Applies to every technical document in this repo.

| Label | Meaning | When to use |
|---|---|---|
| `CONFIRMED` | Multiple independent verifiable sources, or primary source (official doc, public source code, directly observable and reproduced behavior). | CPU core count, clock rates cited by IBM/Microsoft + Free60 + Copetti with citations. |
| `PARTIALLY CONFIRMED` | Strong evidence but single-source, incomplete, or version-dependent. | Specific eDRAM transistor counts, NAND sizes per revision where only one wiki table covers it. |
| `INFERRED` | Reasonable deduction from evidence, explicitly reasoned. Never presented as fact. | Performance implications (“~600 cycles per cache miss observed via PIX sample” — reported by Copetti citing SDK profiler). |
| `UNCONFIRMED` | Reported in community/forums without reproducible evidence. | Random forum claims about timings, pinouts without photos/measurements. |
| `UNKNOWN` | No reliable public information found yet. | Exact internal register maps not publicly documented. |

## Rules

1. Every section with a technical claim should carry a label, or inherit a labeled table row.
2. If a source itself says “speculation” (e.g., Free60 XEX page title “File Format Speculation”), propagate at most `PARTIALLY CONFIRMED` and note the source’s own caveat.
3. Contradictions: document both sides with sources. Do not silently resolve.
4. Downgrade on doubt. It is better to mark `INFERRED` than to overclaim `CONFIRMED`.

## Example table pattern

```markdown
| Claim | Confidence | Evidence | Source |
|---|---|---|---|
| Xenon: 3 cores × 2 SMT threads = 6 threads @ 3.2 GHz | CONFIRMED | Free60 specs + Copetti + Wikipedia tech specs converge | see Sources |
```

## Sources

- This methodology is a repo-local convention. No external source required.
- Inspired by standard evidence grading in RE writeups and wiki curation (Free60, XenonLibrary editorial practice of citing dumps/docs).
