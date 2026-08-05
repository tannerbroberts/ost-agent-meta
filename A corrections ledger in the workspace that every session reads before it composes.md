---
type: Solution
created: '2026-08-05'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion

**The mechanism: give the correction a carrier.** When a guard refuses a call, the refusal is appended to a durable per-workspace ledger — what was attempted, what it was refused for, and the permitted form. A session reads that ledger before it composes anything, so the seventh occurrence of `sleep 45 && gh pr checks` never gets written, because the session already knows how that ends.

**Why this shape.** It is the smallest change that makes the guard stop being the only memory in the system. Nothing about the refusal logic changes, nothing about the tool surface changes; the message simply stops evaporating when the session does. The evidence supports it directly — the same refusal on seven sessions across four days is not a reasoning failure, it is a storage failure, and storage is cheap.

**Compared to its siblings.** The only one of the three that carries *reasons* rather than just outcomes, which matters because refusals are not all alike and a ledger entry can say what the permitted form was. It is also the only one that works for corrections nobody has yet turned into a constraint — a guard can refuse something long before anyone has decided how to make it unexpressible. Against that, it is the one that depends on the reader actually reading: it adds a document to be consulted, and the whole premise of the problem is an agent reaching for a reflex rather than consulting anything.

**What would make this the wrong pick.** A ledger that grows without bound becomes a thing nobody reads, which is the exact failure it was built to fix, one level up. It also puts the correction in the same place as the reflex — inside the composer's judgement — and a reflex that survived seven explicit refusals may well survive a note about them.

⚠️ Unvalidated. Agent-ideated on 2026-08-05 from machine-captured session friction, by the agent whose own repeated failure the evidence records — which is a reason to discount its confidence that a note to itself would have helped.
