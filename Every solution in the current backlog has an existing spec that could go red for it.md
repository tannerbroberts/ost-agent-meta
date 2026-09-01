---
type: AssumptionTest
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
threshold: >-
  Across the 61 solutions currently in `solutionsMissingInstruments`, at least
  55 can be assigned an existing spec file in the product suite whose assertions
  would go red for the named behaviour without misfiling it. Fewer than 55
  refutes the rule and argues for the escape hatch becoming the default.
instrument: npx vitest run test/instruments/spec-path-resolution.test.ts
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**What it measures.** Whether the refusal is livable at the scale the tree actually has. The bar is a census over the real backlog rather than a fixture, because the question is empirical: it is about this repository's spec layout, not about the rule's logic.

The spec form is the mechanical half — that the tool resolves a path against the configured repo, refuses an absent one, and names the escape in its message. The census half is what decides the assumption, and a builder running this should record the census number in the result even though the exit code only covers the resolution.

**Why it is red today.** `ost_set_instrument` accepts any spec-shaped string without resolving it, which is how every instrument in this tree came to name a file that does not exist.

**Honest limit on the instrument.** Written without repo sight, so the path is invented; its first red is an absent file. The irony is load-bearing rather than incidental — this is a blind instrument for the rule that would forbid blind instruments, and it is exactly the artefact "An instrument records whether the pass that wrote it could see the repository" wants marked.

**What a green here does not settle.** The census. A passing resolution check says the guard works; it says nothing about whether 55 of 61 solutions have a home, and that number is the assumption.

## Instrument Log
- 2026-08-07 **red** (exit 1) `npx vitest run test/instruments/spec-path-resolution.test.ts` — No test files found, exiting with code 1
- 2026-08-12 **green** (exit 0) `npx vitest run test/instruments/spec-path-resolution.test.ts` — Duration  4.33s (transform 176ms, setup 0ms, collect 290ms, tests 3.85s, environment 0ms, prepare 31ms)

## The census half now has a denominator — read from the repository, 2026-08-10

**No test was run and nothing here clears a gate.** This node's own text says the census half is what decides the assumption and that the exit code only covers path resolution. The census still has not been done. What this pass could do, with repo sight the author did not have, is measure the population the census would run against — and that alone bears on the threshold.

**The product suite, listed directory by directory.** Seventeen of the twenty directories under `test/` were enumerated (`automation`, `fixtures` and `processes` were not, and no instrument names them). They hold roughly **184 spec files**, the largest being `test/mcp` (26), `test/security` (22), `test/ost` (21) and `test/release` (18).

**Against that, this vault carries 277 `instrument:` fields naming 277 distinct paths, of which 27 resolve.** So the backlog is not asking to be reassigned across a suite with room for it — it is asking for more distinct spec files than the entire suite currently contains, by half again.

**Why that is not yet a refutation, and I want to be precise about it.** This node's threshold is *"at least 55 of 61 can be assigned an existing spec file whose assertions would go red for the named behaviour without misfiling it."* Assignment is many-to-one: several backlog solutions could legitimately land in one existing spec, and 184 files is not obviously too few homes for 61 solutions. The count above refutes a different and easier claim — that the tree's *current* instrument paths are mostly assignable — and that claim is not this one. Read it as sizing, not as a verdict.

**What it does establish, and it is the part worth carrying.** The gap between 27 resolving and 277 named is not a backlog of files waiting to be written into a settled layout. Seventeen of the unresolved paths name one of seven directories that do not exist in the suite at all — `test/instruments/`, `test/preflight/`, `test/tools/`, `test/guards/`, `test/evidence/`, `test/gate/`, `test/rank/` — and `test/instruments/spec-path-resolution.test.ts`, this node's own instrument, is one of them. So the escape hatch this node's threshold contemplates is load-bearing for at least those seventeen, because there is no existing spec to resolve them against and the rule as stated would refuse every one.

**What a builder should record if they run the census.** Two numbers, not one: how many of the backlog solutions get an existing home, and how many of those homes are the *same* file. A census reporting 55 of 61 assignable would mean something quite different if the 55 landed in 50 specs than if they landed in 6.

**What this does not settle.** The census itself. Whether an assignment would misfile a solution — the qualifier doing the real work in the threshold — cannot be judged from a directory listing, only from reading each spec. And nothing about desirability or viability; this is a feasibility measurement over committed code.

_Method: `ost_read_repo` listings of seventeen directories under `test/` in the OST-Agent repository, matched against every `instrument:` field in this vault, 2026-08-10. Read of committed code; no command executed, no result recorded, this node's rung unchanged._

## 2026-08-31 — the census, run from the other end, and it points at refutation

**Still not the census this node asks for, and not a recorded result.** This node's threshold is an *assignment* count: how many backlog solutions can be given an existing spec file whose assertions would go red without misfiling them. That requires reading each candidate spec, and this pass did not do it. What this pass did is measure the population from the other end — how many of the backlog's tests are of a kind a spec could settle **at all** — which bounds the numerator from above and is cheaper than the assignment.

