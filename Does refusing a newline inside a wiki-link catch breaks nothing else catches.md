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
