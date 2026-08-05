---
type: Solution
source: 'TRANSCRIPT:785ea509-96b9-4225-b45a-babd5321aafc'
created: '2026-08-05'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[One expiry period fits the real flake timeline without firing on unresolved flakes]]

Every exclusion carries an expiry. When it lapses the test rejoins the suite whether or not anyone fixed it, and the run goes red until somebody either fixes it or consciously renews the quarantine with a fresh reason.

**This is the permanence half of the need.** Its siblings make the workaround convenient ("A quarantine list committed to the repo, so the exclusion is declared once instead of retyped") and honest ("A result carries its own exclusion set, so a gate cannot read it as full coverage"). Neither creates any pressure to ever remove one. This candidate is the only one that does, and it is the reason a human comparing the three should be suspicious of adopting the first without it.

**The mechanism is forcing a decision back onto a schedule.** The failure this addresses is not a wrong decision, it is a decision that was never revisited: quarantining a test is usually right on the day, and almost never right forever. An expiry converts silence from consent into a scheduled re-ask.

**The strongest objection, which this vault has already run into elsewhere.** Something that goes red on a timer, without anybody having changed anything, is a gate that cries wolf — and the vault's own reasoning on drift detection is blunt about the consequence: an operator who learns to skip a report misses the real one. If the expiry is too short it becomes noise and gets disabled; too long and it never fires before the flake has been forgotten anyway.

**Which suggests the real question is not the mechanism but the period**, and that is empirical rather than arguable. The vault has flake evidence on record — two friction notes naming the same test flaking on 2026-08-01, and its exclusion still being typed by hand on 2026-08-04 — so there is at least one real case whose timeline can be read to see what expiry would have helped and what would merely have interrupted.

_Agent-ideated, unvalidated — one of three competing candidates under this opportunity, for a human to compare rather than adopt._

## Definition of done

"Replay the recorded flake timeline to see whether any single expiry period would have helped"

```
npx vitest run test/telemetry/quarantine-expiry-period.test.ts
```

Red today: nothing reconstructs a flake as a timeline, so no period can be swept against it. Green when a single expiry period fires after every recorded flake was resolved, before it was forgotten, and never against an unresolved one.

**Read a green here sceptically.** The recorded sample is one flake, and a period that fits one case is fitted to it. The threshold demands zero bad firings precisely so a thin sample fails rather than flatters — if the record cannot support a period, the finding is that this candidate should not ship on a guessed number.

**What this does not settle.** Whether an operator renews a lapsed quarantine thoughtfully or reflexively, which is what decides whether expiry creates real pressure or just ceremony. No replay can see that.

## History
- 2026-08-05 unlinked "Replay the recorded flake timeline to see whether any single expiry period would have helped" — moved under "One expiry period fits the real flake timeline without firing on unresolved flakes" — the belief this test measures now has a node of its own
