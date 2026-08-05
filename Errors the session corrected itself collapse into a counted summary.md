---
type: Solution
status: unvalidated
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Blind-rate ten records as typo or friction and compare against the recovery rule]]

Judge an error by what happened next. If the session recovered within a turn or two and carried on, it is a typo and belongs in a summary line; if it changed what the session went on to do, cost it several attempts, or ended the work, it is friction and gets a record.

**Compared with the alternatives:** this is closest to what a human means by friction — the cost, not the error — and it needs no judgement about which tools count. It is also the most inferential: recovery has to be detected from what follows in the transcript, and it will misread a session that quietly gave up on something as a session that recovered cleanly. That is the same blind spot the tree already names under "The friction that matters leaves no error behind", so this candidate is strongest paired with something that can see silent abandonment.

Unvalidated, agent-ideated: a candidate for comparison, not a recommendation.

## Definition of done

[[Blind-rate ten records as typo or friction and compare against the recovery rule]]

`npx vitest run test/adapters/friction-recovery-rule.test.ts`

The spec asserts the rule judges by what happened next rather than by the error itself: recovered within a turn or two collapses into a counted summary line; changed the session's direction, cost several attempts, or ended the work gets its own record. Red today because the harvester emits every `tool_error` as a flat event with no recovery classification — which is exactly why 24 sessions produced 82 undifferentiated items.

**What a green here does not settle.** Whether the rule agrees with what a person means by friction — that is the blind rating, and it is the test. The node also names its own blind spot, which no spec can close: recovery is inferred from what follows in the transcript, so a session that *quietly gave up* on something reads as a session that recovered cleanly. That is the failure already recorded in this tree as "The friction that matters leaves no error behind", and it means a passing suite here would report clean recovery for precisely the sessions that went worst.
