---
type: Solution
source: 'agent-run:unattended-sweep-2026-08-28'
created: '2026-08-29'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[Most of what this loop waits on is work the harness tracks, not shell-backgrounded jobs it started itself]]

**Variation dimension: who-does-the-work. Position taken: nobody — the step is removed.**

Neither the agent nor the operator waits, because nothing polls. Work started through a channel the harness tracks reports its own completion, and that report is what causes the next turn. The waiting primitive is not made better, longer, or more informative; it is taken off the path for this class of work entirely.

**Why this is a real position and not a wish.** The mechanism already exists on the surface that produced the observed failure. This session's own `ScheduleWakeup` description states it outright: *"when harness-tracked work finishes, you are re-invoked automatically, so polling is wasted"* — and goes on to say a short-interval wakeup to poll for background work is precisely the thing not to schedule. So the nine expired `await` calls were spent re-implementing, badly, a notification the surface was already prepared to deliver. The candidate is to stop paying for that.

**What it gives up, and this is the sharp edge.** It only covers work the harness can see. External state — a CI run, a deploy, a remote queue, another machine's lock — emits no completion event here, and for that class this candidate offers nothing at all and something still has to wait. So it does not close the opportunity; it removes the largest and cheapest slice of it and leaves a smaller, harder remainder. A reader should not mistake that for a full answer.

It also gives up mid-flight visibility. A polling loop that greps a log can report progress at 30s; a completion notification is silent until it is not, which is the exact "either healthy or dead" ambiguity recorded on "Scheduled ambient passes that page the operator only at hard gates". Removing the poll removes the bad signal and the only signal together.

**Against its siblings.** The sibling that reports liveness makes waiting *informative*; this one makes it unnecessary, and the two are not additive — if nothing polls, there is nothing for a liveness report to improve. The bought-vs-built sibling still has the run doing the waiting, just with somebody else's primitive. This is the only one of the three where the 300s number stops meaning anything rather than being replaced by a better number.

**What would make this the wrong pick.** If most of what this loop actually waits on is *not* harness-tracked — and the observed session was waiting on a vitest suite writing to `/tmp`, which is exactly that case — then the removed slice is the small one and this candidate is a distraction from the remainder. That is a countable fact about this vault's own firings and nobody has counted it. It is the first thing to check before building anything here.

Unvalidated, and ideated by an unattended pass. Not blind: this surface holds no grant to run independent parallel ideators, so all three candidates under this opportunity were composed in one context by one author, which is the condition the blind-ideation rule exists to prevent. Read them as one author's three answers and discount their apparent distinctness accordingly.

## Definition of done

"Classify every waiting case in the corrections corpus by whether its target was harness-tracked"

```
npx vitest run test/loop/wait-target-census.test.ts
```

The bar is at least 50% of classified waiting cases targeting harness-tracked work, pre-committed on the test node before any run. That spec does not exist yet, so the command is currently a `no-spec` red rather than an assertion red — disclosed on the test node along with the corpus to read (`test/fixtures/corrections/<session>*.jsonl`), the two buckets, and the field `WAITING_CASES` is missing. Not finished until the spec exists and fails on its assertion.

The test title is quoted rather than wikilinked on purpose: its one backlink belongs to its parent assumption.

**Settle this one first, and be prepared for it to retire this candidate.** The four waiting cases already visible — the observed vitest-suite session plus the three in `src/loop/wait.ts`, whose intents are a `gh` CI poll, a directory listing and a git-status condition — all look self-backgrounded rather than harness-tracked. If the census confirms that, this candidate is a distraction from the remainder and the liveness sibling is the branch's real work. A cheap refutation that redirects the branch is worth more here than a confirmation would be.
