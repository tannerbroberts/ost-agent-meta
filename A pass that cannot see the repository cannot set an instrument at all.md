---
type: Solution
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Operators would rather have honest gaps than guessed commands]]
[[What is in the 33 queue entries no tool has ever listed]]
[[The write boundary can refuse a blind instrument without refusing every instrument]]

**The idea.** Instrument-writing is gated on repo sight. A surface without it gets a refusal instead of a write, and the test routes to a named lane (work waiting on an attended pass) rather than being cleared blind.

**Why this shape.** It is the only candidate that makes the guarantee unconditional — every instrument in the tree was written by something that had read the code, and the cost is paid visibly as a named backlog rather than silently as guessed paths. It also answers what a blind pass should *do* with `solutionsMissingInstruments`: nothing, and say so — which many sweeps have now done by hand.

**Comparison to siblings.** "An instrument records whether the pass that wrote it could see the repository" is the observe-only floor; this is the ceiling — both could ship, in that order. "An instrument naming a spec path that does not exist is refused" catches a weak artefact even from a sighted author, which this rule alone does not.

**Where it fails, stated so it can be judged.** Trades throughput for groundedness at an unknown exchange rate: under this rule an unattended fleet contributes zero instruments to a backlog that (see below) turns out to be almost entirely non-mechanical anyway. The blunter risk: gating on capability argues for handing an unattended loop repository access, which is a distinct safety conversation and should be had deliberately, not as a side effect of this rule.

**Cost.** A capability check and a lane. Small to build, large to live with.

**Definition of done.** "Five operators choose between sixty-one weak instruments and sixty-one blanks" — deliberately no command; this solution trades throughput for a preference no repository can hold, so it is `humansRequired` by design. A builder should not start this until that result exists.

## The standing finding — established 2026-08-10, reconfirmed every sweep since

**The queue's blocker is composition, not sight, and this was proven rather than assumed.** A complete census (2026-08-10) opened every test beneath all 58 entries then in `solutionsMissingInstruments` — not just their solution's title — and classified each by what its test could actually measure:

| Class | n of 58 | What it actually needs |
|---|---|---|
| A person is the measurement (pricing, positioning, willingness) | 40 | An interview or an operator's answer |
| Elapsed calendar time is the measurement | 7 | Weeks of ordinary running, not a spec |
| Already `status: shipped`, listed anyway | 7 | Nothing — a green-on-arrival command measures nothing |
| No command by design, stated in the node's own body | 1 | This node |
| Premise superseded by the product already existing | 1 | — |
| Threshold conflates a mechanical clause with a human one | 2 | Splitting the test — a structural edit, not an unattended pass's call |
| **Genuinely mechanical** | **0** | — |

Two firings that *held* repo sight (`ost_read_repo` answering, or built-in `Glob`/`Read` access confirmed live) wrote **zero** instruments anyway, because there was nothing in the queue a command could settle — the strongest possible refutation of "sight is the blocker." One further finding, useful for any future gate design: `ost_read_repo` and built-in file tools (`Glob`/`Read`) are **separable grants** over the same directory — a pass can hold one and not the other, observed both ways across different firings on the same machine.

**The queue has grown since (58 → 70, stable at 70 through 2026-08-17) purely by new solutions entering already-classified families** — commercial/pricing, axiom/goal-acquisition, highlight-digest, CONVO opportunity-grammar — and every new entrant checked has landed `people` or `elapsed-time`, never mechanical. The one near-miss worth a future builder's attention: "Every new sibling opportunity states its differentia at creation, or the create is refused" is genuinely code behaviour (a create-time guard), but its current test asks whether the differentiae authors write are *good*, which no exit code holds — splitting it into a feasibility half (guard refuses without a differentia) and a desirability half would give this queue its first real mechanical entry. That split is a human/attended-pass call.

**A related batch defect, still unfixed:** tests created with `lane: humans-required` at creation still surface their solution in `solutionsMissingInstruments` on the next sweep — reproduced across at least three separate founder-theory/highlight batches. The repair belongs to "Work I already finished keeps coming back in the queue, so the pass can never say it is done", by excluding humans-required-laned tests from this bucket's count.

⚠️ Unvalidated. Agent-ideated.

## History
- 2026-08-07 → 2026-08-11: repo-sight-gating hypothesis tested directly across ~14 firings, both with and without the grant; queue moved 58 → 70 purely via new non-mechanical entrants. `mechanical = 0` held at every recount.
- 2026-08-17 body compressed (this edit) — 14 dated "not a recorded result" entries folded into the standing finding above; nothing dropped, see git log.
- 2026-08-17 body edited — 14 dated "not a recorded result" entries (2026-08-07 through 2026-08-17) grew this node to 38KB restating the same finding — the queue's blocker is composition, not repo sight. Compressing to the standing finding plus a compact trend log, following the same precedent already applied to the Outcome node (2026-08-04) and to the sibling ledger node on this same pass. No claim dropped; git history holds the full prior text.

## Issues
- 2026-08-07 A human-required test still reads as instrument debt (see "batch defect" above) — this node's own only test, "Five operators choose between sixty-one weak instruments and sixty-one blanks", is itself an instance: created `humansRequired` correctly, and still listed in `solutionsMissingInstruments` on the very next sweep. `ost_flag_humans_required` is withheld from the unattended surface, so this cannot be relabeled from here.
- 2026-08-17 Queue held at 70 with no new family since the highlight-digest batch (2026-08-11). Composition finding unchanged; no repo-sight grant held this sweep (by design — see "What this surface withholds").
- 2026-08-20 2026-08-20 unattended sweep, repo sight held (`ost_read_repo` live; built-in Glob on the product still denied). Queue 91 → 89. Enumerated the whole backlog from the vault rather than the capped list: 397 AssumptionTest files minus 329 carrying `instrument:` or `lane:` = 68 prose-only, unlaned tests; by title and body 66 are people, elapsed time, already-shipped, or premise-superseded — consistent with the standing `mechanical = 0` finding. The two exceptions were both the conflated-lane shape this node predicted, and both were split rather than instrumented whole: "Apply the escalating message to the five-failure session…" (now deferred; replay half carries `test/loop/repeat-class-escalation.test.ts`, live half is humans-required) and the differentia gate, which gained its missing feasibility assumption and a test carrying `test/ost/sibling-differentia-guard.test.ts`. Both instruments are no-spec reds, declared as such on the nodes, with the absent mechanism named from the code (`src/loop/corrections.ts` is cross-session and drops non-zero exits; `ost_create_node` has no differentia argument). Observed along the way: `ost_create_node` refuses a no-spec instrument unless the `threshold` carries a numeric bar — the same prose threshold was refused with spelled-out numbers and accepted with digits.
- 2026-08-22 2026-08-22 unattended sweep, fourth firing, repo sight held. Continued the reframe the third firing established (that the census measured existing tests and never the missing beliefs) and got three more counter-instances, from a different family than the five it found: the commercial/pricing cluster was deliberately not touched, and the mechanical halves came from an unattended-runtime opportunity instead. Two of them were pulled off the `outstandingAsks` queue rather than invented — "Ask someone with the build loop's source and persisted state open whether a per-target failure record already exists" is a question about `src/loop/`, which is in this repository, so it was grounded by reading `src/loop/state.ts` in full and given a spec-settleable sibling test rather than left costing a person an afternoon. The pattern generalises: at least three more entries on that queue ("whether target selection re-reads live status", "whether it filters candidates on status", "whether anything reads dist off the shared trunk") name this repository's own source as the thing to be read, and are mis-laned as human asks for the same reason. That is a fourth relocation of this node's argument and worth a human's read: the blocker for those is neither sight, nor the write capability, nor threshold discipline — it is that the test was addressed to a person when the answer was on disk. Standing `mechanical = 0` finding untouched; every solution touched still carries a genuine human ask alongside the new mechanical one.

