# TCW Learnings

> **Additive only. Never delete entries. Append new entries at the TOP (most recent first).**
>
> Patterns we discovered, anti-patterns we hit, gotchas to avoid, breakthroughs to repeat.

---

## 2026-06-11 — Cross-thread coordination works even before tooling is installed (the discipline matters more than the files)

**Pattern:** Even before the STATE.md system was committed to the repo, the cross-thread coordination worked in real time on 2026-06-11. The build thread asked the architectural question ("Is there a CFO orchestration module Marshall reports to?"). The audit thread answered ("Mansa Musa is the CFO ambassador, status active. Marshall joins as peer agent under him, no new orchestration layer."). The build thread immediately converted the answer into a Codex-ready B.U.I.L.D dispatch matching the existing codebase idioms.

**What enabled it:** The operator served as the manual context router carrying the architectural answer between threads. The cost was real — operator's time and attention. The state system replaces that cost with file-based coordination.

**The deeper learning:** The state system isn't the magic. The DISCIPLINE is the magic. The state system just lowers the cost of the discipline by making the shared memory file-based instead of memory-based. Two threads with the discipline (read shared state, write shared state) coordinate even without files. Two threads without the discipline don't coordinate even with the best files. **Build the discipline first; the files just make it cheap.**

---

## 2026-06-11 — Parallel work across threads is fine if both threads have the same architectural understanding

**Pattern:** The build thread and the audit thread both produced Marshall build dispatches independently. They were functionally equivalent — same architecture (peer agent under Mansa Musa, no new orchestration), same tables (case_docket, violations_log, deadlines), same self-verify gate. Only the idioms differed (file paths, enum naming, verbosity).

**Counter-anti-pattern:** This is NOT duplicate work. Both dispatches captured the same decision from different angles. The build thread's dispatch is execution material. The audit thread's dispatch is architectural reference. Both have value — one for "how to build it" and one for "why it's built this way."

**Generalization:** Parallel work across threads is a feature when both threads share the architectural foundation. It's a problem only when threads disagree on architecture. Source of truth (STATE.md, decisions.md) ensures alignment.

---

## 2026-06-11 — First major shipped deliverable (Credit Quing catalog) finally inverts the 15-day spec/ship ratio

**Pattern:** For 15 days, the project trended heavily toward specification velocity (high) vs. shipping velocity (low). On 2026-06-11, the Credit Quing catalog rebuild SHIPPED — all 10 kits generated, packaged, verified, passing hard gates. This is the first major shift in the ratio.

**What changed:**
- Hard gates were added (prevented fake-success runs)
- Self-verify gate became binding (per PRODUCT_AGENT_STANDARD)
- Build thread refused to declare success without confirmable output
- Operator's "boil the ocean" principle was respected at the agent level, not just the dispatch level

**Generalization:** Spec → ship requires gates that fail loudly. Without them, "running" gets reported as success even when nothing actually ran. With them, the gap between "specced" and "shipped" finally closes.

---

## 2026-06-11 — Smallest possible launch beats the perfect platform

**Pattern:** "10 products ready" sat at "ready" for days because the launch platform decision (Gumroad vs Stan.store vs Shopify vs Squarespace integration) was treated as the blocker. In reality, the smallest possible launch is one $7 product on the platform with the lowest friction (Gumroad, $0/mo, ~30 min setup). The "right long-term platform" can be migrated to when revenue justifies it.

**Anti-pattern observed:** Letting platform sophistication preference (Stan.store funnel features, queendommanagement.com hosted) delay validation. The funnel features are only useful at volume — they're irrelevant for the first 10 sales.

**Counter-pattern:** First launch on the lowest-friction platform. Validate demand. Migrate later if/when warranted. Don't commit to monthly platform overhead before first sale.

**Generalization:** When a launch is being held by a platform decision, take the lowest-friction option immediately and migrate when revenue earns the upgrade. The platform is rarely the moat — the product, the customer list, and the brand are.

---

## 2026-06-11 — Specification velocity ≠ shipping velocity

**Pattern:** Across 15 days, specification quality has gone UP significantly (PRODUCT_AGENT_STANDARD, hard gates, B.U.I.L.D dispatches, Marshall charter, federal-benefits dispatch). Shipping velocity has stayed flat — almost nothing new is running automated.

**Cause:** Default mode is "spec the next thing better" instead of "close the existing thing." Polish-loop migrated from ChairWoman UI to agent governance documents.

**Counter-pattern:** Every dispatch should answer:
1. What's the smallest version that can run in production by end of session?
2. What value does that smallest version produce?
3. What loop measures whether it's working?

**Not:**
1. What's the optimal architecture?
2. What standards must it meet?
3. What's the full feature set?

---

## 2026-06-11 — Cross-thread context loss is a real productivity tax

**Pattern:** Each new thread spends ~30% of its context budget re-discovering known state. Operator becomes the manual context router between threads, carrying answers from Thread A back to Thread B who couldn't see them.

**Specific examples observed:**
- Heygen/Credit Quing thread asked: "Is there already a CFO agent/orchestration module in ChairWoman that Marshall reports up to?" → answer was already known in this thread but invisible
- Operator had to manually re-summarize state in audit prompt to give Claude enough context
- Decisions made in one thread (Reddit deprecation, Runway cancellation) didn't propagate without operator restating them

**Fix:** docs/state/ folder system (this folder). Every thread reads at open, writes at close.

---

## 2026-06-10 — Codex CI green ≠ Codex actually built the thing

**Pattern:** Two Credit Quing build runs (27218352484, 27233683281) reported GitHub Actions success while having never actually run the product-builder against the corpus. They were packaging-only passes — they validated that files could be zipped, not that products were generated.

