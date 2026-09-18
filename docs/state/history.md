# TCW History — Chronological State Log

> **Additive only. Never delete entries. Append new entries at the TOP (most recent first).**
>
> Each entry: date · thread · what changed · why

---

## 2026-06-11 (Chuck) — Subscription ledger finalized + subscriptions_tracker dispatched
- Removed the phantom "Google AI" line; added ManyChat Pro ($15+) and Stripe ($0+txn); flipped the confirm note to confirmed (ManyChat Pro, Quo $21, Gemini $20, Stripe $0+txn).
- Wrote docs/dispatches/2026-06-11-subscriptions-tracker.md — CFO subscriptions_tracker agent (Mansa Musa peer). Marshall having shipped (#57), this is now next in queue, not blocked.
- Applied via Terminal MCP-bypass (Claude Desktop MCP write path chronically hangs ~4 min; routed around it).

## 2026-06-11 (later, build thread report-back) — Credit Quing 10-SKU catalog COMPLETE + flagship guide narrative gap identified

**What:** Build thread completed Credit Quing catalog rebuild. All 10 kits generated, packaged, verified. ALL HARD BLOCKS PASSED (10 products, flagship 24 letters = union 24). Clickable Contents (every entry `<a href="#sec-N">`, Puppeteer preserves anchors). One transparent CQ logo everywhere — crownSvg vector + opaque crown.png crest deleted. Packaging fix: downscaled `logo-sm.png` (86 KB) for letter headers so flagship bundle stays within Supabase max object size.

**Honest heads-up from build thread:** Flagship $497 Greene Process — guide narrative (Who-this-is-for, The Method, Handling Every Response, FAQ, escalation) didn't survive the earlier flagship reassembly. Flagship currently reads as a (well-organized, clickable) letter library without the system walkthrough its positioning promises. Other 9 kits have full narratives.

**Build thread offer:** Regenerate just the flagship's guide section (one targeted call) and re-stitch it above the 24-letter library.

**Operator decision:** APPROVE — regenerate. $497 premium pricing requires the methodology, not just letters. New open loop tracked.

**Why this matters:** First major deliverable shipped vs. specced. 15-day spec/ship ratio finally inverts. Storefront dispatch becomes immediately actionable — product files exist NOW.

---

## 2026-06-11 (later, build thread response) — Marshall dispatch written by build thread

**What:** Build thread converted the architectural answer (Marshall reports to Mansa Musa as peer agent, no new orchestration) into a Codex-ready B.U.I.L.D dispatch. Their version uses tighter idioms matching the existing chairwoman-v1 codebase: drop folder at `~/iCloud/Marshall/Inbox/`, charter path `docs/agents/credit-enforcement/MARSHALL.md`, briefing_status enum `(none|info|watch|urgent)`.

**Why:** The cross-thread architectural question got answered, the build thread immediately operationalized it. This is the system working as intended — even before the state files are committed.

**Decision:** Use build thread's dispatch as execution path; mine at `docs/dispatches/2026-06-11-marshall-build.md` becomes architectural reference documentation. Both paths land at the same outcome.

---

## 2026-06-11 (later in same session) — Operator confirmed Runway cancellation + storefront dispatch written

**What:** Operator confirmed Runway cancelled in dashboard. Last access day 2026-06-29. Third dispatch written: Credit Quing storefront launch ($7 Cease-the-Calls on Gumroad, smallest possible launch path).

**Why:** Closing loops. Runway was the duplicate-capability spend identified in the audit. Storefront dispatch is the missing piece between "10 products ready" and "first dollar earned."

**State changes:**
- Runway: cancelled, expires 2026-06-29 (closed in open-loops.md)
- Cost ledger updated in STATE.md
- New dispatch file: `docs/dispatches/2026-06-11-credit-quing-storefront-launch.md`

---

## 2026-06-11 — Claude (audit + architecture thread)

**What:** Created the docs/state/ folder structure and STATE.md as the cross-thread coordination layer.

**Why:** Per-thread context loss identified as a real productivity bottleneck. Operator confirmed: *"there needs to be a doc in the archives that can be accessed by all threads."* Threads were re-discovering known facts and asking questions other threads could answer.

**Additional state changes from this session:**
- Confirmed `reddit_painpoint_agent` deprecated — Reddit Nov 2025 Responsible Builder Policy killed self-service API keys
- Confirmed Federal Benefits Finder bugs: (1) panels overflow / bleed (CSS), (2) links route to "how-to" articles instead of official claim portals
- Confirmed 10-SKU Credit Quing catalog ready to ship — Codex run 27247424124 succeeded
- Confirmed Runway $35/mo to be cancelled — Heygen + ElevenLabs replaces capability, no duplicate spend
- Wrote Marshall build dispatch (docs/dispatches/) for execution by Codex
- Wrote Federal Benefits Finder bug-fix dispatch (docs/dispatches/) for execution by Codex

---

## 2026-06-09 — Heygen subscription thread (Credit Quing build)

**What:** Committed `PRODUCT_AGENT_STANDARD.md` as binding operating standard. Expanded corpus dispatch with INGEST roots + QUARANTINE list. Wrote formal verification report documenting prior Codex runs (27218352484, 27233683281) as packaging-only passes. Added hard gates preventing future fake-success reports. Third Codex run (27247424124) launched with cq_catalog + product_versions tables newly created.

**Why:** Two prior runs had reported green CI checks while having never actually run the product-builder against the corpus. Hard gates were needed to prevent silent failures.

---

## 2026-06-04 — Reddit agent thread

**What:** Built `reddit_painpoint_agent` Python package — full pipeline with IDF²-cosine clustering, 56-test suite passing, source-agnostic architecture.

**Why:** Operator needed a tool to mine Reddit for pain points across MTR, real estate, plus-size swimwear, tax deeds verticals to validate product opportunities.

**Note for future:** This was deprecated 2026-06-11 due to Reddit policy change. The analysis engine (IDF²-cosine clustering, opportunity scoring) is durable IP and source-agnostic — can be rewired to a different data source if needed.

---

## 2026-05-31 — Phase 4.5.5.3 (Session Room reframe)

**What:** Shipped cinematic Stage modal (520-720px ambassador, FaceTime-style), wider left rail (300px column, 128px ambassador thumbnails), removed scanline/hologram treatment in favor of warm session-room feel. Pixelation fix via lighter filters. Commits 4123a27 + de6def4 + e6d3227.

**Why:** Operator feedback: "still too small for the animation, details, and shows pixelated... I'd like this presented like a FaceTime call realistic look and feel of each Ambassador. They are not AI, they are not videos, but a rendering of what they could have been like in real life and agreed to mentor."

---

## 2026-05-31 — Quo phone activated

**What:** Phone number 442-255-6585 went live. Plan upgraded to $19.50 + $1.50 carrier fee. Full IVR (Press 1 Book / Press 2 Pricing / Press 3 Voicemail) + Sona AI receptionist + during/after-hours SMS auto-replies. Pricing $25/$15/$40/$60 locked across all scripts.

**Why:** Super Clean Bins needed an automated phone presence so the operator never answers calls. Initial silent-loop bug on Press 2 resolved by operator reframing pricing audio to ask "want to schedule today?" — activates Sona naturally.

---

## 2026-05-31 — Phase 4.5 Ambassador foundation

**What:** Shipped 8 ambassadors with CGI portraits → Runway idle-loop videos. Mansa Musa activated (CFO, 53+ runs). 7 others stubbed. Voice perspectives defined in `lib/ambassadors.ts`. Holographic UI initially, refined to Session Room (see 2026-05-31 entry above).

**Why:** C-suite metaphor for organizing agents under named ambassador identities. Each brand/domain reports to its ambassador. Mansa Musa owns the cashflow recovery lane.

---

## 2026-05-30 — Athlos Training Grounds spec site shipped

**What:** Complete Next.js 16 + Tailwind v4 + Framer Motion site at athlos-training-grounds.vercel.app. 14 sections including the breakthrough Locomotive Mtl-style cinematic MeetCoach section (v7) that locked the "premium = compositional depth" pattern. Outreach sent.

**Why:** First Ashe Systems spec build to close a local gym. Set the technical bar for subsequent gym site builds.

**Status as of 2026-06-11:** Live, conversion 0%.

---

## 2026-05-27 to 2026-05-29 — Vault foundation

**What:** Built `operators-second-brain` private GitHub repo with 7-zone structure, 8 domains. Recovered from a data wipe incident mid-build. Set up vault_cache Supabase table with 1hr TTL for ChairWoman to consume vault data.

**Why:** Operator's personal data (statements, profile, notes) needed to live separately from application code. Vault as source of truth, ChairWoman as the application that reads it.

---


## 2026-06-11 — Chuck thread: Marshall charter landed, flagship verified, cost ledger corrected
- Landed `docs/agents/credit-enforcement/MARSHALL.md` (the charter the Marshall build depends on; prior commit had hung). Deployed READY.
- **Flagship $497 verified WHOLE** via independent DB read: all 6 Greene Process guide sections + letter library present in `cq_catalog` body (~180k chars). #56 regen confirmed effective at the content level. All 10 content-verified ready to publish.
- Corrected subscription ledger from operator signup data: Heygen Creator $29 ACTIVE (billing 6/30), ElevenLabs Creator $22 ACTIVE (started 5/30; was mis-tracked Starter $5), Gemini $10→$20. Removed Heygen/ElevenLabs from "to add" + "blocked"; SCB now gated only by the content pipeline.
- Closed the Heygen+ElevenLabs subscription loop.
- Declined the Higgsfield annual 55%-off offer (annual prepay breaks locked rule; premature spend).

## 2026-09-18 — Claude (Cowork, GCG thread): government contracting lane built into TCW

**What:** GCG/BHF government contracting added as a standing lane under Mansa Musa —
team lead `govcon-lead`, three agents, two tables, a board at `/govcon`, 47 tests.

**Why:** GCG was being run out of a chat thread, an iCloud folder and two pinned
artifacts. The operator could not find the dashboard on returning to the thread, and
asked (not for the first time) that it live inside TCW instead of beside it.
`opportunity_finder` exists to surface lanes worth systematizing; federal contracting
is the first one to graduate, so it got the standing-lane treatment rather than a
separate system.

**Built:**
- `supabase/migrations/phase_govcon_board.sql` — team lead, 3 agents, `govcon_entities`,
  `govcon_solicitations`, seeded with the three real registrations.
- `lib/agents/govcon/scoring.ts` — the 100-point model and hard gates, PURE.
- `lib/agents/govcon/findings.ts` — registration window rules, PURE.
- `lib/agents/govcon/{profile,scanner,assessor,registrations}.ts` — I/O wrappers.
- `app/govcon/page.tsx` + `app/api/govcon/board/route.ts`.
- `__tests__/govcon/` — 47 tests.

**Design decision worth keeping:** the model judges the nine factors, the pure scorer
makes the decision. Thresholds and the hard-gate override stay deterministic and
testable, so a persuasive solicitation cannot talk the system into a GO.

**Found along the way:** 2 test files were already failing on the operator's machine
under Node 20 (`@supabase/realtime-js` needs native WebSocket). Everything passes on
Node 26, which is installed. Not caused by this work, but it means `npm test` on the
default node has been misleading.

**Open at close:** migration not yet run; `SAM_API_KEY` not set; branch not merged.
