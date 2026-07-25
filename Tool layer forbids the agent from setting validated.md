---
type: Solution
status: unvalidated
source: 'INBOX:2026-07-22-dogfooding-idea.md'
created: '2026-07-25'
---
#Solution #ported-from-ost-agent-vault
[[Test humans can promote while the agent is blocked from validating]]

**Candidate solution (unvalidated).** Enforce in the tool layer that everything the agent originates enters as `unvalidated`, and that promoting a node to `validated` requires human-provided real-world evidence recorded in the note. The agent structurally cannot certify its own ideas.

**Approach:** *make self-validation impossible by construction*.

**Contrast with siblings:** unlike the independent judge (adds review) this removes the capability to self-approve; unlike the outcome gate it governs individual nodes, not the top-level outcome.

_Addresses: "Worry the agent is grading its own homework". Unvalidated — human to review._