**The denominator, counted whole rather than sampled.** Every prior entry here works from the 25 entries `ost_next_work` shows. Grepping the vault's own frontmatter across the whole alphabet: **494 AssumptionTests, 367 carrying an `instrument:`, 60 carrying a `lane:`, 67 carrying neither.** Those 67 are the entire population behind the 68 solutions now in the bucket — 35 in A–H, 14 in I–R, 18 in S–Z. The threshold's "61" is now 68 and the population it draws from is 67 tests.

**What those 67 are, on the slice counted exhaustively.** All 18 of the S–Z entries were classified by reading titles and, where ambiguous, bodies:

- **16 of 18 are irreducibly about a person** — recruiting supply, selling an engagement, whether operators would accept the agent living in its own vault, whether a digest makes an operator willing to walk away, unprompted-fear interviews, a week of decisions through a docket from a phone. No spec assertion reaches any of them, and assigning one would be the misfiling the threshold's qualifier exists to exclude.
- **2 of 18 are already answered**, not unassigned — "Sweep both vault histories for writes that landed as undefined or empty" was run on 2026-07-27 (106 commits, 306 entries, threshold survived, v0.18.0 shipped the consequence), and "Test humans can promote while the agent is blocked from validating" has its whole mechanical half asserted by `test/security/self-validation.test.ts`, read in full this pass. For these, an existing spec exists and would be **green**, which fails the threshold's "would go red" clause from the opposite direction to the one this node anticipates.
- **0 of 18 are a solution waiting for a spec that could go red for it.**

**Why that bears on the bar.** The threshold needs **55 of 61** assignable. On the one slice counted exhaustively, the assignable count is zero out of eighteen. If the other two slices resemble it — and the 2026-08-06 census on "Filter the queue on shipped and count what is still unsatisfiable" found 11 of 11 inspected unassignable for the same two reasons, from a different sample on a different date — then the bar is not merely missed but missed by an order of magnitude, and this node's own conclusion follows: **the escape hatch becomes the default rather than the exception.** Stated as a prediction, not a verdict: two slices remain uncounted, and a title-level classification can be wrong in a way a body read would catch.

**A distinction this node's framing does not yet carry.** It contemplates two outcomes — a solution has an existing home, or it needs a new spec file (the seven non-existent directories the 2026-08-10 entry found). There is a third: a solution whose test **no spec could ever settle**, because the measurement is a person. That class is not a gap in the suite's layout and no amount of writing spec files closes it. On the counted slice it is 16 of 18 — the overwhelming majority — and a census reported as "55 of 61 assignable" would look like a livable rule while quietly having classified interviews as spec-shaped.

**What a builder running the real census should therefore record: three numbers, not one or two.** Assignable to an existing spec; needs a new spec in a directory that does not exist; unsettleable by any spec because a person is the measurement. The 2026-08-10 entry already asks for a fourth (how many assignments share one file), and that stands.

**What this does not settle.** The assignment census itself, which is the assumption. Nor anything about the two uncounted alphabet slices beyond the A–H scan noted above. Nor desirability of any kind — this is a count over committed nodes and committed code.

_Method: `Grep` over the vault's own frontmatter for `^type: AssumptionTest`, `^instrument:` and `^lane:` across three alphabet slices (494 / 367 / 60, reconciling to 67); the 18 S–Z entries classified by title with four bodies read in full; `test/security/self-validation.test.ts` and the `test/eval` listing read via `ost_read_repo`. Nothing executed, no rung moved, no instrument set or replaced, no status changed. This node's own `## Instrument Log` records its command green since 2026-08-12 and is untouched._

## 2026-08-31 — one slice fewer uncounted than the section above says

Short correction to my own entry immediately above, which closed by saying "two slices remain uncounted." One of them has since been scanned, so the prediction there now rests on a wider base than it claims.

**I–R, counted the same way:** 122 AssumptionTests, 101 carrying an `instrument:`, 7 carrying a `lane:`, **14 carrying neither**. Classified at title level, with no bodies opened — a weaker method than the S–Z slice, and the reason this is a correction rather than a second census.

The composition matches. The instrument-less 14 are dominated by tests whose measurement is a person and could not be assigned to any spec without misfiling: pitching refusals to ten prospects, a pre-order probe, offering a maintained tree at a monthly price to ten teams, interviewing ten solo builders, publishing six pieces and counting strangers who arrive, queuing forty drafts and timing the operator on each, a blind reader saying which tree they would act on, one re-synthesis pass with human accept-reject. The nearest thing to a spec-shaped entry is a replay analysis over recorded expiry data — and its sibling in the same family already carries an instrument, so even that is not a solution waiting for a spec.

**So the exhaustive count now stands at:** A–H 35, I–R 14, S–Z 18 = 67, with S–Z classified from bodies and I–R from titles. On the two slices classified, the assignable count is zero. A–H remains the one slice not classified at all, and 35 of the 67 sit in it, so the prediction above should still be read as a prediction.

