---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Every source of new work in this vault can be watched as an event]]

The loop does not choose an interval at all. It finishes its work, registers interest in the things that could give it more — a file landing in a watched folder, a check completing, a human recording a result — and blocks. Something arriving wakes it. Nothing arriving costs nothing.

This removes the question the opportunity is really about. A loop that must decide when to run next is forced to guess whether work exists, and guessing wrong in one direction wastes money while guessing wrong in the other leaves the tree stale. A woken loop never guesses.

**Compared to the alternatives.** Strictly better than a stop predicate at the moment of stopping, because it also answers when to start — but it needs every source of new work to be observable as an event, and some are not. Against a spend ceiling, this addresses the cause rather than capping the symptom, and so it does nothing at all about a loop that is genuinely busy doing worthless work.

**What would make this the wrong pick.** If the meaningful triggers cannot all be watched, a woken loop will sleep through real work and look perfectly healthy doing it — a quieter failure than idling, and a harder one to notice.

## Definition of done

"Census every source of new work in this vault and check which can be watched as an event"

```
npx vitest run test/loop/work-source-census.test.ts
```

Green means every channel that can put new work in front of a pass is enumerated in one place and each exposes a watchable event source rather than only a poll — the six ingest adapters (`inbox`, `friction`, `transcript`, `usage`, `atlassian`, `slack`) and the human-initiated mutations a sleeping loop must not miss (`result`, `promote`, `lane`, `retract`). It is red today because nothing in the repository enumerates work sources and no channel exposes an event at all.

**Why the census is the right shape for the test and not a stand-in for it.** The risk this solution carries is not that a listener is hard to write; it is that one source turns out to be unwatchable and the loop sleeps through it while looking perfectly healthy. That failure is invisible at run time and cheap to find at enumeration time, which is why the enumeration is the check.

**What green does NOT settle.** It says every source has a watcher, not that the watcher fires when it should, nor that waking on an event costs less than the poll it replaces. A source that produced nothing in the sampled history is absent from the census entirely, so the enumeration is bounded by what has happened rather than by what can happen. Latency, duplicate wakeups, and whether the operator is better off are all untouched.

## History
- 2026-08-05 unlinked "Census every source of new work in this vault and check which can be watched as an event" — moved under "Every source of new work in this vault can be watched as an event" — the belief this test measures now has a node of its own
