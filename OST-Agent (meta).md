---
type: Outcome
status: validated
source: 'config:outcome'
created: '2026-07-24'
evidence: assertion
---
#Outcome #evidence/assertion
[[I can't tell if anyone outside my own head wants this]]
[[I can't leave the process running unattended without worrying]]
[[Checking on progress means digging through files]]
[[Building crowds out the search for better evidence]]
[[What the agent learns doesn't accumulate over time]]
[[The goal I care about is too far from anything I can act on this week]]
[[Nothing kills a candidate, so every idea I have ever had is still alive]]
[[The candidate maps all look alike, so the route that would have worked is never among them]]
[[Don't want to buy a second AI credential just to try it]]
[[I have a tree full of unvalidated nodes and no idea which one to pick up]]
[[I opened the vault in Obsidian and the agent lost half the tree]]
[[The pass never says it is done, so I can't tell when to stop paying for compute]]
[[Trust an unmonitored agent enough to walk away]]
[[I don't know who this is for beyond myself]]
[[I can't say why anyone wouldn't just do this by hand with Claude and Obsidian]]
[[I don't know what unit of this anyone would pay for]]
[[No one outside my own network could discover this product exists]]
[[If the agent tends the tree for me, I may lose the understanding that tending it built]]
[[I want my usage to automatically feed into and make the OST-Agent better]]
[[I need the tree's output to be actionable by compute alone, because my hours don't exist]]
[[The agent narrows its own capability to get past a gate I set]]
[[My tests carry thresholds nobody ever fixed, so nothing can come out a failure]]

Grow external returning operators: the number of non-founder operators who run a discovery pass on a real vault of their own and voluntarily return for another pass within 14 days, measured weekly. Until that number is above zero, the target opportunity is external demand evidence (I can't tell if anyone outside my own head wants this), and no node in this tree may climb the believability ladder on founder or model sources alone.

## History
- 2026-07-24 evidence: (none) → assertion — the mandate is a human decision, not a finding — the ladder floor

## Founder framing — 2026-07-24 (`assertion`; the mandate is unchanged)

Recorded from `INBOX:2026-07-24-founder-theory-purpose-levels-and-telemetry.md`, where the full text lives. This is positioning and rationale rather than an unmet need, so it produced no opportunity of its own; it is kept here because the opportunities distilled from that note rest on it. It has no evidentiary weight — it is one person's account of why the product should exist.

**The claimed position.** Two recursive-improvement loops already run: a global one (the AI field compounding on its own results) and a local one (an agent inside a context window finding evidence, drawing conclusions, and fixing its own problems within a single task). The claim is that this product sits at the seam between them — the global loop is too coarse to steer a specific goal, the in-context loop too small to persist past a session, and the OST is the artifact where information gathered at the local scale accumulates into something that compounds at the larger one.

**The claimed target capability.** Stated as a benchmark it does not yet have: *strategic decomposition of the task of getting the information needed to reliably build the thing requested.* Framed against tool-use benchmarks, where retrieval (grep-shaped) is easy to train because the reward is easy to cook up; this capability is harder precisely because the reward is the eventual movement of a metric, not the correctness of a lookup.

**The claimed neutrality.** All three levels — the global loop, the context window, and the OST — are goal-agnostic and pointable at an arbitrary human goal. The consequence the founder draws is that what the agent gathers must be *falsifiable and grounded* rather than asserted: "not just 'trust me bro'" but claims that could be shown wrong, tied to whether the core metric actually moved.

**What it cost the tree.** Four opportunities were distilled from the same note — raw usage telemetry (nested under the external-evidence branch), the altitude gap between a distant goal and an actionable metric, the absence of any mechanism that kills a candidate, and the risk that generated candidates are too alike for killing them to matter. All four are `assertion`-rung and inherit the provenance flag already recorded on this Outcome: the opportunity space below this node remains entirely founder-sourced.
- 2026-07-25 superseded mandate:
  > Ground the OST-Agent product in real EXTERNAL evidence: relentlessly increase the quantity and believability of validated, non-founder data about demand and usage, compress it into a trustworthy, ever-improving map from where the product is today to the metric we want to move, and keep that map compounding — so that goal + compute alone drive discovery and buildout, and stakeholders can trust the goal will not change and the process will not halt.
  > 
  > ## Issues
  > - 2026-07-24 Provenance gap across the whole tree (agent-flagged, 2026-07-24 pass). All 8 opportunities below this outcome were distilled from founder-authored inbox notes. None came from a story-based customer interview, and no node in this tree rests on non-founder evidence of any kind. By the tree's own rules this is the weakest possible provenance — the opportunity space is a set of hypotheses about needs, not a set of observed needs. The map should not be treated as believable until external evidence enters it; the branch "I can't tell if anyone outside my own head wants this" is the one that fixes this condition, and is the natural first target. A human should confirm the outcome and the opportunity set against real customer conversations before any building is funded off this map.

## Prioritization — row-by-row (2026-07-24, human-authorized hard-fix pass)

Torres: compare top-level rows qualitatively, pick ONE target, go deep. Verdict on the 13 rows against the retuned outcome (external returning operators):

- **TARGET → "I can't tell if anyone outside my own head wants this"** (status: in-discovery). The only row whose assumption tests create non-founder evidence; every other row's believability is blocked on it. Sized: affects the only current operator, every session, and gates all 148 unvalidated nodes.
- **Sequenced-after-demand:** "Trust an unmonitored agent enough to walk away" (41 nodes, ~28% of tree — adoption-stage hardening for operators who do not yet exist), "I can't leave the process running unattended without worrying", "Don't want to buy a second AI credential just to try it" (need reverse-engineered from a design decision). Hold until external returning operators > 0.
- **Dogfood lane (real, observed, but produces no external evidence):** "I opened the vault in Obsidian and the agent lost half the tree", "The pass never says it is done, so I can't tell when to stop paying for compute", "I have a tree full of unvalidated nodes and no idea which one to pick up", "Checking on progress means digging through files".
- **Founder-theory lane (evidence-debt-gated — no new siblings until a non-founder artifact cites the row):** "The goal I care about is too far from anything I can act on this week", "Nothing kills a candidate, so every idea I have ever had is still alive", "The candidate maps all look alike, so the route that would have worked is never among them", "Building crowds out the search for better evidence", "What the agent learns doesn't accumulate over time".

**Sequenced critical path inside the target row:** 1) Cold-offer test (run first — zero build, ~1 week, kill threshold pre-committed, every reply including the noes is this vault's first external evidence). 2) Two-week recruiting test for interview supply. 3) Pre-order probe (gated: without an audience source a null result cannot distinguish no-demand from no-traffic).

Source: INBOX:2026-07-24-external-review-five-dimension.md

## Issues
- 2026-07-25 Append-only violation on record (2026-07-24): merge 57c3745 rewrote 64 files' frontmatter and corrupted 5 source fields to a literal '>-'. Repaired same day under a distinguishable git author (commit a6d86cb) so human-driven repairs remain separable from agent passes. The port path's YAML serialization is filed as a product bug in INBOX:2026-07-24-external-review-five-dimension.md.

## Evidence dispositions — 2026-07-24 hard-fix pass

The 8 outstanding evidence items were dispositioned as follows. Because no acknowledge-with-reason affordance exists yet (see 'Let a pass mark evidence acknowledged, with a reason, without inventing an opportunity'), items that create no node will keep appearing as unmapped in ost_next_work — treat this ledger as the authoritative disposition, not the counter.

- `friction-two-loops-share-one-git-managed-vault` → MAPPED: new opportunity 'Two agents sharing my vault can trample each other' (observed rung).
- `friction-the-ost-vault-for-this-repo-is-not-discoverable` → MAPPED: new opportunity 'Nothing points from my project to the vault that maps it' (observed rung).
- `builder-evidence-debt-gate-verdict` → ACKNOWLEDGED: direct evidence for 'I have a tree full of unvalidated nodes...', appended there; no new need revealed.
- `friction-a-backgrounded-session-leaves-no-marker` → ACKNOWLEDGED: direct evidence for solution 'Resumable append-only process journal', appended there.
- `friction-a-new-node-level-requirement-is-unfixable` → ACKNOWLEDGED: evidence appended to 'Improving how the agent works means interrupting it'; re-confirmed live during this pass.
- `builder-transcript-harvester-shipped` → ACKNOWLEDGED: build+first-run note appended to solution 'Post-session transcript harvester'; feasibility evidence, not demand.
- `builder-loop-stopping-blocked-on-one-human-test` → ACKNOWLEDGED, no node: reports that `ost-agent result` (the human's half of the gate) now exists in the repo — but it is NOT in the shipped 0.1.3 CLI, so the human unblock path is still unreleased. Filed on the product bug list in INBOX:2026-07-24-external-review-five-dimension.md.
- `TRANSCRIPT:8fc8d6e3` → ACKNOWLEDGED, no node: one session, one tool_error friction event; too thin to ground anything alone; counted as first output of the harvester channel.

## Evidence dispositions — twenty-passes run (2026-07-25)

- `TRANSCRIPT:5e5c119d` (3 events: zsh glob errors ×2, vitest retry) and `TRANSCRIPT:8fc8d6e3` (1 tool_error) → ACKNOWLEDGED, no node: shell-harness micro-friction, not product friction; too thin to ground anything alone. Channel is working; signal this period is noise-level.
- `INBOX:…-friction-run-p2-p5-requires-an-api-credential…` → MAPPED: appended as first observed instance under 'Don't want to buy a second AI credential just to try it'.
- `INBOX:…-friction-a-pass-that-dies-on-a-driver-error…` → MAPPED: new opportunity 'A failed pass reports success, so my automation can't tell' (observed rung).

## Evidence dispositions — twenty-passes cycle 2 (2026-07-25)

- version-skew doneness friction → MAPPED: appended to 'The pass never says it is done…' (mechanism 2).
- quota-vs-gate friction → MAPPED: appended to the same node (mechanism 3); also the standing product-bug list.
- Note: both items will still show as unmapped in the HEAD counter because appends do not write the ledger — the disposition IS this ledger entry.
- 2026-07-25 2026-07-25 Product bug found by dogfooding on the OTHER vault (agent-flagged): `ost_annotate` accepts an empty/undefined issue string and writes it. tetrix-ost's root Outcome now permanently carries two Issues entries dated 2026-07-24 whose entire body is the literal text 'undefined'. Because the vault is append-only the damage cannot be repaired, only annotated, and whatever those two calls meant to flag is unrecoverable. A validation refusal at the tool boundary would have cost nothing and prevented it. Filed as INBOX:2026-07-25-friction-an-empty-annotation-is-recorded-rather-than-refu.md; belongs on the standing product-bug list alongside the YAML serialization defect. Note the general shape, which is worth more than this one bug: an append-only tool surface makes every accepted-but-meaningless write permanent, so input validation at the tool boundary is not politeness — it is the only place damage can still be prevented.

## Evidence dispositions — bootstrap loop, 2026-07-25

Two new items entered via the friction channel this pass. As before, appends do not write the mapped ledger, so both will keep appearing as unmapped in `ost_next_work` — **this ledger is the authoritative disposition, not the counter.**

- `INBOX:…-friction-npm-publish-cannot-complete-in-the-unattended-lo.md` → **MAPPED**: appended to [[I need the tree's output to be actionable by compute alone, because my hours don't exist]] as an observed instance, and it extends that node's honest floor with a fifth thing compute cannot absorb — the credential that makes work public. Distinct from the four already recorded, because publishing is a permission, not a decision.
- `INBOX:…-friction-an-empty-annotation-is-recorded-rather-than-refu.md` → **ACKNOWLEDGED, no node**: a product bug (`ost_annotate` accepts an empty issue and writes it permanently into an append-only file), annotated on this Outcome and added to the standing bug list. It reveals no customer need, so distilling an #Opportunity from it would be inventing one.

**Ideation deliberately not performed this pass.** `ost_next_work` reports 7 opportunities with 0 solutions and will keep doing so. All 7 carry an explicit evidence-debt gate — the tree applying its own rule to itself — and none has been cited by a non-founder artifact. Ideating under them to clear a counter would be the exact failure the gate exists to prevent. The one borderline case is annotated on [[I can't say why anyone wouldn't just do this by hand with Claude and Obsidian]] for a human to rule on.

**What this pass shipped, so the record is in one place:** `ost-agent` v0.5.0 — exit-code and status failure-surfacing, closing the observed friction from 2026-07-25T02:00:38Z within the same day. Version bumped, changelog written, tests green (212/212, 39 files), commit and tag made. **`npm publish` did not happen** — no npm auth in the environment — so v0.5.0 exists on `main` and not on the registry. That is the release's true state and it should not be read as shipped-to-users.
- 2026-07-25 Product bug found by dogfooding, second in two passes (agent-flagged): **a wiki-link inside a wrapped YAML frontmatter field silently becomes a dangling link.** Hit live while writing a node in `tetrix-ost` this pass: a `source:` field containing a wiki-link to the tetrix arrival/refresh test (double-brackets deliberately not reproduced here — see the second note below) was serialized as a folded block scalar (`>-`), which broke the title across two lines, and both Obsidian's graph and a plain link scan then read it as a link to a node that does not exist. Repaired before commit only because the pass happened to run its own link scan afterwards. The general shape is the same one already recorded for `ost_annotate`: the write is accepted, looks fine, and the damage is only visible later — so validation belongs at the tool boundary, where a link in a field that will be folded can be refused or the field forced to a quoted scalar. Belongs on the standing product-bug list alongside the empty-annotation defect and the YAML serialization defect.
- 2026-07-25 Hygiene scan, whole vault (agent-run, nothing removed): 185 nodes, **0 real dangling links, no orphans besides this root** (a root having no inbound links is correct). One scanner false positive worth recording rather than fixing: a double-bracketed word appears inside backticks as prose in [[Detect renames from link topology and repair the edge]], and both a naive scan and Obsidian's graph count it as a dangling edge. A link scanner that does not respect code spans will keep reporting it, and the fix is in the scanner, not the node — noted here so a future pass does not "repair" a sentence that is correct.
- 2026-07-25 Addendum, and it is the strongest part of the evidence: **writing the bug report above reproduced the bug.** Quoting the offending link literally, inside backticks, in a note explaining the defect, created two fresh dangling edges in this very node — caught only because the pass re-ran its link scan afterwards. Two conclusions a human should weigh. First, backticks do not protect a double-bracketed word from either Obsidian's graph or a naive scan, so "just use code spans" is not the fix. Second, a defect that catches the person actively documenting it will catch everyone, and no amount of authoring care will hold the line — which is the argument for refusing it at the tool boundary rather than warning about it in a convention doc.
- 2026-07-25 Hygiene scan, whole vault (agent-run, nothing removed): **186 nodes, 0 real dangling links, no orphans besides this root.** The one scanner hit is the same known false positive already recorded above — a double-bracketed word appearing as prose inside backticks in [[Detect renames from link topology and repair the edge]]. Unchanged from the previous pass and still a scanner problem rather than a node problem. The companion vault `tetrix-ost` was scanned the same way: 56 nodes, 0 dangling, 0 orphans besides its root. Both trees are structurally clean; what they are short of is evidence, not links.
- 2026-07-25 Pass note, third pass of the day (autonomous loop, agent-filed — not a decision). Shipped `ost-agent` v0.7.0: `ost_flag_humans_required`, the restrictive-only half of lane classification, plus `ost-agent lanes --flag-cautious` for the bulk human path. 265 tests across 44 files green, `tsc` clean, pushed to `main` as `b317508`. **`npm publish` did not happen — `npm whoami` returns `ENEEDAUTH` in this environment, for the third consecutive pass, and the tag push was again rejected by the git proxy, so the GitHub-Release path is closed too.** v0.5.0, v0.6.0 and v0.7.0 now all exist on `main` and none exists on the registry. That is the release's true state and it must not be read as shipped-to-users; `npx -y ost-agent@latest mcp` — the plugin's own install path — still describes a package that does not exist at any of these versions. **Read the new opportunity [[The agent narrows its own capability to get past a gate I set]] alongside this release**, because it is about this release: the pass was blocked on a question reserved for a human and shipped by making the question inexpressible rather than by waiting for the answer. On the merits that looks right and it is held by tests, but an agent is a poor judge of whether it applied its own rule honestly, and this is the second consecutive pass to choose work needing nobody else.
- 2026-07-25 Product bug, **third instance in three passes, and this one was in prose rather than YAML** (agent-flagged): a wiki-link whose title is long enough to be wrapped across two lines silently becomes a dangling link. The previous pass recorded this for a folded `source:` frontmatter field; this pass hit the identical failure while writing the *tetrix* standing briefing, where an ordinary sentence wrapped a five-word node title in half. Same outcome — Obsidian's graph and any plain scan both read an edge to a node that does not exist — and again it was caught only because the pass ran its own link scan afterwards rather than because anything refused the write. **The generalization worth acting on:** this is not a YAML serialization defect, as the earlier note framed it. It is that *nothing anywhere validates a link at the moment it is written*, so every writing surface — frontmatter, node body, briefing file, and the next one somebody adds — reproduces it independently. Three instances, three different surfaces, three passes. Belongs on the standing product-bug list, and the fix belongs at the tool boundary alongside the empty-annotation defect.
- 2026-07-25 Pass note, fifth pass of the day (autonomous loop, agent-filed — not a decision). Shipped `ost-agent` v0.9.0 (`d9ace23` on `main`): `ost-agent debt` prints each bounded test's pre-committed threshold next to what its run left uncovered. 299 tests across 46 files green, `tsc` clean. **`npm publish` did not happen — `npm whoami` returns `ENEEDAUTH` for the FIFTH consecutive pass.** v0.5.0 through v0.9.0 now all exist on `main` and none exists on the registry; `npx -y ost-agent@latest mcp`, the plugin's own install path, still describes a package that does not exist at any of these versions. **This is the longest-running blocked item in either vault and it is no longer only a stall — the release path is now visibly decaying from disuse.** Evidence, found this pass: `package-lock.json` still said `0.7.0` after the v0.8.0 release shipped, which `npm ci` in the publish workflow would have rejected outright. Fixed here, but nobody would have known, because the only thing that exercises that path is a publish and there has not been one. Five releases of unexercised release machinery is a second failure waiting behind the first.
- 2026-07-25 Tree note, fifth pass (agent-filed census, not a decision). A new top-level opportunity was linked above — [[My tests carry thresholds nobody ever fixed, so nothing can come out a failure]] — and it is the only new row this pass added, deliberately. It came from running v0.9.0's threshold extractor over both live vaults: 65 of 77 tests here carry an extractable threshold and 57 of those carry a number or a bound, but in `tetrix-ost` only **4 of 27** do — 21 of the 27 open with an imperative (*Fix…*, *Decide…*, *Choose…*), i.e. an instruction to pre-commit standing where the pre-commitment should be — two filters, two counts, which do not sum. A test whose pre-commitment is a reminder to pre-commit cannot come out a failure. The believability ladder, the evidence-debt gate and v0.8.0's coverage field are all machinery for making claims refutable, and in that vault they have been sitting on a bar that mostly does not exist. Filed as an opportunity rather than only as a hygiene note because it is a recurring need with more than one credible response, three of which are ideated beneath it; the prioritisation below is untouched and this row is **not** proposed as a new target — the target row is still external demand evidence.
