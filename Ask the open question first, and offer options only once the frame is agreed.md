---
type: Solution
status: deferred
source: 'agent-ideated:2026-08-04-unattended-sweep-question-shape'
created: '2026-08-04'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The run's proposed options are wrong often enough that framing first saves turns rather than costing them]]

Split the ask in two. The run first states what it is uncertain about in open form — "I don't know what the appended tests should be allowed to do to the build gate" — and lets the operator set the frame. Only then, with the frame in the operator's words, does it offer concrete options, which are now guesses inside a shape it did not invent.

**Compared to the alternatives.** This is the only candidate that treats the diagnosis seriously: the observed failure was not a bad reply channel, it was a question asked before the run understood what the question was. Framing first is also the most honest about the run's actual state — it says "I am uncertain" rather than performing a confident menu. Its cost is the obvious one: two exchanges where the current design attempts one, so it is strictly worse in every case where the run's first guess would have been right.

**What would make this the wrong pick.** If the run's options are usually correct, this trades a rare three-turn failure for a routine two-turn tax, and the arithmetic goes the wrong way. The recorded session shows two questions rejected; it does not show how many were accepted, so the base rate this depends on is precisely what nobody has measured.

⚠️ Unvalidated. Proposed by an unattended pass from one observed session.

## Definition of done

"Replay the recorded question sessions and count whether framing first adds stops or removes them"

```
npx vitest run test/loop/two-stage-question-stop-count.test.ts
```

Green means the two-stage form costs no more operator turns on the recorded history than the one-stage form did — the arithmetic this candidate depends on, computed rather than assumed. It does not settle whether framing first produces better decisions, only cheaper ones.

## History
- 2026-08-05 unlinked "Replay the recorded question sessions and count whether framing first adds stops or removes them" — moved under "The run's proposed options are wrong often enough that framing first saves turns rather than costing them" — the belief this test measures now has a node of its own
- 2026-08-16 status: (none) → deferred — Its own instrument (test/loop/two-stage-question-stop-count.test.ts, "Replay the recorded question sessions and count whether framing first adds stops or removes them") was run by the build loop against real harvested history: two-stage framing costs 92 operator turns vs one-stage's actual 72 across 46 recorded questions — only 28% reframed, well below the ~50% breakeven the arithmetic needs. Build report (INBOX:2026-08-16-build-loop-stuck-ask-the-open-question-first-and-offer-options-only-once-the-.md) confirms tsc clean, full suite green except this designed-to-fail assertion, PR #130 not expected to merge. Deferring per the evidence rather than leaving it live for the build loop to keep retrying — a human should still decide whether to close PR #130 and whether the underlying belief ("The run's proposed options are wrong often enough that framing first saves turns rather than costing them") needs reframing instead.

## Second build attempt, also failed (unattended sweep, 2026-08-19)

`INBOX:2026-08-16-build-loop-stuck-ask-the-open-question-first-and-offer-options-only-once-the-.md` records a second consecutive build-loop firing failing to ship this solution, with its own node file unchanged in between — the loop is re-reasoning about the same unresolved definition each time. The report: the assumption instrument (`src/loop/questions.ts` STOP_COUNT_RULE/stopCount/sessionStopCount) was already complete on branch `two-stage-question-stop-count` (PR #130, not merged) from a prior interrupted pass. Replaying 11 harvested sessions, the loop's own finding is that the solution is falsified by the data it was meant to be judged against: two-stage cost 92 operator turns against one-stage's actual 72 across 46 recorded questions, only 28% reframed (well below the ~50% breakeven the arithmetic needs), and only 1 of 11 sessions favors two-stage. `tsc` clean, full suite green except the one assertion this instrument makes, which fails by design. The build loop's own recommendation: record the solution as disproven.

This corroborates the `status: deferred` this node already carries — a second independent replay reached the same falsification the first one did, not a new finding requiring a different disposition. No action beyond this citation: promotion/disposition changes stay a human's call, and this node is already correctly deferred.

_Source: `INBOX:2026-08-16-build-loop-stuck-ask-the-open-question-first-and-offer-options-only-once-the-.md` — observed, an exit code the loop watched. Corroboration only; status and evidence rung unchanged._

## Third build attempt, also failed (unattended sweep, 2026-08-19)

`INBOX:2026-08-19-build-loop-stuck-ask-the-open-question-first-and-offer-options-only-once-the-.md` records a third firing landing on the same diagnosis: nothing to build (already shipped as PR #171, distinct from the earlier PR #130), `tsc` clean, vitest red on exactly the one pre-committed assertion — two-stage framing costs 92 operator turns against one-stage's actual 72 across 46 recorded questions. The build loop's own report is explicit that this is now the third time this identical diagnosis has been produced (#130, a note in between, now #171), because — in its words — "the vault node was never updated after the first two runs to reflect that the assumption failed."

That claim does not match this node's own History: `status: deferred` was set on 2026-08-16, citing this exact falsification. The build loop is either re-selecting a `deferred` node into its build queue regardless of status, or reading a stale copy of this node. Either is worth a human's attention on its own — a build loop that keeps re-deriving a result the tree already recorded is spending build cycles a `deferred` filter should have prevented.

No disposition change: this node is already correctly deferred, and a third independent replay reaching the same falsification is corroboration, not new information about the solution itself.

_Source: `INBOX:2026-08-19-build-loop-stuck-ask-the-open-question-first-and-offer-options-only-once-the-.md` — observed, an exit code the loop watched._

## Issues
- 2026-08-19 2026-08-19: build loop re-selected this deferred solution as a target a third time (after #130 and the 2026-08-16 note, now #171) and re-derived the same falsification the first run already recorded. Deferred status did not stop it from being re-selected — worth a human checking whether the build loop's target-selection logic actually excludes `deferred` nodes.
