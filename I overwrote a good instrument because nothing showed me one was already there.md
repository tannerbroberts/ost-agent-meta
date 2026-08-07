---
type: Opportunity
source: 'TRANSCRIPT:49d6b2d3-b867-4996-9d9d-8f10dd0871de'
created: '2026-08-07'
evidence: observed
---
#Opportunity #unvalidated #evidence/observed

`ost_set_instrument` does two different jobs behind one call: it attaches a runnable command to a test that has none, and it replaces the command on a test that already has one. The first is pure repair. The second is destructive — the tool's own contract says a replacement deliberately un-clears any permit the old command held, so a swap costs a verification that has to be re-run by hand.

Nothing on the maintenance surface distinguishes the two cases before the call. `ost_next_work` reports which *solutions* lack an instrument; it does not report which *tests* have one. `ost_read_tree` returns titles, layers, statuses, tags and links, not instrument fields. So a pass working the instrument backlog picks a test by title, cannot tell which of the two operations it is about to perform, and finds out from the tool's own success message afterwards.

The failure is quiet in the direction that matters. A pass told to attach instruments, working from a list of titles, will silently downgrade well-grounded commands to guesses, and every count it reports will improve.

## What was observed

On 2026-08-07 an unattended pass called `ost_set_instrument` on "Attach thirty self-observations to one node and require the rung not to move", believing it to be prose-only. The test already carried `npx vitest run test/adapters/corroboration-actor-ceiling.test.ts` — a path under `test/adapters/` that locates the ceiling rule at the corroboration adapter, and so was written with knowledge of the repository. It was replaced by `npx vitest run test/evidence/self-observation-ceiling.test.ts`, a path invented by a pass that had been refused repository sight entirely. The original was restored in the next call, but the permit the swap un-cleared was not, and cannot be from this surface.

That pass then stopped its instrument work, because it had no way to avoid repeating the mistake.

## What would fix it

Either a read that answers "does this test have an instrument, and what is it" before the write, or a `ost_set_instrument` that refuses to overwrite unless told explicitly that replacement is intended — the same shape as the guard that stops a merge from clearing a gate it did not earn.

## History

- 2026-08-07 — Created from a first-party observation during an unattended maintenance pass: the pass made this error, caught it from the tool's own diff output, reverted it, and abandoned the remaining instrument work as unsafe to perform blind.
