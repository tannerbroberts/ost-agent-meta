---
type: AssumptionTest
source: 'agent-ideation:2026-08-20-unattended-sweep'
created: '2026-08-20'
evidence: assertion
lane: humans-required
threshold: >-
  At least 4 of the next 5 builder-filed disconfirmations are judged by the
  operator, spec open, to be genuine refutations rather than an unfinished build
  described as one
---
#AssumptionTest #unvalidated #evidence/assertion

**The procedure.** Once the disconfirmation channel exists, the operator reads each of the first five it carries with the spec and the recorded numbers open, and answers one question per entry: is the red a refutation of the pre-committed bar, or a build that did not finish wearing a refutation's vocabulary? Record the tally.

**Lane: humans-required.**

**Pre-committed reading.** 4 or 5 of 5 supports the assumption and the channel is worth reading. 3 or fewer refutes it: the channel is noise a human must re-check every time, which is the state the report file is already in, and the counting sibling beneath the same opportunity should carry the need.

**Until the channel exists.** This test cannot start; it is listed so that a builder who ships the channel knows what the first five entries are for. The one already-recorded instance (PR #130, "fails by design and should not be loosened") is not counted — it was written before anyone was watching for this.

**What this does NOT settle.** Five entries from one builder on one repo says nothing about a different model or a different codebase, and honesty on five is not honesty under pressure on the fiftieth.

**Recording.** `ost-agent result "<this title>" -v <supported|refuted|inconclusive> -n "<tally and which entries>" -b <operator> -u "<what the five did not cover>"`.

A person outside the building is the measurement here: Whether a builder's stated reason for a red is honest is a judgement a person makes by reading the spec and the numbers; no exit code holds it.
