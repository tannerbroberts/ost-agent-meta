---
type: Solution
source: 'TRANSCRIPT:081b644b-e90a-472e-9b3d-15562a030a94'
created: '2026-08-06'
evidence: assertion
---
#Solution #unvalidated #evidence/assertion
[[A pass can know which tools it needs before it makes its first call]]

**The idea.** A pass names its required tool set as a precondition and checks it against what is actually callable before the first unit of work. A missing tool stops the pass at second zero, with the name of what is absent, rather than surfacing forty calls in as a denial the agent then works around.

**Why this shape.** Observed first-party on 2026-08-06: an unattended sweep instructed to flag human-only tests found `ost_flag_humans_required` was not granted on that surface, discovered at the moment it tried to use it. The same sweep found `Bash` absent and `ost_read_repo` ungranted. Each was a mid-pass discovery, and each silently changed what the pass could deliver — the sweep continued and produced a smaller result that looks from the outside like a complete one.

**How it differs from its siblings.** This one fails loudly and early, and buys nothing else. It does not record the gap for later ("Every refusal a surface returns is recorded as tree evidence") and it does not let the operator pin an intended surface ("One surface profile per pass, pinned in config"). It is the cheapest of the three and the only one that prevents a degraded pass rather than explaining one afterwards.

**Where it fails.** A pass that legitimately adapts to a smaller surface — an unattended sweep that genuinely should not hold repo sight — would be refused by a naive requirement list. The precondition has to distinguish *needed* from *would use*, and getting that split wrong makes the check either useless or an obstacle.

⚠️ Unvalidated. Agent-ideated, from friction the ideating agent hit in the same pass.
