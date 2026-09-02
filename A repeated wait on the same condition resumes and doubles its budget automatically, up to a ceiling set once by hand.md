---
type: Solution
source: 'agent-ideation:2026-08-29-unattended-sweep'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Conditions that expire are more often genuinely slow than never going to be true]]

**Variation dimension: automated-vs-manual. Position taken: the escalation is automated, the ceiling is deliberately manual.**

The wait keeps a small on-disk record keyed by the condition string. The first wait on a condition runs its default budget. A second wait on the *same* condition does not start over: it recognises the key, reports how long it has already spent in total, and doubles its budget — 300s, then 600s, then 1200s — until a total ceiling that a person sets once. When the ceiling is reached the wait refuses to run again and says so, naming the accumulated time.

What stays manual is the ceiling, because it is the only part that encodes a judgement nothing local can make: how much unattended wall clock this operator is willing to spend on one condition before the honest answer is that the approach is wrong.

**Why this shape addresses the observed failure directly.** The 2026-08-29 record on the parent shows five expiries and two byte-identical re-issues. Under this candidate the second call would have said "already spent 300s on this condition, extending to 600s" and the fifth would have refused outright. The information the session lacked — that it was repeating itself and how much it had already burned — is information the waiter already has and currently throws away between invocations.

**Against its siblings.** The heartbeat candidate makes one expiry informative; this one makes a *sequence* of expiries informative and needs no cooperation from the process being waited on, so it works on remote and queued subjects the heartbeat cannot reach. The operator-recorded-instruction candidate is cheaper and asks nobody to build state, but it cannot tell the caller that this is the fourth attempt.

**What would make this the wrong pick.** It rewards patience mechanically, and patience is often the wrong answer: a condition that will never become true gets 2100s of automatic indulgence instead of 300s, which is worse, not better, for an unattended run paying by the minute. It is the right pick only if genuinely-slow subjects are commoner than never-true ones — which nothing here has counted. It also inherits an identity problem: two different waits on the same condition string in the same session are indistinguishable from one wait retried, and collapsing them is sometimes wrong.

**Adjacent node a human should read beside this.** The tree already carries "A budget that is missing, empty or non-numeric makes the wait say so rather than quietly using 300" under a different parent. That is about a budget that never arrives; this is about a budget that arrives, is honoured, and is then discarded between calls. Related mechanism, different failure.

**No instrument.** The helper is on the session's PATH and supplied by the harness, not in this repository, so no spec in this product's `test/` can reach it.

Unvalidated. Agent-ideated on 2026-08-29; a human to review.

## Definition of done — and it is not a command

"Count the recorded expiries that later succeeded against those whose condition could never have become true"

There is deliberately no instrument. The bar is: at least 2 of every 3 expiries were genuinely slow rather than never-true. A never-true condition and a slow one produce byte-identical expiry lines, so no exit code can separate them — the classification is the judgement, and the corpus is the operator's own transcripts.

The test title is quoted rather than wikilinked on purpose: its one backlink belongs to its parent assumption.

**Sequencing:** run the count before building. This candidate is the only one of the three that can make things actively worse if its direction is wrong, and the corpus needed to check the direction already exists.

## 2026-09-01 — a second instance, and it shows the doubling key would not have engaged

Kept short, per this branch's convention. Only what is new.

**A second independent record of the failure this candidate is built on.** `TRANSCRIPT:e7e72b8f-c632-4900-a9b4-68cfa7bc3b86`, captured at this pass's own ingest (mirrored 0d ago), carries **6 `await: gave up after 300s; the condition still exits 1` expiries and 4 byte-identical re-issues** — against the 5 expiries and 2 re-issues the 2026-08-29 record on the parent shows. Same shape, different session, larger. The subject both times is a test suite that had not finished.

**The new mechanical fact: the caller did try to buy more time, and the knob it reached for does not govern.** Every one of the 4 re-issues carries `"timeout": 600000` in its Bash arguments — the caller had already doubled its tool-level allowance to 600s. The helper expired at 300s regardless, because that cap is the helper's own and the tool-level timeout never binds it. So this is not a session that failed to ask for more time. It asked, through the only knob visible to it, and the request was a silent no-op: the expiry line names 300s and says nothing about the 600s allowance sitting unused above it. That strengthens this candidate's central claim — the waiter holds information the caller does not — and adds a second item to the list of what it withholds.