## Third sighting with repo sight held — unattended sweep, 2026-08-18

Correction to the 2026-08-17 Issues line below: this sweep's surface DID grant `ost_read_repo` (confirmed live — read the repo root, `src/`, `test/loop`, `test/loop/*.ts` listings, and the full text of `src/loop/health.ts`, `src/adapters/friction.ts`, `src/adapters/transcript.ts`, `examples/automation/autonomous-pass.sh` and `build-pass.sh`). So "no repo-sight grant held this sweep" was not durable across sweeps on the same surface — the withholding is not fixed, or the note describing it was wrong. Either way, worth a human's attention as its own small finding.

With sight held, this pass reviewed several `solutionsMissingInstruments` entries closely (friction-summary-in-report, friction-count-threshold, deny-write-on-automation-paths) and confirmed the standing finding rather than refuting it: none reduced to a command a spec file could settle today. Two needed a design decision no test can make (which existing report/mechanism a friction summary should hook into — none exists yet) and one needed external documentation this repo cannot hold (whether Claude Code's own permission flags support path-scoped Write/Edit, not just whole-tool grants — confirmed absent from both automation scripts' current usage, which is evidence of non-use, not proof of incapability). A fourth data point for the `mechanical = 0` column, not a new family.

## Sight was never the binding constraint — the *write* capability is (read from source, 2026-08-21 unattended sweep)

This node's standing finding says the queue's blocker is composition, not sight, and that two sighted firings wrote zero instruments anyway. That holds. What follows is a mechanism the census could not see, because it is in the instrument grammar rather than in the queue — established this pass by reading `src/knowledge/instruments.ts` and `src/ost/instrument.ts` in full, which no prior entry here records doing.

**Even a perfectly mechanical entry cannot be given a non-vacuous red by any agent surface.** Four facts compose:

1. `INSTRUMENT_FORMS` holds exactly one form: `^npx vitest run (?<target>…\.test\.ts)$`. One whole spec file. No `-t` filter, no second path.
2. `SHELL_METACHARACTERS` refuses `[;&|`$(){}<>\\\n\r*?!#~'"]` on sight — so `-t "the assertion this test needs"` is rejected before the form is even tried. Confirmed empirically this pass: that exact instrument was refused with "contains shell punctuation. Name one spec file."
3. `runInstrument` short-circuits on `!existsSync(target)` and files `no-spec` — no permit, nothing measured.
4. `verifyInstrument` refuses to record a first-run green, because a command that passes against a repo where the solution does not exist measures nothing.

An agent has no tool that writes a spec file. So for behaviour that has not been built, its only two reachable outcomes are a `no-spec` filing (naming a file nobody has written) or a refused green (naming an existing passing spec). **A genuine red requires a spec that exists and fails, and producing one requires the write capability the discovery surface deliberately lacks.**

**This re-reads the tree's own headline number.** `src/ost/instrument.ts` cites 260 of 266 recorded reds in this vault reading "No test files found" on 2026-08-09, and frames it as the tree's stock of falsifiability turning out to be 241 unwritten files. The framing is right about the consequence and wrong about the cause: that was not carelessness by past passes, it was the only state the grammar leaves reachable for an author who cannot create the file. The 2026-08-20 entry above is consistent — both instruments it set are recorded there as no-spec reds.

**What this changes for the gating question this node argues.** Gating instrument-writing on repo sight would not raise the rate of genuine reds, because sight does not close the gap; the gap is between naming a spec and authoring one. The orderings that would are different in kind — the builder writes the failing spec and discovery names it afterwards; or a `no-spec` filing is treated as a *commissioned* spec with an owner rather than as a finished instrument; or the grammar gains a form that can point at an assertion inside a file that already exists. Each is a product decision and none is an unattended pass's call, so they are named here rather than ideated as siblings.

**A caveat against over-reading this.** The `no-spec` mechanism is not a defect — the code argues for it explicitly and the argument is good: a missing file is red for every question equally, so it distinguishes none of them. Nothing above disputes that. The finding is narrower: given that rule, the instruction that unattended sweeps should prefer assertion-specific reds over missing-file reds cannot be complied with from this surface, and a sweep that appears to comply is naming files it has not written.

_First-party observation of this product's own source, read this pass via `ost_read_repo`. Grounds feasibility only; it says nothing about whether anyone wants the queue cleared. Rung stays at the `assertion` floor._

## Correction to the section above, same pass (2026-08-21)

The finding above states that an agent's only reachable outcomes are "a `no-spec` filing (naming a file nobody has written) or a refused green", and in listing the four composing facts it says a `no-spec` run mints no permit. **That last part is wrong, and the error matters because it undersells what a sweep can hand a builder.** Corrected after reading `src/eval/buildable.ts`, which the earlier section had not yet read.

`confirmPermit` treats a `no-spec` run conditionally, not fatally:

```
if (observed.observation === "no-spec") {
  if (permit.thresholdBound) return permit;   // permit stands
  return { cleared: false, … }
}
```

