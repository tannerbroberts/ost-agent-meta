---
type: AssumptionTest
status: unvalidated
source: >-
  founder-directive:2026-07-24 — compute-only actionability, stated in session
  as first operator
created: '2026-07-25'
evidence: assertion
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption (viability):** an unattended loop stays useful and affordable — it pages rarely, doesn't grind tokens on no-ops, and never crosses a hard gate on its own.

**Method:** schedule the loop for two weeks. Mechanically count from the usage trace and run journals: pages sent, passes with zero structural output, tokens/compute consumed, gate approaches. Requires the exit-0 defect fixed first (the loop must be able to signal its own failure).

**Pre-committed threshold:** <= 1 page/week, >= 1 genuinely useful unprompted output/week (operator's judgment), grind passes < 50% (the twenty-passes baseline was 43% no-op WITH governance), zero gate violations, spend within the protected budget. Grind >= 50% means idle-down must ship before scheduling does.

**Decides:** whether set-and-forget is real for this product's first real operator, with numbers.

*Proposed by the agent — verdicts recorded only by a human via ost-agent result.*
