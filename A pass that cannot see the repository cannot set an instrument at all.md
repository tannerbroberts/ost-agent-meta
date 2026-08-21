---
type: Solution
source: 'agent-ideation:2026-08-07-unattended-sweep'
created: '2026-08-07'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Operators would rather have honest gaps than guessed commands]]
[[What is in the 33 queue entries no tool has ever listed]]

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
