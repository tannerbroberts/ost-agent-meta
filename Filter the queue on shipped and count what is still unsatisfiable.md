---
type: AssumptionTest
source: 'agent-run:autonomous-loop-2026-08-06'
created: '2026-08-06'
evidence: assertion
threshold: >-
  No solution with status `shipped` appears in `solutionsMissingInstruments`,
  and of the entries that remain, at most 10% are ones no spec file could ever
  settle.
instrument: npx vitest run test/ost/instrument-queue-excludes-shipped.test.ts
---
#AssumptionTest #unvalidated #evidence/assertion

**Who runs it.** An attended session with a build environment, or a human. This pass could not set a lane label — that is a human's `ost-agent lane --set`.

**What this measures.** Build a fixture tree carrying solutions in each status, including shipped ones with prose-only tests and market-shaped ones whose claims are about pricing rather than mechanism. Run `computeNextWork` over it. Assert two things: no `shipped` solution appears in `solutionsMissingInstruments`, and the entries that survive are ones a spec file could actually settle.

**The bar, pre-committed.** Zero shipped solutions in the queue, and at most 10% of the remainder unsatisfiable-by-any-spec. The second half is the real test: it is what tells the difference between fixing a fifth of the problem and fixing it.

**Why it is red today.** The exclusion does not exist. This pass read the live queue and found "A result must state what it did not cover", "Post-session transcript harvester", "Refuse a proving command whose exit code cannot report failure", "Refuse a wiki-link that contains a newline" and "Refuse a write whose content is empty or literally undefined" in it, and grepped the vault to confirm all five carry `status: shipped`. A spec asserting their absence fails against today's code for the strongest available reason: the behaviour is observably not there, not merely unimplemented in a file nobody has written.

**What a green run does NOT settle.** It says the queue no longer lists shipped work. It says nothing about whether `status: shipped` was set truthfully — that field is written from prose by a human or an agent and is verified against the repository by nothing, so a solution marked shipped in error vanishes from the queue silently and this test passes anyway. It also says nothing about whether the operator wanted a draining queue rather than a queue that asks shipped work for something else; that is desirability and no spec touches it.

## History
- 2026-08-06 body edited — The body declared "Lane: compute-only", which this pass had no power to set — `ost_flag_humans_required` is withheld on this surface and only a human's `ost-agent lane --set` moves what compute may run. The node carries no `lane:` field, so its effective lane is needs-humans (confirmed: it landed in `assumptionWork.needsHumans`), and the prose contradicted that. Replaced with the vault's established "Who runs it" phrasing, which describes without claiming.

## Instrument Log
- 2026-08-06 **red** (exit 1) `npx vitest run test/ost/instrument-queue-excludes-shipped.test.ts` — No test files found, exiting with code 1

## A hand count of the queue's composition — unattended sweep, 2026-08-06

This test asks what is left in the instrument queue once shipped solutions are filtered out. A pass instructed to work that queue counted it by hand instead of instrumenting into it. **Not a recorded result** — this test's instrument is unrun, no verdict is recorded, and nothing here moves a rung or a gate. The numbers are a census of node frontmatter and bodies, offered so the threshold has a real denominator when someone does run it.

**The queue on this date: 63 solutions, 25 shown.** Of the 25 shown, 11 were inspected individually. **None of the 11 could carry an honest red-now instrument**, for two structurally different reasons.

**Reason 1 — shipped, so red-now is impossible by construction (5 of the 25 shown).** A `status: shipped` solution describes behaviour that exists; a spec asserting it passes on the day it is written, so it cannot fail and measures nothing. These five are in the queue with `status: shipped` already set in frontmatter: "Refuse a wiki-link that contains a newline", "Refuse a write whose content is empty or literally undefined", "Refuse a proving command whose exit code cannot report failure", "Post-session transcript harvester", "A result must state what it did not cover".

A grep of the whole vault finds **exactly 10 nodes with `status: shipped`**, and the other five are also solutions of the same vintage — "Every self-observation channel names which of its sources each item came from", "Every count states the denominator it was taken over", "Every recorded step carries the directory and argv it actually ran with", "Flag a threshold that is still an instruction to choose one", "The uncovered statement printed next to what the test asked for". So the shipped contamination of the full 63-item queue is bounded above by 10, i.e. **at most ~16%**, and 5 of those 10 are confirmed present in the visible quarter of the list.

**Reason 2 — the load-bearing assumption is about a person, not the code (6 of 6 non-shipped nodes inspected).** This is the larger finding and this test's framing does not currently anticipate it. Filtering on `shipped` would remove at most 16% of the queue; it would leave behind a majority whose single Assumption child is a claim about what a human wants, notices, or will pay for. A spec file cannot settle one, and writing one would assert that a passing test proves somebody valued something. Every non-shipped solution opened this pass was of this kind:

| Solution | Its one Assumption child | Who is the measurement |
| --- | --- | --- |
| Rendered tree view with diff since last visit | A rendered tree orients a reader faster than the files do | a reader |
| Remote push optional and off by default | Operators get real value with the vault staying entirely local | operators |
| Nested sub-outcomes between the distant goal and the opportunity space | Two practitioners place the same opportunity under the same sub-outcome | two practitioners |
| Scheduled ambient passes that page the operator only at hard gates | Two unattended weeks produce few enough pages, and little enough grind, to be worth the spend | a real two-week spend |
| Route view showing the shortest credible path from here to goal-achieved | Seeing a path instead of a taxonomy changes which work a builder starts on | a builder |
| Real-world signal gates outcome achievement | Teams can define an external signal that decides whether their outcome was met | teams |

Reading the other 14 titles shown supports the same shape without their nodes being opened: 13 of them are pricing, cohort, interview, publishing or side-by-side-comparison candidates — "Charge for the maintained tree", "Charge per assumption test designed and run", "Concierge design-partner cohort", "Continuous story-based interview habit", "Instrumented public trial with a willingness-to-pay probe", "Offer to run one free tree for a stranger's product", "Run both for two weeks on the same evidence and publish what diverged", and so on. Willingness to pay and whether a stranger's result travels are not exit codes.

**So the queue's real composition, on this sample, is roughly: a small shipped fraction that is unsatisfiable because the work is done, a large human-irreducible fraction that is unsatisfiable because a spec is the wrong instrument, and a small remainder that is genuinely feasibility-shaped.** The threshold on this test should probably be restated to count three classes rather than two, because filtering on `shipped` alone would leave the queue looking actionable when most of what remains still is not.

**Why the correct disposition was unavailable to this pass.** For the human-irreducible class the sanctioned action is `ost_flag_humans_required`, which moves the test out of compute's reach and is the legitimate outcome rather than a skipped step. That tool is **withheld from the unattended surface by design**, so this pass could name the class but could not label a single member of it. The consequence is that the six nodes above stay in the queue looking runnable, and the next unattended pass will be handed the same list with the same instruction.

**One more reason not to instrument into this queue,** already recorded on "Most opportunities the sweep calls underserved are categories whose children are already served": an instrument does not make work compute-runnable, because tests without a `lane:` land in `assumptionWork.needsHumans` regardless. So even a correctly-written instrument here would not grow the compute-only lane, and today that lane is empty — `runnable: []`, with all 319 tests waiting on a person.

_Method: `ost_next_work` for the queue, a vault-wide grep of `status:` frontmatter for the shipped count, and direct reads of 11 of the 25 shown for their Assumption children. `ost_read_repo` and direct reads of the product directory were both unavailable, so no claim here rests on the code — see "The agent's repo sight fails mid-pass, because nothing checked the product path before it was needed". No test was run._
