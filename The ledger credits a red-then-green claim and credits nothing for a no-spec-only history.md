---
type: AssumptionTest
created: '2026-08-22'
evidence: assertion
threshold: >-
  exactly one credit for a red-then-green history and zero credits for each of
  the four other histories, including a legacy red whose command now collects no
  spec
instrument: npx vitest run test/eval/autonomy-ledger-credit.test.ts
sight: grounded
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: compute-only.** The question is what a reader credits given a history, which is settled against fixture nodes and needs nobody's judgement.

**Design.** Build tests carrying each history and assert what the ledger credits:

| Instrument-log history | Credit |
|---|---|
| `**red**` then `**green**` | one survived claim |
| `**no-spec**` only, then `**green**` | zero — nothing was ever measured |
| `**no-spec**` repeated | zero, however many times |
| `**red**` recorded before the no-spec marker existed, command now collects no spec | zero, on re-run |
| `**green**` under one command, instrument since swapped | zero for the new command |

The fourth row is the one that decides whether this is worth building. Legacy reds read `**red**` in an append-only log that cannot be corrected, so a ledger that trusts the marker inherits every vacuous red this vault ever filed — 260 of 266 as of 2026-08-09. `confirmPermit` already answers this by re-running the command rather than trusting the line, and a ledger that widens permission must be held to at least that.

**Pre-committed threshold:** exactly one credit for the red-then-green history, zero credits across all four other histories, and the count of credited claims is no greater than the number of distinct commands observed green after a genuine red.

**What this does not settle.** Everything the node is actually risky about. Whether the operator will let a track record widen a real permission without a fresh approval is the sibling assumption and stays a person's answer — "Ask the operator to name one permission class a survived stake may widen with nobody watching". Nor does a green here address claim *difficulty*: it stops the cheapest claims being counted, and says nothing about whether the ones that remain are hard or useful, which is the failure mode this node named at birth and which no exit code holds.
