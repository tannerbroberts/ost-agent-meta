---
type: Opportunity
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
---
#Opportunity #unvalidated #evidence/assertion
[[Drop shipped solutions from the instrument queue]]
[[Ask a shipped solution for its observed exit code instead of an instrument]]
[[Refuse an instrument that passes on arrival]]
[[Withhold deferred opportunities from the under-served count]]
[[A flag I already judged false comes back every pass, because the clear is keyed to wording nothing told me to repeat]]
[[I map evidence the way the method says — onto an existing node — and the queue counts it as untouched]]

**The need.** When I finish a piece of work and record it as finished, the queue should stop asking me for it. Right now it does not, so every pass re-reads the same items, and the pass cannot reach `done` no matter how much real work gets done.

**What was observed, and how.** This pass read `solutionsMissingInstruments` (64 solutions, 25 shown) and then grepped the vault for `status: shipped`. Ten nodes in the whole vault carry that status. Five of them were in the 25 shown:

| Solution | status |
|---|---|
| A result must state what it did not cover | shipped |
| Post-session transcript harvester | shipped |
| Refuse a proving command whose exit code cannot report failure | shipped |
| Refuse a wiki-link that contains a newline | shipped |
| Refuse a write whose content is empty or literally undefined | shipped |

So 5 of 25 shown — 20% of the visible queue, and half of every shipped node in the vault — are being asked for an instrument. The remaining 39 unshown may hold more.

**Why this is unsatisfiable rather than merely annoying.** The queue asks for a command that is RED today and goes green when the solution is built. For a solution that is already built, no such command exists: any honest spec asserting the shipped behaviour passes on arrival, so it cannot fail, measures nothing, and hands a builder no definition of done. The instruction and the node's state contradict each other, and the only ways out are to invent a command that fails for a bad reason (the file is missing) or to do nothing. Both leave the item in the queue for the next pass.

**What it costs.** The 2026-08-05 sweep hit this on "Refuse a wiki-link that contains a newline", worked out that an instrument was impossible, corrected the status to `shipped` instead — and the node is in this pass's queue anyway. That is the whole cost in one example: a pass paid attention to reason it out correctly, recorded the right answer, and the queue did not read it. Every future pass pays that again, and a pass that reasons less carefully pays it by writing a green-on-arrival instrument, which is worse than paying it twice.

**Why it belongs under this parent.** The parent's complaint is that the pass never declares itself done, so the operator cannot tell when to stop paying for compute. This is one identified mechanism behind that: a queue that does not drain when the work is done. It is not the only one, but it is the only one this pass could demonstrate from the tree's own output rather than infer.

**Litmus test.** More than one way to address it: drop shipped nodes from the queue, change what the queue asks a shipped node for, or refuse the wrong answer at the write boundary. Three candidates sit beneath this, and they differ in what they believe the queue is for.

⚠️ Unvalidated. Distilled by an unattended pass from the tool's own output; no human has confirmed that a draining queue is what they want, and one could reasonably argue a shipped solution still owes evidence that it works.

## Issues
- 2026-08-06 2026-08-06 A second, independent way this queue reports unsatisfiable work — noted here rather than as its own node because it may be the same defect wearing a different hat, and a human should decide. Of the 25 entries in `underservedOpportunities` this pass, roughly 17 are the Outcome's own category buckets — "Checking on progress means digging through files", "Trust an unmonitored agent enough to walk away", "The agent has to guess what resources it's actually working with" and so on — each reported as having 0 solutions and needing 3. But the rollup shows solutions beneath every one of them: "Checking on progress means digging through files" carries 2 opportunities and 6 solutions. The sweep counts DIRECT solution children, and a bucket by design holds sub-opportunities rather than solutions, so the shape the ruleset requires (`outcome-files-categories`) is the shape the sweep reports as under-served. Following the instruction literally would attach generic solutions to category nodes, duplicating what already sits one level down and degrading the bucket layer the ruleset exists to protect. This pass did not do that; it put its solutions under specific needs. For a human: either `underservedOpportunities` should skip opportunities that have opportunity children, or the bucket layer should be exempted explicitly — but as it stands the two rules contradict, and roughly two-thirds of the reported backlog is that contradiction rather than real work.

## Half of this node's contradiction shipped; the other half did not — 2026-08-09 (unattended sweep)

Deliberately not re-running the census above — the 5-of-25 table still holds exactly as written, and this pass confirmed it by the same method (5 of the 25 shown carry `status: shipped`, out of 10 in the whole vault). What is new is a **contrast**, because the two halves of this node's complaint have now diverged.

**The bucket half was repaired.** The Issues note below argued that roughly 17 of 25 `underservedOpportunities` entries were the Outcome's own category buckets, reported as needing 3 solutions each because the sweep counted only DIRECT solution children. That is fixed. This pass's `ost_next_work` states: "19 category opportunity(ies) were exempt from the under-served check — they file sub-opportunities and solutions already hang beneath them", and `underservedOpportunities` returned **1 entry, not 25**. The contradiction between `outcome-files-categories` and the under-served count is gone.

