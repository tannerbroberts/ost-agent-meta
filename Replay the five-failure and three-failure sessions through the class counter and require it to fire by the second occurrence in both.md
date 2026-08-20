---
type: AssumptionTest
source: >-
  agent-ideated:2026-08-20-unattended-sweep — the mechanical half of "Apply the
  escalating message to the five-failure session and check where it would have
  fired", split out so one lane answers one question
created: '2026-08-20'
evidence: assertion
threshold: >-
  Against fixtures carrying the tool_error sequences of
  TRANSCRIPT:a615eb46-cc50-41a9-a77f-931c0dc67db0 (five `(eval):1: == not found`
  in a row) and TRANSCRIPT:b7aae32d-150a-462f-9027-cdf7af12badd (the same
  failure three times), the counter places every failure in one class and the
  escalated message — leading with the count and quoting the first correction —
  appears on the SECOND occurrence in both replays. A control fixture
  interleaving two genuinely different classes (a zsh `== not found` and a `File
  has not been read yet` guard refusal) never escalates across classes.
instrument: npx vitest run test/loop/repeat-class-escalation.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Kind: feasibility.** The replay half of the belief beneath it: that failures arriving minutes apart in one session can be grouped into a class mechanically, and that a counter over that grouping fires on the second real repeat — not the first, and not never.

**Lane: compute-only.**

**What the spec asserts.** Feed the counter the two recorded sessions as fixtures (the same shape as `test/fixtures/corrections/`, which already carries seven transcripts in JSONL), and assert three things: (1) all five `== not found` failures in `a615eb46` land in one class, and the message returned for the second carries the occurrence count and quotes what was said for the first; (2) the same holds at occurrence two of three in `b7aae32d`; (3) a fixture that alternates a zsh dialect failure with a read-before-write guard refusal produces two classes and no cross-class escalation — the cry-wolf case the assumption names.

**Why it is red today, and which kind of red.** Read against the repository this pass: `src/loop/corrections.ts` is the only module that groups repeated errors, and it is built for the opposite problem — it keys on the *permitted form* of a guard refusal, runs across *finished* sessions after a quiet window, and explicitly drops a command that merely exited non-zero ("a failure, not a correction"). The five `(eval):1: == not found` failures are exactly that dropped shape, and they are in one live session, so no current code path can count them. The spec file does not exist yet either, so this is filed honestly as a **no-spec red**: the module that would have to exist is named, the assertions are stated, and the builder's job is the spec plus the in-session counter it exercises — not "create this file".

**What a green does not settle.** That a caller shown the escalated message changes approach. That is the other half of the belief, and it is "Show the escalated message to five fresh sessions facing the same failure and count which change approach", which needs people and is laned accordingly. A counter that counts correctly and changes nobody's behaviour leaves the solution unproven.
