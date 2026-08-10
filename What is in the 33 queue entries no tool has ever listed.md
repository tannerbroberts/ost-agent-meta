---
type: Unknown
source: 'agent-ideation:2026-08-10-unattended-sweep'
created: '2026-08-10'
evidence: assertion
---
#Unknown #unvalidated #evidence/assertion

`solutionsMissingInstruments` holds 58 entries and `ost_next_work` prints 25 of them, alphabetically. The same 25 have appeared on every sweep since 2026-08-06. Four passes have now classified some part of the visible head — 25 by subject on 2026-08-09, 12 by opening their tests on 2026-08-10 — and **not one of them has ever seen the other 33**. Every claim this tree makes about the queue's composition is a claim about its alphabetical head, extrapolated.

That is the darkness. It is not "we have not got round to it": no surface available to a sweep can enumerate them. The tool caps at 25 by design, and the derivation that produces the list — a solution none of whose assumption tests carries an `instrument:` — is not something the vault's own files answer in one read, because it needs two hops through the wikilink graph, from solution to assumption to test.

## Format

A table of 33 rows. Each row: the solution's title, its `status:`, and one class from the set the head has already produced —

- `shipped` — the behaviour exists, so no command can be red
- `no-command-by-design` — the node's own body says an instrument would be laundering
- `people` — a person outside the building is the measurement
- `elapsed-time` — only running for weeks or months answers it
- `premise-superseded` — the product has answered the question by moving on
- `mechanical` — a spec file could settle it, and the bucket is right about this one

The count of `mechanical` rows is the answer this unknown exists to produce. Anything else it turns up is a bonus.

## Methodology

Two routes, and the first is cheap enough to try first.

*From the vault.* Enumerate every `type: Solution` file, follow its `[[…]]` child edges to the assumptions beneath it, follow those to the assumption tests, and select the solutions where no test carries an `instrument:` field. This is a whole-vault read plus two hops and needs no repository access. It reproduces the tool's own derivation, so it also serves as a check on it — a disagreement between the two lists would itself be worth knowing.

*From the tool.* Raise or page the 25-item cap on `solutionsMissingInstruments`. That is a product change and belongs to whoever owns the response-size budget; the vault route does not wait on it.

Either route produces the titles. Classifying each still needs the node opened and its test read, which is what the 2026-08-10 pass did for twelve and is the expensive half — roughly one full read per row.

## Rationale

**What it darkens.** "A pass that cannot see the repository cannot set an instrument at all" carries this tree's census of the instrument queue, and that census states its own limit in its own words: the unlisted entries "were never classified by either, both read titles as a proxy for the majority class". It also darkens the assumption "Every solution in the current backlog has an existing spec that could go red for it", whose threshold is stated over 61 backlog solutions and cannot be evaluated against a backlog nobody can list.

**What would change if it were answered.** The estimate of how much of the queue is genuinely mechanical is currently an upper bound of seven, derived from the head and shown on 2026-08-10 to be measured at the wrong level. If the 33 are mostly mechanical, the queue is roughly right and repo sight was the blocker after all — which the 2026-08-10 sweep's zero instruments argues against, but only over the head. If the 33 look like the head, the bucket is mostly asking for commands that should not be written, and the repair is to the queue rather than to any solution beneath it. Those two answers point at different builds, and nothing currently distinguishes them.

**Why it is worth naming rather than absorbing.** Four consecutive passes have each re-derived "I can only see 25" and moved on. Written down, the gap is costable — 33 reads — instead of being rediscovered every sweep at the price of the rediscovery.
