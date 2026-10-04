# Contribution and quality gates

> Binding checklist before every important commit.

## Before commit

- [ ] Links resolve (spot-check every new URL).
- [ ] No invented names/offsets/registers/APIs. Every table row has evidence or a downgraded confidence label.
- [ ] Uncertainties marked (`INFERRED`/`UNCONFIRMED`/`UNKNOWN`).
- [ ] Contradictions documented, not hidden.
- [ ] No duplicates (grep for existing coverage).
- [ ] Terminology consistent with glossary.
- [ ] Each doc has `Sources / References` with URL + title + what-evidence.
- [ ] No secrets/keys/tokens/personal data. No piracy/malware instructions.
- [ ] Code marked `PSEUDOCODE` when not a real implementation; incomplete parts listed.

## File granularity

- Prefer dozens/hundreds of small specialized Markdown files over one giant file.
- Split when a section has enough sourced material for its own page.
- Keep filenames `kebab-case.md`.

## Commits

- Group logically (e.g., `docs(cpu): xenon core docs from Free60+Copetti`).
- Push to `main` after each research block. Local-only is not done.
- If push fails (auth/network/GitHub), report exactly what happened. Do not claim “done”.

## Sources

- Repo-local convention. No external citation required.
