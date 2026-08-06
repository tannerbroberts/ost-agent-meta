---
type: Solution
source: 'USAGE:2026-08-05'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Excluding shipped solutions removes items that are genuinely done, not items being dodged]]

**The idea.** `solutionsMissingInstruments` excludes solutions whose status is `shipped`. An instrument must fail against the repository today and pass once the solution is built; for behaviour that already ships, no such command exists, so demanding one asks for something that cannot be supplied.

**Why this shape, and why now.** Four solutions in the 2026-08-06 queue — "Refuse a wiki-link that contains a newline", "Refuse a write whose content is empty or literally undefined", "Refuse a proving command whose exit code cannot report failure", "A result must state what it did not cover" — were each worked by the previous day's sweep, which reached the correct conclusion and wrote it into their histories: the mechanism ships, a spec asserting it would pass on arrival, so status was corrected rather than an instrument invented. All four were back in the queue the next pass. The work was done right and the queue did not notice.

This is the opportunity's mechanism in miniature. The cost is not the four items; it is that every future pass re-reads four solution bodies, re-derives the same conclusion, and either repeats the correction or invents a fake instrument to make the number go down.

**How it differs from its siblings.** The narrowest of the three and the only one that removes items rather than explaining them. It fixes one queue by one rule and touches nothing else; "Each queue reports its delta" makes any queue's movement legible, and "An item a pass declined is suppressed until its reason stops holding" generalises to items that are not shipped.

**Where it fails.** It trusts `status: shipped`, which an agent can set. A solution wrongly marked shipped would vanish from the one queue that would have chased it — so this shifts weight onto a field with no gate behind it, and is only safe while status changes are recorded in `## History` with the reasoning attached, as those four are.

⚠️ Unvalidated. Agent-ideated, from the queue this pass was working.

## Definition of done

"Audit every shipped solution against the repository before trusting the exclusion"

```
npx vitest run test/ost/shipped-status-audit.test.ts
```

Named in plain text rather than linked: the test is already wikilinked by its parent assumption, and a title is linked exactly once in the vault.

## Confirmed in the same pass that proposed it — 2026-08-06

This node was written from four solutions the 2026-08-05 sweep had corrected to `shipped` and which were back in the 2026-08-06 queue. That is consistent with the claim but does not isolate it: those four were promoted by a different pass, and something else could have re-admitted them.

The 2026-08-06 sweep then ran the experiment directly. It promoted "Post-session transcript harvester" to `shipped` — on the builder report of 2026-07-24 recording `src/adapters/transcript.ts`, 19 tests, wired into config and live on this vault — and re-called `ost_next_work` in the same pass. The solution appears in `solutionsMissingInstruments` in the very next call.

So the queue's membership test does not consult `status`, and one promotion is enough to show it. Five solutions are now known to be in this state: the four from 2026-08-05 and this one.

**What this does not settle.** Only that the exclusion is absent, which was never really in doubt once the four recurred — it is now observed rather than inferred. Whether the exclusion is the *right* fix is what this node's assumption test is for, and its safety edge is untouched: `status: shipped` is agent-settable, and this very entry is an agent promoting a solution and then citing the promotion. A human should check that the transcript harvester really is built before treating this as clean evidence.
