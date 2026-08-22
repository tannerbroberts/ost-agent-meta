---
type: Solution
source: 'agent-ideated:2026-08-19-unattended-sweep'
created: '2026-08-19'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The build loop selects a target from a cached list rather than re-reading its live status at commit time]]
[[The build loop re-runs a candidate's instrument before spending a model pass on it]]

If the loop selects candidates from a list built earlier in its run (or carried over from a prior firing) and does not re-check the node file at the moment it commits to building one, a status change written between selection and commit is invisible to it. Fix: re-read the target node's frontmatter (status at minimum) as the last step before starting work, and skip to the next candidate if it has changed.

**Why this reading fits the evidence better than a missing filter would.** The third build-loop report claims "the vault node was never updated after the first two runs" — which is false; it was updated on 2026-08-16, before the second and third re-selections. A loop that had simply never filtered on status would not need to make that (incorrect) claim about the node being unchanged; it would just not care about status at all. A loop reading a stale copy would genuinely see an unchanged node and say so honestly, while being wrong about the live file. This candidate targets that specific failure.

**What would make this the wrong pick.** If the loop has no caching layer at all and reads fresh every time, this fix is a no-op and the real bug is the missing filter (see the sibling solution).

⚠️ Unvalidated. Proposed by an unattended pass; distinguishing this from the sibling requires reading the build loop's own source, which this pass could not do (repo sight unavailable).

## Definition of done

"A candidate whose instrument turned green since it was recorded is dropped before any model pass is spent"

```
npx vitest run test/loop/confirm-before-spend.test.ts
```

Red today because nothing re-runs a candidate's instrument before the spend (bounded observation — see below) and the spec is unwritten; green when the confirmation is wired in and reports its drops.

**The blocker this node's prose names is discharged.** It closes "distinguishing this from the sibling requires reading the build loop's own source, which this pass could not do (repo sight unavailable)". A pass with repo sight read `examples/automation/build-pass.sh` and `src/eval/buildable.ts` on 2026-08-22. The distinction resolves, and **neither of the two readings this node offered is right**:

- Not a cached snapshot. Every candidate title is put back through `buildable "$sol"` individually, which re-reads the vault. That half of this candidate is a no-op, as its own "what would make this the wrong pick" clause anticipated.
- Not a missing status filter either (the sibling's reading).
- The actual gap is that the *permit* is a recorded observation, and `buildPermit` never re-runs the command. `confirmPermit` exists precisely to close that and is documented as opt-in to "the caller about to spend something" — and `buildable.ts` records the resulting failure with a date: on 2026-08-06 a full model pass went to a solution whose instrument had been green for seventeen minutes.

**This command settles feasibility only**, and the affordability question is left wide open: each confirmation spawns the test runner, and this same script already caps verification at eight per firing. A green here may be bought at a wall-clock cost nobody has measured.
