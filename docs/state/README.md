# docs/state/ — Cross-Thread Coordination Layer

This folder is the **shared memory** for every chat thread working on ChairWoman (TCW).

## Why this exists

Per-thread context loss was identified on 2026-06-11 as a real productivity bottleneck. Threads were repeatedly re-discovering known facts, asking questions other threads could answer, and accumulating "open loops" that no single thread owned. The userMemories layer is helpful but lossy at the detail level needed for active execution.

This folder fixes that by giving every thread a canonical place to read and write shared state.

## File structure

| File | Purpose | Behavior |
|---|---|---|
| `../STATE.md` (one level up at repo root) | Living current-state snapshot — what's true right now | **Overwritten** each session with current truth (structure preserved) |
| `history.md` | Chronological log of state changes | **Additive only** — never delete, append new entries at top |
| `decisions.md` | Decision log with rationale | **Additive only** — every meaningful decision gets an entry |
| `learnings.md` | Things discovered along the way (patterns, anti-patterns, gotchas, breakthroughs) | **Additive only** — keep everything we learn |
| `open-loops.md` | Active cross-thread coordination items | **Updated** as loops open/close, with attribution |

## Protocol

**At session OPEN:**
1. Read `../STATE.md` fully
2. Read `open-loops.md`
3. Read `decisions.md` if working in a domain that's had prior decisions
4. Begin work

**At session CLOSE (mandatory):**
1. Update `../STATE.md` — overwrite with current truth, preserve structure
2. Append to `history.md` — what changed this session, why
3. Append to `decisions.md` — any decisions made, with rationale + alternatives
4. Append to `learnings.md` — anything new we figured out
5. Update `open-loops.md` — open new loops, close completed ones
6. `git add -A && git commit -m "state: <summary>" && git push origin main`

## Why additive (never delete)

The point of `history.md`, `decisions.md`, and `learnings.md` is that they remember *everything we've ever known*. Even when something changes — for example, "Reddit pain-point agent was deprecated" — the prior decision to build it stays in `decisions.md`, and the new decision to deprecate it gets a new entry. The reasoning trail is preserved. This protects against repeating mistakes.

`STATE.md` is different — it's a snapshot of current truth, so it gets overwritten. But the history of how it got to today is preserved in this folder.

## Cross-thread etiquette

- If you're closing an open loop another thread opened, leave a closing note in `open-loops.md` with your thread's name, the close date, and a one-line outcome
- If you're opening a new loop, name the closing condition clearly (so any thread can pick it up and close it)
- Decision entries should always include "alternatives considered" so future threads understand the path not taken
