---
type: Solution
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

When a newer build first opens a vault written by an older one, it reconstructs the new ledger from whatever the old accounting used — node sources, history entries, whatever carried done-ness before — writes the result once, and appends a visible migration entry saying what it inferred and from what.

**The trade it makes:** it is the only sibling that leaves the vault genuinely correct afterwards rather than merely tolerable, and it pays the cost once instead of on every read. The price is that a migration is a *guess about the past* — it infers a fact the old build never recorded. Where the inference is wrong it will mark something done that was not, which is the more dangerous direction of error, and append-only means the wrong migration entry is permanent (see [[A call the tool should have refused is permanent, because append-only cannot take it back]]).

**How it differs from its siblings.** [[Keep reading the legacy signal as a fallback so old work still counts]] never writes anything and never guesses — it just keeps understanding the old dialect. [[Report the accounting change explicitly instead of folding it into the counts]] does not try to preserve done-ness at all; it makes the reinterpretation visible. This is the only one that ends with a single, current source of truth.

**What makes it urgent.** The Issues section on this opportunity records a live instance: `.ost-agent/state/mapped.json` lists two TRANSCRIPT ids as mapped while `ost_next_work` reported both outstanding in the same minute. The ledger and the counter disagree *right now*, so migration here is not only a historical concern.

Distinguishing assumption: that old done-ness is reconstructible from what the old build left behind. If the old accounting existed only in the old binary's logic and left no trace, there is nothing to migrate and this candidate is empty.