**A weak red keeps its permit when the test names a bound threshold, and loses it only when there is neither a spec nor a fixed bar.** The code argues the point from this vault's own history: "Declare a required tool set and check a pass refuses before doing any work" was recorded red on 2026-08-06 with "No test files found" and went green on 2026-08-07 — a builder read the path, found nothing there, and built to the node's pre-committed threshold instead. Refusing every weak red would have blocked that lifecycle.

So the structural claim survives in weakened form, and the practical advice inverts:

- **Still true:** an agent that cannot author files cannot produce a non-vacuous *red*. The grammar admits one form, refuses shell punctuation, and `runInstrument` short-circuits on a missing file. That part stands, and it still explains the 260-of-266 figure.
- **False as stated:** that this makes the resulting instrument worthless. A `no-spec` instrument **with a bound threshold** is a working build permit by design, not a failure the system tolerates.
- **What follows for a sweep:** the thing that decides whether an unattended pass hands a builder anything is not repo sight and not the spec path — it is **whether the threshold is a fixed bar**. That is entirely within an agent's power to write, and it is the one lever here that does not need a capability nobody granted.

That reframes this node's own gating argument a third time. Sight is not the blocker (the standing finding). The write capability is not really the blocker either. **The blocker is threshold discipline** — which is the subject of a different opportunity already on this tree, "My tests carry thresholds nobody ever fixed, so nothing can come out a failure", whose own measurement found 20 of 63 tests in one bucket stating no fixed bar. Those two nodes are pointing at the same lever from opposite ends, and a human may want to read them together.

_Correction recorded by appending rather than by rewriting the section above, so the mistaken claim and its correction both stay visible. First-party read of `src/eval/buildable.ts`._

## The threshold lever is reachable only at creation time — a bound on the correction above (2026-08-22 unattended sweep)

The correction above ends by relocating the blocker a third time: not sight, not the write capability, but **threshold discipline** — "entirely within an agent's power to write, and the one lever here that does not need a capability nobody granted." That conclusion is right about *which* lever matters and wrong about who can pull it for the tests that need it. The distinction is creation time versus afterwards, and it decides whether ~78 existing tests are an agent's work or a human's.

**What an agent surface can and cannot do to a threshold, enumerated from the tool contracts held this pass:**

| Act | Tool | Available? |
|---|---|---|
| Set `threshold:` when creating a test | `ost_create_node` (`threshold` argument) | Yes |
| Set `threshold:` on a test that already exists | — | **No such tool** |
| Change status / evidence / lane / instrument on an existing test | `ost_set_status`, `ost_set_evidence`, `ost-agent lane`, `ost_set_instrument` | Yes — each a typed transition |
| Rewrite a test's prose | `ost_edit_node` | Yes, prose only |

`ost_edit_node` states the rule that closes this: "Frontmatter is untouched — status, evidence, lane and instrument each have their own tool because each records a typed transition." **Threshold is absent from that list of four, and has no tool of its own.** It is the one frontmatter field with no typed-transition path, so on this surface it is write-once at creation and immutable thereafter.

**Why that matters against `confirmPermit`.** The correction above establishes that a `no-spec` run keeps its permit **iff** `permit.thresholdBound`. Composed with the table:

- A **new** test can be given a bound threshold and a no-spec instrument in one `ost_create_node` call, and that is a working build permit — the correction's advice holds in full.
- An **existing** thresholdless test cannot be repaired the same way. Setting an instrument on one produces precisely the artefact the ruleset condemns: a no-spec red with no bound bar, `cleared: false`, nothing handed to a builder. **So the correct action on a thresholdless entry in `solutionsMissingInstruments` is still to leave it alone** — the standing "write nothing" finding survives this reframing, for a different reason than it was originally given.

**The size of the affected set, and the caveat on the number.** Summing the rollup's per-bucket "N of M test(s) state no fixed bar" lines gives **78** across 18 buckets. Treat that as approximate rather than a census: a test beneath an opportunity filed under two buckets would be counted twice, and this pass did not de-duplicate it. The order of magnitude is what the argument needs — this is a two-figure backlog, not a handful.

**One question decides whether any of it is agent-repairable, and this pass could not answer it.** Does the no-fixed-bar counter read the `threshold:` frontmatter field, the prose lead-in, or both? Observed in the vault this pass: both conventions are in live use. `Ask ten buyers what happened the last time a tool they relied on shut down` carries a `threshold: >-` field; `Test does a 10 percent sample estimate whole-tree quality` carries no such field and states its bar only in prose as "**Pre-committed success threshold:** sample estimate within ±10% of the full-tree score."

- If the counter reads **prose**, then the 78 are agent-repairable after all — `ost_edit_node` can write a properly-formatted lead-in with digits in it, and the correction above is right for existing tests too.
- If it reads **frontmatter only**, the 78 are a human's or an attended pass's work, permanently, and no amount of prose discipline touches them.

**Weak evidence for the prose reading, stated as the inference it is.** The tree already holds a test named "A wrapped pre-commitment lead-in is read, so the absent count stops being a formatting artefact" — a question that only makes sense if the counter parses the prose lead-in and mis-parses hard-wrapped ones. That is an inference from a sibling node's title, not a read of the parser, and it should be checked rather than believed. Whoever holds repo sight next: this is a five-minute read of the counter, and it decides the disposition of ~78 tests.

**Why this is filed here rather than ideated as a sibling.** It sharpens the argument this node makes about what gating buys, and it names a decision — repair the 78, or accept them as sunk — that belongs to a human. It proposes no new solution.

_Method: tool-contract enumeration over the surface held this pass, plus four `Grep`/`Read` passes over the vault's own node files to confirm both threshold conventions are in live use. No repo sight this pass, so the parser question is left open rather than guessed. First-party on the tool surface and on the stored nodes; silent on whether anyone wants the queue cleared. Rung stays at the `assertion` floor._

## Answered from source: the counter reads BOTH, and prose wins the ~78 back (2026-08-21 unattended sweep, repo sight held)

The section above ends by naming one question and asking whoever holds repo sight next to settle it: "Does the no-fixed-bar counter read the `threshold:` frontmatter field, the prose lead-in, or both?" — with the note that it "decides the disposition of ~78 tests" and is "a five-minute read of the counter." This pass held `ost_read_repo` and read it. **The answer is both, frontmatter first and prose as a fallback, and the practical consequence is the one the section hoped for rather than the one it feared.**

**The chain, named so it can be re-checked rather than believed.** `src/eval/rollup.ts` computes `withFixedThreshold` as `tests.filter(t => thresholdKindOf(t) === "bound")` — so the rollup line quoted in the section above is `thresholdKindOf` and nothing else. `thresholdKindOf` (`src/eval/coverage.ts`) calls `askedOf`, whose first eight lines are:

