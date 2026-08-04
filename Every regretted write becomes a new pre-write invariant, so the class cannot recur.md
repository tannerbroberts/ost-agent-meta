---
type: Solution
status: unvalidated
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[Take the last ten regretted writes and check whether each could have been refused mechanically]]

When a human finds a write that should never have been accepted, the response is not to fix that node but to write the check that would have refused it, and add it to the set every mutating call runs before touching disk. The backlog of regretted writes becomes the specification for the refusal set.

The vault already works this way in places — reserved headings that no argument may contain, a status value that simply does not exist on the tool, an evidence ceiling enforced at the call. Each of those is a lesson that became a mechanism. This proposes making that conversion routine rather than occasional.

**Compared to the alternatives.** The only option that reduces the number of bad writes rather than managing them afterwards, and the only one whose benefit compounds — every invariant added protects every future call for free. It is also the slowest to pay off, since it can only learn from mistakes already made, and it does nothing whatsoever for the write that is on disk right now. Retraction and this one are natural partners: retract the instance, then add the invariant.

**What would make this the wrong pick.** Invariants are themselves permanent and accumulate. A refusal set grown one regret at a time will eventually refuse something legitimate, and the person hitting that refusal will have no idea which past mistake they are being protected from.

## Definition of done

[[Take the last ten regretted writes and check whether each could have been refused mechanically]]

```
npx vitest run test/ost/regretted-write-invariants.test.ts
```

Green means at least 6 of the 10 regretted writes already recorded in this vault are refused by a pre-write invariant evaluable over the call's own arguments and the tree's state — no model opinion in the loop. It is red today because no invariant set exists and no regretted write is committed as a fixture.

**Why 6 of 10 and not all 10.** If most regrets turn on judgement rather than on anything checkable, the refusal set cannot grow to meet them and this whole approach is the wrong shape. Six is the point at which the mechanism carries more than half its own weight; demanding ten would make the test unpassable for a reason that has nothing to do with whether the idea works.

**What green does NOT settle, and it is a selection problem rather than a coverage one.** The fixture set is drawn from regrets that were *noticed and written down*. Bad writes nobody has spotted are absent by construction, and there is a live reason to think they are the harder class: a write that looked fine at the time is exactly the one no invariant over call-time information would have caught. Green says the recorded regrets were mechanical; it cannot say the unrecorded ones are.
