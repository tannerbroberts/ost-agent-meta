---
type: AssumptionTest
source: 'agent-run:unattended-sweep-2026-08-28'
created: '2026-08-29'
evidence: assertion
lane: humans-required
threshold: >-
  at least 1 wait form that blocks on job exit is confirmed accepted on the
  unattended surface
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: humans-required.**

Put the question to someone with the Monitor tool's implementation, or this vault's surface profile, in front of them: *is a wait that blocks on a job's exit — a PID wait, or the background-task handle returned when a command is started with `run_in_background` — accepted on the unattended surface, or refused the way `until … done` polling and `command_substitution` are?*

**Pre-committed bar.** The threshold above is the whole verdict: one confirmed-accepted exit-blocking form supports the assumption; none refutes it. A "probably" is `inconclusive`, not support — the point of asking a person who can read the grammar is to get an answer better than the one composing a command and seeing what happens would give.

**Why this is not the ask already on the queue.** `outstandingAsks` carries "Ask someone with the Monitor tool's implementation open whether a bounded until sleep primitive is addable without reopening arbitrary shell execution". That one asks whether the grammar can be **extended** to admit a new polling primitive — a change to the harness. This one asks whether the grammar **already admits** a form nobody here has tried, which needs no change to anything and is answerable by reading rather than by deciding. Same person, same artefact, opposite direction, and this one should be cheaper. Whoever picks up either should answer both in the same sitting; they are asked separately because they can come back with opposite verdicts.

**What a result here does not settle.** Only permission. It says nothing about whether an accepted form reports liveness, which is the sibling candidate's question, and nothing about how much of this loop's waiting is on harness-tracked work, which is the other sibling's. A `supported` verdict here narrows the branch sharply; it does not close it.

**Why no instrument.** Recorded in this node's humans-required reason: the deciding artefact is not in this repository, so no exit code available here can answer it. That is a genuine lane, not a skipped step.

**Lane note for a human:** created in the humans-required lane at creation time. `ost_flag_humans_required` is withheld on the unattended surface, so if the lane ever needs changing it is `ost-agent lane --set`.

A person outside the building is the measurement here: The artefact that decides this is the Monitor tool's own permission grammar, which lives in the harness and not in this repository — no spec under `test/` can reach it, and probing it by composing candidate commands would answer only "this exact string was refused today", which is the discovery-by-violation this tree already records as the failure mode. It needs a person who can read that implementation, or the person who owns the surface profile, to say what the grammar admits.