```
export function askedOf(test: OstNode): string | null {
  if (test.threshold) {
    const trimmed = test.threshold.trim();
    if (trimmed) return trimmed;
  }
  const lines = test.body.split("\n");
  ...
```

The frontmatter field is preferred **when present and non-empty**, and every node without one falls through to a prose scan of the body. The function's own docstring says so outright: "Falls back to the prose scan for every node written before the field existed, which is most of both live vaults."

**So the disjunction in the section above resolves to its first branch.** Quoting it: "If the counter reads **prose**, then the 78 are agent-repairable after all — `ost_edit_node` can write a properly-formatted lead-in with digits in it, and the correction above is right for existing tests too." That is the case. The alternative branch — "If it reads **frontmatter only**, the 78 are a human's or an attended pass's work, permanently" — is false, and the ~78 tests are **not** stranded. The weak inference the section flagged for checking (that a sibling test about hard-wrapped lead-ins only makes sense if prose is parsed) was correct, and `coverage.ts` confirms it in detail: `paragraphAt` exists precisely so a hard-wrapped lead-in reads the same as an unwrapped one, and its docstring records that mis-parse as "observed twice in a live vault."

**What an agent must write for a paragraph to count `bound`.** The classifier is two regexes, and neither requires a digit:

- `PRECOMMIT_LEAD` — a **bold** span containing the substring `pre-commit`, case-insensitive, anywhere in the paragraph. "Pre-committed threshold", "Pre-committed success threshold", "Pre-commit the threshold before starting" all match; the docstring says the loose match is deliberate because "tightening this to one spelling would silently report the tree as thresholdless."
- `A_BOUND` — `/\d|[≥≤]|>=|<=|\b(at least|at most|no more than|no fewer than|fewer than|more than|majority|unanimous|exactly|zero|none|half)\b/i`, tested against the text following the lead-in.

A bar in words scores exactly as well as a bar in digits: **"at least 4 of 5" and "at least four of five" both read `bound`**, because `at least` alone satisfies `A_BOUND`. That is worth stating flatly, because the 2026-08-20 Issues note below records the opposite behaviour at the *other* boundary — `ost_create_node` refusing a no-spec instrument whose threshold spelled its numbers out, and accepting the same threshold with digits. **Those are two different checks with two different rules, and only the create-time one cares about digits.** A pass that generalised from the create-time refusal to the census counter would wrongly conclude its word-bars are invisible. They are not.

**Where this leaves the node's own argument, a fourth time.** The correction above relocated the blocker to threshold discipline and called it "the one lever here that does not need a capability nobody granted." The section after it bounded that to creation time only, on the grounds that no tool sets `threshold:` after the fact. The bound is real about the *field* and wrong about the *outcome*: `ost_edit_node` rewrites prose, prose is the fallback the counter reads, and a rewritten body carrying a `**Pre-committed threshold:** …` paragraph with a bar in it lands `bound` just as a frontmatter field would. The tool-contract table in that section is accurate and its conclusion does not follow from it.

Concretely, and this is the part a future sweep should act on: **`confirmPermit` reads `permit.thresholdBound`, which is `thresholdKindOf(chosen) === "bound"`** (`src/eval/buildable.ts`, `permitFrom`). So the repair path for an existing thresholdless test is open end to end — edit the prose to carry a bound pre-commitment, and a `no-spec` instrument on that test keeps its permit instead of being refused with "there is no number to build to."

**One caution against over-running this finding.** It does not make the instrument queue mechanical. The standing `mechanical = 0` finding is untouched: this pass re-checked two more queue entries ("A highlights digest distilled from what vault history already records" and "Alert only when a run's friction count crosses a set threshold") and both bottom out in tests that are correctly `lane: humans-required` with bound thresholds already in the field — a person is the measurement, and no spec can stand in. What the finding changes is narrower and still large: the ~78 no-fixed-bar tests are repairable from an agent surface, which was believed closed an hour ago.

_Method: first-party reads of `src/eval/rollup.ts`, `src/eval/coverage.ts` and `src/eval/buildable.ts` in full via `ost_read_repo`, plus `ost_read_tree` on the two queue entries named. Nothing executed — the regex conclusions are read off the source, not observed by running the classifier, and a sweep with a shell should confirm one repaired node actually moves the rollup count. Grounds feasibility only; silent on whether anyone wants the queue cleared. Rung stays at the `assertion` floor._

## Bound on the section above: the prose repair path reaches 117 of 430 tests, not all of them (2026-08-22 unattended sweep, repo sight held)

The section above ("Answered from source: the counter reads BOTH...") ends by declaring the repair path open: "the repair path for an existing thresholdless test is open end to end — edit the prose to carry a bound pre-commitment, and a `no-spec` instrument on that test keeps its permit." **That is true for a minority of the tests it was written about, and the boundary is one clause in the function it quotes.**

**The clause.** `askedOf` opens:

```
if (test.threshold) {
  const trimmed = test.threshold.trim();
  if (trimmed) return trimmed;
}
```

It **returns**. When a node carries a non-empty `threshold:` frontmatter field, the prose scan below it is never reached — not consulted as a second opinion, not merged, not fallen back to. The section above quotes these exact eight lines and reads the fallback correctly, but then generalises the conclusion to "every existing thresholdless test", and the field-carrying case is the one where the generalisation fails.

**Composed with the tool-contract table two sections up, this closes a door that section left open.** That table established there is no tool on any agent surface that sets `threshold:` on an existing node — it is write-once at `ost_create_node` and absent from `ost_edit_node`'s list of typed transitions. So for a test that already carries a field reading `prose` or `instruction`:

- `ost_edit_node` can rewrite the body, and `askedOf` will not look at it.
- No tool can rewrite the field.
- Therefore **no agent surface can move that test to `bound`, by any route.** It is a human's `ost-agent` work permanently, and the earlier section's bound-to-creation-time conclusion was right after all for this subset — it was only wrong about the subset's size.

**Census, so the split is a number rather than an impression.** Counted this pass over the vault's own files: **313 of 430 AssumptionTest nodes carry a `^threshold:` field.** So the prose repair path is reachable for **117** tests and unreachable for **313**. The ~78 no-fixed-bar figure the section above computed by summing rollup lines is drawn from both groups without distinguishing them, so it cannot be read as a repairable backlog — some unknown share of it is field-carrying and permanently out of reach from here.

