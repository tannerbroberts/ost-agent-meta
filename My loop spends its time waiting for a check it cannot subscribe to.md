---
type: Opportunity
status: unvalidated
source: 'TRANSCRIPT:f48dc76d-9bb6-45c3-b624-5b386609d720'
created: '2026-08-02'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed
[[The pass ends at the handoff, and the finished check wakes the next one]]
[[One cheap blocking wait replaces the poll-and-retry loop]]
[[Take up independent work while a check is outstanding]]

One captured session's entire friction record is a command that timed out after two minutes, having reported `still pending` five times in a row. The verification the loop depends on is asynchronous, and the only way it can be observed is by asking repeatedly. So the agent polls, and polling is both the natural instinct and the thing the environment declines to make cheap. Time that reads as work in the record is time spent waiting, and a run's cost is dominated by an event it has no way to be notified of.

**The need:** I want to be told when the check finishes, rather than pay to keep asking whether it has.

More than one way to address this: subscribe to completion instead of polling for it, hand the wait to something built to block cheaply, structure the pass so other work proceeds while a check is outstanding, or end the pass at the handoff and resume when the result lands.

## Running census — the unsubscribable wait

One census, maintained across passes, replacing seven overlapping sections written on 2026-08-02, 2026-08-03 (twice), 2026-08-04 (twice) and earlier, plus the body of the node folded in here on 2026-08-06. Add new sightings here rather than appending another section. Window to date: **2026-07-24 → 2026-08-06.**

**Twenty sessions, mechanically captured.** `f48dc76d` (originating — a two-minute timeout after five `still pending` reads), `0d27cebf`, `081b644b`, `3d729ebc`, `470cb94a`, `4ff7b605`, `516fdfb8`, `5960b7ec`, `5bbed804`, `785ea509`, `87a025f8`, `8fc8d6e3`, `92cc492d`, `97546e2f`, `995b8ab1`, `a0eb3fd4`, `a615eb46`, `b7aae32d`, `e335a680`, `fd2c6d71`.

**Fourteen distinct pull requests polled with the identical construct:** 9, 10, 12, 13, 14, 17, 18, 19, 22, 25, 30, 39, 54, 55. The shape is `sleep N` followed by `gh pr checks <PR>`, blocked every time with the same guidance — *"To wait for a condition, use Monitor with an until-loop … To wait for a command you started, use run_in_background"*. Fourteen distinct subjects spread across the numbering matters more than a repeat count: this is not one stubborn check re-polled, it is the same reflex arriving fresh at every new PR.

**The sleep interval varies — 25, 30, 45, 60, 240 seconds.** The agent tunes the wait to the thing it is waiting for, which is evidence it is reasoning about the delay rather than pattern-matching a remembered snippet, and it still reaches for the one form the environment declines.

## What the volume establishes

**1. It is not confined to CI.** The same blocked wait targeted a log tail (`0d27cebf`), an `ls` on a workflow journal directory (`4ff7b605`), `git status --porcelain` (`470cb94a`), a local test suite (`785ea509`) and a background task id (`516fdfb8`, `5960b7ec`). Three subjects with nothing in common except the absence of an event to wait on. A fix scoped to `gh pr checks` would leave most instances standing, and any candidate here should be read against all three.

**2. The sanctioned path is also unsatisfying.** `516fdfb8` shows what happens when the agent does poll: `gh pr checks 17` exited 8 reporting `bundle-drift pass 14s` next to `test pending 0` — a non-zero exit that means *not finished yet*, indistinguishable at the call site from a failure. Polling does not merely cost turns; it returns an answer that cannot be read.

**3. Polling costs its own turns, measured.** `785ea509` re-issued the same full-suite command four times in one session at 600s each, three of them byte-identical, with no code change in between — the run checking whether the thing it started had finished by starting it again. Up to four full suite runs to learn one suite result. `516fdfb8` and `5960b7ec` each re-issued `TaskOutput` with `block: true, timeout: 600000` — a ten-minute blocking wait, which is the same wait relocated to a tool permitted to hold it. That relocation is the tell: the folded node recorded three identical `TaskOutput` re-polls of one task id as "the same need expressed through a channel that does not refuse it."

**4. The lesson is not missing, it is unreachable.** The refusal names the correct alternative at the moment of the error, and the run complies that turn, every time — then the next session reaches for `sleep` again. Across eight days and fourteen PRs it never carried forward. So this is not an instruction-reading failure that better wording would fix. (The retention half of that is held separately by "The same refusal is rediscovered every session, because nothing carries the lesson forward"; what belongs here is the wait itself.)

**5. The recommended remedy was itself learned by failing at it.** In `785ea509` the agent did try `Monitor`, the primitive the refusal recommends, and got `InputValidationError: An unexpected parameter 'timeout' was provided`.

**A pre-committed bar for anything built here.** Twelve of the twenty-two transcript records outstanding in one sweep window contained a blocked sleep-then-check. That count, machine-recorded, is the baseline: a mechanism that lets the loop wait properly should reduce it, and one that does not reduce it has not worked.

## Provenance

Distilled from `TRANSCRIPT:f48dc76d-9bb6-45c3-b624-5b386609d720` and corroborated by the nineteen further sessions named in the census, each read in full across the passes that recorded them. Evidence class throughout: observed behaviour of this product's own agent, captured mechanically from session transcripts with no narrator. **It grounds usability, not desirability** — it is not outside-user evidence that anyone wants this fixed. The node's rung is unchanged by this consolidation and promotion remains a human's call.

Several of the transcript ids above remain listed as unmapped evidence in `ost_next_work`: citing an evidence id in a body does not clear the item from the sweep. That is the tooling gap recorded on "Evidence that fits no layer keeps coming back, so the pass never runs out of work", and it is the reason this node accumulated seven censuses before this consolidation.

## History
- 2026-08-06 merged "Waiting on a slow external check burns the session, because every obvious way to wait is refused" into this node and deleted its file — Same claim. The folded node's own Issues section (2026-08-06) laid out both sides and its keep-separate argument defeats itself: it says the node's distinguishing content is the *rediscovery* cost, then concedes "the rediscovery cost is exactly what its parent already holds, which leaves this node holding the intersection of two needs the tree carries separately." So its unique half belonged to its parent (now detached) and its remaining half is this node's need in this node's words — that node's stated want, "no first-class way to express waiting for something slow", is this node's "hand the wait to something built to block cheaply". The evidence overlapped too: both rested on 516fdfb8 and the same sleep-then-poll construct. Any candidate ideated under it would have landed on one of the three solutions already here. Its session 081b644b and PRs 54/55 are carried into the census below. This edit also consolidates SEVEN overlapping corroboration sections written on 2026-08-02, 08-03 (x2), 08-04 (x2) and earlier into one census — the same accumulation pathology already consolidated on "The same refusal is rediscovered every session". Every session id and every distinct analytic point from all seven is preserved below; prior wording is in git.
