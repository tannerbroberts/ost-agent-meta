---
type: Solution
status: shipped
source: 'INBOX:2026-08-11-founder-vision-restatement.md'
created: '2026-08-11'
evidence: assertion
---
#Solution #compression #unvalidated #evidence/assertion
[[The fields a verdict reads can be declared ahead of time and checked mechanically, with no model in the loop]]

Give compression a fitness function before giving it more machinery. Every bounded surface in the product (rollup, next-work excerpts, briefing, capped lists) exists to serve a downstream decision, and each decision reads specific things from the bounded form. This solution makes that explicit: a registry of compression surfaces — like the sense census in src/loop/senses.ts, but for outputs instead of inputs — where each surface declares the decision it serves and the fields that decision reads, plus a harness that mechanically verifies the bounded output preserves those fields for arbitrary inputs. Model-free, so it runs in CI.

This is deliberately the first increment of the generic compression system, because it is the piece that turns every subsequent sense from a guess into a gradient: with a fidelity measure in place, any new distillation can be scored the moment it is written, instead of tuned by waiting for the next injury. The eye evolved fast because every intermediate form paid off measurably; this is the measure.

## History
- 2026-08-11 status: (none) → shipped — Built and merged to main as OST-Agent PR #108 (commit 5baac77), 2026-08-11. src/compression/registry.ts registers all 30 bounded surfaces (41 cap constants, 22 modules) with decision-fields contracts; test/compression/fidelity-contract.test.ts is the instrument — census (new caps fail the build unregistered), name-pinned ratchets on the 16 silent clips and 26 declaration-only contracts, behavioral drives on the four core surfaces. Observed red before green on this node's assumption test; the red caught a real store-normalization subtlety. Shipped says built, not worth it — the threshold verdict remains a human's ost-agent result.
