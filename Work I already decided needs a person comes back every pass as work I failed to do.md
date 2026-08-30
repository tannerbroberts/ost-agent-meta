---
type: Opportunity
source: 'REPO:src/eval/buildable.ts'
created: '2026-08-30'
evidence: assertion
authorship: machine
---
#Opportunity #unvalidated #evidence/assertion
[[The bucket gains the lane filter the function two doors down already has]]
[[Route the humans-required solution into the ask queue instead of dropping it from the instrument queue]]
[[Exclude only on a lane a human set, copying the shipped-status audit rather than trusting the field]]

**The need.** When I decide that a question can only be answered by a person, I want that decision to be recorded as a decision — not to reappear on every future pass as an outstanding failure to write a command. Today the opposite happens: the deliberate answer and the un-done work are indistinguishable in the queue, so every firing pays to re-derive a conclusion the tree already reached, and each one arrives at a node whose prose is arguing with the counter that summoned it.

**Observed this pass, first-party, and this is the mechanism rather than a theory.** `solutionsMissingInstruments` in `src/eval/buildable.ts` (read in full via `ost_read_repo`) filters a Solution out of the bucket on exactly three conditions: `status === "deferred"`, `trustsShippedStatus(n)`, and any test beneath it carrying a parseable instrument. **There is no lane check.** Two functions below it in the same file, `testsAwaitingVerification` does have one — `if (n.lane === CAUTIOUS_LANE) continue;` — with a comment explaining why: "A test a human put beyond compute's reach is never run by compute." `CAUTIOUS_LANE` is `humans-required` and `computeMayRun` returns false for it (`src/knowledge/lanes.ts`). So the codebase already holds the exact predicate that would settle this, applies it to one queue, and does not apply it to the other.

**The consequence, and why it compounds rather than merely annoys.** A Solution whose every assumption test is correctly labelled `humans-required` can never leave `solutionsMissingInstruments`. The only call that could label a test into that lane from an unattended surface is `ost_flag_humans_required`, and it is not granted on `/ost-pass` — pinned in `test/eval/clearability.test.ts`, whose `lane-conflict` row records the reason as "on `/ost-pass` the tool is not granted at all (R7's containment)". So the sweep is handed a bucket, told to clear it, and holds neither the tool that would clear it nor an honest command to write instead. The instruction and the grant disagree, and the pass in the middle absorbs the difference.

**What that costs, measured on this pass.** The bucket stood at 68 solutions. Four were opened in full. All four had already reasoned explicitly that no instrument belongs on them, in prose written by earlier firings: two say "No command: this one is humans-required on purpose"; one says "There is deliberately no instrument here" and adds a lane note explaining that `ost_flag_humans_required` is withheld; the fourth says "No honest instrument exists for this node as worded" and records that seven consecutive passes declined for that reason. One of those tests was read directly and carries `lane: humans-required` in frontmatter, so the label is present and the bucket ignores it. Four of four opened is a small sample of 68 and is stated as such — but the mechanism is read off the source, not inferred from the sample, and the mechanism does not depend on how many nodes it currently catches.

**The precedent is in the same file, which is why this is a gap rather than a design choice.** `solutionsMissingInstruments`' own doc comment records that "Four solutions correctly parked as `shipped` recurred in this list on every pass until each future sweep either re-derived the same conclusion or was tempted to invent a command that could not fail." That is this defect, in a different clothing, already recognised and already fixed once — for `shipped`, by `trustsShippedStatus`. The humans-required case is the same failure with the same two outcomes, and the second of them is the dangerous one: a pass that resolves the pressure by inventing a command puts a test into the tree that cannot measure the belief it hangs under.

**Litmus test (more than one way to address this?):** Yes, and the candidates disagree with each other about who should act. Filter the bucket in code so the listing never mentions them. Route them instead to `outstandingAsks`, which already exists and already ages a pending ask, so the work is re-labelled rather than hidden. Or copy `trustsShippedStatus` exactly and exclude only on a lane a human's `ost-agent lane --set` recorded in History, distrusting the bare frontmatter field. Passes.

