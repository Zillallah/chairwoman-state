# TCW Open Loops

> **Updated as loops open/close.** Each loop has an owner who can close it.
>
> Closed loops move to the bottom under "Closed" — keep them for trail.

---

## OPEN — Critical (real exposure / blocking revenue)

### Flagship $497 Greene Process — guide narrative regen

- **Opened:** 2026-06-11 by build thread (post-catalog-completion verification)
- **Description:** All 10 Credit Quing kits generated, packaged, verified. **However:** Flagship's guide narrative (Who-this-is-for, The Method, Handling Every Response, FAQ, escalation) didn't survive the earlier flagship reassembly. Flagship currently reads as a clickable letter library without the system walkthrough its positioning promises. Other 9 kits have full narratives. **$497 price point requires the methodology, not just letters.**
- **Build thread offer:** "Regenerate just the flagship's guide section (one targeted call) and re-stitch it above the 24-letter library."
- **Operator decision:** ✅ **APPROVE — regenerate.** Premium pricing requires the system. Don't ship $497 flagship without the methodology.
- **Closing condition:** Flagship contains full guide narrative (Who-this-is-for, The Method, Handling Every Response, FAQ, escalation) above the 24-letter library. Re-verified through hard gates. Self-verify pass confirmed.
- **Owner to close:** Build thread (Codex execution)

### Marshall build dispatch → Codex execution

- **Opened:** 2026-06-11 by Claude (audit thread)
- **Description:** Marshall charter is designed but not yet built into chairwoman-v1 codebase. Real deadlines are on the wire across collections-validation, reinstatement-watch, regulatory-complaint, and civil-litigation lanes (specifics in `docs/state/PRIVATE-LEGAL.md`, not mirrored).
- **Update 2026-06-11:** Build thread independently wrote a functionally equivalent Codex-ready dispatch (uses `~/iCloud/Marshall/Inbox/` for drop folder, `docs/agents/credit-enforcement/MARSHALL.md` for charter path, briefing_status enum `(none|info|watch|urgent)`). **Use the build thread's dispatch as the execution path** — they're closer to Codex's idioms. My dispatch at `docs/dispatches/2026-06-11-marshall-build.md` becomes architectural reference documentation. Both paths land at the same outcome.
- **Closing condition:** Marshall registered in `lib/agents/registry.ts` under `ambassador_id: 'mansa_musa'`. Tables created (`case_docket`, `violations_log`, `deadlines`). Drop-folder intake endpoint live. Deadline scheduler running. First successful agent run logged in `agent_runs`. Hard gate per PRODUCT_AGENT_STANDARD §self-verify passes.
- **Dispatch file:** `docs/dispatches/2026-06-11-marshall-build.md` (mine) + build thread's parallel version
- **Owner to close:** Build thread (Codex)

### Federal Benefits Finder bug-fix → Codex execution

- **Opened:** 2026-06-11 by Operator + Claude (audit thread)
- **Description:** Two observed bugs:
  - **(1) CSS:** Result panels overflow / bleed beyond container bounds
  - **(2) Agent output:** Links route to "how-to" articles instead of official government claim portals (e.g., article on "how to file an OPM data breach claim" instead of the actual OPM portal URL)
- **Closing condition:** Panels render within container bounds (no overflow at any viewport width). Every work item from the agent includes an official claim portal URL (not informational article). Agent prompt validated — if no official portal URL can be found, the work item is rejected from the result set rather than padded with an article.
- **Dispatch file:** `docs/dispatches/2026-06-11-federal-benefits-finder-bugfix.md`
- **Owner to close:** Codex

### Runway $35/mo cancelled

- **Opened:** 2026-06-11 by Claude (audit thread)
- **Description:** Runway provides idle-loop video generation only. Heygen + ElevenLabs replaces this capability AND adds talking avatars + lip-sync. Duplicate capability spend.
- **Closing condition:** Runway subscription cancelled in Runway dashboard. Final renewal date noted for downloading any in-flight projects before account loses access.
- **Owner to close:** Operator
- **Status:** ✅ **CLOSED 2026-06-11** — Operator cancelled. Last access day: 2026-06-29. Follow-up: verify no auto-renewal charge after June 29.

### First Credit Quing product live for sale

- **Opened:** Heygen / Credit Quing thread
- **Description:** 10 products are ready to ship per operator confirmation 2026-06-11. None are live for purchase. Smallest possible launch: the $7 Cease-the-Calls tripwire on a storefront with checkout + email delivery.
- **Dispatch:** `docs/dispatches/2026-06-11-credit-quing-storefront-launch.md` — Gumroad recommended, Stan.store alternative
- **Closing condition:** $7 Cease-the-Calls product live on Gumroad checkout. First transaction recorded. ChairWoman dashboard shows the sale under Eshu.
- **Owner to close:** Heygen/Credit Quing thread + operator

---

## OPEN — Medium priority

### Subscription tracker agent under Mansa Musa

