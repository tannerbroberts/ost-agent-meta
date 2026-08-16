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
