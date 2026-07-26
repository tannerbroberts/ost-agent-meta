---
type: AssumptionTest
status: unvalidated
source: 'agent-run:autonomous-loop-2026-07-26-pass7'
created: '2026-07-26'
evidence: assertion
---
#AssumptionTest #unvalidated #feasibility #evidence/assertion

**Assumption under test (feasibility).** That a rule this blunt — reject any `[[…]]`
containing a newline — is both **sound** (never fires on a link that actually works) and
**useful** (fires on breaks nothing else in `check` already reports).

**Why it needs testing at all, given how obvious it looks.** Two ways it could be a bad
idea, and both are cheap to settle before writing it. It could be **redundant**: if the
existing dangling-link check already reports a wrapped link as dangling, this adds a
second message for one defect and the honest answer is to improve the wording of the
first. Or it could be **unsound**: a `[[…]]` spanning lines inside a fenced code block, a
table cell, or a quoted example — this vault contains prose *about* wiki-links, and the
`wikilinks` false positive already living in `check` is proof that literal-text-in-prose
is a real hazard here.

**Proposed test.** Run the candidate rule, as a throwaway script, over the full history of
both live vaults — every commit, not just the working tree. Both are append-only, so the
history is the sample and it is free to obtain. Compare, per hit, against what
`ost-agent check` reported for the same commit.

**Pre-committed threshold.** Two numbers, both fixed here and neither to be adjusted after
looking. **Soundness: 0 hits on a link that resolves.** Any single false positive kills
the rule as written — it becomes a warning, not a failure, or it does not ship. **Utility:
at least 3 of the 4 known occurrences must be caught AND at least 1 of them must be a
break that `check` did not already report at that commit.** If every hit was already
reported by the dangling-link check, this rule is redundant and the right change is to the
existing message instead; that outcome is a **failure of this assumption**, not a partial
pass, and must be recorded as one.

**What it does NOT test.** Whether operators care. This is a check on the agent's own
output, for a defect the agent causes, found by the agent — no external party is involved
at any point, and it must not be recorded against anything that claims otherwise. It is
plumbing, and this vault has 212 nodes of plumbing and 0 external operators.

**Lane: compute-only.** It reads two local git histories and runs a regex. No credential,
no outside person, no judgement call inside the run — the judgement is the threshold
above, and it is fixed before the run.

⚠️ Proposed only — the agent does not run tests or record results.


## Run — compute lane, 2026-07-26 — and it cleared all three pre-committed numbers

**Not a recorded result.** `ost-agent result` is human-only and the agent recorded nothing.
This is the run and its output, annotated so a human can record the verdict in one line if
they agree with the reading. A paste-ready line is in
`.ost-agent/drafts/compute-docket-2026-07-24.md`.

**What was run.** Exactly the test this node proposed: the candidate rule as a throwaway
script over the **full history of both live vaults** — every commit, not the working tree —
comparing each hit against what the existing dangling-link check would have reported at that
same commit. 100 commits (50 per vault), roughly 275 node files per pass, `.ost-agent/`
excluded because `check` does not read it.

| Pre-committed | Bar | Result |
|---|---|---|
| Soundness | 0 hits on a link that resolves | **0** — pass |
| Utility (catch) | ≥3 of the known occurrences | **3 of 3** that reached a commit — pass |
| Utility (novelty) | ≥1 not already reported by `check` | **3 of 3** — pass |

**The three hits.**

| Vault | First seen | Node | Flattened target resolves? |
|---|---|---|---|
| `ost-agent-meta` | `e4ded22` | *A Context node type for evidence that is true, useful, and not a customer need* | yes |
| `ost-agent-meta` | `5fdb1cc` | *A first-run branch that walks a stranger to a vault in one question* | yes |
| `tetrix-ost` | `6aebdf7` | *Let the invited stranger play the board they were sent* | no |

Two of the three had a target that resolves once the newline is flattened: **real edges an
author wrote and the graph never got.** None was reported by anything at the time, which is
the structural point rather than a lucky sample — a split `[[…]]` never becomes a link, so
there is nothing for a dangling-link check to find.

**Zero hits inside a fenced code block**, which was the named soundness hazard: both vaults
contain prose *about* wikilinks, and the `wikilinks` false positive already living in
`check` proved literal-text-in-prose is a real risk here. It did not materialise in 100
commits. That is evidence, not proof — a future doc that shows a wrapped link as an example
would be the first false positive, and this node's own rule says one kills it.

**Read the denominator honestly, because it is the weak part.** The node's table lists six
occurrences; history can only show three. The other three were repaired by hand before
committing, so no commit contains them. **3 is what got past both the humans and the tools**
— which is the number that matters for a check — but it is not "3 of 6," and the utility bar
should be read as cleared against a smaller sample than the node's own table implies.

**Still not evidence about operators.** Unchanged from what this node said before it ran:
a check on the agent's own output, for a defect the agent causes, found and run by the
agent. No external party at any point. It must not be recorded against anything claiming
otherwise.
