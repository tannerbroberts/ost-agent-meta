---
type: AssumptionTest
status: unvalidated
source: >-
  founder-directive:2026-07-24 — compute-only actionability, stated in session
  as first operator
created: '2026-07-25'
evidence: assertion
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

**Assumption (viability):** an unattended loop stays useful and affordable — it pages rarely, doesn't grind tokens on no-ops, and never crosses a hard gate on its own.

**Method:** schedule the loop for two weeks. Mechanically count from the usage trace and run journals: pages sent, passes with zero structural output, tokens/compute consumed, gate approaches. Requires the exit-0 defect fixed first (the loop must be able to signal its own failure).

**Pre-committed threshold:** <= 1 page/week, >= 1 genuinely useful unprompted output/week (operator's judgment), grind passes < 50% (the twenty-passes baseline was 43% no-op WITH governance), zero gate violations, spend within the protected budget. Grind >= 50% means idle-down must ship before scheduling does.

**Decides:** whether set-and-forget is real for this product's first real operator, with numbers.

*Proposed by the agent — verdicts recorded only by a human via ost-agent result.*

## 2026-09-02 unattended sweep — examined for an instrument, and it cannot take one

Recorded here so no future pass re-derives it. This test was the last of the four genuinely-unexamined entries named in the residue on "The biggest queue on my report is one the surface reading it to me has no tool to clear", and it is the most instrumentable-looking of the four, which is why it is worth stating exactly where it stops.

**Verdict: not repo-answerable, though three of its five bars are.** The pre-committed threshold is a conjunction: `<= 1 page/week`, `>= 1 genuinely useful unprompted output/week (operator's judgment)`, `grind passes < 50%`, `zero gate violations`, `spend within the protected budget`. Pages, grind share, gate approaches and spend are all counts over artefacts this repository already writes — the usage trace and the run journals — and a spec could compute every one of them from a fixture. The second bar cannot be computed from anything: it names the operator's judgement explicitly, and one genuinely useful unprompted output is exactly the quantity no exit code reaches. A conjunction is only as instrumentable as its weakest term, so a command here would report on four bars and be silent on the one that decides whether set-and-forget is real.

**And the wall-clock half is not incidental.** The method is "schedule the loop for two weeks" against this product's first real operator. A fixture can replay two weeks of journals; it cannot produce two weeks of a real operator being paged, which is the thing being measured.

**A prerequisite this node states and nothing enforces.** The method requires "the exit-0 defect fixed first (the loop must be able to signal its own failure)" — running the count before that lands produces numbers nobody can interpret. No `prerequisite` is recorded on the frontmatter, so this test does not appear in `blockedOnPrerequisite` and reads as merely unlabelled. Declaring a prerequisite is a human's `ost-agent prerequisite` and no tool on this surface can do it.

**What the repair is, and why this pass cannot make it.** The operator is irreducibly one of the measurements. `ost_flag_humans_required` is withheld from the unattended surface by design; the fix is one `ost-agent lane --set` naming this test humans-required, and optionally one `ost-agent prerequisite` recording the exit-0 dependency above.

_Nothing was executed, no instrument set, no lane set, no rung moved, no status changed. Read first-party from disk during the 2026-09-02 unattended sweep._
