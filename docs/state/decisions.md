# TCW Decision Log

> **Additive only. Never delete entries. Append new entries at the TOP (most recent first).**
>
> Each entry: date · decision · rationale · alternatives considered · who/where

---

## 2026-06-11 — Consented-founder content: preserve the founder's name, default-strip third parties
**Decision:** Credit Quing's source-redaction (`sanitizeSource`) changes from "strip all client names" to **"strip if not consented; preserve if consented."** The founder **Shimira Greene** is the operator/architect AND the consented client whose real, lived story powers the brand — her name is **preserved** in generated products (BAQ founder story, the Greene Process flagship narrative, any product whose source includes her methodology). The hard ex-wife boundary (**"Sweetz By Bee"**) is always stripped. DEFAULT for any other (third-party) client name is to strip — added to `STRIP_NAMES` — so future non-consented stories stay protected.
**Rationale:** This is consented founder content per PRODUCT_AGENT_STANDARD §4, not third-party PII. An earlier build wrongly conflated Shimira with the ex-wife rule and anonymized her own success story ("a real Credit Quing client"), weakening the brand's true proof. Consent is the right axis, not blanket anonymization.
**Implementation:** `lib/agents/credit-quing/product-builder.ts` — `CONSENTED_CLIENTS` (founder, preserved) + `STRIP_NAMES` (ex-wife brand, stripped); the catalog system prompt now instructs the model to KEEP the founder's name in her consented result story (disclaimed: results vary). Corpus front-matter carries `consented_client:` on founder-sourced files. Restored on the next BAQ + flagship regen.
**Alternatives considered:** keep stripping all names (rejected — erases the founder's real proof); per-file allowlist only (folded in via the corpus `consented_client` marker + the code lists).
**Where:** Build thread (Codex), `feat/consented-founder-content`.

---

## 2026-06-11 — Subscription ledger finalized; subscriptions_tracker is a CFO agent (post-Marshall)
**Decision:** Finalize the cost ledger (ManyChat Pro $15+, Stripe $0+txn, drop the unrecognized "Google AI" line) and queue subscriptions_tracker as Mansa Musa's next agent now that Marshall (#57) has shipped.
**Rationale:** Operator confirmed the remaining costs. "Google AI" wasn't a recognized charge — removed rather than guessed. Recurring-spend tracking is a CFO function; making it an agent (with a subscriptions table the ledger becomes a VIEW of) stops the next Runway-style duplicate from slipping.
**Alternatives considered:** keep ledger hand-maintained (rejected — drifted twice); build before Marshall (rejected earlier for Marshall's real deadlines; now moot).
**Where:** Chuck thread, via Terminal MCP-bypass.

## 2026-06-11 — Subscription ledger corrected from operator signup data; Higgsfield annual offer declined

**Decision:** (1) Reclassify Heygen + ElevenLabs from "to add"/blocked to ACTIVE with correct figures — Heygen Creator ~$29/mo (billing 6/30), ElevenLabs **Creator $22/mo** (started 5/30); prior ledger mis-tracked ElevenLabs as Starter $5. Gemini corrected $10→$20. (2) Decline the Higgsfield "personal 55% OFF" Ultra offer.

**Rationale:** Operator supplied actual signup tiers. ElevenLabs is on Creator, not Starter — $5 was wrong. On Higgsfield: the 55% discount is gated behind ANNUAL prepayment (~$840 upfront), which violates the locked monthly-only / no-annual-prepay rule; Higgsfield also isn't wired into the content loop yet (nothing posting), so it's premature spend. The on-screen countdown is manufactured urgency — these personal-promo popups recur.

**Alternatives considered:**
- Higgsfield annual at $70/mo: rejected — breaks no-annual-prepay; $840 locked before content/revenue exists.
- Higgsfield monthly (~$129/mo): rejected for now — expensive for a tool not in the pipeline; revisit when content flows + a CQ sale lands.
- Leave ledger stale: rejected — cost-tracking is an explicit standing assignment.

**Where:** Chuck thread (Marshall/storefront/cost). Source: operator signup figures + Higgsfield offer screenshots.

---

## 2026-06-11 — APPROVE flagship $497 Greene Process guide narrative regen

**Decision:** Approve build thread's offer to regenerate just the flagship's guide section (one targeted call) and re-stitch it above the 24-letter library.

**Rationale:** $497 is premium pricing. Customers paying that expect a system, not a letter library. The "Greene Process" positioning name promises a methodology. The other 9 kits have full narratives — flagship being structurally inconsistent looks like a quality miss. One targeted call has low regression risk (letters are already verified passing hard gates). Better to fix before first sale than after a refund.

**Alternatives considered:**
- Ship flagship as-is (letter library only): rejected — undercuts $497 positioning, damages trust if customers feel they paid more than they received
- Reduce flagship price to match: rejected — the methodology IS the product; reducing price doesn't fix the deliverable
- Wait for v2 (per versioning model): considered but rejected — narrative is core to v1 positioning, not a v2 enhancement; better to fix now within the v1 release before any sale

**Where:** Claude audit thread, build thread offered, operator approved.

---

## 2026-06-11 — Use build thread's Marshall dispatch as execution path (mine as architectural reference)

**Decision:** When two threads have produced functionally equivalent dispatches, use the build thread's version as the Codex execution path. My version becomes architectural reference documentation.

**Rationale:** The build thread is closer to Codex's idioms and the existing chairwoman-v1 codebase conventions. Their tighter B.U.I.L.D dispatch will execute more cleanly. My dispatch's value is in the explanatory rationale (Why this matters now, ADDENDUM sections, the architectural decision) — that's reference documentation, not execution material.

**Alternatives considered:**
- Use my dispatch (built first): rejected — build thread is closer to execution
- Merge both dispatches: rejected — adds clutter, no functional benefit
- Discard mine entirely: rejected — the rationale sections are useful architectural record
- Have build thread copy mine verbatim: rejected — they already converted it to their idioms; that work is done

**Generalization:** When parallel work happens across threads, default to the thread closer to execution as the canonical path. The state files (history.md, decisions.md) preserve the architectural reasoning regardless of which dispatch executes.

**Where:** Claude audit thread, after build thread response.

---

## 2026-06-11 — Gumroad for Credit Quing first-launch (Cease-the-Calls $7), Stan.store deferred to MRR threshold

**Decision:** Launch the $7 Cease-the-Calls tripwire on Gumroad ($0/mo + 10% per transaction). Migrate to Stan.store ($29/mo monthly) when total Credit Quing monthly revenue exceeds ~$200.

**Rationale:** Smallest possible launch. Gumroad has zero monthly drag, fastest setup (~30 min), and validates demand before committing to a $29/mo platform. 10% transaction fee on a $7 sale is $0.70 — trivial. At scale (e.g., $1K MRR) the 10% fee starts to matter and Stan.store's funnel sophistication justifies migration.

**Alternatives considered:**
- Stan.store at launch: rejected for first product — $29/mo before first sale is cash flow drag; mirrors @automations.bae long-term but premature optimization for a $7 tripwire validation
- Shopify: rejected — $39/mo minimum + monthly platform fees + needs theme work; massive overhead for a single digital product
- Sellfy: comparable to Gumroad ($19/mo entry tier) — rejected (Gumroad's $0 entry wins on cash flow)
- Direct Stripe checkout on queendommanagement.com: rejected — Squarespace integration overhead + email delivery automation work; longer path to live
- Wait until Heygen is subscribed for video product page: rejected — text + image launches are standard for digital downloads; Heygen video is a v2 enhancement

**Where:** Claude audit thread, dispatch in `docs/dispatches/2026-06-11-credit-quing-storefront-launch.md`.

---

## 2026-06-11 — Runway $35/mo cancelled (executed, expires June 29)

**Decision:** Operator cancelled Runway Standard subscription. Last access day: 2026-06-29.

**Rationale:** Decision made earlier in the audit (see entry below from same day). Operator executed the cancellation in the Runway dashboard. Net cost change after Heygen + 11Labs additions: -$1/mo.

**Where:** Claude audit thread, operator-side action.

---

## 2026-06-11 — Cancel Runway, add Heygen + ElevenLabs (monthly)

**Decision:** Cancel Runway Standard ($35/mo). Subscribe Heygen Creator ($29/mo monthly) and ElevenLabs Starter ($5/mo monthly).

**Rationale:** Runway provides idle-loop video generation only. Heygen provides lip-synced talking avatars + custom avatar from 2-min portrait upload + 175+ languages. ElevenLabs provides voice cloning. Together they replace Runway capability AND add what Runway can't do (speech, lip-sync, custom characters). Duplicate spending on overlapping capability is wasteful.

**Net cost change:** -$1/mo ($35 cancelled, $34 added).

**Alternatives considered:**
- Keep Runway + Heygen + 11Labs simultaneously: rejected (duplicate capability, ~$70/mo for content tools alone)
- Higgsfield Plus ($34-49/mo) instead of Heygen: deferred — Heygen is the proven @automations.bae stack; Higgsfield can be added later if needed for character video variety
- Annual subscriptions for discount: rejected — operator principle is monthly only until cash flow supports prepayment

**Where:** Claude audit thread, confirmed by operator 2026-06-11.

---

## 2026-06-11 — Marshall reports to Mansa Musa as peer agent (no new orchestration layer)

**Decision:** Marshall (credit-repair / consumer-protection enforcement agent) joins the existing CFO ambassador (Mansa Musa) as a peer to `unclaimed_money_finder`, `class_action_finder`, `federal_benefits_finder`. Uses existing `lib/agents/registry.ts` pattern with `ambassador_id: 'mansa_musa'`. Existing `agent_runs` infrastructure handles his run lifecycle.

**Rationale:** Mansa Musa is already the active CFO ambassador with 53 historical agent runs. Building a new orchestration layer just to give Marshall a CFO to report to would be over-engineering. The existing registry pattern already does this.

**What's new for Marshall specifically (vs. existing agents):**
- New tables: `case_docket`, `violations_log`, `deadlines`
- New endpoint: `/api/marshall/drop-folder/ingest` (watches operator's drop folder)
- New scheduler: cron checking `deadlines` table for warning windows (90d, 30d, 7d, 24h)
- Per `PRODUCT_AGENT_STANDARD.md` §self-verify gate

**Alternatives considered:**
- Marshall as a sub-agent of one existing finder: rejected (forces awkward parent-child where peers make more sense)
- Build a new "Recovery Lane" orchestration module: rejected (Mansa Musa IS that module already)
- Marshall under a new ambassador (e.g., Ma'at CLO since this is legal): rejected (would require activating Ma'at and building her supporting infra; defer until justified)

**Where:** Claude audit thread, answering question from the Heygen/Credit Quing thread.

---

## 2026-06-11 — Deprecate `reddit_painpoint_agent`

**Decision:** Reddit pain-point agent is no longer in active use. The analysis engine (IDF²-cosine clustering, opportunity scoring) is preserved as durable source-agnostic IP.

**Rationale:** Reddit's November 2025 Responsible Builder Policy killed self-service API keys. All access now requires explicit approval via a developer support form. GummySearch (category leader) shut down commercially Nov 2025 after failing to reach Reddit commercial agreement. The agent could still run via public `.json` endpoints, but the operator's stated focus has shifted to shipping existing assets (10 Credit Quing products, Super Clean Bins launch, Marshall) rather than market research.

**Alternatives considered:**
- Migrate to public `.json` endpoints + run on credit/landflipping subreddits: deferred (not blocking anything currently)
- Rewire analysis engine to a non-Reddit source (X/Twitter, Hacker News, forums): deferred (no immediate need)
- Apply for Reddit commercial API access: rejected ($1,000+/mo, not justified by current revenue)

**Where:** Claude audit thread, confirmed by operator 2026-06-11.

---

## 2026-06-09 — Credit Quing 10-SKU ladder configuration locked

**Decision:** 10 differentiated products spanning $7 → $497.97:
1. Cease-the-Calls tripwire — $7
2. Hard Inquiry Removal
3. DIY Credit Repair
4. Late Payment Liberation
5. BAQ (Bankruptcy Removal)
6. Repossession Removal
7. ChexSystems / Banking Restoration
8. Debt Validation + Medical (HIPAA folded in)
9. Tax Lien Removal
10. Greene Process — $497.97 flagship

**Parked:** Student Loan Relief, Business Funding (require repositioning care).

**Scoped out entirely:** homeowner / foreclosure materials — these become a separate future homeowner-education offering, post-resolution. Not part of the credit catalog. (Any party/case specifics live in `docs/state/PRIVATE-LEGAL.md`.)

**Rationale:** BAQ and Late Payment Liberation are mechanically distinct products with different statutes/mechanisms (BAQ = LexisNexis/PACER freeze + FCRA §611 public-record source verification; Late Payment = goodwill + inaccuracy disputes on tradelines). Cease-the-Calls at $7 is the tripwire that proves the buyer journey works. Greene Process at $497.97 is the flagship that consolidates everything.

**Where:** Heygen subscription thread, operator confirmation.

---

## 2026-06-09 — Sovereign-citizen / redemption / "credit sweep" materials QUARANTINED

**Decision:** Block all sovereign-citizen, redemption-theory, UCC-1099-OID, and "credit sweep" materials from any sellable Credit Quing product.

**Rationale:** Legal liability + ethical harm to buyers. These tactics expose operators to fraud charges and consumers to civil/criminal exposure. They also don't work — they get accounts re-reported with worse status, get bank accounts closed, and trigger fraud investigations.

**Implementation:** QUARANTINE list in the corpus dispatch blocks these files from ingest. Hard gate in product-builder agent rejects any product whose source materials reference these tactics.

**Alternatives considered:** None viable. This is a hard ethics + liability line.

**Where:** Heygen subscription thread.

---

## 2026-06-09 — Versioning model: v1 great → v2 phenomenal within 90 days

**Decision:** Ship v1 "great" now, never block launch waiting for "phenomenal." When v2 ships within a 90-day window, recent buyers get the upgrade free with a changelog.

**Rationale:** Perfection-as-launch-gate has cost weeks of velocity. The PRODUCT_AGENT_STANDARD codifies this: v1 ships on quality bar pass, v2 ships when materially better, buyers within the upgrade window get the new version automatically.

**Alternatives considered:**
- Ship only when "phenomenal": rejected (proven to cause indefinite delay)
- Ship v1 with no upgrade promise: rejected (customer experience degrades when v2 ships and they don't get it)
- 30-day upgrade window: rejected (too tight, not enough margin for development)

**Where:** PRODUCT_AGENT_STANDARD.md §9, Heygen subscription thread.

---

## 2026-06-09 — Claude = strategist + verifier · Codex = builder

**Decision:** Claude does not manually author products or write code into the chairwoman-v1 codebase. Claude specs work, crafts content, and verifies output. Codex executes builds.

**Rationale:** Each tool used for what it's best at. Claude's strategist/verifier discipline is high. Codex's autonomous execution is high. Mixing roles led to lower-quality work in both lanes.

**Where:** Heygen subscription thread, operator-set role.

---

## 2026-05-31 — "Premium" means compositional depth, not element tricks

**Decision:** When operator requests "premium" or "push the limits," default to compositional moves referencing Locomotive Mtl / Active Theory / Awwwards-tier sites — multi-photo layered composition, sticky narrative elements, asymmetric grids, real parallax depth. Never element-level tricks (SVG turbulence, 3D cursor tilt, scroll-reveal gating).

**Rationale:** Operator feedback after 7 iterations of Athlos MeetCoach section. The v7 breakthrough was a 250vh section with sticky 100vh viewport and six explicit parallax depth layers. Operator: "FINALLY CHUCK!!!! YOU DID IT!!!!!"

**Where:** Athlos Training Grounds thread, locked as standing instruction.

---

## 2026-05-29 — Vault ↔ ChairWoman: two separate repos

**Decision:** Operator's personal data lives in `operators-second-brain` (private). Application code lives in `chairwoman-v1`. ChairWoman reads vault via `vault_cache` Supabase table with 1hr TTL.

**Rationale:** Data ≠ code. Different update cycles, different privacy concerns. Vault can be backed up / restored / migrated independently of the app. App can be open-sourced or shared without exposing personal data.

**Alternatives considered:**
- Single monorepo with `app/` and `data/` folders: rejected (privacy boundary unclear)
- Vault as a private package consumed by ChairWoman: rejected (added complexity, no real benefit)
- ChairWoman reads vault directly from disk: rejected (deployment to Vercel needs Supabase-cached data)

**Where:** Vault foundation thread.

---
