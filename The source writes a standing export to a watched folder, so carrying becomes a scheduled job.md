---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
authorship: machine
---
#Solution #unvalidated #evidence/assertion
[[A scheduled export keeps arriving, and a stopped one does not look like an empty experiment]]

The human's work moves from carrying each result to setting up, once, a recurring export from the source into a folder the vault already watches. Most tools that hold experiment data can email, sync, or scheduled-export a sheet. The vault needs no new code at all: the drop folder it already reads is the destination.

**Compared to the alternatives.** Uniquely, this requires no engineering on the vault side — it is configuration, and it can be in place today rather than after an adapter is written. It also degrades gracefully, since a stale export is still an export. Against a pull adapter, it gives up structure: what arrives is whatever shape the source felt like emitting, and something still has to parse it. Against a webhook it gives up latency, running at the export's cadence rather than the experiment's.

**What would make this the wrong pick.** It quietly relocates the fragility rather than removing it. A scheduled export that silently stops — expired share link, changed sheet name, a source that stops sending — looks exactly like an experiment that produced no results, and the vault has no way to tell those apart. That failure mode is worse than a human forgetting, because a human eventually notices.

## History
- 2026-08-05 unlinked "Set up one scheduled export and check every week whether it is still arriving" — moved under "A scheduled export keeps arriving, and a stopped one does not look like an empty experiment" — the belief this test measures now has a node of its own

## Definition of done

"A drop folder that stopped receiving files is reported overdue, not as zero new"

```
npx vitest run test/adapters/inbox-cadence.test.ts
```

Green means a drop folder with a declared cadence reports **overdue** once its newest file is older than that cadence, still reports a normal 0 new inside it, and reports a vanished folder as **unreadable** rather than 0 new. It is red today. `InboxSource.fetchSince` (`src/adapters/inbox.ts`) returns `items: []` both for "nothing new" and for "folder gone", and `test/adapters/inbox.test.ts` asserts that behaviour ("missing inbox directory yields no items"). This is a **no-spec** red until the spec is written, so the builder delivers the cadence field, the overdue/unreadable report and the spec together.

It settles only this candidate's own stated failure mode: that a stopped export looks exactly like an empty experiment. Whether a real external export keeps arriving is "Set up one scheduled export and check every week whether it is still arriving", and that needs a person.

The test title is quoted rather than wikilinked: its one backlink belongs to its parent assumption.