- **Opened:** 2026-06-11 by audit thread, queued by Chuck thread
- **Description:** CFO function. Track subscriptions in Supabase, surface renewals/duplicates/total spend through Mansa Musa to the ChairWoman dashboard.
- **Sequencing:** Marshall has SHIPPED (PR #57) — this is now unblocked / next in the Mansa Musa queue.
- **Dispatch:** docs/dispatches/2026-06-11-subscriptions-tracker.md
- **Closing condition:** subscriptions_tracker agent live in registry under mansa_musa; subscriptions table seeded from the current ledger; renewal warnings firing 7d out; dashboard rolled-up spend view live.
- **Owner to close:** Build thread (Codex).

### queendommanagement.com repurposed as Queendom authority hub

- **Opened:** Multiple threads, restated 2026-06-11
- **Description:** Paid Squarespace + Google domain sitting unused. Should host landing pages for each Tier-1 brand (Super Clean Bins, Credit Quing, GreenEscapes, Ashe Systems, Cash Flow Queen) with lead magnets, ManyChat funnel deep-links, email opt-ins.
- **Closing condition:** Top-level queendommanagement.com landing page live with links to each brand sub-page. At least 2 brand sub-pages live with working lead magnet + email capture.
- **Owner to close:** New dedicated thread (not opened yet)

### Land consulting infrastructure

- **Opened:** 2026-06-11 by Claude (audit thread)
- **Description:** Operator's stated business north star vertical (land transactions consulting — Inyokern CA, Georgia, expanding). Proprietary assets exist (Quiet-Title Playbook, MTR Operating Playbook) but neither is packaged, neither is in the repo, neither is producing income.
- **Closing condition:** Quiet-Title Playbook documented as a sellable package. MTR Operating Playbook same. Land consulting page live on queendommanagement.com or dedicated domain. First paying consult booked.
- **Owner to close:** New dedicated thread (not opened yet)

### Super Clean Bins automated launch (Phase 6 Operations)

- **Opened:** Multiple threads, restated 2026-06-11
- **Description:** All set up (Quo phone, brand kit, content batch, mascot images, real before/after photos in iCloud). Nothing automated yet. Needs: Phase 5.0 content generator → posts → Phase 5.4 ManyChat → ChairWoman webhook → Phase 6 booking + dispatch + payment.
- **Closing condition:** First customer booking received through automated flow (no operator manual touch). First service dispatched to contractor (no operator manual touch). First payment processed (no operator manual touch).
- **Owner to close:** Phase 5 + Phase 6 build threads

### Gym outreach 0% response — root cause diagnosis

- **Opened:** Implicitly from 0% conversion data
- **Description:** Athlos closed (one signal), Alpha Omega 6 touches / 0 response, Rebirth 3 day-one touches / 0 response. Pattern unclear — message, channel, timing, prospect quality, or value prop?
- **Closing condition:** Root cause identified (which of the 5+ possible variables). Fix tested on next outreach batch. Either response rate improves or pivot decision made.
- **Owner to close:** New dedicated thread or operator review

---

## OPEN — Low priority

### Blotato $29.99/mo wired to actual content flow

- **Opened:** 2026-06-11 by Claude (audit thread)
- **Description:** Subscription active since June 2026. Distribution capability paid for. Nothing being distributed because content generation pipeline (Phase 5.0) not yet built.
- **Closing condition:** First content batch posted automatically via Blotato to at least 3 platforms (IG, FB, Threads minimum).
- **Owner to close:** Phase 5.3 build thread (auto-posting agent)

### Reddit pain-point agent re-purposed (or archived)

- **Opened:** 2026-06-11 by Claude (audit thread)
- **Description:** Reddit API access changed (Nov 2025 policy). Agent's analysis engine is durable IP. Could be rewired to public `.json` endpoints OR archived for future revival.
- **Closing condition:** Decision documented (archive OR rewire) and executed.
- **Owner to close:** Future dedicated thread (low urgency)

---

## CLOSED — Historical trail

### Heygen + ElevenLabs subscriptions activated
- **Opened:** Multiple threads, restated 2026-06-11
- **Closed:** 2026-06-11 by Operator (confirmed at signup)
- **Outcome:** Both ACTIVE on monthly Creator plans — Heygen Creator (~$29/mo, billing 6/30) + ElevenLabs Creator ($22/mo, started 5/30). Ledger corrected (ElevenLabs had been mis-tracked as Starter $5). Subscription question resolved.
- **Follow-up:** First Heygen avatar (Quing) + first ElevenLabs voice clone — tracked under the content pipeline (Phase 5.0), not a subscription blocker.

### Runway $35/mo cancelled
- **Opened:** 2026-06-11 by Claude (audit thread)
- **Closed:** 2026-06-11 by Operator
- **Outcome:** Operator cancelled Runway in dashboard. Last access day 2026-06-29. Heygen + 11Labs replaces capability. Net cost change after Heygen + 11Labs add: -$1/mo.
- **Follow-up needed:** Verify no auto-renewal charge after June 29. Add to next session's open check.

### Credit Quing 10-SKU catalog generation (Codex run 27247424124)
- **Opened:** Heygen/Credit Quing thread, 2026-06-09
- **Closed:** 2026-06-11 (operator confirmed 10 products ready to ship)
- **Outcome:** Third Codex run successfully generated 10 differentiated products per PRODUCT_AGENT_STANDARD. Hard gates passed. Now blocked on storefront wiring → see "First Credit Quing product live" open loop.

### Quo phone IVR + SMS configuration
- **Opened:** Earlier thread (May 31)
- **Closed:** 2026-05-31
- **Outcome:** 442-255-6585 live with Press 1/2/3 IVR, Sona AI receptionist, during/after-hours SMS auto-replies. Pricing $25/$15/$40/$60 locked across all scripts.

### Ambassador Session Room UI (Phase 4.5.5.x)
- **Opened:** 2026-05-31
- **Closed:** 2026-05-31 (commits 4123a27, de6def4, e6d3227 pushed to main)
- **Outcome:** Rail at 300px / 128px thumbnails. Stage modal at 520-720px. FaceTime/session-room aesthetic (warm, not sci-fi). Convene Council button. Keyboard shortcuts. Accessibility preserved.

---