**The shipped half was not.** `solutionsMissingInstruments` went 64 → 62 across the same interval, and the five shipped solutions are still in it. So the queue learned to withhold one class of already-settled work and did not learn to withhold the other.

**A third instance, and it is the sharpest of the three.** The single remaining `underservedOpportunities` entry is "Want proof no hijackable capability even exists" — reported as having 2 solutions and needing 3. That node carries `status: deferred`, and its History records the deferral as a **human-authorized merge** on 2026-07-24 into "Fear the agent could take a destructive, irreversible action", with its solutions relinked under the survivor. Ideating a third solution there would resurrect a branch a human deliberately retired, so this pass did not.

What makes it sharper than the shipped case is that **the same tool response contradicts itself about this one node.** `retiredFromDuplicateScan` lists it explicitly — "status: deferred — retired, withheld from the duplicate scan" — while `underservedOpportunities` demands work for it. One analysis in the response knows the node is retired; another, computed from the same frontmatter, asks the pass to build on it. That is not a missing filter so much as a filter applied inconsistently across analyses, which is a different repair from the one the three solutions below propose.

**Why this matters for the parent's question.** All three instances share a shape: the sweep holds the fact that would drain the item (`status: shipped`, `status: deferred`, "this is a category") and applies it to some analyses and not others. The bucket fix shows the repair is cheap once the fact is applied consistently. Two applications remain.

_First-party observation by the unattended sweep of 2026-08-09, from its own `ost_next_work` response and a grep of the vault's frontmatter. Observed behaviour of this product's own tooling — it grounds feasibility and usability, not demand. No test was run, no result recorded, and this node's rung is unchanged._

## Corroboration — a fresh instance, inconsistent within the same sweep (unattended sweep, 2026-08-18)

This pass created three AssumptionTests this sweep, all `humansRequired` at creation with `lane: humans-required` confirmed by direct read. Two of the three solutions correctly dropped out of `solutionsMissingInstruments` on the next `ost_next_work` call; the third ("A background task's own output directory is automatically readable by the Monitor call that started it") did not, despite its test reading identically (`lane: "humans-required"`, confirmed via `ost_read_tree`). Same defect already on record here, now shown to be inconsistent even across sibling nodes created in the same batch, not just across separate batches as the earlier sightings found.

_Source: this pass's own writes and re-reads, 2026-08-18 — first-party observation. Grounds usability, not demand._

## The queue now directs the agent into calls the product itself refuses — machine-captured (unattended sweep, 2026-08-22)

Every instance recorded above is a pass *reasoning its way out* of unsatisfiable work: it read the queue, worked out that the item was already settled, and declined. The cost was attention. `TRANSCRIPT:14f184b4-6ca1-41d3-bf1f-b9e036b2a1a0` (2026-08-21, nobody watching) shows the next stage, where the cost is refused calls instead of reasoning — three consecutive `ost_set_instrument` failures on one node:

- ×2 — `cannot set that instrument on "Have someone with the vault-write code open confirm every commit path can carry a session id without breaking commit-message parsers": "npx vitest run test/git/commit-provenance.test.ts -t …` (the `-t` filter, refused as shell punctuation)
- ×1 — `refusing to instrument "Have someone with the vault-write code open confirm every commit path can carry a session id without breaking commit-message parsers": it is labelled humans-required, so a person is the measurement`

**The third refusal is the finding.** `ost_set_instrument` read `lane: humans-required` off that test and refused on exactly those grounds — while `solutionsMissingInstruments`, computed from the same field in the same product, had listed the solution as owing an instrument. One half of the tool surface knows the answer and states it as a refusal; the other half asks the question anyway. Same session, minutes apart, no human involved.

That is the "filter applied inconsistently across analyses" shape this node already names, at its strongest yet, and it changes the argument in one respect worth a builder's attention: **the queue is no longer merely failing to drain, it is issuing an instruction the product is built to reject.** A pass following the queue literally cannot comply, and the refusal it earns is the product telling it so. The earlier sightings here were inferred from status fields a pass went and looked up; this one is a mechanically captured transcript of the contradiction being executed.

**Note the sequencing cost, too.** The refusal that would have ended the attempt immediately — "it is labelled humans-required" — arrived third, after two refusals about grammar. The lane check runs after the instrument-form check, so a pass pays for composing a well-formed command before learning that no command was wanted. Cheap to reorder if someone is already in that code.

**What this does not settle.** It says nothing about whether an operator wants the queue drained — the caveat above still stands, and one could argue a humans-required solution should stay visible as owed evidence, just not as owed *instrument*. That is the design question; this record only fixes what the current behaviour costs.

_Source: `TRANSCRIPT:14f184b4-6ca1-41d3-bf1f-b9e036b2a1a0`, read in full this pass. Observed behavior of this product's own tooling, captured mechanically from an unattended firing's transcript; grounds usability and feasibility, not demand. No command executed, no result recorded, rung unchanged._
