---
type: Solution
status: unvalidated
source: 'TRANSCRIPT:89ac8277-29ce-4d80-827e-cefea0bebabf'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[The measurement and the criterion, side by side, are enough to tell noise from regression]]

**The idea.** A wall-clock gate asserts one thing today: `measured < BUDGET`. That single comparison cannot separate "the code got slower" from "this box is slower", so every failure is arguable and the cheapest reading always wins. Make the gate print, and assert against, a second number it already has access to: the figure the criterion recorded when it was last met. Then a failure says which of the two it is — `1,603ms measured, 620–750ms recorded at Z3, budget 2,000ms` names a 2.4x regression, and `900ms measured, 620–750ms recorded, budget 2,000ms` on a slow runner names a slow runner.

**Why this, rather than raising the budget or calibrating the machine.** Both of those were the obvious moves and both are wrong here. Raising it launders the regression the gate was built to catch. Calibrating against a synthetic baseline measures a CPU loop that has nothing to do with the workload. The recorded figure costs nothing to consult — `docs/reference/v1-readiness.md` already carries it, in prose, updated by hand whenever a criterion is closed — and it is the only number in the system that says what the code *used to* cost.

**What it is worth, measured on this repository (2026-08-06).** The Z3 budget gate failed six CI runs out of six across three days, on `main` as well as on branches, at 2,045–2,183ms against a 2,000ms budget. It was read as a flaky timing test every time, twice into this vault's friction inbox on 08-01. The real answer was three `tree.filter(...)`-per-node scans in `checkInvariants` added by the 08-05 tree-rule work — 44% of all CPU, `ost_next_work` 620ms → 1,603ms — and a five-minute profile named it. What made it invisible was not difficulty: local runs still passed at 1,600 of 2,000ms, so nobody developing against it saw anything, and the one comparison that would have settled it in a minute (measured against recorded) was available all week and nobody made it.

**The trade.** The recorded figure is prose maintained by hand, so this gate is only as honest as the last person who closed a criterion — and a stale recorded number produces a false alarm rather than a silent miss, which is the right direction to fail but is still noise. It also cannot be asserted tightly: machines legitimately differ by 2–3x, so the useful bar is a wide one (fail when measured exceeds recorded by more than ~2x, whatever the budget says), which catches step-changes and not slow creep.

**Where it sits.** This is the machine-vs-me confusion the parent opportunity names, in the one place the system already has both numbers. It generalises past perf: any gate with a recorded figure — node counts, spend, coverage — can report the same pair.

## Definition of done

A committed spec, `npx vitest run test/release/perf-drift.test.ts`, that reads Z3's recorded figures out of `docs/reference/v1-readiness.md`, runs the same benchmark the budget gate runs, and fails when the measured figure exceeds the recorded one by more than the stated multiple — with the failure message carrying all three numbers. Red today: the file does not exist. That is the weaker of the two red forms (missing spec, not failing assertion), and it is named here rather than left to be discovered.

## Provenance

Written by the session that made the mistake, immediately after fixing it (`perf(invariants)`, 2026-08-06). The measurements quoted are from that session's own profile and from the six CI runs on PR #64.

## Issues
- 2026-08-06 unresolved-citation (flagged by ost_check): frontmatter cites `TRANSCRIPT:89ac8277-29ce-4d80-827e-cefea0bebabf`, and no record under `.ost-agent/evidence/` carries that id. Same fault, same missing id, on four nodes created in one sitting; the full diagnosis and the check that would settle it are recorded on "A guard derived the rule it was checking, so it agreed with the bug for 23 releases". Until it is settled, treat this node's evidence rung as unsupported: a citation that resolves to nothing is the same as no citation.

## Definition of done

"Replay recorded perf failures with the pair alone and check whether they separate"

```
npx vitest run test/eval/perf-gate-noise-band.test.ts
```

Red today: the spec and the fixture of cause-labelled failures do not exist.

Read this one as a falsification rather than a build target. The spec is designed to show that the two numbers this solution renders are *not* enough — if it comes out red on the pair and green on the pair-plus-spread, the correct response is to rewrite this node around the spread, not to declare the solution built. A builder who makes the command pass by rendering the pair more prettily has confirmed nothing.
