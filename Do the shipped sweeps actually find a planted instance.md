---
type: AssumptionTest
created: '2026-07-27'
evidence: assertion
authorship: machine
---
#AssumptionTest #evidence/assertion

**The single assumption.** That the sweeps and checks this project has already shipped would each find an instance deliberately planted in their subject — i.e. that they are actually looking at what they claim to be looking at.

**Why it is worth checking rather than assuming.** Three of this codebase's reporting rules have been found blind AFTER shipping green: the lane reader (fragment read as declaration), the eleven audio tests that could not fail, and now the history sweep. In every case the rule reported success while covering less than it claimed. The common property is that none had ever been observed finding anything.

**Proposed test.** For each shipped check — `ost-agent check`'s invariants, the lane-conflict rule, the debt/threshold scan — plant one synthetic violation in a scratch copy of a vault and confirm the check reports it. Record which checks pass this and which do not.

**Lane: compute-only.** Scratch copies of two local vaults and the CLI. Nothing written to either real tree, no credential, no outside person.

**Pre-committed threshold, fixed before the test runs.** If **2 or more** shipped checks fail to find their planted instance, blindness is the codebase's default rather than an accident, and "Seed every sweep with a known-present instance it must find" becomes the primary fix rather than a nice-to-have. **0 or 1** means the existing verify-failing-first discipline is mostly working and the positive control is a belt-and-braces addition that can wait. The count is of CHECKS, not of planted instances, so a single check missing three plants counts once.

**What this cannot tell anyone.** Nothing about a check that finds its planted instance and still misses real ones for an unrelated reason — a plant is by construction the shape its author already imagined.

⚠️ Proposed only — the agent does not run tests or record results.

## Run 2026-07-27 — compute-only lane, by the autonomous loop (twelfth firing)

**Not a human-recorded result.** `ost-agent result` remains humans-only; this is an agent's
observation of a compute-only run, recorded here so the verdict is inspectable.

**Against the pre-committed threshold (>=2 checks failing to find their plant):
12 plants, 12 found, 0 checks blind. THRESHOLD NOT CROSSED.** Per the pre-commitment,
"Seed every sweep with a known-present instance it must find" stays a belt-and-braces
addition rather than becoming the primary fix.

Plants, each run against a baseline first asserted clean so a hit is demonstrably the plant
and not fixture noise: all eight `checkInvariants` rules (single-outcome, dangling-link,
wrapped-wikilink, opportunity-connected, solution-mapped, assumption-mapped, evidence-class,
no-self-validation); the lane-conflict rule via both `check` and `lanes`; the debt scan via
an untested solution and via an unfixed threshold.

### The run is worth more than its verdict

Three plants came back as apparent MISSES on the first pass. All three were defects in the
**plant**, not in the check:

1. A wikilink appended to the prose body rather than the contiguous edge block — the parser
   is right that a link in prose is not an edge.
2. A "lane conflict" whose two halves agreed (frontmatter `compute-only`, prose
   `Lane: compute-only`) — there was nothing to conflict.
3. An assertion grepping for the word "conflict", where `lanes` prints "contradicts their
   own prose" and never uses the word at all.

**An unattended pass that had not verified its own plants would have reported three blind
checks, crossed the threshold, and triggered the wrong primary fix.** That is the same
failure this test exists to catch, arriving from the direction nobody was watching — the
instrument rather than the subject. Worth carrying into any future positive control: a plant
that is not the shape the check looks for proves nothing about the check.

### Incidental observation

The lane reader flagged two of the new Tetrix tests as *likely humans-required* for
containing the word "stranger", where the strangers are the subject of the data rather than
people to interview. A false positive, in the fail-closed direction, pointing at a person for
the decision. Left alone rather than reworded — rewording a node to dodge a check that is
working is how a check stops working.

### Left behind as a permanent test

`test/eval/planted-instance.test.ts`, shipped in v0.20.0, with a negative control (a prose
lane that AGREES with its label must not be reported).

## Issues
- 2026-08-31 2026-08-31 unattended sweep, repo sight held — recording why this node keeps surfacing as owing an instrument and cannot be given one. Its own Run section closes by naming what the run left behind: `test/eval/planted-instance.test.ts`, shipped in v0.20.0. That file was confirmed present in the repository this pass via `ost_read_repo`. So a command answering this test exists and is GREEN, and the ruleset forbids setting it: an instrument must fail against the repository today, and one that passes on arrival measures nothing. The question was answered — 12 plants, 12 found, threshold not crossed — and the answer is in prose rather than in a `## Results` block, which is the only reason any analysis still counts it outstanding. Note also that this node declares **Lane: compute-only** in its own text while carrying no `lane:` frontmatter field, so the fail-closed lane reader counts it as needing a person while its prose says compute may run it. For a human, either would drain it: `ost-agent result` to record the 12-of-12 verdict, or `ost-agent lane --set` to make the declared lane a field. Neither call is on the unattended surface. Counted as one of four of this shape under "Work I already finished keeps coming back in the queue, so the pass can never say it is done". No instrument was set, no rung moved, nothing re-run.