**The distinction the third candidate turns on, worth stating here because it is the trap.** A lane can reach a node two ways: a human's CLI call, or `ost_create_node`'s own `humansRequired:` argument, which an agent passes at creation time. A filter that trusts the bare field therefore lets an agent take its own work off the queue by declaring it needs a person — the same self-certification `trustsShippedStatus` was written to refuse. Whichever candidate is chosen has to answer that, and any answer that trusts the bare field is choosing to.

**What this node does not claim.** It does not say the 68 are all of this kind; that census is uncounted and is named as the open question under the candidates. It does not say `humans-required` is the correct lane for any particular one of them — several of the four opened argue their own case and a reader may disagree. And it says nothing about desirability: this is observed behaviour of the product, read from its own source and its own sweep output, which grounds usability and is not evidence that anybody outside this project wants it fixed.

**Provenance:** first-party read of `src/eval/buildable.ts`, `src/knowledge/lanes.ts` and `test/eval/clearability.test.ts` via `ost_read_repo`, plus this firing's own `ost_next_work` response and four node bodies. Rung `assertion` — a claim from inside the building. No test was run and no result is recorded.

## The defect demonstrated itself within one pass, with a control

Recorded because it is a first-party observation rather than a restatement, and because it arrived with the comparison that makes it discriminating.

This pass created three solutions beneath this opportunity in one sitting, by one author, on the same day. Two carry an assumption test with an `instrument:`; the third carries one created with `humansRequired:`, because whether an operator answers a routed ask cannot be settled by an exit code. The sweep was then re-run.

- `solutionsMissingInstruments` went from **68 to 69**.
- The two instrumented candidates are absent from the list, correctly.
- The added entry is "Route the humans-required solution into the ask queue instead of dropping it from the instrument queue" — the candidate written to describe this defect, listed as an instance of it, minutes after being written.

That is the mechanism this node reads off `src/eval/buildable.ts`, observed operating rather than inferred: the lane label was set at creation, the bucket does not read it, and a correctly-decided node joins the queue of things the next pass will be told to fix. The two instrumented siblings are the control — same author, same pass, same parent — so the difference is the lane and not the quality of the writing or the age of the node.

**What this adds beyond the code read, and what it does not.** It rules out the reading that the 68 are simply old nodes written before lanes mattered, which a reader could otherwise have taken from a bucket full of long-standing entries: a node created under the current rules, with a lane set deliberately at creation, lands in the bucket immediately. It does not establish the share of the other 68 that are of this kind — that census is still uncounted and is named as open under the candidates. And it is one increment, not a rate.

**One consequence for whoever picks a candidate.** The filter sibling would have excluded this new node on day one; the routing sibling would have moved it to the ask queue; the audit sibling would have kept it exactly where it is, because its lane was agent-set at creation and no human ratified it. The three candidates therefore disagree about this very node, which is a cheap way to feel the difference between them before building any of them.

_Source: this firing's own `ost_next_work` responses before and after the writes. Observed behaviour of this product; grounds usability, not desirability. No test was run and no result is recorded._

## The census, run over 10 of the 25 visible entries — and it is not a backlog (2026-08-30)

This node has named the census as its open question three times, and the strongest count on record was 4 of 68. This pass opened **10 solutions in full** from the 25 `ost_next_work` showed (of 69 total) and classified each by *why* no instrument belongs on it. **Ten of ten were legitimately not-instrumentable.** Not one was a pass that simply failed to write a command.

**The four kinds, which matter more than the count.**

