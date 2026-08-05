---
type: Solution
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Judge the eighteen reopened items — were they genuinely finished]]
[[The fallback is bounded by the version boundary and goes inert at a stated release]]

The new build keeps the old build's reading as a second source: an item counts as done if the new ledger says so **or** if the legacy signal did. Nothing is rewritten, nothing is inferred into permanence, and a vault last touched by an older version simply keeps working.

**The trade it makes:** it is by far the safest — no write, no guess, fully reversible, and it cannot produce a wrong permanent entry. It also fixes the symptom immediately for every existing vault without anyone running anything. The price is carried complexity: two accounting schemes must both be understood forever, the union rule quietly becomes the real definition of done, and the next upgrade inherits three dialects instead of two. That is how compatibility layers become the thing nobody can remove.

**How it differs from its siblings.** [[Migrate the old accounting into the new ledger on first run, and record that it happened]] converts once and then forgets the old dialect; this one never converts and never forgets. The choice is a bet about how many more accounting changes are coming — one more, and migration wins; several, and each one is another permanent fallback branch.

**A bounded version:** read the legacy signal only for items created before the version boundary, and drop the fallback after a stated release. That caps the carrying cost at the price of a deadline someone has to honour.

Distinguishing assumption: that the two schemes can be reconciled by a simple OR. If the new ledger deliberately *narrowed* what counts as done — that is, the reopened items were genuinely not finished by the new standard — then the union does not fix a bug, it reintroduces one.