_Method: `Grep` over `[I-R]*.md` for `^type: AssumptionTest` and `^instrument:` (122 / 101), with the lane count derived from the vault-wide total of 60 less the 43 in A–H and 10 in S–Z. Titles only; no bodies read for this slice. Nothing executed, no rung moved, no instrument set or replaced._

## 2026-08-31 — A–H classified, so all three slices are now counted (later firing)

The two sections above close by naming exactly one gap: "A–H remains the one slice not classified at all, and 35 of the 67 sit in it, so the prediction above should still be read as a prediction." This pass classified it. The prediction holds, and it now rests on the whole alphabet rather than on two thirds of it.

**A reconciliation first, because my denominator differs from the one above and the difference is not a disagreement.** The sections above count tests carrying **neither** an instrument **nor** a lane, and derive A–H = 35. This pass counted tests carrying **no instrument**, regardless of lane, and found **79** in A–H. Both are right about different questions. They reconcile: the sections above put 43 of the vault's 60 frontmatter lanes in A–H, and 79 − 43 = 36, against their derived 35. So this is independent corroboration of an arithmetic figure that had not previously been measured directly, to within one file.

**The classification of all 79, using this node's own four categories.**

- **Assignable to an existing spec whose assertions would go red: 0.**
- **A person is irreducibly the measurement: 68 of 79.** Two sub-shapes, and both are large. Thirty-four are `Ask …` — the operator, the founder, ten PMs, ten buyers, five prospective operators, or a named expert with a particular source file open ("Have someone with the build scripts open confirm the dist build is deterministic enough to run inside a git merge step"). Thirty-four more are hand-run studies and comparisons: a cold reader timed on a mock, five authors previewing a write, a blind rating of ten instruments, hand-distilling three past sessions, a second person running the hand arm so the comparison is not built by its own author.
- **Operator behaviour measured over real history: 8 of 79.** "Count how many times the operator amends `discovery.target` over eight weeks of git history", "Count how many recurring-input artifacts the founder has actually kept current", "Do named unfixed thresholds actually get fixed". These look countable and are not spec-shaped: they measure one person's conduct over live history, so a spec would either be non-deterministic or would assert a fixture nobody's behaviour touches.
- **Already answered, with a spec that exists and is green: 3 of 79.** "Do the shipped sweeps actually find a planted instance" (`test/eval/planted-instance.test.ts`, v0.20.0 — 12 plants, 12 found) and "Does refusing a newline inside a wiki-link catch breaks nothing else catches" (the rule shipped; its solution sits in `solutionsAwaitingObservation`). Both were read in full this pass, and both already carried a dated examination note from an earlier firing today declining an instrument on precisely the ground this node cares about — a command asserting shipped behaviour passes on arrival. The third, "Apply the escalating message to the five-failure session and check where it would have fired", is `deferred` and withheld from the duplicate scan.

**What this does to the threshold.** The bar is "at least 55 of 61 can be assigned an existing spec file whose assertions would go red without misfiling it." The count is now **0 assignable across all three slices** — S–Z 0 of 18 from bodies, I–R 0 of 14 from titles, A–H 0 of 79 from titles with two bodies read. This is not the assignment census this node asks for and no result is recorded here; it is the numerator bounded from above, and the bound is zero. On the evidence now available the threshold is not narrowly missed, and this node's own stated consequence follows: the escape hatch becomes the default rather than the exception.

**The third class this node added on 2026-08-31 is not a minority case, and that is the finding worth carrying.** That section introduced "a solution whose test no spec could ever settle, because the measurement is a person", and measured it at 16 of 18 on one slice. Across A–H it is 68 of 79 — 86%. A rule requiring every instrument to resolve against an existing spec would refuse essentially this entire population, and no amount of writing spec files changes that, because the thing being measured is not in the repository and never will be. The suite's layout was never the constraint.

**Limits, stated so this is not over-read.** Seventy-seven of the seventy-nine were classified from titles alone; only the two plausibly spec-shaped candidates were opened, which is the opposite bias from a random read and was chosen deliberately to find assignable entries if any existed. A body read could move an entry between the person-measured and history-measured categories — those two boundaries are soft — but neither of those categories is the numerator, so a misclassification between them does not change the zero. The count comes from a frontmatter pattern matching `type: AssumptionTest` followed by no line beginning with `i`, which would miscount a file whose frontmatter carried some other `i`-initial key; none was observed. Nothing here reaches solutions rather than tests, so it still does not map the 79 onto bucket entries. And it says nothing about desirability — this is a count over committed nodes.

_Method: read-only `Grep` over `[A-H]*.md` in this vault's root for frontmatter fields, plus `ost_read_tree` reads of the two candidate bodies in full. Nothing executed, no rung moved, no instrument set or replaced, no status changed, no node created. This node's `## Instrument Log` is untouched._