**A worked instance, checked by hand rather than asserted.** "Ask the operator whether firings on the shared checkout can ever overlap in time" carries `threshold: 'Operator confirms strict serialization, or confirms overlap is possible'`. Against `A_BOUND` that string holds no digit, no `≥`/`≤`/`>=`/`<=`, and none of the listed words (`at least`, `at most`, `no more than`, `no fewer than`, `fewer than`, `more than`, `majority`, `unanimous`, `exactly`, `zero`, `none`, `half`). Its opener, "Operator", is not in `DEFERRING_VERBS`. So it classifies `prose`, counts against the rollup's fixed-bar line, and would fail `confirmPermit`'s `thresholdBound` check — and no amount of editing its body changes any of that.

**What a future sweep should do with this.** Before spending an edit on a thresholdless test, check whether the node carries a `threshold:` field. If it does, the edit is wasted motion; name it for a human instead. If it does not, the section above is correct and the edit works.

_Method: first-party `ost_read_repo` of `src/eval/coverage.ts` and `src/eval/rollup.ts` in full, plus a count over the vault's own node files for the 313/430 split. Nothing executed — the classifications are read off the regexes, not observed by running them. Grounds feasibility only. Rung stays at the `assertion` floor._

## The reachable repair backlog was 6, not 117 — measured and cleared (2026-08-22 unattended sweep, second firing, repo sight held)

The section above establishes the split correctly — 313 of 430 tests carry a `threshold:` field and are permanently out of reach from an agent surface, 117 do not and are prose-repairable — and then advises: "Before spending an edit on a thresholdless test, check whether the node carries a `threshold:` field. If it does, the edit is wasted motion." That advice is right. What it does not say, because nobody had counted, is **how many of the 117 actually need the edit.** This pass counted, and the answer is small enough to change what a sweep should do about it.

**The count.** `askedOf` falls back to a prose scan only for field-less nodes, and that scan looks for a bold span containing the substring `pre-commit`. Grepping the vault for that lead-in shape and intersecting against the 117:

| Of the 117 field-less tests | n |
|---|---|
| Already carry a pre-commitment lead-in | 111 |
| Carry none at all — classify `absent` | **6** |

**All 6 are now repaired**, by appending a `**Pre-committed threshold:** …` paragraph to each. Every one of them already stated a real bar in its opening line as a bare `Threshold: …` sentence — a form that matches no lead-in and reads as `absent`. So this was the formatting artefact the sibling test "A wrapped pre-commitment lead-in is read, so the absent count stops being a formatting artefact" was written about, in a second shape: not a hard-wrapped lead-in, but no bold at all. No question was changed and no bar was invented; each appended paragraph restates the node's own sentence in the form the reader can see, and each says what clearing it does not settle. Verified after the fact: the lead-in grep went 194 → 200 files, and all 6 titles appear in it.

The 6, all of them `lane: humans-required` and all of them on the `outstandingAsks` queue:

- Ask someone with the build loop's target-selection source open whether it filters candidates on status
- Ask someone with the build loop's source open whether target selection re-reads live status or works from a cached snapshot
- Ask someone with the build loop's source and persisted state open whether a per-target failure record already exists across firings
- Ask the operator whether reading Monitor's stated constraints before composing would have changed how these two sessions wrote their commands
- Ask someone with the Monitor tool's implementation open whether a bounded until sleep primitive is addable without reopening arbitrary shell execution
- Ask someone with the harness's sandbox implementation open whether a per-task scoped read grant is addable without widening the sandbox generally

**What this does and does not settle about the ~78 figure.** The section above computes ~78 by summing the rollup's per-bucket "N of M state no fixed bar" lines, and correctly warns it double-counts. It cannot be read as a repairable backlog, and now the reason is sharper than "some unknown share is field-carrying": `absent` among the field-less was exactly 6. Whatever else in the 78 is field-less is a lead-in **present with a bar-less paragraph** — `prose` or `instruction` — which is repairable by rewriting that paragraph rather than by adding one, and needs `ost_edit_node` on prose a sweep has to read first. **That subset was not counted this pass**, and counting it is the obvious next measurement: it is the only remaining agent-repairable share.

**Consequence for this node's own argument.** The relocation chain now ends somewhere concrete. Sight is not the blocker; the write capability is not the blocker; threshold discipline is the blocker; the discipline is reachable for field-less tests only; and the reachable-and-unstarted part of that was 6 nodes, which took one pass. The remaining backlog is either field-carrying (a human's, permanently) or bar-less prose (agent-repairable, uncounted). Neither is the "sight" story this node was created to argue, and the standing `mechanical = 0` finding is untouched — this pass opened 6 more queue entries and found people-or-design questions in every one.

_Method: `Grep` over the vault's own node files for `^type: AssumptionTest` (430), `^threshold:` (313) and the bold `pre-commit` lead-in shape, diffed by hand; plus a first-party `ost_read_repo` of `src/eval/coverage.ts` read in full (`"truncated": false`) to confirm the early-return and the `A_BOUND` word-bars rather than take the section above on trust. Nothing executed — the classifications are read off the regexes, not observed by running them, so a surface with a shell should confirm the rollup's absent count actually fell by 6. Grounds feasibility only; silent on whether anyone wants the queue cleared. Rung stays at the `assertion` floor._

## Refinement to the section directly above, same pass: do NOT go on to rewrite the remainder

The section above ends by naming the next measurement — count the `prose`/`instruction` share of the 111 field-less tests that already carry a lead-in, "the only remaining agent-repairable share." **That framing is wrong in a way worth catching before a future sweep acts on it**, and the correction comes from the same file the section quotes.

**`prose` is deliberately not a defect.** `computeUnfixedThresholds` returns `unfixed: readings.filter(r => r.kind === "instruction" || r.kind === "absent")` — `prose` is excluded on purpose, and `thresholdKindOf`'s own docstring says why: it is "often a perfectly good falsifiable bar written in words ('the piece survives a page reload'), which is why it is not flagged." So a `prose` threshold is a bar a person can judge and a regex cannot, not a bar nobody wrote.

**Two readers disagree, and that is the real finding.** The rollup's "N of M state no fixed bar" line counts `withFixedThreshold = thresholdKindOf(t) === "bound"`, so it counts every `prose` test against the tree. `computeUnfixedThresholds` does not. `confirmPermit`'s `thresholdBound` sides with the rollup. So a well-written word-bar is simultaneously "fine" to one reader and "unfixed" to two others — which means part of the rollup's no-fixed-bar figure is not debt at all, and no amount of editing would honestly clear it.

