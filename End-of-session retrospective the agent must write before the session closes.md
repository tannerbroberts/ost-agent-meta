---
type: Solution
source: 'agent-ideated:2026-08-02-maintenance-pass-2'
created: '2026-08-02'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Check three past pass notes for the wrong turn they left out]]

**The idea.** Before a session ends, the agent writes one short structured retrospective: the wrong turn it took, roughly what that turn cost, and what it would have needed to know at the start to avoid it. Not a summary of what it did — a confession of where it was confused. It lands in the inbox like any other evidence item, with the session id as provenance.

**Why this is not [[In-the-moment friction events filed by the agent]].** That sibling fires at the moment of pain, which is exactly when a conceptual mistake is invisible: an agent halfway down a wrong framing does not know it is on one, and the thing it would file is "this is going fine." Conceptual friction is only legible *after* the reversal — the moment you discover the approach was wrong is the moment you can name it. In-the-moment filing catches surprises; a retrospective catches misconceptions. They are complementary, not redundant, and the census on the parent argues for both: 82 mechanical events in 24 sessions, and not one of them is a misconception.

**The obvious weakness, stated up front.** This is self-report by the party whose confusion is being reported, at the end of a session it wants to declare successful. Every known bias runs the wrong way: retrospectives will under-report, will be written to look competent, and will be thinnest exactly in the sessions that went worst. Compare that against its one real advantage — it is the only mechanism here that has access to *why* the agent believed what it believed, which neither an outside reader nor an artifact scan can recover.

**Second-order cost worth weighing against the alternatives.** It spends tokens in every session, including the many where nothing conceptual went wrong, and it produces one more item for a mapping pass to disposition. The channel's current problem is not volume — 82 events already arrive and none of them is useful. A retrospective that mostly says "nothing notable" makes that worse, not better, so the design question this candidate has to survive is whether it can stay silent credibly.

⚠️ Unvalidated. Agent-ideated during the 2026-08-02 maintenance pass, from this vault's own session census. No human has reviewed it and no test has been run.

## Definition of done

[[Check three past pass notes for the wrong turn they left out]]

`npx vitest run test/adapters/session-retrospective.test.ts`

The spec asserts the design question the node says this candidate must survive — whether it can stay silent credibly. A session with nothing conceptual to report produces **no inbox item**, not a "nothing notable" one; a retrospective that is written lands with the session id as provenance and enters at the `assertion` floor as self-report. Both halves matter: the channel's problem is not volume but that 82 events already arrive and none is useful, so a mechanism that adds a mostly-empty item per session makes it worse. Red today because nothing is required before a session closes.

**What a green here does not settle, and every bias runs the wrong way.** This is self-report by the party whose confusion is being reported, at the end of a session it wants to declare successful. Retrospectives will under-report, will be written to look competent, and will be thinnest exactly where the session went worst — a spec can force the field to exist and cannot make it honest. Reading three past pass notes for the wrong turn they left out is the humans-required check, and it is the only thing that would catch a fluent, silent omission.