**Specific failures masked by false green:**
- Greene Process flagship ($497.97) had ZERO letters
- Hard Inquiry and DIY contained identical letter sets (broke the DIY value wall)
- Late Payment's "letters" were guide chapters, not letters
- All products shared one generic positioning line
- Old $46.97 published twins remained live alongside new drafts

**Fix:** Hard gate blocks added — agent run fails loudly if:
- Product count < 10
- Placeholder naming patterns present (e.g., `letter-N-letter-1`)
- Flagship letter count < union of all other kits
- Any two products share an identical letter set

**Generalization:** Don't trust CI green alone. Every build agent needs a self-verify gate with named pass/fail checks against the actual output, not just "did the run complete."

---

## 2026-06-09 — Live law verification before citing statutes (always)

**Pattern:** Operator's previous credit content cited the CFPB January 2025 medical-debt rule as enforceable. Live verification found it was vacated by federal court July 2025 and unenforceable as of 2026. Shipping products citing it as live would have created class-action liability.

**Fix:** PRODUCT_AGENT_STANDARD.md §research-rigor — every product requires a Research Note documenting:
- Statute(s) cited
- Live verification date
- Effective status (in force / vacated / amended / proposed)
- Risk flags

**Generalization:** Law changes faster than documentation. Any time-sensitive citation requires live verification before publication. Never assume your training data has the current state of regulation.

---

## 2026-06-09 — Reddit Nov 2025 API policy killed scrapers (industry-wide)

**Pattern:** Reddit's "Responsible Builder Policy" (Nov 2025) ended self-service API keys. GummySearch (category-leading pain-point tool) shut down commercially the same month after failing to reach a commercial agreement. Free non-commercial tier exists at 100 queries/min via explicit dev support form approval.

**Generalization:** Platform API access is a moving target. Any agent dependent on a single platform API needs:
- Source-agnostic core (analysis engine separate from data fetcher)
- Documented policy state (when was access verified, what tier, what limits)
- Backup data sources identified

---

## 2026-06-04 — Source-agnostic architecture is durable IP

**Pattern:** When `reddit_painpoint_agent` was built, the analysis engine (IDF²-cosine clustering, opportunity scoring, pros/cons analysis) was kept separate from the Reddit-specific fetcher. When Reddit policy changed, the engine remained reusable.

**Generalization:** Separate the *durable IP* (analysis, ranking, scoring algorithms) from the *fragile interface* (specific API, specific schema). The fragile interface dies when policies change. The durable IP outlives platform shifts.

---

## 2026-05-31 — "Premium" = compositional depth, never element tricks

**Pattern:** Athlos MeetCoach section took 7 iterations. v1-v6 used element-level tricks (SVG turbulence filters, 3D cursor tilt, scroll-reveal gating, custom shaders). v7 used compositional moves (250vh section with sticky 100vh viewport, six explicit parallax depth layers at different speeds). Only v7 landed.

**Operator quote when v7 shipped:** "FINALLY CHUCK!!!! YOU DID IT!!!!!"

**Generalization:** When operator requests "premium" or "push the limits," reach for Locomotive Mtl / Active Theory / Awwwards-tier compositional moves: multi-photo layered composition, sticky narrative elements, asymmetric grids, real parallax depth. Element-level tricks are diminishing returns.

---

## 2026-05-31 — Spec-build pipeline is not a permanent funnel

**Pattern:** Athlos closed. Alpha Omega: 6 outreach touches, 0 response. Rebirth: 3 day-one touches, 0 response. Pattern was to keep building more spec sites instead of diagnosing the 0% response rate.

**Generalization:**
- Spec work opens the door, not the permanent funnel
- After 2-3 closes, transition to paid discovery audit ($497) → proposal model
- Cap active spec builds at 4-5 to prevent burn rate from killing margins
- 0% response on multiple prospects is a signal — diagnose before adding more

---

## 2026-05-29 — Operator's domain knowledge is the irreplaceable input

**Pattern:** Operator personally removed her bankruptcy from credit report with ONE letter to ONE bureau. This domain knowledge is the differentiator for Credit Quing. AI agents amplify it — they don't replace it.

**Generalization:** The proven playbooks (Quiet-Title, MTR Operating, Greene Process for credit) are the durable IP. AI's job is to package, distribute, and scale them. Operator's job is to keep building the playbooks and structuring deals. Don't let AI work crowd out playbook development.

---

## 2026-05-27 — Data wipe risk is real; vault needs backup discipline

**Pattern:** Mid-build of `operators-second-brain`, a data wipe incident required recovery. Underscored the importance of:
- Multiple backup locations (GitHub remote + local + iCloud)
- Frequent commits (don't accumulate uncommitted work)
- Branch protection on main
- Verification of push before assuming work is preserved

**Generalization:** Treat the vault repo with the same discipline as a code repo. Every meaningful state change gets a commit. Every session ends with verified push.

---


## 2026-06-11 — Chuck thread
- **Verify catalog content by the RIGHT key.** A price-substring match ("497" inside "4797") grabbed the wrong product row. Match flagship by exact `price_cents==49797` or `sku_id`, not a loose `/497/` test.
- **Vendor "personal % OFF + countdown" popups gate the discount behind ANNUAL billing.** Higgsfield's 55% off = ~$840 upfront. Treat these as fake urgency; they recur. Enforce the no-annual-prepay rule regardless of the timer.
- **`product_versions` holds version/changelog metadata only; the product markdown lives in `cq_catalog.body`.** Read body for content verification, not product_versions.