**And the finding that cuts against this candidate, from the same record.** This node already names an identity problem, but in the direction of over-collapsing: "two different waits on the same condition string in the same session are indistinguishable from one wait retried." Today's record is the opposite failure. The re-issues carry **at least two distinct condition strings** — `await 'grep -q "Test Files" /tmp/full-suite-2.txt'` and the same against `/tmp/full-suite-3.txt`. Keyed by condition string, as this candidate specifies, those are two different keys. Each would start fresh at 300s and the doubling would never engage, even though the session burned roughly half an hour on what is semantically one wait: *has the suite finished yet*. The escalation this node proposes would not have fired on the very record that best demonstrates the need for it.

That is not fatal, and it is worth stating as a design constraint rather than a refutation: whatever key the record is held under has to survive a caller that renames its output file between attempts. Keying on the condition string is the cheapest choice and it is defeated by an incrementing filename, which is an ordinary thing for a caller to do.

**Limits.** Two records is not a rate, and both are this vault's own unattended firings, so this is the agent's usage of its environment rather than any outside operator's. The 6 expiry lines do not carry their own commands — only the 4 retry events do — so "at least two distinct conditions" is a floor read off the retries, and the true spread across the 6 could be wider. The claim that the tool-level `timeout` cannot extend the helper's 300s cap is read off the arguments and the expiry text together, not from the helper's source, which is not in this repository. Nothing was executed, no rung moved, no instrument set, no status changed.

_Source: this pass's own `ost_ingest_inbox` output and the evidence body served by `ost_next_work({evidence})`. Observed behaviour of this agent's own environment — it grounds usability, not desirability, and is not evidence that anyone wants anything._

## 2026-09-02 — a third instance, which answers this node's own stated limit and repeats the key-defeat finding

Kept short, per this branch's convention. Only what is new.

**This node's 2026-09-01 section closes with "Two records is not a rate."** That limit is what this entry addresses, and nothing else here is novel. `TRANSCRIPT:64ee1d07-f9ab-4941-a104-54e01c72dde7`, captured at this pass's own ingest (mirrored 0d ago), is a third independent session with the same shape: **6 `await: gave up after 300s; the condition still exits 1` expiries**, against 5 in the 2026-08-29 record on the parent and 6 in the 2026-09-01 record above. Three sessions, all this vault's own unattended firings, all waiting on a test suite that had not finished.

**The 600s-allowance finding reproduces.** The single retry event carries `"timeout": 600000` on `await 'grep -q "Test Files " /tmp/suite2.txt'` — the caller had again doubled its tool-level allowance, and the helper again expired at 300s regardless. That is now observed in two separate sessions rather than one, so the claim that the tool-level knob does not bind the helper's cap is no longer resting on a single record.

**The key-defeat finding reproduces too, and that is the part that bears on this candidate's design.** The 2026-09-01 section found the doubling would not have engaged because the caller renamed its output file between attempts (`/tmp/full-suite-2.txt`, then `-3`). Today's condition waits on `/tmp/suite2.txt` — an ordinal filename, so the same incrementing pattern, in a session that shares no filenames with the previous one. Keying the escalation record on the condition string is defeated the same way for a second time. Whatever key this candidate is eventually built on has to survive a caller that renames its output file between attempts; that is now a repeated observation rather than a single one, and it is the sharpest constraint on this node's cheapest form.

**Limits, and they are the same ones.** Three records is a shape, not a rate, and all three are this agent's own usage of its environment — usability, never desirability, and no evidence that anyone wants this built. The 6 expiry lines do not carry their own commands; only the single retry does, so the spread of distinct conditions across the six is unknown and "one ordinal filename" is read off that one retry. The claim about the 300s cap is still read off arguments and expiry text together, not from the helper's source, which is not in this repository. Nothing was executed, no rung moved, no instrument set, no status changed, and this node's humans-required Definition of done stands unchanged.

_Source: this pass's own `ost_ingest_inbox` and the body served by `ost_next_work({evidence})`. Observed behaviour of this agent's own environment, read first-party._
