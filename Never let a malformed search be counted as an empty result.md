---
type: Solution
status: unvalidated
source: 'TRANSCRIPT:5e5c119d-e5e8-4dbd-ab7c-c4bfc1247a18'
created: '2026-08-06'
evidence: observed
---
#Solution #unvalidated #evidence/observed
[[An unread marker survives to the summary instead of being flattened to zero]]

Give up on preventing the parse failures and make it impossible for one to be mistaken for a finding.

The expensive part of `rg: error parsing glob '{Charge'` is not the wasted call. It is that a caller which does not read the message carefully now holds zero results, and zero results is what "nothing is wrong here" looks like. The tree already names the consequence one bucket up — a sweep that cannot read its subject reports a clean result — and this is the argument-level mechanism that produces it.

The proposal is a single rule applied at every search path a pass uses: a search returns either results, or an explicit unread marker naming the subject it could not examine. It never returns an empty set for a question that did not run. Downstream, an unread marker is not zero — it propagates, so a summary built over ten subjects where two failed to parse reports eight examined and two unread, rather than a count of findings across ten.

The bet is that miscounting is the whole harm and prevention is optional. If a pass reliably knows what it did not read, then a malformed pattern costs one retry and no false confidence, and the escaping problem stops being urgent. Compared with its siblings this is the least elegant and the most robust: it makes no claim about which searches can avoid a pattern language, and it keeps working for failure modes nobody anticipated — a timeout, a permission denial on a directory, a file too large to read.

That last point is the strongest argument for it. Four of this vault's recorded friction events were reads denied on the product directory, and one was a read refused for exceeding a size cap. Neither is a syntax problem, and both produce exactly the same false zero.

The cost is that every caller has to handle a third return state, and a caller that maps unread to empty for convenience has silently reintroduced the bug. Whether the unread state survives the trip through real call sites, rather than being flattened at the first convenient boundary, is what the test beneath this node is for.

## Definition of done

"Feed every search path a malformed pattern and require the total to say two were unread"

```
npx vitest run test/ost/unread-subject-propagation.test.ts
```

Red today: there is no unread state to propagate, so the spec has nothing to assert against. The stronger half of it — that no call path yields a bare count without handling the unread case — will stay red until the search interface stops returning a plain collection, which is a design change rather than an addition.

Green here proves the mechanical path preserves the distinction. It does not cover prose: a model writing "no issues found" over a subject it could not read is the same error, and no type system prevents it.
