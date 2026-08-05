---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Check whether naming the acceptable rung leads callers to take it without new grounds]]

Since the tool knows enough to refuse, it usually knows enough to say what would have been accepted. A rung refusal names the highest rung this source can carry. A hierarchy refusal names the layers this parent will take. A reserved-heading refusal names the headings that are free. One round trip, and the caller has the answer rather than a diagnosis.

The tree's own trace shows the difference this makes. The three failed calls on 2 August each carried a long explanation of why `stated` was unavailable; a caller who had been told `assertion` was the ceiling would have needed one call, not two.

**Compared to the alternatives.** Cheap, entirely local to each refusal, and it cannot drift out of sync the way a published schema can, because the answer is computed by the same code that refused. It still costs the failed call, which published preconditions would have avoided altogether, and it only helps a caller who was close to right.

**What would make this the wrong pick.** Suggesting the acceptable value invites the caller to take it without thinking. A rung refusal that names the ceiling is one keystroke from a caller declaring the ceiling reflexively, which is the ladder being climbed by autocomplete rather than by evidence.

## Definition of done

[[Check whether naming the acceptable rung leads callers to take it without new grounds]]

```
npx vitest run test/telemetry/rung-suggestion-reflex.test.ts
```

Red today for two compounding reasons: the refusal does not name the acceptable ceiling yet, so there is no suggestion to be taken reflexively, and nothing pairs a refused call with the retry that followed it — the trace stores calls, not call sequences. Green means at most 5 of 20 retries adopt the named rung with the justification unchanged from the refused attempt.

Read the green narrowly. Taking the named ceiling is often correct, because it may be the honest rung; separating a reflexive acceptance from a right one means reading the justification, which is a judgement. **This command produces the flag, never the verdict** — and a solution whose whole risk is that a helpful message becomes an autocomplete is one where mistaking the flag for the verdict is the specific way a reader gets it wrong.
