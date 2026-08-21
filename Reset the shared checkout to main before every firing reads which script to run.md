---
type: Solution
source: 'INBOX:2026-08-16-audit-loop-efficiency-and-checkout-drift.md'
created: '2026-08-16'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Resetting the shared checkout to main before every firing doesn't clobber a still-running firing's in-flight work]]
[[Resetting the shared checkout to main before every firing never discards in-flight work a concurrent firing depends on]]

Before any firing (build or discovery loop) reads which automation script to run, force the shared working directory back to `main` — `git checkout main && git reset --hard origin/main` (or equivalent) — so a prior firing's transient branch, and any edit it made to `examples/automation/*.sh` on that branch, can never carry forward as the next firing's executable policy. Cheapest mechanism: a few lines at the top of the loop's entry point, no new infrastructure, no change to the single-checkout model. Does not stop a build session from editing a script mid-session and running the edited version within its own firing — it only stops that edit from persisting into the *next* firing.

## Issues
- 2026-08-17 Assumption surfaced ("Resetting the shared checkout to main before every firing doesn't clobber a still-running firing's in-flight work") but its test is not created: it's a feasibility/safety question the repository can answer, and naming `humansRequired` just to satisfy the tool would misstate that. This unattended sweep holds no `ost_read_repo` grant, so it cannot ground a real instrument. Needs an attended pass (or a human) with repo sight to write the spec-file instrument.

## Repo sight this pass — the concurrency this depends on does not hold (unattended sweep, 2026-08-21)

The Issues note above deferred this solution's test for want of repo sight. This pass held the grant, and what it found argues against the mechanism rather than for it.

**Two firings can be live at once, and they deliberately do not coordinate.** `examples/automation/build-pass.sh` keeps its own `mkdir` lock under `$OST_BUILD_STATE`, outside the vault, and says why in its own comments: it is deliberately not `ost-agent loop due`, because "that machinery is per-vault and single-tenant... Two loops sharing it would each see the other's firing as their own." Further down, explaining why it stages one named file instead of `git add -A`: "The discovery loop may be mid-firing in the same vault — the two hold separate locks and neither waits on the other."

So a `git checkout main && git reset --hard origin/main` at one loop's entry point can land on the other loop's live working tree. This node describes that step as the "cheapest mechanism: a few lines at the top of the loop's entry point, no new infrastructure" — and against the concurrency model actually in the repository, a few unconditional lines are not safe. Whatever gets built here has to be lock-aware, which is more than a few lines and less cheap than the body claims.

**A second hazard, in the same file.** The build loop breaks its own lock when the directory is older than `OST_BUILD_LOCK_TTL_MINUTES` (default 60) on the grounds that the prior firing is "assumed dead". A firing that is slow rather than dead already has a second firing starting beside it, and an entry-point reset would meet its live tree.

The test proposed beneath the first assumption is written to this: it requires the reset to refuse while either lock is held, and to run when neither is.

## Definition of done

"A pre-firing reset is refused while either loop's lock is live, and runs only when neither is"

```
npx vitest run test/loop/pre-firing-reset-safety.test.ts
```

Named in plain quoted text rather than as a `[[wikilink]]`: that test's one backlink belongs to its parent assumption, and a second link anywhere in the vault fails `check`'s single-backlink rule.

## Issues
- 2026-08-21 The two assumptions beneath this node read as one belief written twice — "Resetting the shared checkout to main before every firing doesn't clobber a still-running firing's in-flight work" and "...never discards in-flight work a concurrent firing depends on". Not merged here, because merging assumptions is a judgement about whether they could come apart (one could conceivably be about the firing's own branch and the other about a dependency relationship) and this pass is not confident they are the same claim. What would settle it: name a solution, or a failure, that satisfies one and not the other. If none exists they are one node. Flagged rather than acted on; the duplicate scan reports sibling opportunities, not sibling assumptions, so nothing surfaces this automatically.

_Source: this pass's `ost_read_repo` read of examples/automation/build-pass.sh. First-party read of committed code; grounds feasibility, not demand. No command executed, no result recorded, rung unchanged._