- **A humans-required belief — 6 of 10.** "Route the humans-required solution into the ask queue instead of dropping it from the instrument queue", "An operator-set evidence window in ost.config.yaml, amended by hand like discovery.target", "Group the queue by error signature at read time, and change nothing on disk", "A human-edited manifest of loop-prescribed call sequences the harvester suppresses", "Name the specific mechanisms a hand process structurally cannot have", "Axioms elicited at the moment a derivation needs them, one accept-or-reject ask at a time". Each rests on whether a person answers, maintains, acts, or is persuaded.
- **The subject is not in this repository — 2 of 10.** "A repeated wait on the same condition resumes and doubles its budget automatically, up to a ceiling set once by hand" is about the harness's `await` helper on the session PATH; "Maintain a running per-item task list the next pass reads before reconstructing state itself" is about the harness's own task list. No spec under `test/` can reach either artifact, however the belief is worded.
- **Already built; a spec would pass on arrival — 1 of 10.** "Remote push optional and off by default" is pinned green in two places (`test/config/load.test.ts` asserts `cfg.remote.enabled` is false; `test/release/outward-mutation.test.ts` withholds `git_push` from the agent surface with a positive control).
- **The premise is superseded and needs a human's disposition — 1 of 10.** "Append-only tool surface with no delete or shell tool" describes a surface that no longer exists. A spec asserting "no delete tool" would go red — and that red would invite a builder to *remove* `ost_merge_nodes`, which is worse than no spec.

**The finding that discriminates between this node's own three candidates, and it is new.** Only the first kind is lane-shaped. Two lanes were read directly this pass, and they disagree in the way that decides the question:

- "Count the recorded expiries that later succeeded against those whose condition could never have become true" carries `lane: humans-required` in frontmatter — **set by an agent's `humansRequired:` argument at creation**, not by a human's `ost-agent lane --set`.
- "Test do operators get value with remote push off" carries `lane: null`, and is a pure desirability test ("Observe ~5 trial operators over their first week"). Nothing labelled it, because the sweep that met it had no tool that could.

So the three candidates fail in three different amounts, and none of them clears the bucket:

- **The lane filter** ("The bucket gains the lane filter the function two doors down already has") clears only the labelled subset. The other-three-kinds solutions carry no lane at all, so they stay exactly where they are.
- **The lane audit** ("Exclude only on a lane a human set, copying the shipped-status audit rather than trusting the field") clears **approximately none of them**, because every lane found in this sample was agent-set at creation. It is the candidate that best answers the self-certification trap this node names, and on today's data it is also the candidate that does the least.
- **The routing candidate** moves the labelled subset to `outstandingAsks` and leaves the unlabelled six-of-ten kinds in place.

**The consequence for whoever picks one.** A lane check alone is not sufficient, and this sample says so with numbers rather than by argument. At least three distinct exclusions are needed — the lane, "the subject is outside `product.repos`", and the already-built case that `trustsShippedStatus` half-covers — or the bucket keeps summoning passes to nodes that have already reasoned their way to "no command belongs here." Six of the ten opened *already carried that reasoning in prose written by earlier firings*, which is the re-derivation cost this node exists to name, now measured at 60% of a ten-node sample.

**Limits, stated so this is not over-read.** Ten of the twenty-five shown, of sixty-nine total — the 25 are the unfiltered head ordered by id, not a random sample, which is the defect "An operator-set evidence window in ost.config.yaml, amended by hand like discovery.target" names. The 44 entries past the cap were unreachable from this surface and may contain genuinely instrumentable solutions; nothing here claims otherwise. Ten of ten is a strong signal about the head and not a proof about the tail. Two of the four kinds were established by reading the solution's prose rather than its test's frontmatter, so the lane counts above are exact for the two tests read and inferred for the rest.

_Source: first-party `ost_read_tree` reads of ten Solution nodes, two Assumption nodes and two AssumptionTest nodes, plus `ost_read_repo` on `src/eval/buildable.ts`. Observed behaviour of this product; grounds usability, not desirability. No test was run and no result is recorded._
