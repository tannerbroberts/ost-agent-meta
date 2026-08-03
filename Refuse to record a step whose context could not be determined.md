---
type: Solution
source: 'agent:ideation-2026-08-03'
created: '2026-08-03'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

Invert the goal. The stated cost here is not that context is missing — it is that **the record looks complete**, so a failure that cannot be reproduced also cannot be dismissed. Fix the looking-complete part: if the recorder cannot establish where a step ran, it declines to write a normal failure record and writes an explicitly incomplete one instead, or nothing at all.

**The trade it makes:** it is the cheapest of the three by a wide margin and needs no new capture machinery — it is a precondition, not an instrument. It also fails safe in the direction this vault already leans (a check with an empty subject is a failure, not a pass). The price is that it throws away information: a failure with unknown context is still a signal that something broke, and refusing to record it loses that.

**How it differs from its siblings.** The other two make the record *better*. This one makes the record *honest about being bad*, which is a different bet: that the operator's real loss is misplaced trust rather than missing detail. If most unreproducible records turn out to be rare, this is the right answer and the other two are over-built; if they are common, this deletes a lot of signal to fix a labelling problem.

**Middle version worth considering:** record it, but mark it `context-unknown` so it is excluded from any count that implies reproducibility, and surface it as a hygiene issue rather than a build failure.

Distinguishing assumption: that the recorder can reliably tell when it does *not* know the context. If it cannot, this refuses honest records and admits dishonest ones — strictly worse than doing nothing.