**What a sweep would actually be doing if it rewrote them.** Adding `at least`/`exactly`/a digit to a paragraph that already states a judgeable bar changes nothing about the test and everything about the count. That is fitting the regex, not fixing the test, and it is the same shape of defect as a red that every question would produce. **So: do not.** The 6 `absent` nodes were worth repairing because they stated their bar in a form no reader could see; a `prose` node's bar is already visible to the reader that matters, which is the person answering it.

**The `instruction` class appears to be empty.** Grepping the vault for a `pre-commit` lead-in followed immediately by any of the 13 `DEFERRING_VERBS` returns **zero files**. Method limit, stated because it bounds the claim: `paragraphAt` joins hard-wrapped lines before matching, so a lead-in whose deferring verb fell on the next line would not be caught by a single-line grep. Read this as "no `instruction`-kind threshold in the common unwrapped form", not as a census.

**Net.** The agent-reachable threshold backlog was the 6 `absent` nodes, and it is now empty. What remains splits into field-carrying (313, a human's permanently) and `prose` word-bars (visible to a human, invisible to the regex, and not this surface's to rewrite). The honest repair for the latter is not an edit — it is a decision about whether the rollup should count `prose` as unfixed at all, which is the operator's call and is already half-stated by the product's own two disagreeing readers.

_Method: first-party `ost_read_repo` of `src/eval/coverage.ts` (read in full), plus one `Grep` over the vault. Nothing executed. Rung stays at the `assertion` floor._

## `mechanical = 0` measured the tests, never the missing beliefs — five counter-instances (2026-08-22 unattended sweep, third firing, repo sight held)

The standing finding classifies queue entries by "what its test could actually measure" and lands `mechanical = 0` at every recount. Every recount asked the same question, and it is the wrong question by one step: **it takes each solution's assumption set as given.** The census opened the tests. It never asked whether the belief a spec *could* settle had been written down at all.

It usually has not. Sampled entries share one shape: **the solution carries exactly one assumption, and it is the desirability or viability one** — the operator's preference, the founder's attention, the buyer's willingness. That single assumption is correctly `humansRequired`, so the entry classifies `people` and the census is right about it. Meanwhile the solution's *mechanical* premise sits unstated in its prose, where no counter can see it, and `solutionsMissingAssumptions` reads empty because "has ≥1 assumption" is satisfied.

The classifier is honest and the tree is what is thin. `assumptionWork` this pass: **0 runnable, 0 awaiting-one-command, 0 blocked-on-permission, 430 needs-humans** — a tree whose every test is a person's, which is not a fact about the world.

Five entries were re-opened and each yielded a mechanical belief nobody had written, now on the tree with a bound threshold and a no-spec instrument (a working permit, per the correction chain above):

| Queue entry | Belief that was missing | Why a spec settles it |
|---|---|---|
| Buckets ordered by branch… | grouping withholds no item the flat listing showed | set equality over a capped listing |
| Append a one-line friction summary… | one completion path exists that can carry the count | where a report is assembled |
| Alert only when friction crosses a bar | the would-have-fired verdict is computable from stored records | parse and label, with a denominator |
| Announce a red-to-green flip… | every landed build is announceable | `transitioned` is false after a no-spec-only history |
| Build dist on its own branch only | no entrypoint runs the bundle without building it | `build-pass.sh`, read this pass |

**The fourth is the one that pays for the exercise.** `verifyInstrument` sets `transitioned` only when `observedRed` matched, and `observedRed` deliberately does not match `**no-spec**`. Since this node's own finding is that no-spec is the *only* red an agent surface can produce, announcing on `transitioned` would be silent for very nearly every build this loop completes — a notification channel that reports nothing and looks healthy. That defect was invisible while the solution's only assumption was about the founder's attention span.

**The bound, stated so this is not over-read.** Five entries is a sample, not a recount, and the standing finding is not refuted: each of these five *still* carries a genuine human ask, and none became buildable. What changed is the accounting. The mechanical half was never absent from these solutions, only unwritten — so `mechanical = 0` should be read as "no queue entry's *existing tests* are mechanical", which is true, and not as "no queue entry has a mechanical half", which these five contradict. A full recount under the second reading is the measurement this node now wants, and it is a different and larger job than the 2026-08-10 census.

**One consequence for the surface.** All five solutions stay in `solutionsMissingInstruments` until something runs `ost-agent verify` on the new tests, and their human asks stay unlaned because `ost_flag_humans_required` is withheld here — so the queue will not appear to move on the next sweep even though five entries now hand a builder a command and a bar.

_Method: `ost_read_tree` on each entry and its assumptions, plus first-party `ost_read_repo` reads of `src/ost/instrument.ts`, `src/eval/buildable.ts`, `src/eval/coverage.ts`, `src/knowledge/instruments.ts`, `src/mcp/server.ts` and `examples/automation/build-pass.sh` (all `"truncated": false` except `build-pass.sh`, read to the report-branch section). Nothing executed; the `transitioned` conclusion is read off the mechanism, not observed. Grounds feasibility only. Rung stays at the `assertion` floor._

## Three more counter-instances, from the founder-theory families the census wrote off (2026-08-22 unattended sweep, fifth firing, repo sight held)

Continuing the third firing's reframe — that `mechanical = 0` measured each solution's *existing tests* and never the beliefs nobody had written. The third firing drew its five from the loop/reporting family, the fourth from unattended-runtime and the `outstandingAsks` queue. This one deliberately went to the families the standing log lists as "already-classified" entrants and has never re-opened: **axiom/goal-acquisition and the altitude branch**. Same result, three for three.

| Queue entry | Belief that was missing | Why a spec settles it |
|---|---|---|
| A proof lane where derivations from declared axioms count as evidence | a rung whose weight is a function of citations can live in a ladder whose consumers read a scalar | `rungRank` returns one integer per id; `weakestRung` is the needed fold and is never called across a citation edge |
| A standing axiom register the human curates | the reverse index revocation needs already exists, minus its keying | `scanExtentOverlap` builds `recordId → citers` and discards it per parent |
| Nested sub-outcomes between the distant goal and the opportunity space | the metric field is the schema change; the nesting is already free | `serialize`/`deserialize` enumerate keys, so an unenumerated `metric:` is dropped on round-trip |

