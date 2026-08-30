---
type: Opportunity
source: 'TRANSCRIPT:fe8409a0-c892-4e5b-8f0e-3b304132a75d'
created: '2026-08-30'
evidence: observed
authorship: machine
---
#Opportunity #unvalidated #evidence/observed
[[A validate-only mode the caller can spend one call on before writing]]
[[Semantic checks accumulate into a list, and only the severity ordering stays hand-kept]]

When I compose one call that gets three things wrong, I want to be told three things once — not one thing three times. Today I fix the objection I was given, re-issue, and meet the next objection that was knowable before I sent the first call.

**The record this is distilled from.** Session `fe8409a0-c892-4e5b-8f0e-3b304132a75d` (2026-08-30, unattended, nobody watching) spent three of its seven friction events on a single `ost_create_node` call for one test title:

1. refused — the `threshold` fixes no bar ("a threshold needs a comparator and the number it commits to");
2. refused — the `instrument` carries a quoted `-t "twenty old r…"` filter;
3. refused — the `instrument` carries an unquoted `-t uncited-signa…` filter.

Three turns, one node, and the caller never saw objections 2 and 3 until it had cleared objection 1. The same shape is already on record one layer up for `ost_set_instrument`: session `14f184b4-6ca1-41d3-bf1f-b9e036b2a1a0` was refused twice for the instrument's form and only on the third call learned the test was labelled humans-required and could never carry an instrument at all.

**Why this is a distinct need from its parent, and not a restatement of it.** The parent is about a rule the caller could not know before calling — the remedy is declaration or preflight. This is about several rules the *surface already knew simultaneously* and chose to report serially. A preflight manifest listing every precondition would not fix it: a caller who read the manifest and still got two things wrong would still pay two turns. Conversely, batching the objections would not tell a first-time caller the read-before-write handshake exists. Different mechanism, different remedy, and a solution can address either without touching the other.

**The cause, read first-party off the code this pass.** `src/mcp/server.ts` runs two validation layers with opposite behaviour on the same call:

- **Schema objections are batched.** `validateToolInput` returns `problems: string[]`, and the dispatcher renders every one of them — `problems.map((p) => "  - " + p).join("\n")` — in a single refusal. This layer already does the right thing.
- **Semantic objections are serialised.** Everything else — the threshold grammar, the instrument grammar, the lane eligibility check — throws from inside `tool.run(args)` and is caught by a handler that returns exactly one `e.message`. A `throw` short-circuits, so the first semantic defect is the only one a caller ever sees.

The rules that are cheap to guess are the ones reported together; the rules that are expensive to guess are the ones reported one at a time. That inversion is the defect, and it is why a call with three semantic defects costs three turns while a call with three schema defects costs one.

**Litmus test (more than one way to address this?):** Yes, and they trade off against each other. Collect semantic problems into a list the way `validateToolInput` already collects schema ones, and report them together. Offer a dry-run that validates without writing, so a caller can pay one turn to learn everything. Lift the stable grammars (threshold, instrument) into the JSON schema itself, where the batching layer already lives. State each grammar in the tool description so the common cases never reach a refusal. Or order the checks so a disqualifying fact — the lane — is reported before any objection about an argument, which spends one turn instead of three even without batching. Distinct mechanisms with real trade-offs. Passes.

**What this does not claim.** It does not claim the refusals were wrong: every one of them was correct and each protected something worth protecting. Nothing here proposes relaxing a check. The cost is in how many round trips it takes to learn about the checks, not in the checks existing. It also does not measure how often this happens — two sessions are on record, both from this vault's own unattended firings, and no census has been run.

**Provenance caveat.** Observed behaviour of this product, captured mechanically from the agent's own transcripts, plus a first-party read of `src/mcp/server.ts` via `ost_read_repo` on 2026-08-30. It grounds usability, not desirability — it is not evidence that anyone outside this building wants the product. No test was run and no result is recorded.
