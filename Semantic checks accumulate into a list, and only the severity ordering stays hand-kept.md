---
type: Solution
source: 'agent-ideation:2026-08-30-unattended-sweep'
created: '2026-08-30'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion

**Variation dimension: automated-vs-manual. Position taken: the collection is automated, the severity ordering is deliberately manual.**

Change the semantic checks from `throw` on first failure to accumulate into a `problems: string[]`, and render them through the same formatter the schema layer already uses. `src/mcp/server.ts` proves the shape works: `validateToolInput` returns a list and the dispatcher prints every entry. This candidate says the semantic layer should return a list too, so that a call with a bad `threshold` and a bad `instrument` is refused once, naming both.

What stays manual is the **order they print in**, and that is the interesting half. "This test is labelled humans-required, so no instrument may ever be set on it" and "your threshold needs a comparator" are not equally urgent: the first says the call can never succeed, the second says this attempt did not. A caller reading them in arbitrary order will fix the cheap one first and re-issue a call that was doomed either way. Nothing in the code can rank them — disqualifying-vs-fixable is a judgement about what each check protects — so the ranking is a hand-maintained list beside the checks, and a new check with no entry prints last with a marker saying it is unranked.

**Why this position and not another.** The automated half is mechanical and the manual half is genuinely a judgement, so splitting them there is not a shortcut. Any attempt to infer severity — "checks that mention the node's frontmatter are disqualifying" — would be reading a proxy, and would silently mis-rank the first check that broke the pattern.

**Against the siblings.** Unlike the validate-only flag, this fixes the default path: a caller that knows nothing about the improvement still pays one turn instead of three. Unlike moving the rules into a bought validator, it keeps the refusal wording this product has deliberately tuned — several of these messages name what they are protecting and say what to do instead, and a library's error string does not.

**What it gives up, plainly.** Accumulation means every check must run even when an earlier one already failed, so a check that assumes a prior one passed will now throw on garbage input rather than being skipped — each check has to become independently safe, which is real work spread across every one of them rather than concentrated in one place. It also makes refusals longer, and a wall of six objections is its own kind of unreadable. And the hand-kept ordering is an artifact asking for recurring maintenance, which this tree already records as the class of artifact that goes stale.

**Cheapest form.** One accumulator threaded through the semantic checks in the tools layer, returned rather than thrown, rendered by the existing formatter; the ranking as a plain ordered array of check ids in the same module, with unranked checks sorted last.

**How it would be wrong.** If multi-defect calls are rare and most refusals name exactly one thing, this is a refactor across every check for a case that almost never fires. Two sessions are on record and no census has been run.

**Honest note on how this was ideated.** The sweep asks for one blind ideator per dimension. This surface holds no grant to run independent parallel ideators, so all three candidates under this opportunity were composed in one context by one author — the exact condition the blind-ideation rule exists to prevent. Read them as one author's three answers and discount their apparent distinctness accordingly.

Unvalidated. Agent-ideated 2026-08-30; a human to review.