**The third is the one that pays for the exercise**, and it is a correction rather than an addition. That node's own prose calls it "the most invasive option — it changes the schema and every existing node's ladder-up path." The ladder-up path needs no change: `ost_create_node` already lets an Opportunity attach under an Opportunity, and this vault's 37 category buckets *are* an intermediate layer between the root and the needs, in production, today. So a solution has been carrying a self-assessed cost several times its real one since 2026-07-25, and any prioritisation that read that sentence was reading a wrong number. That is a failure mode the census could not have caught, because the node's cost claim is prose and no counter reads prose.

**A second-order consequence worth a human's eye.** That node's Issues section holds an unmerged possible duplicate (sub-outcome versus milestone) and names the deciding question as "whether nesting is meant to be recursive." If recursion is already free, that question does not separate them and the human's decision needs re-framing around the metric field instead. The duplicate stays unmerged — this pass is no more confident than the 2026-08-05 one that they are the same claim.

**The bound.** Three entries is a sample and the standing finding is not refuted: all three still carry a genuine human ask, none became buildable, and none left the queue. What generalises is the accounting — the mechanical half was unwritten, not absent, and that has now held across three separate firings sampling four different families. A full recount under the second reading remains the measurement this node wants.

_Method: `ost_read_tree` on each entry, plus first-party `ost_read_repo` reads of `src/knowledge/believability.ts`, `src/ost/extent.ts`, `src/ost/node.ts` and `src/ost/frontmatter.ts`, all `truncated: false`. `src/processes/tree.js` deliberately not read, so the `claimsStoredEvidence` question is left open on the node rather than guessed. Nothing executed. Grounds feasibility only. Rung stays at the `assertion` floor._

## The commercial family was written off unread — three for three (2026-08-22 unattended sweep, sixth firing, repo sight held)

The standing log records the commercial/pricing cluster as "deliberately not touched" (third firing) and lists it among the already-classified families that new queue entrants land in. It is the largest single family in `solutionsMissingInstruments` and the one the `people` classification is most obviously right about. This firing went there specifically because of that: if the third and fifth firings' reframe — that `mechanical = 0` measured each solution's *existing tests* and never the beliefs nobody had written — is a real finding rather than an artefact of sampling loop-adjacent families, it should hold where it is least likely to.

It held. Three entries opened, three mechanical beliefs missing, each now on the tree with a bound threshold and a no-spec instrument.

| Queue entry | Belief that was missing | Why a spec settles it |
|---|---|---|
| Compete on the vault being plain files… | the *provenance* survives the tool, not just the prose | `source:` pointers resolve into `.ost-agent/`, which Obsidian hides |
| Lead with what this refuses to do… | each claimed refusal is bound to a guard whose removal reddens | the negative half already exists; the positive half does not |
| Charge per assumption test… to a pre-committed threshold | the *ordering* is auditable from the record | `recordResult` never reads the threshold before filing |

**All three have the shape this node's reframe predicts, and each solution carried exactly one assumption, a buyer's.** That is not a criticism of the earlier classification: a census that asks "what could this solution's tests measure" is answered correctly by `people` in all three cases. The beliefs above were not among the tests to be classified.

**The third is the one that pays for the exercise.** `src/ost/results.ts` refuses a blank `by`, a blank `note` and a blank `uncovered`, and argues each refusal in the code — an unattributed result "cannot be told apart from a fabricated one." Its date is `filing.on ?? new Date()...`, caller-supplied and compared against nothing. So the one file in the product most careful about the integrity of a result is silent about whether the bar predates it. That matters beyond pricing: `pre-committed` is load-bearing in the ruleset, in `confirmPermit`, and in every claim this tree makes about not grading its own homework, and nothing anywhere checks it. A pricing node is a strange place for that to surface, which is exactly why nobody had.

**A second finding, smaller and adjacent.** The positioning entry's belief is not speculative — this repository has already shipped the failure it describes. `test/release/withdrawn-claims.test.ts` exists because four operator-facing surfaces, one of them the *generated* `SKILL.md`, carried a false bound-the-damage claim into the model's own context on every pass until 2026-07-29. The guard prevents that claim returning and binds no currently-asserted claim to anything. A product positioned on its refusals has no drift check on the refusals it asserts.

**The bound.** Three entries is a sample, the standing `mechanical = 0` finding is untouched, none of the three became buildable, and all three keep a genuine human ask that is still correctly a person's. What has now held across four firings and five families is the accounting: the mechanical half is unwritten, not absent. A full recount under that reading remains the measurement this node wants, and it is now overdue rather than merely proposed — five families sampled, five hits, zero families where the reframe failed.

**One consequence for the surface, unchanged from the third firing.** All three solutions stay in `solutionsMissingInstruments` until something runs `ost-agent verify`, and their human asks stay unlaned because `ost_flag_humans_required` is withheld here.

_Method: `Read` over the three solution nodes in the vault, plus first-party `ost_read_repo` reads of `src/ost/results.ts` and `test/release/withdrawn-claims.test.ts` in full (`truncated: false`), and listings of `src/`, `src/ost/`, `src/product/`, `test/`, `test/ost/`, `test/eval/`, `test/product/`, `test/release/`, `test/security/`, `test/instruments/` to confirm the three named spec paths are absent. `test/product/committed-capability-profile.test.ts` read in full to confirm it does not already cover the claims-versus-code question. Nothing executed. Grounds feasibility only; silent on whether anyone wants any of this. Rung stays at the `assertion` floor._

## Correction, same firing: the three entries left the queue immediately

The section above ends by repeating the third firing's prediction — "All three solutions stay in `solutionsMissingInstruments` until something runs `ost-agent verify`". **That is wrong, and it was wrong when the third firing wrote it.** Measured on the sweep taken directly after the three writes: the bucket went **71 → 68**, and all three worked entries — "Compete on the vault being plain files…", "Lead with what this refuses to do…", "Charge per assumption test…" — are absent from the new listing, with three previously-hidden entries surfacing into the capped 25 to replace them.

**Why, and it follows from the bucket's own definition rather than from anything new.** `solutionsMissingInstruments` lists solutions whose tests are *prose only*. Each of these three now carries a second assumption whose test names a command, so the solution no longer qualifies. Nothing was verified, nothing was observed, no permit was cleared — the entry leaves on the presence of an instrument, not on a run. The third firing conflated leaving the bucket with clearing the gate, and this firing repeated it uncritically an hour later.

**What it changes for a future pass.** The repair path this node has been arguing about is visibly self-scoring: writing the missing mechanical belief moves the counter the same firing, so a sweep can tell whether it made progress without waiting on a human. That cuts against the standing "write nothing" advice more than anything else in this node's chain — the earlier reason for it was that a blind pass produces vacuous artefacts, which remains true; "and it will not move the queue anyway" was never true and should not be cited again.

