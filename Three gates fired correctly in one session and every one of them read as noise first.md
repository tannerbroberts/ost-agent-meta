---
type: Solution
status: unvalidated
source: 'TRANSCRIPT:89ac8277-29ce-4d80-827e-cefea0bebabf'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[What made those firings read as noise is something the gate's own wording can fix]]

**The idea.** When a gate fails on CI and passes locally, the session's first move should be a fixed, cheap triage — not a judgement call. Three questions, in order, each with a command behind it: *what number did the criterion record?* (compare against the doc), *does it fail at the commit before mine?* (run it there), *what is the machine actually doing?* (profile, or read the error's own mechanism). Only after those three may a session write the word "flaky", and then it must write which of the three ruled the alternatives out.

**Why a checklist rather than better judgement.** The judgement was available and was not used. In one session on 2026-08-06, three separate gates fired, and all three were first read as environmental:

| gate | first reading | what it actually was |
| --- | --- | --- |
| Z3 wall-clock budget, 6 CI runs over 3 days | "flaky timing test, slow runner" — twice filed into this vault's friction inbox | a 3x regression: three `tree.filter(...)`-per-node scans, 44% of CPU |
| `corrections-ledger` quiet-window | "stale fixture, ignore" | a test asserting the age of the working copy, green only for 30 minutes after checkout |
| `commit.test.ts` ENOTEMPTY | "CI flake" | the fixture deletes a repository while `git gc --auto` is still writing in it |

Two of the three were **real defects in the thing being measured**, and the third was a real defect in the measurement. None was the machine. The cost of the first was a week of every merge in the repository being blocked, and of the six failures nobody made the one comparison — measured against recorded — that would have named it in a minute.

**Why the environmental reading wins by default, which is the actual mechanism.** It is the cheapest hypothesis that explains the evidence and it requires no work. It is also *usually right elsewhere*, which is what makes it dangerous here: a reader arrives with a prior calibrated on other codebases where CI flakes are common, and this repository's gates are unusually deliberate. The tell is not the failure — it is that the same failure is arriving repeatedly and being dismissed repeatedly, which is a fact about the reader rather than the machine.

**The trade.** Three commands per red gate, on a surface where most reds are real, is cheap. On a repository whose CI genuinely is flaky it would be a tax paid on every run, and the honest version of this solution says so and gets turned off there.

## Definition of done

A red gate produces a triage the next session can read: the recorded figure beside the measured one, the result at the parent commit, and either a profile or a named mechanism. Whether that changes what a session concludes is the thing to measure, and it needs a person to judge — the same session that writes the triage cannot grade whether it stopped a wrong call.

## Relationship to its sibling

The sibling solution "A perf gate reports its measurement next to the number the criterion recorded" builds the first of the three questions into the gate itself, so it is answered whether or not anyone remembers to ask. This node is the general habit; that one is the part that can be made automatic. If only one gets built, build that one.

## History
- 2026-08-06 body edited — The closing paragraph wikilinked its sibling in prose, which broke `single-backlink` — exactly one link, from the parent — and turned the whole tree red, which is the state that stops the discovery loop firing. Same rule the product enforces and the same one I had just been reading about. Reworded to name the sibling as plain text; nothing else changed.

## Issues
- 2026-08-06 unresolved-citation (flagged by ost_check): frontmatter cites `TRANSCRIPT:89ac8277-29ce-4d80-827e-cefea0bebabf`, and no record under `.ost-agent/evidence/` carries that id. Same fault, same missing id, on four nodes created in one sitting; the full diagnosis and the check that would settle it are recorded on "A guard derived the rule it was checking, so it agreed with the bug for 23 releases". Until it is settled, treat this node's evidence rung as unsupported.

## Definition of done

"Count how buried each of the three firings was before assuming the wording was at fault"

```
npx vitest run test/telemetry/gate-signal-density.test.ts
```

Red today: neither the density measure nor the spec exists, and the recorded session it reads has never been queried this way.

Run this one *before* building anything. It can only kill the content hypothesis, never confirm it — but killing it is worth the whole cost, because the placement remedy and the wording remedy do not overlap and building the wrong one costs a full cycle.
