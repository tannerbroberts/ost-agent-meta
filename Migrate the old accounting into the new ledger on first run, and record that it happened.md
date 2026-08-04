---
type: Solution
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Reconstruct the old accounting on a copy and see if it agrees]]

When a newer build first opens a vault written by an older one, it reconstructs the new ledger from whatever the old accounting used — node sources, history entries, whatever carried done-ness before — writes the result once, and appends a visible migration entry saying what it inferred and from what.

**The trade it makes:** it is the only sibling that leaves the vault genuinely correct afterwards rather than merely tolerable, and it pays the cost once instead of on every read. The price is that a migration is a *guess about the past* — it infers a fact the old build never recorded. Where the inference is wrong it will mark something done that was not, which is the more dangerous direction of error, and append-only means the wrong migration entry is permanent (see [[A call the tool should have refused is permanent, because append-only cannot take it back]]).

**How it differs from its siblings.** [[Keep reading the legacy signal as a fallback so old work still counts]] never writes anything and never guesses — it just keeps understanding the old dialect. [[Report the accounting change explicitly instead of folding it into the counts]] does not try to preserve done-ness at all; it makes the reinterpretation visible. This is the only one that ends with a single, current source of truth.

**What makes it urgent.** The Issues section on this opportunity records a live instance: `.ost-agent/state/mapped.json` lists two TRANSCRIPT ids as mapped while `ost_next_work` reported both outstanding in the same minute. The ledger and the counter disagree *right now*, so migration here is not only a historical concern.

Distinguishing assumption: that old done-ness is reconstructible from what the old build left behind. If the old accounting existed only in the old binary's logic and left no trace, there is nothing to migrate and this candidate is empty.

## Definition of done

[[Reconstruct the old accounting on a copy and see if it agrees]]

```
npx vitest run test/ost/accounting-reconstruction.test.ts
```

Green means the reconstruction, run against the vault state that produced the 9-versus-27 split, agrees with `ost-agent@0.1.3`'s own answer on at least 26 of 27 items, with **zero** items marked done that the old build called outstanding. It is red today because no reconstruction exists.

**The asymmetry in the threshold is the whole design and should not be smoothed out.** A migration is a guess about the past — it infers a fact the old build never wrote down — and the two error directions cost very different things. Marking something outstanding that was done costs a wasted pass. Marking something done that was not costs a silently dropped piece of work, permanently, in a store built not to forget. So one miss is tolerated in the safe direction and none in the dangerous one, and a command that averaged the two would pass on exactly the failure that matters.

**This test can eliminate an option, which is why it goes first in this row.** All three siblings need to detect that a vault was written under different accounting; only this one needs to *reconstruct* it. A red result means the row's answer is [[Keep reading the legacy signal as a fallback so old work still counts]] or [[Report the accounting change explicitly instead of folding it into the counts]], and no further migration work is warranted.

**A live case the spec should carry as a fixture.** This opportunity's Issues section records `.ost-agent/state/mapped.json` listing two TRANSCRIPT ids as mapped while `ost_next_work` called both outstanding in the same minute — the same disagreement happening now rather than historically, and a cheaper oracle than the archived split.

**What green does NOT settle.** It says the inference is recoverable against one known disagreement on one vault. It says nothing about a vault whose divergence has a different cause, and nothing about whether recording that the migration happened is enough for a later reader to trust the counts.
