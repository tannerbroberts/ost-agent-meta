---
type: Solution
source: 'INBOX:2026-08-11-founder-vision-restatement.md'
created: '2026-08-11'
evidence: assertion
---
#Solution #compression #unvalidated #evidence/assertion

Give compression a fitness function before giving it more machinery. Every bounded surface in the product (rollup, next-work excerpts, briefing, capped lists) exists to serve a downstream decision, and each decision reads specific things from the bounded form. This solution makes that explicit: a registry of compression surfaces — like the sense census in src/loop/senses.ts, but for outputs instead of inputs — where each surface declares the decision it serves and the fields that decision reads, plus a harness that mechanically verifies the bounded output preserves those fields for arbitrary inputs. Model-free, so it runs in CI.

This is deliberately the first increment of the generic compression system, because it is the piece that turns every subsequent sense from a guess into a gradient: with a fidelity measure in place, any new distillation can be scored the moment it is written, instead of tuned by waiting for the next injury. The eye evolved fast because every intermediate form paid off measurably; this is the measure.
