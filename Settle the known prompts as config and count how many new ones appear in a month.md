---
type: AssumptionTest
status: unvalidated
created: '2026-08-03'
evidence: assertion
threshold: At most 2 previously unseen prompts stop a run in the month.
authorship: machine
---
#AssumptionTest #unvalidated #evidence/assertion

The assumption is that the set of prompts is small and stable. It must be maintained — a new tool in the chain brings a new prompt nobody has settled — so the question is the arrival rate.

**Risk category: feasibility.**

**Design.** Settle every prompt observable in the harvested transcripts as committed configuration. Then run normally for a month and count how many previously unseen prompts stop a run. Record each one and whether it had a stable right answer.

**Why it is small.** The initial settling is a handful of config lines, and the measurement is a count of stalls over four weeks.

**What it will not cover.** A month during which the tool chain happens not to change will understate the rate. Noting whether any new tool was introduced during the month is what makes the number readable.

## 2026-09-02 unattended sweep — examined for an instrument, and it cannot take one

Recorded here so no future pass re-derives it. This test was one of the four remaining genuinely-unexamined entries named in the residue on "The biggest queue on my report is one the surface reading it to me has no tool to clear".

**Verdict: not repo-answerable, and the buildable half is not the half this test measures.** The threshold is "At most 2 previously unseen prompts stop a run in the month" — the measured quantity is an arrival rate over four weeks of real runs. Settling every prompt observable in the harvested transcripts as committed configuration is ordinary work a spec could cover; this test does not measure that. It measures what arrives afterwards, and its own "what it will not cover" paragraph makes the count unreadable without a person noting whether any new tool entered the chain during the month. No exit code from this product's vitest suite spans wall-clock, and none can observe a tool chain the repository does not contain.

**What the repair is, and why this pass cannot make it.** A person is the measurement here, and the frontmatter carries no lane saying so, which is why this test sits in neither the ask queue nor any labelled count. `ost_flag_humans_required` is withheld from the unattended surface by design, so the fix is one `ost-agent lane --set` naming this test humans-required.

_Nothing was executed, no instrument set, no lane set, no rung moved, no status changed. Read first-party from disk during the 2026-09-02 unattended sweep._
