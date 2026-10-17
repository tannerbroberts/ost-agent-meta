---
type: AssumptionTest
source: 'agent-ideation:2026-10-17-unattended-sweep'
created: '2026-10-17'
evidence: assertion
lane: humans-required
threshold: >-
  no more than 1 of the 10 records has a same-id retry the operator says they
  would still have investigated
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Lane: humans-required.**

**Design.** Take ten real records from this vault's evidence store that contain at least one retry. Hand-annotate each one with the split this candidate would print, using the raw session file to check ids, as was done for `TRANSCRIPT:8275c757-fcf0-46d1-9d35-bfab1fdd33f9`. Mix in records that have only new-id retries, so the label is not the same every time. Show the operator the annotated records with no explanation beyond the label itself. For each record, ask: would you still have opened the session to find out what went wrong?

**Why it is small.** Ten records, an hour of preparation, about fifteen minutes of the operator's time, and no code.

**What it will not cover.** Whether an unattended pass, rather than the operator, discounts the label. That is a separate reader and needs its own check once the label exists. A careful operator reading ten records in one sitting is also the most attentive this reader will ever be. A pass would also need to know this test exists.

A person outside the building is the measurement here: The operator is the reader this label is for, and whether they act on it is a judgement only they can report.