**The bound.** Three entries, one observation, one sweep. It does not follow that the third firing's five also left — that was not checked, and the count between those firings moved for other reasons too. Anyone re-reading this should recount rather than infer.

_Method: `ost_next_work` before and after the three writes in one firing, listings compared by hand. First-party observation of this product's own sweep output. Nothing executed. Rung stays at the `assertion` floor._

## Bound on this firing's own claim: the harness family is where the reframe fails

The commercial-family section above closes with "five families sampled, five hits, zero families where the reframe failed." Before reporting that, this firing tested it against the family most likely to break it, and it broke. The claim should read *five of six*.

**The family.** The Monitor/harness entries — "Monitor states its accepted command grammar up front rather than discovered by refusal", "Monitor accepts a vetted until-loop primitive instead of raw shell polling", "A background task's own output directory is automatically readable by the Monitor call that started it". Read this pass: the first is four lines long and asks that Monitor "surface its constraints in its own tool description or a preflight probe."

**Why there is no mechanical half to write.** The subject is a tool description belonging to the harness. No spec in this repository can assert what Claude Code's Monitor tool documents, and one that tried would be asserting a fact about a dependency the suite does not own — a green that means the fixture was written correctly and nothing else. Unlike the commercial entries, where the unwritten belief was about *this* product and simply nobody had written it, here the belief is about someone else's product and this repository is the wrong place to hold it. The existing `humansRequired` framing is correct, and these entries should be read as permanently non-mechanical rather than as unrecounted.

**The distinction worth carrying forward,** because it makes the proposed full recount cheaper: the reframe finds a mechanical half when the solution's premise is a claim about **this** product's behaviour, however commercial the solution sounds. It finds nothing when the premise is a claim about an external dependency, however technical the solution sounds. Sorting the queue on that question first would skip the families that cannot pay.

**One adjacent thing this firing declined to do.** These transcripts' friction — compose, get refused, retry — is arguably answerable here, via whatever carries a recorded correction into the next composing session. That belief belongs beneath the corrections solution, not beneath a Monitor-documentation solution, and filing it here to make a family produce a hit would be the exact defect this node's chain keeps catching. Left for a pass working that branch.

_Method: `Read` of the solution node in the vault; no repo read was needed, because the subject is not in the repository. Rung stays at the `assertion` floor._

## The queue's real blocker, measured with repo sight (unattended sweep, 2026-08-22)

This node carries the tree's census of `solutionsMissingInstruments`, so the finding belongs here. Six passes reported repo sight dead and declined to instrument; this firing had it, and what it found is that sight was never the whole blocker. The write boundary's own rules are, and they are stateable exactly.

**The three rules, read first-party from the code this pass:**

1. **One form, anchored.** `INSTRUMENT_FORMS` in `src/knowledge/instruments.ts` accepts `npx vitest run <path>.test.ts` and nothing else, and `SHELL_METACHARACTERS` rejects quotes, `-t` filters, and every other punctuation mark on sight. A test whose question needs a named case within a spec file cannot be expressed at all.
2. **A path that does not resolve is refused** against `product.repos` (`specResolves`), at both write boundaries.
3. **Unless the test carries a *bound* threshold.** That is the deliberate escape for genuinely new behaviour: `test/instruments/spec-path-resolution.test.ts` accepts "at least 5 of the 20 replayed sessions are refused" and refuses "the resolver feels correct to whoever reads it", which `thresholdKindOf` reads as `prose`.

**The consequence nobody has written down, and it explains the whole backlog.** Put those three together against a legacy test — prose question, no bound bar — and there is no honest instrument that can be set on it *in place*:

- A new spec path is refused, because the bar is not bound.
- An existing spec path is accepted, and is then almost always the wrong answer: the suite is green, so `verifyInstrument` meets a first-run green and refuses to record it, by the red-before-green rule. The instrument field would be written and could never produce an observation.
- And **no tool on any agent surface can bind the bar**. `threshold` is an argument of `ost_create_node` only; there is no `ost_set_threshold`, and `MCP_TOOL_NAMES` has no equivalent. (Whether the CLI offers one was not checked — `src/cli/index.ts` is 141KB and exceeds this surface's read cap. A human should confirm before treating this as closed.)

So the instruction each sweep is given — "re-write those tests rather than adding more" — is, for the un-barred class, not expressible with the tools the sweep holds. The only legal move that produces a runnable question is to create a *new* test carrying a bound bar, which is the thing the instruction forbids. That is a genuine contradiction between the ruleset and the write boundary, not a pass declining work, and it is why the queue has not moved.

**What that implies for the 68.** Read alongside the answer recorded on "What is in the 33 queue entries no tool has ever listed" — `mechanical` = 0 of 33 in the unlisted tail — the queue is mostly work no exit code can settle, and its residue is mostly work no agent tool can re-bar. Both halves point at the same repair, and it is to the queue rather than to any solution beneath it.

**One entry was paid off this pass, to show the escape works.** A feasibility assumption was surfaced beneath this node — "The write boundary can refuse a blind instrument without refusing every instrument" — and its test carries a bound bar and a new spec path, accepted by rule 3. It is red for a reason specific to itself: `test/instruments/spec-path-resolution.test.ts` asserts the *opposite* behaviour under "with no product repo configured, the guard stands down". That is the shape a grounded instrument takes here, and it took repo sight to write.

**A gap in this firing's own surface, recorded because it is not a choice this pass made.** `ost_flag_humans_required` is withheld from the unattended sweep. So for a queue entry whose test genuinely needs a person — which the census says is most of them — this pass can neither instrument it nor label it into the humans-required lane. It can only write this. A surface that is told silence is unacceptable and is given no way to say "a person is the measurement" will keep producing notes like this one.

_Method: `ost_read_repo` over `/Users/tanner/dev/OST-Agent` — `src/ost/instrument.ts`, `src/knowledge/instruments.ts`, `src/mcp/server.ts`, `test/instruments/spec-path-resolution.test.ts`. No command was run and no result recorded. First-party; rung unchanged at the floor._

## Definition of done

"A blind set-instrument call is refused, while a sighted one on the same vault still writes"

```
npx vitest run test/instruments/blind-instrument-refusal.test.ts
```

Named in plain text rather than linked: the test's one backlink belongs to its parent assumption, and a second would break the single-backlink rule. This covers the feasibility half only — the desirability half beneath "Operators would rather have honest gaps than guessed commands" still needs a person, and green here is not evidence for it.
