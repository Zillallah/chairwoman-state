# ChairWoman State Mirror (Public)

**Auto-synced public mirror** of cross-thread state from the private
[chairwoman-v1](https://github.com/Zillallah/chairwoman-v1) repo. Any Claude thread can
read these to get current on TCW project state without private-repo access.

## What's here
- `STATE.md` — current state snapshot (deadlines shown as generic windows + lanes only)
- `docs/state/` — additive logs (history, decisions, learnings, open-loops, README)

## What's deliberately NOT here (stays private)
- `docs/dispatches/` — build AND legal dispatches (Marshall litigation, federal benefits)
- `docs/state/PRIVATE-LEGAL.md` — real case numbers / parties / statutes / deadlines / strategy
- Application code, vault content, operator PII

State files are kept PII- and case-specific-free at the source. If you spot leaked
identifiers (case numbers, opposing parties, specific litigation strategy), flag it — the
source files in the private repo need to be cleaned and the offending content moved to
`PRIVATE-LEGAL.md`.

## Read at session open
- https://raw.githubusercontent.com/Zillallah/chairwoman-state/main/STATE.md
- https://raw.githubusercontent.com/Zillallah/chairwoman-state/main/docs/state/open-loops.md
- https://raw.githubusercontent.com/Zillallah/chairwoman-state/main/docs/state/decisions.md

## DO NOT push directly here
Writes happen in the private repo; this mirror auto-syncs on every push to main affecting
state files. Direct pushes here are overwritten on next sync.
